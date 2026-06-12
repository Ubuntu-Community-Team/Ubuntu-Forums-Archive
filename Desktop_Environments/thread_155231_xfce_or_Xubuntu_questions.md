---
title: "xfce or Xubuntu questions"
date: 2006-04-04
forum: Desktop Environments
---

### Post by jamesr on 2006-04-04
I was wondering where to post my questions and to search for answers.

I have installed Xubuntu on my server just so that I could use gparted easily. 

Some how I have changed the desktop and I am not sure how. The original desktop had a toolbar with icons which I no longer have.

I also wish to add a printer but when trying the web interface my password do not seem to work. This is a follow error to the CUPS server saying the  "admistrative tasks have been disabled for security reasons" 

The Xubuntu works amazing well for 64MB system. This system is normally console only.

---

### Post by dermotti on 2006-04-04
Worse case scenario you could always create a new user and everything will be default.....

---

### Post by Kapre on 2006-04-04
[QUOTE=jamesr]I was wondering where to post my questions and to search for answers.

I have installed Xubuntu on my server just so that I could use gparted easily. 

Some how I have changed the desktop and I am not sure how. The original desktop had a toolbar with icons which I no longer have. [/quote]

Try running this "xfce-4 panel &" on the Run Program

> I also wish to add a printer but when trying the web interface my password do not seem to work. This is a follow error to the CUPS server saying the  "admistrative tasks have been disabled for security reasons" 

Try running it with "sudo"

> The Xubuntu works amazing well for 64MB system. This system is normally console only. 

I think it's still slow (on 64 MB) but at 128 I would say it is flying (like what I have right now - Celeron 433, 128 MB, Intel 810 MB with video)

K

---

### Post by jamesr on 2006-04-05
I googled re the error and there seems to be a missing user "cupsys". I will be checking this out thanks for the info.

---

### Post by yxvaan on 2006-04-05
[QUOTE=jamesr]I have installed Xubuntu on my server just so that I could use gparted easily. 

Some how I have changed the desktop and I am not sure how. The original desktop had a toolbar with icons which I no longer have.[/QUOTE]

I probably had the same problem a few weeks ago - either the panel or the toolbar (can't remember which one) vanished without my knowing why. I did manage to get it back but can't unfortunately remember how. However, for the first thing check the panel/toolbar autohide setting:

right-click the desktop and choose Settings -> the appropriate tool(s)

or give the command xfce-setting-show at the terminal prompt and choose the tool(s).

In my case the solution wasn't that simple but I think that after fiddling with the different settings and perhaps even having had a look at the xfce docs (/usr/share/xfce4/doc//C/index.html) I got the pieces where I wanted and showing & hiding as I wanted.

[QUOTE=jamesr]I also wish to add a printer but when trying the web interface my password do not seem to work. This is a follow error to the CUPS server saying the  "admistrative tasks have been disabled for security reasons" [/QUOTE]

This, too, sounds familiar. I remember having managed to open the CUPS admin  section in the browser, most probably by following these instructions ([http://pingswept.org/category/ubuntu/):](http://pingswept.org/category/ubuntu/):)

" The last tweak was to add a printer to CUPS manually. To enable the web administration for CUPS, I added a root password:

sudo -s

passwd

In /etc/cups/cupsd.conf, I changed RunAsUser to No, so that CUPS would run as root, and not switch to run as the user cupsys, as I believe this is what disables the web interface:

RunAsUser No

Then restart CUPS:

/etc/init.d/cupsys restart"

There's also another get-around: console-based CUPS administration tools. See CUPS docs ([http://localhost:631/documentation.html](http://localhost:631/documentation.html)) and appropriate man pages for details. And preface the commands with "sudo" if they don't otherwise work.

---

### Post by jamesr on 2006-04-05
Thanks xyvaan but I have already added the user cupsys, restarted CUPS and added the printer.

The next stage is to add it to the console and Samba.

I still have not got the desktop looking the way that I would like it but I am loathe to change things as  the changes are not immediate so I need to keep going in and out of Console to see the changes. I will try your suggestions later.

By the way the link [http://pingswept.org/category/ubuntu/):](http://pingswept.org/category/ubuntu/):) did not work directly  error 404 not found but I saw the section on Xubuntu and Ubuntu

---

### Post by barnz on 2006-04-29
Thanks yxvaan worked well here too.

Are there security issues with leaving "RunAsUser No" in CUPS?

Should I set it back to "Yes" once I have set up my printer?

Thanks all

---

