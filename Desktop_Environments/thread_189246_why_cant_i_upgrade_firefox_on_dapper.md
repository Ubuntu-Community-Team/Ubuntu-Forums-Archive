---
title: "why cant i upgrade firefox on dapper?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by yusufm on 2006-06-05
there is a newer version of firefox out, but its not updating itself. The check for updates option under the help menu is grayed out and the checkbox to update firefox in the preferences is checked, but is also grayed out... how do i update it?

thanks.

---

### Post by Rondonjin on 2006-06-05
[QUOTE=yusufm]there is a newer version of firefox out, but its not updating itself. The check for updates option under the help menu is grayed out and the checkbox to update firefox in the preferences is checked, but is also grayed out... how do i update it?

thanks.[/QUOTE]

Looks like it's been disabled, even when Firefox is run as 'sudo'. I suppose because the version from Mozilla wouldn't know where to put itself. You can download and install  the tarball (under /opt, for example) or wait till a new package becomes available.

I've also noticed that Thunderbird is at version 1.5.0.4 but the version installed here is 1.5.02. I updated my kids' PCs (Win) from 1.5.03.

Wayne

---

### Post by aysiu on 2006-06-05
The new Firefox (1.5.0.4) is expected to be updated in the repositories by next week.

If you don't want to wait for the Ubuntu developers to package it, use the Firefox from Mozilla. [This script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) will make it easy to install.

---

### Post by Rondonjin on 2006-06-05
[QUOTE=aysiu]The new Firefox (1.5.0.4) is expected to be updated in the repositories by next week.

If you don't want to wait for the Ubuntu developers to package it, use the Firefox from Mozilla. [This script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) will make it easy to install.[/QUOTE]

Can the installed version safely be removed or does it want to take half of the Gnome desktop with it? :mrgreen: 

I've noticed with the Ubuntu version of Firefox there is no 'Clear Search History' option when you right click on the Google search box. I find this useful as I like to have things nice and clean after I've done searching ;) 

Wayne

---

### Post by nanotube on 2006-06-05
[QUOTE=Rondonjin]Can the installed version safely be removed or does it want to take half of the Gnome desktop with it? :mrgreen: 

I've noticed with the Ubuntu version of Firefox there is no 'Clear Search History' option when you right click on the Google search box. I find this useful as I like to have things nice and clean after I've done searching ;) 

Wayne[/QUOTE]
it's safer to keep the ubuntu version alongside the mozilla official version, since several apps use the gecko rendering engine in the ubuntu version. the install script aysiu pointed you to will automatically take care of keeping the old version but linking the official mozilla to be the default browser.

---

### Post by Rondonjin on 2006-06-05
[QUOTE=nanotube]it's safer to keep the ubuntu version alongside the mozilla official version, since several apps use the gecko rendering engine in the ubuntu version. the install script aysiu pointed you to will automatically take care of keeping the old version but linking the official mozilla to be the default browser.[/QUOTE]

I see, although it hurts my sensibilities as I hate having stuff hanging around !8) 

Anyway, the script barfed on me, I think I'll wait till an upgrade package becomes available.

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/wayne/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Previous command did not complete successfully. Exiting.


Wayne

---

### Post by aysiu on 2006-06-05
Can you be more specific than that the script "barfed" on you? I wrote the original script, and nanotube made significant revisions to it.

If anyone can help you debug what went wrong with the script, it's nanotube.

---

### Post by Rondonjin on 2006-06-05
[QUOTE=aysiu]Can you be more specific than that the script "barfed" on you? I wrote the original script, and nanotube made significant revisions to it.

If anyone can help you debug what went wrong with the script, it's nanotube.[/QUOTE]

Done! I edited my original post! Meant to include the info but was in a hurry, doorbell was ringing, so was the phone and the cats were fighting :D 

Wayne

---

### Post by aysiu on 2006-06-05
I don't know much about gpg. Nanotube, this is all you.

---

### Post by nanotube on 2006-06-05
[QUOTE=Rondonjin]I see, although it hurts my sensibilities as I hate having stuff hanging around !8) 

Anyway, the script barfed on me, I think I'll wait till an upgrade package becomes available.

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/wayne/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Previous command did not complete successfully. Exiting.


Wayne[/QUOTE]
looks like for some reason the permissions on your .gnupg directory are incorrect. see this link for correcting the problem:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html)
and then try running the script again.
(the link basically says, run command "chmod 700 ~/.gnupg" to change permissions on your .gnupg)

---

### Post by Rondonjin on 2006-06-05
[QUOTE=nanotube]looks like for some reason the permissions on your .gnupg directory are incorrect. see this link for correcting the problem:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html)
and then try running the script again.
(the link basically says, run command "chmod 700 ~/.gnupg" to change permissions on your .gnupg)[/QUOTE]

What a mess! some of the folders in my home directory are 700 and others are 755. This is prolly the result of going from Mandrake to Mandriva  to Ubuntu to Fedora Core 5 to Ubuntu ](*,) Had to mess about changing UIDs, don't know what else I may have changed!

Wayne

---

### Post by aysiu on 2006-06-05
You kept the same /home folder through three distributions? It's no wonder the permissions are wrong on your .gnupg folder. "What a mess," indeed!

---

### Post by Rondonjin on 2006-06-05
[QUOTE=aysiu]You kept the same /home folder through three distributions? It's no wonder the permissions are wrong on your .gnupg folder. "What a mess," indeed![/QUOTE]

/home is on it's own partition and very hard to backup, I'd be feeding it blank DVDs all day! It's a 30Gb partition with only 11Gb free (40Gb disk). My second 80Gb disk has prolly the same free space. No matter how big a disk you buy it's never big enough. Don't ask what I have that takes up so much space, all I'll say is I've bought a lot of DVDs from the UK, very Brit stuff, that is not available here and I don't want to have to replace any of it if I damage the disks :-D 

Time to do some disk housekeeping.....

Wayne

---

### Post by aysiu on 2006-06-05
[QUOTE=Rondonjin]Time to do some disk housekeeping.....[/QUOTE] Go for it! We're behind you 100%.

By the way, I keep a separate documents and files partition, but I don't keep a separate /home. I prefer to just redo my settings (well, I do back up my Thunderbird and Firefox profiles)--just to keep things clean.

---

### Post by nanotube on 2006-06-05
[QUOTE=Rondonjin]What a mess! some of the folders in my home directory are 700 and others are 755. This is prolly the result of going from Mandrake to Mandriva  to Ubuntu to Fedora Core 5 to Ubuntu ](*,) Had to mess about changing UIDs, don't know what else I may have changed!

Wayne[/QUOTE]
haha wow hard core. :)
well, good luck getting your things in order. but as far as .gnupg is concerned, it shouldn't take more than that one chmod command.

---

### Post by Rondonjin on 2006-06-05
[QUOTE=aysiu]Go for it! We're behind you 100%.

By the way, I keep a separate documents and files partition, but I don't keep a separate /home. I prefer to just redo my settings (well, I do back up my Thunderbird and Firefox profiles)--just to keep things clean.[/QUOTE]

Thanks for the vote of confidence :mrgreen: 

I'm going to start a new thread on permissions as it has nothing to do with Firefox now.

BTW. Did I thank you for your help? Well, thanks! I appreciate it, now I know there is something wrong with my /home I can fix it.

Wayne

---

### Post by Rondonjin on 2006-06-05
[QUOTE=nanotube]haha wow hard core. :)
well, good luck getting your things in order. but as far as .gnupg is concerned, it shouldn't take more than that one chmod command.[/QUOTE]

Done! Thanks for your advice.

Wayne

---

### Post by nanotube on 2006-06-05
[QUOTE=Rondonjin]Done! Thanks for your advice.

Wayne[/QUOTE]
no prob. glad it worked. :)

edit: so, you are in tokyo? cool! i was in tokyo for a summer, it kicked @$$. ;)

---

### Post by Hitetsu on 2006-06-05
[QUOTE=aysiu]I do back up my Thunderbird and Firefox profiles[/QUOTE]

I know this is a little off-topic, but I was just wondering how you back them up?

I've had to reinstall ubuntu a few times on different hard drives, and I've never been able to figure out how to keep all my mail, and make a copy of all my accounts in Thunderbird.

I do know how to make a copy of my bookmarks in firefox though, so I didn't have to lose all them :D

---

### Post by Rondonjin on 2006-06-05
[QUOTE=nanotube]no prob. glad it worked. :)

edit: so, you are in tokyo? cool! i was in tokyo for a summer, it kicked @$$. ;)[/QUOTE]

Been here basically since summer..... 1980, went home (UK) for a couple of years in the mid 80's and been here now (officially) since '88. Nowhere else to go and no one else will let me in :mrgreen: 

Wayne

---

### Post by aysiu on 2006-06-05
[QUOTE=Hitetsu]I know this is a little off-topic, but I was just wondering how you back them up?[/QUOTE] Firefox settings live in a hidden folder: /home/hitetsu/.mozilla

Thunderbird (if it's Ubuntu's) lives in /home/hitetsu/.mozilla-thunderbird

Or (if it's Mozilla's) in /home/hitetsu/.thunderbird

To see hidden folders in Gnome, press Control-H
In KDE, press Alt-V, then H.

---

### Post by Hitetsu on 2006-06-05
Alright, Thanks a lot! It'll save me a lot of time in future.

Thanks! :)

---

### Post by Rondonjin on 2006-06-05
[QUOTE=nanotube]looks like for some reason the permissions on your .gnupg directory are incorrect. see this link for correcting the problem:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html)
and then try running the script again.
(the link basically says, run command "chmod 700 ~/.gnupg" to change permissions on your .gnupg)[/QUOTE]

OK fixed the permission on that folder and ran the script again. It barfed because there was no /opt so I created that and tried again. Install went through fine but when i ran firefox got this:

wayne@Merlin:~$ firefox
/opt/firefox/run-mozilla.sh: line 131: 19300 Segmentation fault      "$prog" ${1+"$@"}

So I re-linked the old firefox to /usr/bin

Not my day today!

Wayne

---

### Post by gandalf100 on 2006-06-05
meanwhile i use opera 8.54 im not sure, if its 8.54 in the dapper repository - rather 8.51 also with security issues. so my repository is

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

---

### Post by nanotube on 2006-06-05
[QUOTE=Rondonjin]Been here basically since summer..... 1980, went home (UK) for a couple of years in the mid 80's and been here now (officially) since '88. Nowhere else to go and no one else will let me in :mrgreen: 

Wayne[/QUOTE]
hehe nice :)

---

### Post by nanotube on 2006-06-05
[QUOTE=Rondonjin]OK fixed the permission on that folder and ran the script again. It barfed because there was no /opt so I created that and tried again. Install went through fine but when i ran firefox got this:

wayne@Merlin:~$ firefox
/opt/firefox/run-mozilla.sh: line 131: 19300 Segmentation fault      "$prog" ${1+"$@"}

So I re-linked the old firefox to /usr/bin

Not my day today!

Wayne[/QUOTE]

hmm, strange... thats the line that actually runs firefox, so the segfault is coming out of the firefox binary... don't know what's up. maybe try backing up your firefox profile, and starting a fresh one.

---

