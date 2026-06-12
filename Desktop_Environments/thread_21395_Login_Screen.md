---
title: "Login Screen"
date: 2005-03-22
forum: Desktop Environments
---

### Post by vvu on 2005-03-22
Can someone please tell me how I can change the Login screen background and icons for Kubuntu?  Thanks.

---

### Post by lao_V on 2005-03-22
Have a look at the [kde-look.org]("http://www.kde-look.org") KDM Themes section

---

### Post by vvu on 2005-03-22
That's great; however, could you give me the exact link since I do NOT know what I am looking for.  I am only 2.5 days into Linux.  Not only would I like to change the default login theme but also know more of the configuration files and what and where they are stored.  Sorry, but I am a complete newbie - I don't mind reading, I just don't know what to read.

Thank you.

---

### Post by dermotti on 2005-03-22
go into the kde control panel and play around

---

### Post by vvu on 2005-03-22
Thank you...that's all I needed - System Administration section and Login Manager.   

However, that was piece #2.  Piece #1 was the actual logon screen - any input or resource there?  

Thanks.

---

### Post by lao_V on 2005-03-23
There's not GUI to change the login screen at the moment. You will have to download the file from kde-look and:

 To install:
-unpack archive in $KDEDIR/share/apps/kdm/themes/
-edit your kdmrc-file to:
Theme=$KDEDIR/share/apps/kdm/themes/BlueTheme
UseTheme=true

---

### Post by vvu on 2005-03-23
Sorry Lao... Could you please expand on this...

(1)  Could you tell me where $KDIR/.... is located?  Sorry again, just a couple days into Linux.
(2)  Is this for all user's login?  I hope this is for everyone logging into system.
(3)  Semi related - I suppose when you say $KDIR that the system knows this path or it exists (just like windows as an environmental variable) - how do I print on screen the variables of such and WHERE is this file to modify such paths?

Thanks again. :) 


 To install:
-unpack archive in $KDEDIR/share/apps/kdm/themes/  <-- is this for local user and where is this?
-edit your kdmrc-file to:
Theme=$KDEDIR/share/apps/kdm/themes/BlueTheme  
UseTheme=true

---

### Post by lao_V on 2005-03-23
[QUOTE=vvu]
(1)  Could you tell me where $KDIR/.... is located?  Sorry again, just a couple days into Linux.[/QUOTE]
On your Kubuntu with KDE 3.4 this should be /usr
Copy the downloaded login scheme into this folder. Then search for a file called kdmrc. This should be in /etc/kde3/kdm/ and edit as explained below.

[QUOTE=vvu] (2)  Is this for all user's login?  I hope this is for everyone logging into system. [/QUOTE]
Yes, this will be for all the users

[QUOTE=vvu] (3) Semi related - I suppose when you say $KDIR that the system knows this path or it exists (just like windows as an environmental variable) - how do I print on screen the variables of such and WHERE is this file to modify such paths? [/QUOTE]
If you want to know whether your system has a value for $KDEDIR then type "echo $KDEDIR" in terminal 

Good luck!

 To install:
-unpack archive in $KDEDIR/share/apps/kdm/themes/  <-- is this for local user and where is this?
-edit your kdmrc-file to:
Theme=$KDEDIR/share/apps/kdm/themes/BlueTheme  
UseTheme=true[/QUOTE]

---

