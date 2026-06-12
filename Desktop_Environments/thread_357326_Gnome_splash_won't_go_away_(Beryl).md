---
title: "Gnome splash won't go away (Beryl)"
date: 2007-02-09
forum: Desktop Environments
---

### Post by dr_d12 on 2007-02-09
***the solution to the hanging gnome splash is in message #4***

Hello,
I installed beryl on edgy with the following directions:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)
Edgy works great. Beryl works great...except:

...the gnome splash screen when I first log on takes a very long time to disappear (A full minute, at least, after the desktop and beryl already load) When I open a session without Beryl, this doesn't happen.

The delay happens even with the splash screen turned off. During this time, everything including beryl works fine except that I have to wait just about 2 minutes for the power manager and network manager icons to load into the notification area, preventing network-manager-gnome from connecting to wifi for a while.

How can I tell what is taking so long to load?

Is this related to this warning from beryl? ("reloading options" at the bottom takes a long time as well.)

~$ beryl-manager
~$ libGL warning: 3D driver claims to not support visual 0x4b
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x4b
Reloading options

There is a website for the libGL warning: [http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg28133.html](http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg28133.html) They say its cosmetic.

Thanks for your help!
DD

---

### Post by mcduck on 2007-02-10
Try disabling all animations etc. for window type 'splash' in beryl settings.

---

### Post by dr_d12 on 2007-02-11
Thanks Mcduck. I turned off all splash animations but it didn't help. I found a screenshot of the problem here
[http://sernaonubuntu.wikidot.com/beryl](http://sernaonubuntu.wikidot.com/beryl) (under - does it work?)
The same icon shows up twice - I take it one is gnome and the last one is beryl?
Thanks,
Dave

---

### Post by dr_d12 on 2007-02-12
The solution to this problem is described on the Beryl Wiki under 
**"Gnome splash hangs when using Beryl"** (can't get much more obvious than that)
Wikis rule. 
DD

"_______________________________________________________________________________________________________

[http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl](http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl)

There is a possibility that the Gnome splash may become stuck as Beryl tries to load. This will probably go away on it's own after a couple of minutes.

To get rid of this, try the following.


**If you start Beryl in the standard Gnome session.**

Go to System&#8594;Preferences&#8594;Sessions&#8594;Current Session tab. Beryl probably loads with an order of 50. Change this to something like 60, save your changes and logout. If that doesn't work you could try to changing it to 40. If that doesn't work, try creating a new Beryl session within Gnome.


**If you have created a Beryl session via /usr/bin/startberyl.sh**

Login to a normal Gnome session without Beryl, then open System &#8594; Preferences &#8594; Sessions and check "Automatically save changes to session". Logout and login to a Gnome session without Beryl for this to take effect.

Using Applications &#8594; Accessories &#8594; Text Editor, open ~/.gnome2/session. Select and copy all the text and paste it again at the end of the file. Looking at the pasted text, change the line [Default] to [Beryl] and delete the lines starting with 0, so you end up with one default session and one Beryl session. Save your changes.

Using Applications &#8594; Accessories &#8594; Terminal, type the following

 gksudo gedit /usr/bin/startberyl.sh

and in that file replace

 exec gnome-session

with

 exec gnome-session --choose-session Beryl

Save the changes, then log out. Log in using Beryl; you may have gedit open for the first time but the splash screen should now go quickly. 
_______________________________________________________________________________________________________"

---

### Post by eggdeng on 2007-06-02
Followed the second alternative from the wiki and it works as predicted. The splash is gone but both a Nautilus window and gedit open on startup.
EDIT
On reboot, these no longer appear.

---

