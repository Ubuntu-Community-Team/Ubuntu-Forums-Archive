---
title: "Can't add icons (programs) to Panel 1, in XFCE..."
date: 2008-11-20
forum: Desktop Environments
---

### Post by JoeBearPA on 2008-11-20
Hello,

I am using XFCE, on my laptop (I am a new convert to Ubuntu\Linux).  I am having an issue adding icons and programs to Panel 1, so I can launch them without using the main, right click, menu.  I can't drag and drop icons, I cannot add using the dialog box,and I cannot access the "Launcher" option as it is grayed out.

I have considered that it might be a problem with privileges, and have tried the instructions for activating access to the 'Root' account (which has not worked).  Also, 'sudo' is not usable, as I can't access changes to 'xfce-panel' from the text based 'terminal', I can only start the panel up, to which I am being told "xfce-panel is already running".  I CAN add new applets (clock etc.)

I do not know enough about the paths of executable files in Linux, to direct the icon to the proper file, to execute what I want to start from 'Panel'.

Can ANYONE help me?

Feel free to also contact me at [email]epbear@gmail.com[/email]

Joe

---

### Post by mikewhatever on 2008-11-20
> **JoeBearPA said:**
> 
I do not know enough about the paths of executable files in Linux, to direct the icon to the proper file, to execute what I want to start from 'Panel'.


I'm not very familiar with xfce, so will only try to help with this part. Most of the programs installed from the repositories have executables in /usr/bin. For example, if you wanted to add Totem, the path would be /usr/bin/totem, or /usr/bin/vlc for VLC.

It looks like your account doesn't have sufficient privileges to make the changes you want. Can you clarify why you can't use sudo?

---

### Post by JoeBearPA on 2008-11-20
Well,

It isn't that I cannot USE it... it is possible I am newbie enough, that I don't know how.  I can use sudo to start the panel app, but it will report that the panel program is already in use.  This is a configuration change TO the program I am trying to make.  I did try to activate the root account (by following instruction found in the forums) but had no luck in doing so.  I figured I could have the proper privleges that way.

Is this any help?

Thanks!

Joe

---

