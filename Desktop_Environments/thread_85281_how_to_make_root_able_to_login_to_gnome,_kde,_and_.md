---
title: "how to make root able to login to gnome, kde, and xfce?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by kazuya on 2005-11-02
I know this is contrary to the norm in Ubuntu, but I am trying to enable root login so as to have that option to login as root? I have followed the guide and enabled root login from within the security module. I have even changed the Greeter; However, when I reboot the machine, I still do not get allowed to login as root.

would the login session look something like: 

user: root
pswd: ******

What else do I need to do to make root user able to login? Or should I be typing  administrator instead. The login prompt, did not change either.

Any ideas?

---

### Post by Xian on 2005-11-02
What are you trying to do that you would need to login as root?
I'm certain there is a more appropriate method.

---

### Post by ultima2k on 2005-11-02
Can't you just run "sudo su" to change to root?

---

### Post by Kyral on 2005-11-02
Its better to use "sudo -i"

And I actually *won't *tell you how to login graphically as root. You shouldn't need to. All the GUI config apps are configured to use Sudo.

And its just asking for a world of hurt. Heck, XChat will also yell at you for running it as root ;P

---

### Post by NewWithoutClue on 2005-11-02
I did it once by mistake..
Dropped into init 1 then su'ed into root and started x.

Paul.

---

### Post by teaker1s on 2005-11-02
accept what Kyral is telling you, it is possible to enter directly as root-but it's disabled directly because any error will end in disaster

---

### Post by kazuya on 2005-11-02
alright, my reasons are a few. I was trying to use k3b to do a cd burn of an audio as a user, and it failed when I launched it. Upon doing from terminal: sudo k3b, I launched k3b, and this time cdrecord seemed to be able to do the burn successfully. If I try directly, it fails.

My user has limited abilities. But when I think about it, you guys are right. 

As an off topic, why does the bootup, take so long; I have heard of initg requirement, and the problems with that,., is tere any recommendation to make this OS bootup faster. I have 512MB RAM, AMD XP thlon 2200, 250GB and 160GB HDrive, and still it takes almost 5 minutes to bootup. I stare at the black screen for a while before bootup.

Do not get me wrong. I still love the awesomeness of the look and feel and crispness, but the boot-time thing is kicking my butt.

---

### Post by teaker1s on 2005-11-02
system-services disable clock syncronisation service will speed it up a little

---

### Post by angkor on 2005-11-03
[QUOTE=kazuya]it takes almost 5 minutes to bootup. I stare at the black screen for a while before bootup.
[/QUOTE]

This isn't normal. On my 2Gz proc with 1G mem it takes one minute at the most to boot from off->gdm login (Hoary was faster btw).

When is it stalling you say, before grub starts?

---

### Post by kazuya on 2005-11-07
it goes past  the bootscreen or runlevel and touches on the splash screen fo a while and then goes back to the boot screen past the boot image, and just hangs there forever {4 mins}. I have already turned the services clock thing off.

any ideas?

linux-k7 not a working.

---

### Post by teaker1s on 2005-11-09
hit esc when you see grub and try booting 386i kernel

---

### Post by kazuya on 2005-11-21
according to a helpful source here as written in the Ubuntu Guide: Here is the fix for how to enable root login for anyone that may need to use it:

do this in terminal to enable root:

sudo passwd root

# System -> Administration -> Login Screen Setup
# Login Screen Setup

Security Tab -> Options -> Allow root to login with GDM (Checked)

then

System -> Administration -> Users and Groups
and click on root, then add it to all groups
from ubuntuguide.org

this was solved in another post by a very very helpful guy. Now I can isolate the source of one issue with my OS. In the end, it is about choice. If I desire to trash my system further that is my choice, however, if I cannot utilize my system or troubleshoot my issue without enough support on that particular issue :gnomeboyadvance}. I have a right to do whatever it takes to get it going. I have installed like 6 times now .. To try and get it to match my exact needs...

My system appears slow, too because of my use of AMD instead of P4, and not having the right kernel-686 installed. even though my system is AMD Athlon XP and should work wit the k6 or k7., it boots a little faster or seems to work better in linux-686.. I shall investigate this further.

But root login is an essentiality in getting going in a timely manner. Sure, I would risk crashing my system; however, as it is I have reinstalled like 6 times now on various drives and PCs to get past this anormally.. I need all my options open. 

This forum is still an awesome one in my book. Just the post that one knows something, and would not share it to protect me from myself is like taking away my choice... so understand where I am coming from with this.

---

### Post by metoo on 2005-11-21
Pssssst!

KDE root login with KDM:

/etc/kde3/kdm/kdmrc => AllowRootLogin=true

---

### Post by kazuya on 2005-11-21
thanks metoo.

I am not saying that I plan on being logged on in it on my day to day machine, but to expedite the usability of my PC functions. 

Thanks again guys. You all still rock in my book.

---

