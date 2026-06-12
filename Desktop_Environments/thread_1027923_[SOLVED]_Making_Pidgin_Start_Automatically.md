---
title: "[SOLVED] Making Pidgin Start Automatically?"
date: 2009-01-01
forum: Desktop Environments
---

### Post by vonsperb on 2009-01-01
How can I have Pidgin start automatically when I log in? I'm sure there are many ways to accomplish this, but I'd like to know which way is the 'clean' way of doing this... Thanks!

---

### Post by jpmelos on 2009-01-01
Go to:

System > Preferences > Sessions > Startup Programs

Click "+ Add"

Add Pidgin:

Name: Pidgin
Command: pidgin

Press Save

You're done! :D

---

### Post by keithld on 2009-01-01
I saw a Quick & Dirty way to do it but I can't find the link...

Basically you go to Applications> Internet then right click on Pidgin then click "Add this Launcher to Panel" then Right click on the Pidgen Panel Icon and view the properties then copy the text that is in the "Command Field"...

Next go to System> Preferences> Sessions and click on "Startup Items" and then add a new item... Name the item, and paste the command info into the "Command Field" then give it a comment (Description) and it should run the program when you start Ubuntu...

Now you can Right Click on Pidgen on the Panel and remove it...

---

### Post by vonsperb on 2009-01-01
Works beautifully. Thanks!

---

### Post by keithld on 2009-01-01
**vonsperb** if you later on run into some that won't run at Startup try the method I posted...

That's what I had to do for Songbird to get it working...

---

### Post by vonsperb on 2009-01-01
OK, thanks a lot!

---

### Post by keithld on 2009-01-01
Your Welcome...  :D

I'm not sure why but just entering "Songbird" into the command line did not work so I had to find the path also, i.e. "/opt/Songbird/songbird"  thus the reason for adding it to the panel to get that info...

If you have your answer you can go back and edit your original post and then click on: "Thread Tools" and choose the last option "Mark this thread as solved"...

This way others will not look at the post and go onto others that are still unsolved...


Cheers

---

### Post by vonsperb on 2009-01-02
Hmmm, that's probably because Songbird is not on your path (since it's under /opt) and so you have to put the full path to launch it. Thanks for your help and for the forum tips!

---

### Post by mahrizal on 2011-05-04
great thankss

---

