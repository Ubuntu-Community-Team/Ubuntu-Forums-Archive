---
title: "I Want To Make Ubuntu Speedier Than it Already Is"
date: 2005-08-27
forum: Desktop Environments
---

### Post by jlacroix on 2005-08-27
I have the day off today, wanted to take the time to remove unnecessaries from my system. Basically, remove all the programs that I don't even use. The way I see it, unused programs are taking up space. For example, in System-Monitor, it shows Evolution Exchange running, and I don't have an Exchange server, so I shouldn't have this running.

Also, I have Openoffice.org2.0 installed, as well as Openoffice.org1.x installed. I don't need Openoffice.org1.x anymore as I am using the newer release. I try to remove that program, and Evolution Exchange, and it wants to also remove "ubuntu-desktop". That scares me. What is that? Is it safe to remove it? (BTW, I am trying this all in Synaptic).

Anyway, part of the reason I want to do all this, is because my system does run very fast, but when I have more than three programs open, my Opengl games run like crap until I close running programs. I just want to get rid of all the stuff I don't need and save RAM for the stuff I do need, know what I mean?

Here is a list of stupid questions, in addition to the above:
1.)  My Ubuntu system is networked to two other PC's using Samba. That and Internet browsing is the only networking I do. So, do I need the SSH client running?

2.)  Evolution Data-Server, do I need that? I use Evolution for my GMail accounts, just your basic email accounts. Data-server is taking 69.5MB of RAM!

3.)  I think I killed my Postfix email client too, don't use it. It doesn't start up anymore, I know that, but when shutting down it runs a script to shut that down and complains that its not even running. Minor annoyance, but still...

4.)  What is Gnome-VFS? GPG Agent? 

5.)  Attached are some images of BUM (Boot-up Manager) are there any other things I can remove safely other than what I have already?

You guys are awesome, I know its alot to ask but I just want to remove the bloat from my Ubuntu. Thanks!

---

### Post by dbcoder on 2005-08-27
Well, an alternative to removing software is recompiling a more stripped down kernel.


Ubuntu comes with a fairly cumbersome default kernel to cover the wide spectrum of hardware.  With a stripped down kernel you can do so much more in less time.  It's faster and it require much less RAM.  If you follow my advice you should check the preemptive option in the configuration program. (That is if you use the vanilla source from kernel.org).

What I do is uncheck everything and check things I need afterwards.  A tip though, if you are using sata drives add support for scsi and the drivers directly into the kernel. :P

There is a howto you can find by searching for Kernel Compilation.  Sorry I can't link you, search is down right now.  I hope this whole forum mess (and this apt-get mess) fixed soon.

---

### Post by dbcoder on 2005-08-27
Well, an alternative to removing software is recompiling a more stripped down kernel.


Ubuntu comes with a fairly cumbersome default kernel to cover the wide spectrum of hardware. With a stripped down kernel you can do so much more in less time. It's faster and it require much less RAM. If you follow my advice you should check the preemptive option in the configuration program. (That is if you use the vanilla source from kernel.org).

What I do is uncheck everything and check things I need afterwards. A tip though, if you are using sata drives add support for scsi and the drivers directly into the kernel. :P

There is a howto you can find by searching for Kernel Compilation. Sorry I can't link you, search is down right now. I hope this whole forum mess (and this apt-get mess) fixed soon.

---

### Post by manicka on 2005-08-27
You can safely remove ubuntu-desktop, just make sure you reinstall it before upgrading to breezy in the future

---

### Post by jlacroix on 2005-08-27
Will I still be able to do an apt-get dist-upgrade to upgrade individual software after removing ubuntu-desktop?

Also, I tried to compile a kernel, I used to do that with every distro but kernel compiling seems to be broken under Ubuntu.

I got nasty kernel panic's and VFS errors when compiling a custom kernel, using the same method I used when I used to use Fedora back in the day.

---

### Post by dbcoder on 2005-08-27
Are you using a SATA drive?

---

### Post by jlacroix on 2005-08-27
To be honest I don't know what that means. My hard drive is an 80GB Seagate 7200rpm internal IDE drive. My CD Rom drive is a Samsung DVD/RW Combo drive, also IDE.

Not sure if that answers your question...

---

### Post by dbcoder on 2005-08-27
Hrm, well, SATA is similar to IDE because it is a standard for hard drives.  SATA is a faster solution, but requires built-in drivers to boot.  That's why I was asking.  That could be a possible reason why you got kernel panic.  Did you use this howto: [HERE](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation) ??

---

### Post by jlacroix on 2005-08-27
I think I tried that once. However, I don't really use howto's anymore, I used to, but I've done it so many times in other distro's, I have it memorized. This is what I do from the best of my memory:

I got to kernel.org and get the latest kernel, whatever that happens to be.

I extract it to user/src

I "cd" into directory /usr/src/kernelfoldername

make xconfig
(Tweak kernel)
make
make modules
make modules_install
make install

Then I update the grub menu.lst. Of course, I omitted the "sudo" command but you get the idea.

---

### Post by dbcoder on 2005-08-27
Hrm, that sounds right from what I used to do with suse.  But it's much easier in that howto :P.

---

### Post by moopere on 2005-08-27
[QUOTE=dbcoder]Well, an alternative to removing software is recompiling a more stripped down kernel.


Ubuntu comes with a fairly cumbersome default kernel to cover the wide spectrum of hardware. With a stripped down kernel you can do so much more in less time. [/QUOTE]

Is this true?  I know its the standard advice thats been given out for years and years.  From a theoretical point of view I can understand why it _might_ be true but is it in reality?

What benchmark do folks use to test theories like that above?  I've done a bit of fiddling over the years and empirical evidence would suggest to me that fiddling around with compiling my own kernel doesn't appear to produce increases in speed (at the user interface level anyway) that justifies even the small amount of effort required.

In fact, I struggle to find any discernable difference, again from the user interface level, when I change from a 386 kernel to a 686 one.

Comments anyone?

Craig

---

### Post by jlacroix on 2005-08-27
The howto when I tried it a long time ago didn't work either.

---

### Post by dbcoder on 2005-08-27
[QUOTE=moopere]Is this true?  I know its the standard advice thats been given out for years and years.  From a theoretical point of view I can understand why it _might_ be true but is it in reality?

What benchmark do folks use to test theories like that above?  I've done a bit of fiddling over the years and empirical evidence would suggest to me that fiddling around with compiling my own kernel doesn't appear to produce increases in speed (at the user interface level anyway) that justifies even the small amount of effort required.

In fact, I struggle to find any discernable difference, again from the user interface level, when I change from a 386 kernel to a 686 one.

Comments anyone?

Craig[/QUOTE]


Well, I timed my boot times with the stock kernel and my configured kernel and it was about 10 seconds faster.  I've noticed firefox starts faster using the time command.  Just everthing runs faster and I have less ram utilization.  It's simply because it's 1: Preemptive, and 2: doesn't run excess unneeded code.  I mean I STRIP that kernel down.  I uncheck EVERYTHING and then check what I need.  IT's supa-fast.

---

### Post by jlacroix on 2005-08-27
I want to do that, uncheck everything and check only what I need, but I don't know what it is that I need. Know what I mean? I don't think a beginner can do all that. :(

---

### Post by Wide on 2005-08-27
You may also want to look into what starts at boot

You can run rcconf in a terminal & choose not for all programs to start at boot

If you dont have rcconf, sudo apt-get install rcconf

:)

---

### Post by dbcoder on 2005-08-27
Well, I can get you started.  You can get A LOT of junk out of the way by simply removing hardware support for things you don't have.


For example, say you have an SB LIVE! card, uncheck every other sound card listed.  Or if you don't use Firewire, uncheck it. :P

MOST things you haven't heard of (technologies, like firewire, usb, atm) you don't have, so you can uncheck.

---

### Post by doclivingston on 2005-08-28
[QUOTE=jlacroix]Also, I have Openoffice.org2.0 installed, as well as Openoffice.org1.x installed. I don't need Openoffice.org1.x anymore as I am using the newer release. I try to remove that program, and Evolution Exchange, and it wants to also remove "ubuntu-desktop". That scares me. What is that? Is it safe to remove it? (BTW, I am trying this all in Synaptic).[/quote]

"ubuntu-desktop" is a meta-package, which means it's job is to make sure that the default desktop packages are installed. Removing it won't have any effect while running Hoary - however you won't automagically get a full desktop when upgrading to Breezy if it isn't installed. As other people have pointed out, you can just re-install it before upgrading to Breezy.

[QUOTE=jlacroix]1.)  My Ubuntu system is networked to two other PC's using Samba. That and Internet browsing is the only networking I do. So, do I need the SSH client running?[/quote]

Unless you are logged into a remote machine the SSH client shouldn't be running, and the SSH server isn't installed by default.


[QUOTE=jlacroix]2.)  Evolution Data-Server, do I need that? I use Evolution for my GMail accounts, just your basic email accounts. Data-server is taking 69.5MB of RAM![/quote]

EDS does several other things, such as having appointments appear in the calendar that drop down from the clock panel applet, making alarms works, etc. Also it probably isn't actually taking up ~70Mb of RAM, because that includes various libraries that are shared with other programs and only loaded into memory once. A slightly better measure of how much memory an application is using is (RSS - shared memory + a bit), which for EDS on my machine is 4.5Mb.

[QUOTE=jlacroix]4.)  What is Gnome-VFS? GPG Agent?[/quote]

Gnome-vfs is the "Virtual File System" that lets gnome applications access non-local files, e.g. via ftp, samba, sftp, etc. Most gnome application use this so you can't get rid of it.

GPG-agent is the process that deals with you GPG keys, for encrpyed mail, etc.



Hope this helps figure out what is important, and what isn't

---

### Post by jlacroix on 2005-08-28
Thanks, that helps a bunch!

Now, I just finished recompiling a new kernel based on that howto, and it didn't work. Kernel panic, something about VFS and the filesystem. Not sure the exact message. Its really wierd because I can recompile a kernel on any distro, but never Ubuntu.

I did some poking around. I didn't get an initrd file with that howto! So I guess there's no way it can boot without one. How do I make one? My kernel version (the new one) will be 2.6.12.5.

HELP! :(

---

### Post by zee on 2005-08-28
did you try to disable the ramdisk?

although disabling the ramdisk means, you compile the IDE drivers into the kernel and not as modules.

zee

---

### Post by jlacroix on 2005-08-29
How do I do that? I'm confused, and desperate to get this working.

---

