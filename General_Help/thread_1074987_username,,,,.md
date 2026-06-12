---
title: "username,,,,"
date: 2009-02-19
forum: General Help
---

### Post by Nugget_Mon on 2009-02-19
Just curious,
What are the four commas after the user name for? The syntax is usually FirstName Lastname,,,,(username).

Thanks
Mon


SOLVED
TYVM

---

### Post by Joeb454 on 2009-02-19
Where are you referring to? :confused:

---

### Post by Nugget_Mon on 2009-02-19
System>Administration>Users and Groups>unlock

It also shows up if you are in Octave and edit a file.

---

### Post by mb_webguy on 2009-02-20
I don't see that.  Here's a screenshot of my Users and Groups window.  You're saying yours looks different?

---

### Post by calrogman on 2009-02-20
When one hits the "_U_nlock" Button on a dialog such as the Network Settings window and Time and Date window, you get a bar that says "Name,,,(username)", and below that the text box you must type your password into in order to proceed.

See the screen-shot below.

---

### Post by mb_webguy on 2009-02-20
Ooooh...  That's taken from the [/etc/passwd]("http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/files/aixfiles/passwd.htm") file, which stores information about users.  Type "cat /etc/passwd" in the terminal to take a look at this file.  You'll notice that each line includes several colon-separated fields.  What you're seeing are the commas separating empty subfields in the comment field (specifically, I believe, the Office Location, Work Phone, and Home Phone subfields you can specify in Users and Groups).

---

### Post by calrogman on 2009-02-20
Well there we go then!:D

---

