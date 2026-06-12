---
title: "I broke Beryl again..."
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by Nadstar on 2007-06-27
Hi All,

I have managed to break my Berly install on my main user account in Feisty. Basically I was having issue's with Windows drawing correctly (no borders) and so started to fiddle around with the options in Berly Manager to see if that helped. After choosing 'XGL rendering' my system froze and now will always freeze shortly after login on this account (my main account). I guess its just because the 'XGL rendering' option keeps getting applied, but I cannot get to the settings to change it back again. I can retsart X with crtl+alt+backspace and log into a different account (which Beryl runs OK on with no problems - strangely not even the Window drawing problems I was getting on my main account). So I need to be able to edit the settings for Berly Manager on my main account somehow from my 2nd account, or at least stop Beryl from loading on my main account by editing its sessions. But how?

Thanks for any help in advance...

---

### Post by Nadstar on 2007-06-27
Hi - well managed to fix it. So advice to anybody else with similar issue's. I sudo copied the '.beryl-managerrc' file from the home of the working account to the home of my main account and all is well again.

---

### Post by imcc on 2007-06-27
If you get the missing borders again, maybe I can help with that bit..

It might be a case of copying a backup of your xorg.conf file. Hopefully when you installed XGL it made a backup.

If so it should be called etc/x11/xorg.conf.backup

I'm sorry but I can't tell you how to do it in command line, but I messed up my XGL install in a similar way, so i used sudo gedit. I used the recovery boot option and used startx to get in to a safe vga mode on the broken account. If anyone can let me know the command line for this is would be great!

In general the problem seems to be caused when the xorg is changed by installation of XGL.

Beryl or compiz need a window decorator like emerald installed. I installed all the packages for emerald and heliodor. Im guessing XGL isn't writing the xorg.conf to take in to account either Beryl or the Decorator.


Theres several commands to try to get the windows back, most I think are harmless to experiment with (it cant really make it worse than it is, anyway!)

metacity --replace
emerald --replace
beryl --replace
compiz --replace if u have fusion.

Here's a quick vid i made last night of my working compiz fusion desktop, if anyone is interested.
It was made on an AMDX2-4200+ with an Nvidia 7800gtx.

[http://files.filefront.com/my+compiz+desktopogg/;7891858;;/fileinfo.html](http://files.filefront.com/my+compiz+desktopogg/;7891858;;/fileinfo.html)



EDIT : Heh. I need to write replies in under 5 mins it seems. And none of my fixes did it either =( Oh well enjoy the vid

---

