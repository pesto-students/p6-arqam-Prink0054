                    Assignments

## When a user enters an URL in the browser, how does the browser fetch the desired
result ?

1. You type maps.google.com into the address bar of your browser.

2. The browser checks the cache for a DNS record to find the corresponding IP address of maps.google.com.

3. If the requested URL is not in the cache, ISP’s DNS server initiates a DNS query to find the IP address of the server that hosts maps.google.com.

4. The browser initiates a TCP connection with the server.

5. The browser sends an HTTP request to the webserver.

6. The server handles the request and sends back a response.

7. The server sends out an HTTP response.


8. The browser displays the HTML content (for HTML responses, which is the most common).
![Basic Communication Diagram](	https://www.freecodecamp.org/news/content/images/2019/06/dns_resolve.png)


## What is the main functionality of the browser?
- Web browser functions are to provide the resources or information to the user when asked by them.

- It processes the user inputs in the form of URL like http://www.google.com in the browser and allows the access to that page.

- URL is used to identify the resources and fetch them from the server and displays it to the client.

- It allows the user to interact with the web pages and dynamic content like surveys, forms, etc.

- It also allows the user to navigate through the complete web page and see its source code in the HTML format.

- It provides security to the data and the resources that are available on the web that is by using the secure methods.


## What are High Level Components of a browser?
The browser's main components are:
- The user interface: this includes the address bar, back/forward button, bookmarking menu, etc. Every part of the browser display except the window where you see the requested page.
- The browser engine: marshals actions between the UI and the rendering engine.
- The rendering engine: responsible for displaying requested content. For example if the requested content is HTML, the rendering engine parses HTML and CSS, and displays the parsed content on the screen.
- Networking: for network calls such as HTTP requests, using different implementations for different platform behind a platform-independent interface.
- UI backend: used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. Underneath it uses operating system user interface methods.
- JavaScript interpreter. Used to parse and execute JavaScript code.
- Data storage. This is a persistence layer. The browser may need to save all sorts of data locally, such as cookies. Browsers also support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem.

![Basic Communication Diagram](https://web-dev.imgix.net/image/T4FyVKpzu4WKF1kBNvXepbi08t52/PgPX6ZMyKSwF6kB8zIhB.png?auto=format)

## What is rendering Engine and its use?
A rendering engine is software that draws text and images on the screen. The engine draws structured text from a document (often HTML), and formats it properly based on the given style declarations (often given in CSS). Examples of layout engines: Blink, Gecko, EdgeHTML, WebKit.

## Parsers and Processors (HTML, CSS, etc)


HTMLCSS is a lightweight HTML/CSS parser written in C that allows applications to prepare a HTML document for rendering or conversion. HTMLCSS is extremely portable and only requires a C99 compiler like GCC, Clang, Visual C, etc. HTMLCSS is also extremely memory efficient, utilizing a shared string pool and smart CSS cache to minimize the size of a HTML document in memory.

## what is script processor?
The script processor executes Javascript code to process an event. The processor uses a pure Go implementation of ECMAScript 5.1 and has no external dependencies. This can be useful in situations where one of the other processors doesn’t provide the functionality you need to filter events.


## Tree construction

To construct the render tree, the browser roughly does the following:
- Starting at the root of the DOM tree, traverse each visible node.
- Some nodes are not visible (for example, script tags, meta tags, and so on), and are omitted since they are not reflected in the rendered output.
- Some nodes are hidden via CSS and are also omitted from the render tree; for example, the span node---in the example above---is missing from the render tree because we have an explicit rule that sets the "display: none" property on it.
- For each visible node, find the appropriate matching CSSOM rules and apply them.
- Emit visible nodes with content and their computed styles.

## Order of execution of scripts

The order of execution is as follows:
1. Before business rules: Scripts configured to execute before the database operation with an order less than 1000.
2. Before engines. The following are not executed in any specific order:
- Approval engine (for task and sys_approval_approver tables)
- Assignment rules engine (for task tables)
- Data policy engine
- Escalation engine
- Field normalization engine
- Role engine - keeps role changes in sync with sys_user_has_role table (for sys_user, sys_user_group, sys_user_grmember, and sys_user_role tables)
- Execution plan engine (for task tables)
- Update version engine - creates version entry when sys_update_xml entry is written (for sys_update_xml table)
- Data lookup engine inserts or updates
- Workflow engine (for default workflows)
3. Before business rules: Scripts configured to execute before the database operation with an order greater than or equal to 1000.
4. The data base operation (insert, update, delete).
5.	After business rules: Scripts configured to execute after the database operation with an order less than 1000.
6.	After engines. The following are not executed in any specific order:
- Label engine
- Listener engine
- Table notifications engine
- Role engine - keeps role changes in sync with sys_user_has_role table (for sys_user, sys_user_group, sys_user_grmember and sys_user_role tables)
- Text indexing engine
- Update sync engine
- Workflow engine (for deferred workflows)
- Trigger engine (for all Flow Designer flows)
7.	Email notifications. The following are executed based on the weight of the notification record:
- Notifications sent on an insert, update, or delete
- Event-based notifications
8.	After business rules (Only active records). Scripts configured to execute after the database operation with an order greater than or equal to 1000.



## Layout, and Paint
- The DOM and CSSOM trees are combined to form the render tree.
- Render tree contains only the nodes required to render the page.
- Layout computes the exact position and size of each object.
- Paint is the last step that takes in the final render tree and renders the pixels to the screen.

## To construct the render tree, the browser roughly does the following:
- Starting at the root of the DOM tree, traverse each visible node.
- Some nodes are not visible (for example, script tags, meta tags, and so on), and are omitted since they are not reflected in the rendered output.
- Some nodes are hidden via CSS and are also omitted from the render tree; for example, the span node---in the example above---is missing from the render tree because we have an explicit rule that sets the "display: none" property on it.
- For each visible node, find the appropriate matching CSSOM rules and apply them.
- Emit visible nodes with content and their computed styles.