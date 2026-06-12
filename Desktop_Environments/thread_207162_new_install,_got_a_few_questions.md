---
title: "new install, got a few questions"
date: 2006-07-01
forum: Desktop Environments
---

### Post by praxis22 on 2006-07-01
Hi,

I've just installed 6.0.6 desktop, and now I have to go out, so applogies if this is all in a FAQ, but I have a few questions.

What's the root password? It didn't ask me for one? (please no lectures about running as root, I'm a UNIX admin by trade, I know what I'm doing.)

How do I boot in 1024x768? If it boots in VGA, the screen is offset, I had the same issue with the liveCD, every time I booted VGA, the screen is offset, boot 1024, the screen is locked in place properly. I'm using a Sharp Mebius (PC-MT1-P5) laptop that we bought in Akihabara :) Sound isn't working but it wasn't working under windows either, I think it's dead. :-\" 

So far so good, looks fairly slick, figured that if WGA possessed the ability to shut down windows it was only a matter of time untill that ability was abused. So time to make the jump, what the wife is going to think about me installing Ubuntu on her laptop is another matter, but she's got another one anyway :lol: 

later
jb

---

### Post by robglinka on 2006-07-01
Root is disabled by default on Ubuntu.

If you do a little digging you can find out why, but most actions can be taken by simply running sudo "command".

If you want to run as root, you need to set the root password manually.

I was confused completely as well, until I discovered that root was disabled in the install.

As for the screen resolution, I believe 1024x768 is default, if not. You can pull up System->Preferences->Screen Resolution and enable it as the default.

If that doesn't work, post your /etc/X11/xorg.conf and we'll take a look and see what your settings are.

Anyone else know about sound cards?

---

### Post by aysiu on 2006-07-01
[QUOTE=praxis22]
What's the root password? It didn't ask me for one? (please no lectures about running as root, I'm a UNIX admin by trade, I know what I'm doing.)[/QUOTE] No lectures, but this document will explain both Ubuntu's *sudo* model **and** how to re-enable a more traditional root/user account.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by vigleik on 2006-07-01
You might want to run "sudo dpkg-reconfigure xserver-xorg" to fix your display problems. In particular you can set which resolutions you want enabled. It might also help to choose a different driver (search the forum if you have a nvidia or ati graphics card).

Vigleik

---

### Post by praxis22 on 2006-07-01
Hi,

OK, thanks for that usefull, will try the x reconfig, but I was talking about grub the boot loader, it that starts in 1024x768 then the desktop comes up properly too. or at least it did on the live cd part.

Perhaps root was not the right question :) I'm still asked to enter a password to do simple things like change the time, this is annoying. How do I make it stop doing that? 

Also, is it possible to amalgemate the two bars/panels? or dispense with them entirely in favour of a dock?  Now that I think about it the last time I had any serious dealings with X it was 4 or more years ago, I'll have to find fvwm 1.24r and my old config file.

Time for bed I think, and forget that England have just lost :cry:

---

### Post by chalex on 2006-07-01
[QUOTE=praxis22]
Perhaps root was not the right question :) I'm still asked to enter a password to do simple things like change the time, this is annoying. How do I make it stop doing that? 
[/QUOTE]

Well, if you're doing something that requires administrative privileges, it'll ask you for the password, yes.  Why do you find that unusual?

---

### Post by aysiu on 2006-07-01
[QUOTE=praxis22]I'm still asked to enter a password to do simple things like change the time, this is annoying. How do I make it stop doing that?[/QUOTE] Windows is like this, too, actually.

You have to be the administrator to change the time because that's considered a systemwide setting (it affects all users). Of course, most people run Windows *as* administrator, so they don't realize regular users can't change the time.

---

### Post by praxis22 on 2006-07-02
[QUOTE=aysiu]Windows is like this, too, actually.

You have to be the administrator to change the time because that's considered a systemwide setting (it affects all users). Of course, most people run Windows *as* administrator, so they don't realize regular users can't change the time.[/QUOTE]

Hmmm, I guess you can never got away from the shadow of Windows, even on a Linux board huh? :) I can understand why you'd want to do this to a novice, UNIX being "the hole hawg of operating systems" and all, I just think it's a bad design descision personally, it annoyed me when Windows did it too :) I expect to be able to turn off any given feature, somebody else has decided I should have, I guess that's why my other Unix boxes are Solaris 10 and Gentoo.

Why do I find it annoying? That's just because of who I am, I guess, I built my first two computers from soldered  kits, (one of them even worked) :cool:  I'm used to stamping my authority on any computer I own, tweak it, trick it out, make it sing. Both from an "ownership" perspective, where as an admin, personally and proffessionally you don't own the box unless you have root. To a simple personal dislike, born of many years of "arguing" with a computer as to who's right. I actually deeply resent a computer saying to me, "are you sure?" 

I may well kill the computer, (figuratively speaking) if I get the answer wrong, but I'll learn not to do it again. For the same reason I trashed windows the moment that I percieved that WGA meant that somebody other than me controlled what happend to my PC, and hence installed ububtu, what I've been looking for is absolute control over my chosen OS, and if ububtu won't give that too me, I'll replace it, just as it replaced Windows.

You might say I have "control issues" but *that* isn't going to change. :D 

On a completely unrelated note, without checking freshmeat, is there such a thing as a "personal firewall" for Linux/ubuntu? I know the OS is secure, and I've flashed  my wirelessG router already ;) but I want a veto over what leaves my box, as opposed to simply what can come in. 

later
jb

---

### Post by tomchuk on 2006-07-02
I'm not usually the type to post RTFM responses, but you seem to like to get your hands dirty:

`man sudo` - look for the NOPASSWD and how you can apply it to specific commands for specific users.
`man iptables` - if you'd like something to work from I like Uwe Hermann's [script](http://www.hermann-uwe.de/security/my-firewall-iptables-scripts)

Also there's [Firestarter](http://www.fs-security.com) which may be more along the lines of a 'personal firewall'

---

### Post by praxis22 on 2006-07-02
[QUOTE=tomchuk]I'm not usually the type to post RTFM responses, but you seem to like to get your hands dirty:
[snip]
Also there's [Firestarter](http://www.fs-security.com) which may be more along the lines of a 'personal firewall'[/QUOTE]

I do indeed like to get my hnads dirty, but I'm a bit busy this weekend, so I figured I'd avail myself of the legendary "community support" since I don't have time to do extensive research.

RTFM is always a valid response IMO :D

later
jb

---

### Post by praxis22 on 2006-07-02
Hmmm,

So this the user friendly version huh? ;)

Well hopefully I've got the desktop to behave, by dint of /usr/bin/xvidtune, tweaking on the fly,  (hit "auto" then the up & down buttons, etc. Then hit "apply" and "show") This will give you a few lines of text in the terminal you launched xvidtune from. Then you dump the last line prefixed by "ModeLine" (no quotes) into /etc/X11/xorg.conf, less than intuitive and not for the easily spooked, (the line goes into the "Monitor" section btw, after the VertRefresh line.) Indeed much like the X wrangling of old. Didn't quite give me the same buzz as actually getting X working on Gentoo, but so it goes.

Then there are the annoyances such as not being able to launch X apps as root as you need the security cookies setup by Gnome, argh! :-# I'd forgotten about that. 

Worked around sudo too, stick your login ID and ALL=NOPASSWD: ALL at the bottom of /etc/sudoers, and you no longer have to worry about passwords. Not for the novice that one ;) 

Also discovered that gnome runs like a dog on 256Mb of memory, so I've installed  XFCE, then I shall install swiftfox.

All in a night's work :)

Thanks for the pointers btw, useful.

later
jb

---

