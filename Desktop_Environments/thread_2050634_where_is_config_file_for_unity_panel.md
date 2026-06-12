---
title: "where is config file for unity panel"
date: 2012-08-31
forum: Desktop Environments
---

### Post by xitronznz on 2012-08-31
I'm creating a LiveCD based on Ubuntu Desktop 12.04, and I want it to remain as close to the original LiveCD as possible.  The changes I want to make involve setting up some preset items for the users who will be receiving this LiveCD.  The purpose for the CD is for certain users to have a simple Ubuntu desktop presented to them with a few icons in the panel, one of which will be the VPN client connector.

Following the instructions for the LiveCD located at:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

...I reach the point where I'm tweaking the system before running squashfs and creating the new ISO file.  What I want to do is place the information for the VPN client into the panel without having to start up the X environment.  Somewhere on the system MUST be a config file that controls what the panel displays, how it acts, etc., that can be accessed from the command line rather than through the GUI.

Can anyone tell me where that configuration file is located?

Thank you!

Benny /Xitron

---

### Post by xitronznz on 2012-08-31
I created a launch item that I named "gibbygibbygibby", which I'm pretty sure will be a unique string.  After locking it to the launch panel, I did a command line "find | grep" search for it, and it has so far hit on the following item:

  /home/myuser/.config/dconf/user

This is a binary file.  A search for information on this file led me to the following entry in another forum:

===========================================================================
If you would like to edit dconf configuration files i would suggest you use the dconf-editor gui or the gsettings frontend. dconf-editor can be installed by running sudo apt-get install dconf-tools. gsettings should already be installed, but it is much harder to use. 
 
                ===========================================================================

I installed the tools, and ran the GUI to see what I could find, and nowhere in the entire thing with all its pulldown arrows did I find gibbygibbygibby, so I've no idea how to edit this beast.

Am I on the right track?  Suggestions?

Thanks again,

Benny / Xitron

---

### Post by Krytarik on 2012-08-31
First, you should find the link to your newly created .desktop file in DConf-Editor in "com.canonical.Unity.Launcher -> favorites".

Second, see my earlier post here how to override system-wide defaults:[INDENT][http://ubuntuforums.org/showthread.php?p=12178901#post12178901](http://ubuntuforums.org/showthread.php?p=12178901#post12178901)[/INDENT]Third, make sure your respective .desktop file is located system-wide, obviously, in '/usr/share/applications'.

Regards.

---

