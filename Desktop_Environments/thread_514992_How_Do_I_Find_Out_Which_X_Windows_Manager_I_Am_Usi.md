---
title: "How Do I Find Out Which X Windows Manager I Am Using In Feisty?"
date: 2007-08-01
forum: Desktop Environments
---

### Post by cygnis1 on 2007-08-01
I am trying to install and run Beryl on my 7.04 laptop. When I installed the packages I got this message:
I followed the instructions to install Beryl on my Feisty laptop. Everything went well until I typed "beryl-manager" into the terminal. I received this message in the terminal:

Detected xserver : AIGLX

Checking Display :20.0 ...

Checking for XComposite extension : failed

No composite extension
beryl: No composite extension

My question is this:  What is an XComposite extension?  And where do I find it.  I think it might be   referring to the xwindows manager.  I need to know how to find which windows manager ubuntu is using and which manager I need.  Any help will be appreciated. 
Thanks

---

### Post by zidane2 on 2007-08-01
type sudo gedit /etc/X11/xorg.conf

and add to the end of the file
Section "Extensions"
    Option "Composite" "Enable"
EndSection

save and exit then close any applications and press ctrl+alt+backspace to restart the x server
then try beryl again and it should work :)

---

