Download Link: https://assignmentchef.com/product/solved-cmsc216-project-2
<br>
In this project you will implement a document manager program. The program will allow us to add paragraphs, lines to paragraphs, to replace text and edit a document. Notice that the next project relies on the code you will implement for this project.

To practice C structures and string manipulation.

<h2>1.1        Good Faith Attempt</h2>

Remember that you need to satisfy the good faith attempt for every project in order to pass the class (see syllabus). The good faith attempt information for this project (e.g., requirements and deadline) will be posted on the class web page later on.

<h2>1.2        Obtain the project files</h2>

To obtain the project files copy the folder project2 available in the 216 public directory to your 216 directory.

We have supplied three files for your use in this project: (a) document.h, which provides prototypes for the functions you must implement; (b) .submit, which is necessary to submit the project to the submit server; and a (c) Makefile, which will help you work on your project more efficiently.

<h1>2          Specifications</h1>

<h2>2.1        Use of a Makefile</h2>

Makefiles will be covered more in-depth in class, but instead of issuing gcc commands every time you want to recompile your program, you can simply execute “make” from the command line. Make recompiles the public tests provided. Without the makefile you can compile a public tests by compiling the test and document.c. For example, gcc public01.c document.c.

<h2>2.2        Functions</h2>

You must implement the functions described below. Notice that for 0 and -1 you should use the macros SUCCESS and FAILURE defined in document.h.

<ol>

 <li>int init_document(Document *doc, const char *name)</li>

</ol>

Initializes the document to be empty. An empty document is one with 0 paragraphs. The function will initialize the document’s name based on the provided parameter value. The function will return FAILURE if doc is NULL, name is NULL, or if the length of the name provided exceeds MAX_STR_SIZE; otherwise the function will return SUCCESS.

<ol start="2">

 <li>int reset_document(Document *doc)</li>

</ol>

Sets the number of paragraphs to 0. The function returns FAILURE if doc is NULL; otherwise the function will return SUCCESS.

<ol start="3">

 <li>int print_document(Document *doc)</li>

</ol>

Prints the document’s name, number of paragraphs, followed by the paragraphs. Each paragraph is separated by a blank line. The following illustrates an example of printing a document whose title is ”Exercise Description” and has two paragraphs:

Document name: “Exercise Description”

Number of Paragraphs: 2

First Paragraph, First line

First Paragraph, Second line

First Paragraph, Third line

Second Paragraph, First line

Second Paragraph, Second line

Second Paragraph, Third line

The function returns FAILURE if doc is NULL; otherwise the function will return SUCCESS.

<ol start="4">

 <li>int add_paragraph_after(Document *doc, int paragraph_number)</li>

</ol>

Adds a paragraph after the specified paragraph number. Paragraph numbers start at 1. If paragraph number is 0 the paragraph will be added at the beginning of the document. The function will return FAILURE if doc is NULL, the document has the maximum number of paragraphs allowed (MAX PARAGRAPHS) or if the paragraph number is larger than the number of paragraphs available; otherwise, the function will return SUCCESS.

<ol start="5">

 <li>int add_line_after(Document *doc, int paragraph_number, int line_number, const char *new_line)</li>

</ol>

Adds a new line after the line with the specified line number. Line numbers start at 1. If the line number is 0, the line will be added at the beginning of the paragraph. The function will return FAILURE if doc is NULL, the paragraph number exceeds the number of paragraphs available, the paragraph already has the maximum number of lines allowed, the line number is larger than the available number of lines or if new line is NULL; otherwise, the function will return SUCCESS.

<ol start="6">

 <li>int get_number_lines_paragraph(Document *doc, int paragraph_number, int *number_of_lines)</li>

</ol>

Returns the number of lines in a paragraph using the number of lines out parameter. The function will return FAILURE if doc or number of lines is NULL or if the paragraph number is larger than the number of paragraphs available; otherwise, the function will return SUCCESS.

<ol start="7">

 <li>int append_line(Document *doc, int paragraph_number, const char *new_line)</li>

</ol>

Appends a line to the specified paragraph. The conditions that make the add line after fail apply to this function as well. The function will return SUCCESS if the line is appended.

<ol start="8">

 <li>int remove_line(Document *doc, int paragraph_number, int line_number)</li>

</ol>

Removes the specified line from the paragraph. The function will return FAILURE if doc is NULL, the paragraph number exceeds the number of paragraphs available or line number is larger than the number of lines in the paragraph; otherwise the function will return SUCCESS.

<ol start="9">

 <li>int load_document(Document *doc, char data[][MAX_STR_SIZE + 1], int data_lines)</li>

</ol>

The function will add the first data lines number of lines from the data array to the document. An empty string in the array will create a new paragraph. Notice that by default the function will create the first paragraph. You can assume that if data lines is different than 0, the appropriate number of lines will be present in the data array. The function will return FAILURE if doc is NULL, data is NULL or data lines is 0; otherwise the function will return SUCCESS.

<ol start="10">

 <li>int replace_text(Document *doc, const char *target, const char *replacement)</li>

</ol>

The function will replace the text <strong>target </strong>with the text <strong>replacement </strong>everywhere it appears in the document. You can assume the replacement will not generate a line that exceeds the maximum line length; also you can assume the target will not be the empty string.

The function will return FAILURE if doc, target or replacement are NULL; otherwise the function will return SUCCESS.

<ol start="11">

 <li>int highlight_text(Document *doc, const char *target)</li>

</ol>

The function will highlight the text associated with <strong>target </strong>everywhere it appears in the document by surrounding the text with the strings HIGHLIGHT START STR and HIGHLIGHT END STR (see document.h). You can assume the highlighting will not exceed the maximum line length; also you can assume the target will not be the empty string. The function will return FAILURE if doc or target are NULL; otherwise the function will return SUCCESS.

<ol start="12">

 <li>int remove_text(Document *doc, const char *target)</li>

</ol>

The function will remove the text <strong>target </strong>everywhere it appears in the document. You can assume the target will not be the empty string. The function will return FAILURE if doc or target are NULL; otherwise the function will return SUCCESS.