---
title: "fsck screws my filesystem and linux"
date: 2009-01-07
forum: General Help
---

### Post by amit.padhy on 2009-01-07
Hi all,

well!fsck screwed my computer...

the story goes like this..when my computer on ubuntu 7.10 got hanged(well it did ,cpu 100% and memory also probably..keyboard wasnt responding), i switched off my computer. after a successful restart it changed everything to read only and  somethings happened... and it restarted.. this time to tell that the root filesystem has errors .So i had to run fsck as root....
so ,it supposedly fixed some of the "orphan" inodes ,some "unreferenced" ,etc. which were many in number...

This happened two or three times..meaning I had to do this over and over again..a nd the last time I did this..it took many more files/inodes..and
'y's to fix/delete/ reapir inodes...


now ,finally my computer is stable buti am not able to run most of the programs namly-firefox,linuxdcpp,sound driver , uname ,touch ,these are the ones i know not to work.(I am not able to download/reinstal/remove/completely remove and install these also)

Does naybody have a solution for this.

Thnaks in advance!!

---

### Post by blazemore on 2009-01-07
What happens when you try and run these programs?

---

### Post by amit.padhy on 2009-01-07
this is the output of sudo apt-get install firefox:

```
After unpacking 26.6MB of additional disk space will be used.
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.6+2nobinonly-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.6+2nobinonly-0ubuntu1_i386.deb
sh: touch: not found
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by amit.padhy on 2009-01-07
intially it said 
"segmentation fault(core dumped)"...

after removing it ,it says you dont have the application.install it using sudo apt-get ....

as i said some inodes were were altered in my root filesyastem

---

### Post by blazemore on 2009-01-07
whoa, i know the sticky says no, but i would really recommend reinstalling.

---

### Post by amit.padhy on 2009-01-07
i know that its the last resort..but anything else???
please help me

---

### Post by quip on 2009-01-07
> **blazemore said:**
> whoa, i know the sticky says no, but i would really recommend reinstalling.

Seconded.  Normally, I don't advise re-installation as a method to solve things (unless it's a Windows machine), but you are probably not going to want to walk through this thing, re-installing app after app.

Sometimes, all you can do is run fsck, but in case you didn't know, you removed entries in a table the filesystem uses to map references to programs.  When you removed an inode, you removed the information that tells you where on the physical hard drive that program resides.  Thus, you can see that it isn't going to be fun to fix this stuff, and your only realistic option (unless you are an uber-hacker) is to re-install each app.

Might as well back up your desired files, and then re-install it all at once.

---

### Post by Slim Odds on 2009-01-07
> **amit.padhy said:**
> well!fsck screwed my computer...

the story goes like this..when my computer on ubuntu 7.10 got hanged(well it did ,cpu 100% and memory also probably..keyboard wasnt responding), i switched off my computer

Sorry to give you the bad news, but powering down a computer cold can trash the filesystem. It's not fsck's fault.

I take it that it's an ext2 filesystem?  ext3 might have given you a better chance for survival. I usually use ext3 for the system and ext2 for home.

---

### Post by amit.padhy on 2009-01-08
I dont have any problem installing the apps once again...
the problem is my apt-get also got screwed...or some subroutine....

dpkg-deb returns a fail in exec. tar...(see above)

or is there any other way to "manually" install apt-get

---

### Post by amit.padhy on 2009-01-08
I dont have any problem installing the apps once again...
the problem is my apt-get also got screwed...or some subroutine....

dpkg-deb returns a fail in exec. tar...(see above)

or is there any other way to "manually" install apt-get

---

### Post by quip on 2009-01-09
> **amit.padhy said:**
> I dont have any problem installing the apps once again...
the problem is my apt-get also got screwed...or some subroutine....

dpkg-deb returns a fail in exec. tar...(see above)

or is there any other way to "manually" install apt-get

Uhhmmmmm.....I was referring to re-installing the whole operating system.  You could walk it through step-by-step, app-by-app, but it will take MUCH longer than just booting up, saving any desired files that you can still see, and then re-installing the OS.

As the other poster stated, if you were using ext2, you were using a non-journaling filesystem, which means that, in a nutshell, you will have great difficulty repairing the filesystem on a cold powerdown.  In that case, you should move to ext3.

---

