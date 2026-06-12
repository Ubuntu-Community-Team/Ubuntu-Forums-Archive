---
title: "Issues with rdesktop"
date: 2010-09-14
forum: Desktop Environments
---

### Post by Cerpin TaxT on 2010-09-14
Hello all -

I'm in need of help.  I have an ubuntu box that is serving as a terminal with only one purpose - to establish a remote connection with a windows 2k8 server and run a application that allows people to check into a warehouse.  I set up the computer to launch rdesktop via the command line upon login.  I accomplished this by setting up terminal to run on login with the connection command as the default.  It works fine, a bit hacked together, but more than enough to accomplish what I want.  

My problem is that after a period of sitting the connection times out.  The computer makes no announcement before the connection is closed - and you actually have no idea that the connection is closed because it will display whatever was last on the screen until you start typing or move the mouse.  

I checked the windows side of things and all of settings seem to be correct.  I honestly believe that the issue is being caused by rdesktop.  

Has anyone had an issue like this or can point me in the right direction?  I'm pretty lost at this point. 

Thanks in advance.

---

### Post by Cerpin TaxT on 2010-09-15
*Bump*

---

### Post by gb38 on 2011-01-12
On the windows terminal server you can specify a timeout, maybe this is the cause of your problem?
See [http://technet.microsoft.com/en-us/library/cc754272.aspx](http://technet.microsoft.com/en-us/library/cc754272.aspx)

---

### Post by gb38 on 2011-01-12
When using rdesktop for a terminal server connection via rdp or rdp5 from ubuntu to windows server 2008 I experienced following problems:
- in "dos" command line in-line editing (left and right key) and "doskey"-like functionality (going back in command line history with up and down arrow) was not working
I tried to change options of the command prompt such as buffer size and quickedit (see [http://articles.techrepublic.com.com/5100-10878_11-5030802.html](http://articles.techrepublic.com.com/5100-10878_11-5030802.html) ) but had no improvement
- in programs such as openoffice calc, notepad, notepad++ the  possibility to navigate in the document with the keyboard was not  working (no up, down, left, right, pageup, pagedown keys working),  working with the mouse and with the backspace key was possible.

:!: By starting rdesktop on the command-line on the ubuntu machine I could find the problem.

- When I started with following command I got the problems: 
"rdesktop -u myusername -d mywindowsdomain mywindowsservername"
rdesktop answers this command with: "Autoselected keyboard map en-us"
- My windows server is located in Belgium and is configured to use Dutch as default language.
- So I tried "rdesktop -k nl_BE ...", where "nl_BE" is similar to the locale of my ubuntu machine (locales are defined in [http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap07.html](http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap07.html))
rdesktop answered with: "ERROR: Failed to open keymap nl_BE"
- "rdesktop -k be" where "be" is what I would use to set the keyboard on ubuntu via setxkbmap (see "man setxkbmap") caused rdesktop again to give an error message.

By reading the man page on rdesktop ("man rdesktop") I found that the keyboard must be specified according to rfc1766:
Language-Tag = Primary-tag *( "-" Subtag )
Now I tried "rdesktop -k nl-be ..."
rdesktop gives no message about the keymap and my problems went away

---

