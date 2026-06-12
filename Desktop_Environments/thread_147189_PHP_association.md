---
title: "PHP association"
date: 2006-03-19
forum: Desktop Environments
---

### Post by munwin on 2006-03-19
For some reason, when listing files in Nautilus (2.12.1), some .php files have changed their icon to display as html (and type column says HTML page) - while others remain as php (and type column says PHP script). Even in the same directory. When I try to open (by double clicking), the html type php files, it says 

Cannot open abc.php
The filename "abc.php" indicates that this file is of type "PHP script". The contents of the file indicate that the file is of type "HTML page". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "HTML page", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

So, OK, when I chose Open With (as described), I can open it with Text Editor. But next time I try to double click on the file, same error appears... and it stays as a HTML file.

How can I set these files back to PHP script files in Nautilus ???

Mark.

---

### Post by munwin on 2006-03-19
Worked it out.
The particular files didn't contain any actual PHP code.
They were includes, and consisted of only HTML code (menus).
When I put
<?php
?>
at the start of the files, they open like the other PHP files - in Gedit.

Yay !!!

Mark.

---

