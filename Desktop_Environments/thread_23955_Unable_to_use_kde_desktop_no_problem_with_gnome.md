---
title: "Unable to use kde desktop no problem with gnome"
date: 2005-04-04
forum: Desktop Environments
---

### Post by crouchendman on 2005-04-04
Hi i need help

newbee to ubuntu and Debian
I have been using Ubuntu warty since Nov 2004 I have found it a great distibution
after using Mandrake Suse and Red Hat I believe its a winner
I am not a complete newbee,but cannot solve a problem with kde  
I have installed  Ubuntu Hoary Hedgehog 5.04 and been using Gnome desk for about 4 weeks,no problems i am happy with the installation.

The problem i have is running kde

     1. I have installed kde  i am unable to  use kde programs from gnome desktop
        get the following message :-
        Could not start process Unable to create io-slave:
        klauncher said: Unknown protocol 'file'
     2. on running kde desktop I get the desktop screen up and panels but no     program menu's and basic logout button  and run command applet

i have tried removing all kde packages and ~.kde directory, and reloaded packages but this seems to have made no difference

can anybody help #-o   


.

---

### Post by Xian on 2005-04-04
[QUOTE=crouchendman]I have installed kde  i am unable to  use kde programs from gnome desktop
        get the following message :-
        Could not start process Unable to create io-slave:
        klauncher said: Unknown protocol 'file'
[/QUOTE]
Do you mean that you are attempting to launch these applications from a menu entry or from the the command line? If a menu entry then check its properties and determine what command is being issued. If from the command line, what exactly is the input you are providing?

---

### Post by crouchendman on 2005-04-04
for instance, from gnome desktop i can start konqueror but connot open directories, within  konqueror.
also kuickshow opens a window but does not find any directories

when either program is started from menu or command line?

---

### Post by Xian on 2005-04-04
[QUOTE=crouchendman]for instance, from gnome desktop i can start konqueror but connot open directories, within  konqueror.[/QUOTE]
So then are we talking about a scenario where konqueror is freezing and won't function at all but is still visible, or is it that it only loses some functionality such as you described? Are you able to get it to say navigate to websites, and are things like the menu options accessible?

For example, you should be able to open konsole in Gnome, but if you have it enabled in KDE to a transparent display then it loses a large degree of functionality within another DE. If you choose a more basic GUI option it starts to become more usable, even to the point to where there is no difference noted.

---

### Post by crouchendman on 2005-04-05
When konqueror opens, the menu's are accessable
when i try to open a url,  i get a message 'protocol not supported http'
when i try to open my home directory i get 'protocol not supported file'
when i go to configure konqueror i get a blank page

It seems that something is missing or not accessable

I have created a second user and  apart from no sound everything i have tried 
in kde desktop works when logged in  as the second user
it appears that the problem only exists, when kde is used 
by original user (sudo)

another message warns that no mime typs present

---

