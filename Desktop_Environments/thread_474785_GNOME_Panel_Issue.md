---
title: "GNOME Panel Issue"
date: 2007-06-15
forum: Desktop Environments
---

### Post by ShareBuntu on 2007-06-15
Hi folks,

I've got an interesting problem here. Sometimes when I start up Ubuntu and log in, my background loads but the top and bottom GNOME panels don't. Other times it works fine and everything loads perfectly. In order to get to the "perfect state" I need to reboot and login constantly until it loads the panels. The problem seems to occur randomly.

---

### Post by jargoman on 2007-06-15
I have a similar problem where it takes forever to load my desktop. I find it has something to do with another program in my startup list having trouble loading. For example I have network manager set to load on login. If I'm not near my wireless router then i have to wait till network manager gives up trying to connect to the missing wireless network before my panel icons will load. Sometimes though it does seem to be random and sometimes it freezes right away when I enter my password. 

I was wondering if you have any processes that are using a ridiculus amount of ram specifically 17179869180.0 gb. I realize that it's impossible to have that many gigs of ram but that's what it says in my System Monitor. I wonder if this is my problem.

Also to help you out. Instead of rebooting you could hit alt-f2 then type terminal. Then

$ killall gnome-panel nautilus

This is supposed to refresh gnome-panel (and nautilus). I guess nautilus would be optional but it couldn't hurt.

---

### Post by ShareBuntu on 2007-06-15
Thanks for the response. I'll be sure to try that next time it happens. I've tried CTRL-ALT-BACKSPACE to restart X but after I login nothing happens, just the background. Sometimes there's a grey box in the upper left corner too. It's definitely a gnome-panel and/or nautilus issue.

Any idea if this has been submitted as a bug?

---

### Post by sahilbhrany on 2007-07-16
even I have the same problem. 

Did you figure out a solution ?

my problem started after I upgraded Beryl and install compiz. I have to press Alt-Ctrl-Backspace to load the panels sometimes. the first time I start my computer, the panel doesn't load,

---

### Post by Monteaup on 2007-09-10
Same here!

Any solutions?

---

### Post by tipiglen on 2007-09-13
and same here as well.

Booted from scratch via hard disk (cd un-usable) and all went well.  On first boot into new installation, desktop came up right after login and password, and everything worked ok, but after shutdown (it seems to stop at deconfiguring network......) needed hard reset (power off and back on) and rebooot - Everything OK except after login and password, all I get is a lovely dark maroon background with a mouse pointer (arrow).  Just sits there, keyboard inactive except for ctrl/alt/backspace, which gets a terminal.  Tried metacity and got an error ("can't...X...").  If I try sudo, it just hangs and I have to ctrl/alt/del and we go back to a stalled shutdown "disconfiguring network interfaces...."

Very frustrating!  Any ideas?

ed

---

### Post by Hashte on 2007-09-16
Try to **reinstall ** *gnome-panel* in Synaptic :D

---

### Post by Monteaup on 2007-09-18
> **Hashte said:**
> Try to **reinstall ** *gnome-panel* in Synaptic :D

I reinstalled nearly every Gnome package. No success...

Tryed to start a gnome-session romtely using cygwin. I get the following error Message... 

"Process /usr/lib/control-center/gnome-settings-deamon received signal 11"

---

### Post by luisjorge on 2007-09-19
Hello!

> **Monteaup said:**
> I reinstalled nearly every Gnome package. No success...

Tryed to start a gnome-session romtely using cygwin. I get the following error Message... 

"Process /usr/lib/control-center/gnome-settings-deamon received signal 11"

I had a similar problem once, it turned out to be related to the session. The solution that worked for me was to open my Home folder, then show the hidden files (Ctrl+H), open the ".gnome2" folder and delete the "session" file inside it. Then after rebooting, everything ran smoothly.
I really don't know if this is your problem, but maybe you can try this out.

Also, I've had the "grey box at the top left corner" that was mentioned in the first posts of this thread. This was accompanied with my keyboard locking up sometimes at login, or the desktop and panels taking ages to load. All this problems began after I installed the "Wicd" network manager, instead of the one from Gnome, which is a little better, but caused a lot of trouble at least for me :(

Hope this helps!

---

### Post by Monteaup on 2007-09-19
in the .xsession-errors I coulde find a Problem with ESD. So I started gnome-sound-properties using the cygwin XServer and changed the Settings from ESD to OSS. I don't care about sound I don't have any speakers installed. 
After that I coulde login and everything looks good except the logout (the gnome-panel hangs) I'm not able to logout :(

Whis is not a Solution. But anyway I can use Desktop again.

---

### Post by Monteaup on 2007-09-21
Got the solution. 
I tried to reinstall the ESD packages. Got the error Message with "...can't be authenticated..." ?! So I changed the repository from Germany to the Original one. Did an update and reinstalled all ESD and gnome packages. Now everything is fine!

---

### Post by loko on 2007-11-02
> **Monteaup said:**
> Got the solution. 
I tried to reinstall the ESD packages. Got the error Message with "...can't be authenticated..." ?! So I changed the repository from Germany to the Original one. Did an update and reinstalled all ESD and gnome packages. Now everything is fine!

sry, but i doubt this is the solution, because the packages are the same on both servers, also they are secured with a checksum - therefor it is not possible that they are defect.

but one solution which is a bit more faster than rebooting is:

switch to tty1, then "sudo init 1" then "init 5" now it works.

i have to figure out this problem more. since one day it also affects me...

---

### Post by jbayne on 2008-01-14
I had this same problem and deleting the session file as outlined above worked for me.

---

