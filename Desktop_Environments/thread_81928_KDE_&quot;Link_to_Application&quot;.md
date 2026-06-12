---
title: "KDE &quot;Link to Application&quot;"
date: 2005-10-25
forum: Desktop Environments
---

### Post by blubery on 2005-10-25
hello,

i would like to create a link on my desktop to open "snort" but in a TERMINAL. so when i click on this link the command line window comes up and i am ready to begin. How do I do this? I would also or rather move this to my kde taskbar? thanks in advance.

blubery

---

### Post by GeneralZod on 2005-10-25
In "Advanced Options" for your Link to Application, check "Run in Terminal".  You should be able to just drag the shortcut from your desktop onto the application-launch area of the kicker.

HTH,
Simon :)

---

### Post by blubery on 2005-10-25
thanks, however, i need i guess maybe not so much a "link to application" but a "link on my desktop so when i click on it a terminal pops up with say the directory "/etc/snort" just sitting there. so therefore the link does not run any script or exe, it just brings me to that spot so i do not have to cd to it. i know theres not much to cd'ing to that short directory but thats not the point. thanks for taking the time to help me figure this out.

blubery

---

### Post by Staesys on 2005-10-25
Make a link to **konsole** on your desktop. Call it what  you will, but change the work path to **/etc/snort**.

That should do it.

---

### Post by blubery on 2005-10-25
thanks, but when i set the "work path" to /etc/snort and then go to advanced options and check "run in terminal" and "do not close when command exits" when i click on the link the terminal comes up and says some weird message and i am not able to type at all not even the word help like it suggests(cntrl+c does not work on it either), as follows: 

ksystraycmd: No command or window specified
ksystraycmd: Use --help to get a list of available command line options.

thanks

---

### Post by GoldBuggie on 2005-10-25
If I understand your request you want to have a link on the desktop that opens konsole and the current directory will be /etc/snort. To do this right-click on your desktop...choose "Link to application"...in *Application->Command* type the following *konsole --workdir /etc/snort*. Thats it"

---

