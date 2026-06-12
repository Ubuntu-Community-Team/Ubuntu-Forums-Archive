---
title: "Changing Firefox, KMail defaults"
date: 2005-08-24
forum: Desktop Environments
---

### Post by dmanderzen on 2005-08-24
I've switched from Evolution to KMail for my email.  How do I get Firefox to open a KMail, not an Evolution, window when I click an "email to" link on a webpage?  And how do I get KMail to open Firefox, not Konqueror, when I click a link in an email?

---

### Post by incinerator on 2005-08-28
I can only answer the second question for you, as I haven't figured out an answer to the first question, either.

To enable firefox as default webbrowser in kde, do the following:
Click the "System" button in the control panel, that is the one right next to the K-Menu button. A pop-up menu appears. Use it to go Settings. A new konqueror window appears. In that window go to KDE-components -> component selection -> web browser. Activate the second option, enter **mozilla-firefox** in the text field.

---

### Post by plb on 2005-08-28
goto about:config in firefox and change all relevent mail settings  ;-)

---

### Post by incinerator on 2005-08-28
Google saved the day again, I found a solution for the mailto links:

Start firefox, in the url field type
about:config and press enter
In the main browser window a huge list with config settings appears. Make sure that the config item "network.protocol-handler.external.mailto" has its value set to "true".
Then do a right-click anywhere in the config item list to "add" a new "string". The string's name should be made "network.protocol-handler.app.mailto" and its value "kmail" (both without the double quotes btw).

Solution works fine for me, but I haven't got evolution installed, ymmv.

---

### Post by incinerator on 2005-08-28
[QUOTE=plb]goto about:config in firefox and change all relevent mail settings  ;-)[/QUOTE]

goto [http://www.openbsd.org/](http://www.openbsd.org/) and install an operating system that fits your attitude.

---

### Post by plb on 2005-08-28
[QUOTE=incinerator]goto [http://www.openbsd.org/](http://www.openbsd.org/) and install an operating system that fits your attitude.[/QUOTE]

attitude? I simply pointed him in the right direction as I wasn't on my linux box atm and only had access to IE I couldn't remember the actual mail setting

---

