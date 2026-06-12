---
title: "bbc iplayer desktop wont work with out gnome / kde"
date: 2010-01-27
forum: Desktop Environments
---

### Post by markp1989 on 2010-01-27
I have installed bbc iplayer desktop on my htpc, which is running openbox. 

i cannot run the iplayer because it says that only gnome and kde are supported.

is there any way to trick it in to thinking gnome is installed?

or a way to install gnome without the complete ubuntu-desktop package?

i tried just installing gnome-desktop-environment , but it wont let me because of dependencies.


thanks Markp1989


edit: 

sorted out the gnome problem by running this : 

export  GNOME_DESKTOP_SESSION_ID="openbox"

now when i try to run it it says 

mark@torrentslave:~$/opt/BBC\ iPlayer\ Desktop/bin/BBC\ iPlayer\ Desktop 
Unable to store values in GnomeKeyring!
KB: cpsid_49267 ([http://go.adobe.com/kb/ts_cpsid_49267_en-us](http://go.adobe.com/kb/ts_cpsid_49267_en-us))

---

### Post by benjy on 2010-03-30
Thanks for this Markp, I have been running Xubuntu for a while (but with a lot of applications from the gnome desktop - I like my luxuries! All I had to do to get bbc iplayer working was make sure I had gnome-keyring installed (sudo apt-get install gnome-keyring). While in the terminal I exported GNOME_DESKTOP_SESSION_ID as "xfce" instead of "openbox" then ran iPlayer (still from the terminal) with:

 '/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop'

Hey presto - iPlayer Desktop in XFCE! Thanks again.

---

