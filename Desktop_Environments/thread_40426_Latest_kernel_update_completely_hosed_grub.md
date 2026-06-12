---
title: "Latest kernel update completely hosed grub"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Magneto on 2005-06-09
wondering if anyone else had seen this
i updated my kernel since the synaptic updater went off telling me there were updates available

no back up of my menu.lst - completely overwrote it - 
the backup - menu.lst~ is a exact replica of the menu.lst that was just installed :|

erased any memory of the dual boot setup or the other changes I made to it 
this is the worst thing Hoary has done so far so I'm only a little bit aggravated

---

### Post by Robban59 on 2005-06-10
Hi there,

I also got my Ubuntu screwed up since I upgraded an image kernel, am still struggling to reactivate LILO or/and install GRUB, have updated some libraries that were found faulty, please see my post : [http://ubuntuforums.org/showthread.php?t=38011](http://ubuntuforums.org/showthread.php?t=38011)

I'm quite a newbie at Linux, and sadly I have not received much help from the forum, I hope it is because most other users have not run into our problems.. O:) 

Hope you can restore GRUB without loosing your installation.

---

### Post by Joeb on 2005-06-10
[QUOTE=Magneto]wondering if anyone else had seen this
i updated my kernel since the synaptic updater went off telling me there were updates available

no back up of my menu.lst - completely overwrote it - 
the backup - menu.lst~ is a exact replica of the menu.lst that was just installed :|

erased any memory of the dual boot setup or the other changes I made to it 
this is the worst thing Hoary has done so far so I'm only a little bit aggravated[/QUOTE]


You might want to post this on one of the developers list so that whoever is maintaining the kernels might be able to at least make a backup of the menu.lst before overwriting it.  If I'm not mistaken, though, it used to just add the new enteries (obviously, it no longer does).

Actually, this problem is one of the reasons I like grub.  You just edit the menu.lst and don't have to re-run anything (that said, Lilo is definately prettier).

---

### Post by krusbjorn on 2005-06-10
[QUOTE=Magneto]wondering if anyone else had seen this
i updated my kernel since the synaptic updater went off telling me there were updates available

no back up of my menu.lst - completely overwrote it - 
the backup - menu.lst~ is a exact replica of the menu.lst that was just installed :|

erased any memory of the dual boot setup or the other changes I made to it 
this is the worst thing Hoary has done so far so I'm only a little bit aggravated[/QUOTE]

happened to me to. had to rewrite my grub.lst. manually made a backup copy of it this time, just in case. you might want to do that too ;)

---

### Post by Magneto on 2005-06-13
thanks for the replies - I was asking to see if I was nuts -everyone I had spoken to on IRC had no issues 
its not a big deal to me even though I didn't have a backup - im used to grub
just wanted to know to file a bug report 

funny thing is I didn't discover it after a reboot -  I checked before hand lmao I don't trust anything automatically messin with my boot app

krusbjorn so far me and you are the only ones that I know of- 
I will try to see if Robban59 got squared away- I don't know if his issue is the same since he mentions responding to a prompt incorrectly

---

### Post by Robban59 on 2005-06-13
Hi Magneto,

I just read your post and just now I'm at work, so can't give you more info on my problem, but when back home I will be more than happy, and grateful, if you could do a little hand holding with me so that I can get back to my Ubuntu system. 

To briefly summarize : some time ago I run Update Manager to update the kernel images both 386 and 686, although I use the -686 variant to boot; after the update, the installation script runs in a little terminal window inside the Update Manager, right ?  the it asks two questions :first is about something related to the boot block, second if it is to use the current lilo.conf; I'm just remembering on top of my head, sorry if it is incorrect, but you will surely get the point. As you know you can answer Y/N to the two questions, and I answered, if I remember well, No to the first and Yes to the second question. Then the script continued some actions, and an error message resulted.

The Update Manager ended its work,I happily worked some more time undisturbed in Ubuntu, and then shutdown for the day. When booting the next day I could't boot anymore : what I got on the screen is : 

LILO xx.yy.z .................................................................................................
.........BIOS check successful
Unpacking Linuz......

 crc error

- system halted

What is LILO trying to tell me ?? where is the fault ?

I have used both Ubuntu LIVE and Install to boot and try to fix the thing mainly re-running LILO, but to no success so far; I can boot with both of them, mount my Ubuntu root and I have checked that in / I have the 2 sym links to the vmlinuz and initrd files resident in /boot , I have tried to run LILO but get always error msg maybe because booting from CD I must modify the lilo.conf to take into account that the Linux partition where I have my boot record ( hdi1) is maybe remapped differently than when booting the standard way.

When I installed Ubuntu, GRUB didn' t manage to get installed, so I reverted to LILO, I tried grub-install but I got command not found of course.

But I think my problem is not too big, it is just that I miss a little help in restoring my boot sequence........but enough with the bla bla bla...

P.S. what does "squared away" means ?? I though I was a newbie in Linux, now I discover I'm also a newbie in English.. :)    

Regards/Robban59

---

### Post by Magneto on 2005-06-29
Same problem with update-grub

bug filed 

[https://bugzilla.ubuntu.com/show_bug.cgi?id=12277](https://bugzilla.ubuntu.com/show_bug.cgi?id=12277)

updated the kernel again and again had menu.lst wiped clean

---

### Post by Magneto on 2005-06-29
improper use of automagic kernel list markers in menu.lst  was invalidating that bug when the maintainer resolved it

---

### Post by angkor on 2005-06-29
To reinstall / upgrade grub:

1. boot from your Ubuntu InstallationCD
2. type rescue at the boot prompt.
3. select your root partition
(4. mount /usr if it's on a different partition, like it is in my case)
4. type update-grub

And reboot.

It worked for me after I ruined grub out of my own stupidity yesterday. Hope it works for you people as well.

---

### Post by pseudonym on 2005-06-29
I'm assuming you're all referring to this update -

Version 2.6.10-34.3: 

  The "Gracious Gooseberry" Release.

  Changes by Thom May:

  * [SECURITY]: Fix DoS in x86_64 x86 emulation mode:
    - Add patch stolen_from_head_CAN-2005-1765.dpatch
    (CAN-2005-1765)
  
  * [SECURITY]: Fix DoS in ptrace on x86_64 with non-canonical addresses
    - Add patch stolen_from_head_CAN-2005-1762.dpatch
    (CAN-2005-1762)

I've noticed it in the update notifier for the last few days now, but didn't want to install it until I saw an accompanying security announcement in these forums. Judging quickly by these posts, it's a good thing I still haven't :) .

Isn't such an announcement supposed to come with all these updates?

---

### Post by Magneto on 2005-07-02
[QUOTE=pseudonym]I'm assuming you're all referring to this update -

Version 2.6.10-34.3: 

  The "Gracious Gooseberry" Release.

  Changes by Thom May:

  * [SECURITY]: Fix DoS in x86_64 x86 emulation mode:
    - Add patch stolen_from_head_CAN-2005-1765.dpatch
    (CAN-2005-1765)
  
  * [SECURITY]: Fix DoS in ptrace on x86_64 with non-canonical addresses
    - Add patch stolen_from_head_CAN-2005-1762.dpatch
    (CAN-2005-1762)

I've noticed it in the update notifier for the last few days now, but didn't want to install it until I saw an accompanying security announcement in these forums. Judging quickly by these posts, it's a good thing I still haven't :) .

Isn't such an announcement supposed to come with all these updates?[/QUOTE]
 the problems I had were due to my own misuse of the menu.lst file - previously I had been using my own and then I started using Ubuntu's this time around(installation wise) and I neglected to pay attention to the area in the file designated for the automagic kernel list. I added that -34.3 update and even the updated kernel still shows the old version as did the menu.lst entries

---

### Post by littlepr on 2005-07-05
Guys,

Here's is what I get when I try to upgrade/update my kernel:

E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386


I have tried to trick it by renaming the ndiswrapper.ko to ndiswrapper.ko.bak but it still complains about the ndsiwrapper.ko file. I personally would like the script to ask if I would like to keep the current ndiswrapper since it is already configured for my wireless adapter.
 
Has anyone else run into this showstopper?

---

### Post by Magneto on 2005-07-05
[QUOTE=littlepr]Guys,

Here's is what I get when I try to upgrade/update my kernel:

E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386


I have tried to trick it by renaming the ndiswrapper.ko to ndiswrapper.ko.bak but it still complains about the ndsiwrapper.ko file. I personally would like the script to ask if I would like to keep the current ndiswrapper since it is already configured for my wireless adapter.
 
Has anyone else run into this showstopper?[/QUOTE]
 You are gonna have to disable it or run another kernel version without the driver to be able to install it- im guessing that's a custom built driver- the script won't ask to keep the current ndiswrapper since the one you built is dependent on that kernel version you were using when you made it ./configure ./make  etc

I have similar issues in Fedora Core 3 with the atmel driver I use- I dont feel like rebuilding it everytime they want to upgrade the kernel.

---

### Post by commanda on 2005-08-23
[QUOTE=angkor]To reinstall / upgrade grub:

1. boot from your Ubuntu InstallationCD
2. type rescue at the boot prompt.
3. select your root partition
(4. mount /usr if it's on a different partition, like it is in my case)
4. type update-grub

And reboot.

It worked for me after I ruined grub out of my own stupidity yesterday. Hope it works for you people as well.[/QUOTE]

Well it doesn't work for me. And I've got 2 more installations at home as well. Wonder if either of them are gonna work anymore when I get home.

Amanda  ](*,)

Edit:
At least one machine at home rebooted cleanly (haven't tested other).
Maybe the failed machine at work has had a disk failure. Strange coincidence if it has.

---

