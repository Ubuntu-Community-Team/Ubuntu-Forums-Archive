---
title: "KDE on Feisty, shutdown dialog"
date: 2007-04-20
forum: Desktop Environments
---

### Post by polomint on 2007-04-20
I've been having this problem since Feisty herd 4. Basically, having upgraded to feisty, I've lost all the shutdown options, apart from a big log out button. So yesterday I did a clean install of 7.04 final, but the problem is still there. by the way, I installed kde-core over an existing ubuntu installation. I've attached a screenshot of this reduced functionality shutdown dialog. 

I'm sure that this problem has been reported before, with someone suggesting installing KDM. but that doesn't help. Also, I've been using KDE with gdm in edgy and haven't had a single problem, so i'm guessing kdm is not really the issue here...

is there a way to fix this? thanks in advance!

---

### Post by enigmaniac23 on 2007-04-23
Sorry to reply with no fix, but I am having the same exact problem.  I was on Ubuntu 6.10 and installed KDE on top of Ubuntu.  Then I upgraded to Ubuntu 7.04 and I have now lost options on the logout dialog.  The only thing I have is a big logout button.  Has anyone found a fix for this yet?

---

### Post by dao on 2007-04-24
Have a look at this
[http://ubuntuforums.org/showthread.php?t=410486](http://ubuntuforums.org/showthread.php?t=410486)

You can install KDM from your package manager.

Just follow the instructions from the post.

---

### Post by enigmaniac23 on 2007-04-25
Thanks!  That did it.  All I had to do was switch the window manager from GDM to KDM and that took care of the buttons showing at logout.  

sudo dpkg-reconfigure kdm

and then choose kdm and reboot.

Thanks again.

---

### Post by polomint on 2007-04-26
hey all, 

I tried the "sudo dpkg-reconfigure kdm" command, and it worked! 
my bad - guess i didn't configure it after the installation. 

However, I've notice that the shutdown and restart buttons are now missing from Gnome!! does this mean I can only use KDM with KDE and GDM with Gnome.     I used  both desktops for my work!

I hate it when you have to chose one application over the other. imho this problem _must_ be fixed, so whatever login manager people use should work with all desktop enviroments anyway, that's how it used to be back in good old edgy days :) ...

---

### Post by intotheabyss on 2007-04-30
I was having this same problem with gnome after upgrading to Feisty. However I accidentally found out what was causing it and was able to correct it without switching from GDM to KDM or anything like that. It seems like there is a bug of sorts in the login window preferences applet. 

So if you're not seeing your shutdown and restart options you may want to try this before doing anything fancy.

From the main menu select:
**System->Administration->Login Window**

Select the **Local** tab

Make sure the **Show Actions Menu** checkbox is **checked**.

Don't know why, but toggling this option will show/hide these options on the shutdown dialog as well as in the login screen.

Hope this helps someone

---

