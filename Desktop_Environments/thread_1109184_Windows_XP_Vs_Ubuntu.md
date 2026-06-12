---
title: "Windows XP Vs Ubuntu"
date: 2009-03-28
forum: Desktop Environments
---

### Post by JCC_0863668 on 2009-03-28
[SIZE="4"][FONT="Arial Black"]Hello my friends again :)
I was wondering if I can use Ubuntu Desktop Enviroument in Windows XP, please if it can happen could you show how, please :)

Thnaks Alot ;).[/FONT][/SIZE]

---

### Post by andrea000 on 2009-03-28
There are a number of ways to do what you trying to do.Dual booting is one or running in virtual box just to name a few.
My self i run windows xp pro in virtual box and love it but 
i don't run very much software that runs on windows.But if your
wanting to run ubuntu inside windows then virtual box would be
what your looking for. 

here is a [link]("http://www.virtualbox.org/") to virtual box


here to a [link]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") to How to dual boot Windows XP and Linux

---

### Post by toehead2 on 2009-03-28
wubi would allow you to install Ubuntu in Windows, also it is reportedly easier to remove if needed.

---

### Post by UbuntuNerd on 2009-03-28
check this link: [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by jacksaff on 2009-03-28
If you mean you want to be running XP but with the gnome desktop (the desktop ubuntu uses) then you are out of luck.
As already posted, lots of ways to have ubuntu and xp on the same machine, and even running at the same time via virtualisation, but no way to run gnome in xp.

---

### Post by joey-elijah on 2009-03-28
> **jacksaff said:**
> If you mean you want to be running XP but with the gnome desktop (the desktop ubuntu uses) then you are out of luck.
As already posted, lots of ways to have ubuntu and xp on the same machine, and even running at the same time via virtualisation, but no way to run gnome in xp.

Not entirely out of luck - colinux and 'andlinux' do this - running linux inside and alongside windows seamlessly not in a virtual machine or anything like that either.

---

### Post by JCC_0863668 on 2009-03-29
[COLOR="Black"][SIZE="4"]Thanks alot my friends ;)
you've shown some stuff :)

see you soon :)[/SIZE][/COLOR]

---

### Post by Jpardue on 2009-04-08
Thanks for the awesome link andrea, that really helped me out. I need to run Windows XP PRO for one of my Comp classes at school and virtualization is great for that.

---

### Post by andrea000 on 2009-04-08
> **Jpardue said:**
> Thanks for the awesome link andrea, that really helped me out. I need to run Windows XP PRO for one of my Comp classes at school and virtualization is great for that.

no problem Jpardue happy to help out

---

### Post by Trapper on 2009-04-08
Just my 2 cents worth in regards to wubi on XP. I saw this thread referring to that so I booted into my XP for the first time in many months and installed wubi. The install went beautiful....but.....then I did the 256 available updates. Right in the middle of installing them a notification of a crash came up. I wasn't able to determine what crashed though because the machine absolutely froze up and remained that way until I forced a reboot. Haven't been able to reboot the XP install of Ubuntu since. I just get a kernel panic, blah, blah, blah. I have 2 normal installs of Ubuntu on this box and never have a problem. 

I'm not so sure this wubi thing should be used to impress windows users with linux. If I was a windows user it sure wouldn't impress me to see a linux install crap out during updates.


Trapper

---

### Post by Hooya on 2009-04-08
You can run KDE on windows.  Run a google search for "KDE for Windows" and see what you get!

It's not the full desktop environment, but it's pretty cool anyway.  Still kinda buggy.  WUBI is still the best idea for that without dual booting.

---

### Post by crazypeppo on 2009-04-10
> **Trapper said:**
> 
I'm not so sure this wubi thing should be used to impress windows users with linux. If I was a windows user it sure wouldn't impress me to see a linux install crap out during updates.


Trapper

If you just want to impress them why not just run a live cd?

---

### Post by computermacgyver on 2009-04-10
> **crazypeppo said:**
> If you just want to impress them why not just run a live cd?

I think the idea of wubi is to avoid "scary" partitioning. I suggested wubi to a friend for this reason, and he had the same issues. Complete freeze during updates and now kernel panic. I'll visit him this weekend to see if I can sort it out. But this certainly is not an impressive intro to Ubuntu.

---

### Post by Trapper on 2009-04-11
I eventually got the situation with the update failure, kernel panic, etc. sort of figured out in my wubi install. It took uninstalling and reinstalling for me, personally, to do so. The problem apparently lies within the kernel update, of all things. Ultimately, I just removed the kernel update from the update package list. Then everything else updated okay. I've attempted to update the kernel several times since doing that but all attempts have failed. At least now I don't get a kernel panic.

Here's basically what I'm seeing when I attempt to update the kernel:

e. /var/cache/apt/archives/linux-image-2.6.27-7-generic-2.6.27-7.16-i386.deb: unable to make backup link of './boot/vmlinuz-2.6.27-7-generic' before installing new version.

For whoever said

> If you just want to impress them why not just run a live cd?

I am not trying to impress anyone. I am simply saying that anyone that chooses the wubi method to get a look-see of ubuntu linux and gets confronted with this problem is likely going to get a very incorrect impression of ubuntu and perhaps linux in general. Lest we forget, wubi is an automated install and when the user is confronted with havoc simply by doing an initial update they are well aware that they did not create the issue.

As for the Live CD being used to impress someone ... I've never been "impressed" by any OS Live CD. It's slow, awkward and read only, basically. CD does not do an OS justice, nor is it a true representation of it or of it's capabilities. It just gives a generalized look and it's real usefulness for a newbie lies within using it to install the OS to more reasonable media.

Have a good weekend everyone!

---

### Post by crazypeppo on 2009-04-11
Instead of starting a new thread on Live vs. running inside an exsisting os:

The point I was making is that a live cd of any flavor can give a person enough feel for a new operating system to see if they would like to try it out. You could put in a mandriva live disk, a knoppix live disk and a ubuntu live disk and quickly show a new user that many differnet versions are available.
One impressive factor is that most live cd's recognize internet connectio0n without any configuration. Another benefit could be showing users that you can access windows files with linux applications.
For me, I love to "impress" peple who can't accesss their microsoft computer due to bugs, viruses and such by putting in a knoppix disk and retrieve all of their files that would otherwise be "lost".
As far as speed and read only: They are slower than an installed version agreed but, live cd's are not "slow". Read only? You can use a removable media device and save whatever you want.
All in all I would rather show someone who has never used linux a live cd to play around with than install wubi and a linux version in a windows environment.

---

