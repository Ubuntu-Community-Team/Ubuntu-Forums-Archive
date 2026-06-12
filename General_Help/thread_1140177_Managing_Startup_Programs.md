---
title: "Managing Startup Programs"
date: 2009-04-27
forum: General Help
---

### Post by Ubermensch83 on 2009-04-27
Sorry in advance for the noob question, but how do I manage my startup programs? I would like to set Rainlendar 2 to automatically run on the desktop when the computer starts up but I'm a little confused by the startup applications menu

Thanks in advance

/ex windows user

---

### Post by cwbar_1 on 2009-04-27
Go to System >Preferences > Startup Applications. Press add. Type in the name of your application in the first box. Browse for the application's run file (unless you know the location) and add a comment (or not) in the last box.

---

### Post by kolisikepu on 2009-04-27
Go to;
Systems > Preferences > Startup Applications.

Normally, you'd put in a Name of the application, a comment for the application and then the 'Command' for to start the application.

Example for a command.  eg; to start Compiz Fusion for me, I have Command 'fusion-icon' to start the application.
eg;  skype is a command to startup 'Skype'.

I hope this helps.

---

### Post by Ubermensch83 on 2009-04-27
Ok, where would one normally find the run file location. Thats what my original question was I guess, I don't know where programs are installed to. 

Sorry, Linux noob here.

---

### Post by cwbar_1 on 2009-04-27
Have you installed your program yet?  If you have: Places > Search for Files, and type in the name of your program.  (make sure you tic the box and tell search to look in "file system") It will give you the location of all your files associated with the program.  You will be looking for a "bin" file.  {most likely location; /usr/bin or /opt}

---

### Post by gallilaw on 2009-07-08
What do we do if the "System > Preferences" menu does not contain a "Startup Applications" entry?

---

### Post by michy99 on 2009-07-08
In versions before Jaunty, startup programs are under 'Sessions'

---

### Post by Jebtrix on 2009-07-08
Just a small tip, I usually just find the program shortcut in Applications, Right-Click hit "Add this Launcher to Desktop", then you can Right-Click on launcher icon on your Desktop and view its properties to find its command. The reason I like this better is some apps use command line parameters.

---

