---
title: "Firefox 1.5 doesn't run after installing Automatix"
date: 2006-01-26
forum: Desktop Environments
---

### Post by afx on 2006-01-26
First of all I installed Firefox 1.5 on it's own. Afterwards, I installed Automatix turning Firefox option off and Firefox plugins on. Now I can't start it up anymore... I've attached the screenshot of the error I get upon opening Firefox. Any ideas? Btw, can I run Automatix again (from the start menu) and install Firefox again?

---

### Post by rjwood on 2006-01-26
You may want to post this question on the 'automatix' thread, if you have already done that--be patient and someone will answer it. How many firefox's do you now have installed? if more than one then you need to either remove one or move one. Read the automatix thread or the 'firefox script thread by arnieboy'. Seek (search) and ye shall find....

---

### Post by arnieboy on 2006-01-26
[QUOTE=afx]First of all I installed Firefox 1.5 on it's own. Afterwards, I installed Automatix turning Firefox option off and Firefox plugins on. Now I can't start it up anymore... I've attached the screenshot of the error I get upon opening Firefox. Any ideas? Btw, can I run Automatix again (from the start menu) and install Firefox again?[/QUOTE]
u should not have tried to install the plugins again.. they all got installed when u installed firefox 1.5
awrite try this first of all:
**close all firefox windows** and open up terminal and do the following:
```
mv ~/.mozilla ~/.mozilla_new_backup
```
now try running firefox from menu.

---

### Post by Psimon on 2006-01-26
I don't see the point in using Automatix. Firefox runs fine by installing it in your home directory using the installer from the firefox website.

---

### Post by bobbymcsteels on 2006-01-26
is there an automatix amd64 breezy release and if so can some1 point me to the right direction??
cheers

---

### Post by afx on 2006-01-26
[QUOTE=Psimon]I don't see the point in using Automatix. Firefox runs fine by installing it in your home directory using the installer from the firefox website.[/QUOTE]
As I mentioned, I did not install Firefox with Automatix (or vice-versa?), I think that the Firefox-Plugins messed the things up. Anyway, what I actually did next is deleted everything in /opt/firefox/ /usr/lib/mozilla-firefox/ and installed firefox again with Adept. Now I have the version 1.0.7 up and running. I need your advice on the next step. Should I re-run Automatix and install Firefox 1.5 and Firefox Plug-Ins? Or should i do something else? Any suggestion is welcome...

---

### Post by afx on 2006-01-26
[QUOTE=bobbymcsteels]is there an automatix amd64 breezy release and if so can some1 point me to the right direction??
cheers[/QUOTE]
This is the Automatix thread: [http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")

Cheers!

---

### Post by Psimon on 2006-01-27
[QUOTE=afx]As I mentioned, I did not install Firefox with Automatix (or vice-versa?), I think that the Firefox-Plugins messed the things up. Anyway, what I actually did next is deleted everything in /opt/firefox/ /usr/lib/mozilla-firefox/ and installed firefox again with Adept. Now I have the version 1.0.7 up and running. I need your advice on the next step. Should I re-run Automatix and install Firefox 1.5 and Firefox Plug-Ins? Or should i do something else? Any suggestion is welcome...[/QUOTE]

Sorry for not reading your post properly. I installed the plug-ins by copying them from /usr/lib/mozilla-firefox/plugins into the plugins folder in my firefox 1.5 installation. I tried installing firefox and plugins with Automatix but it didn't work very well for me.

---

### Post by afx on 2006-01-27
Sounds reasonable, I'll do the sam thing...
Thanks, mate!

---

