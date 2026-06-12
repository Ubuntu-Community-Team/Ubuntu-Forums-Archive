---
title: "kmail config question"
date: 2007-09-19
forum: Desktop Environments
---

### Post by onegear on 2007-09-19
hello all,

i'm using kmail for my email and have a , hopefully, simple configuration question.  when i repy to an email, is it possible to configure kmail to start at the top of the email versus the end of the email?  i would like to reply to email messages from the top and not the bottom.  i know that i can simply "click" at the top of the email to move the cursor up there but i would really like to configure it to do this by default.

thanks.

---

### Post by theTheme on 2008-01-05
Hey onegear,

to change kmails default to reply at the top of a message here's what you have to do:
Open Kmail -> Click on Settings -> Configure Kmail ->

click on the templates tab -> then click the reply to sender tab below the box with the code in it

Then, erase the code that is inside and replace it with this:

%CURSOR

%REM="Default reply template"%-
On %ODATEEN %OTIMELONGEN you wrote:
%QUOTE

This will give you one space before the reply, if you want more line breaks add more whitespace after %cursor

You can also use this formula for the other templates.

---

