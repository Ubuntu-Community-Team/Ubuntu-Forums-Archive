---
title: "File Operations Window Blank Ubuntu 9.10"
date: 2010-01-06
forum: Desktop Environments
---

### Post by beastrace91 on 2010-01-06
Hey All,

Running Ubuntu 9.10 64bit fully update to date. When I went to move some files around this morning I noticed that all my file operations Windows are blank (however the files are actually still getting copied - however I cannot see the progress)

Ideas? Image:

[IMG]http://i47.tinypic.com/2n9kz9j.png[/IMG]

Regards,
~Jeff

---

### Post by gabreal2k on 2010-02-08
I have this same problem. 

I'm running Ubuntu Karmic Koala on a Dell 8200, p41.8ghz, nvidia geforce2 mx graphics card, 2gb RAM. 

This morning I reinstalled Ubuntu and wound up with no progress bar in my file transfer window.

My system is a 32bit system.

---

### Post by beastrace91 on 2010-02-08
Reboot.

~Jeff

---

### Post by gabreal2k on 2010-02-08
Well I dont know if it was the reboot that did it, as I had already rebooted several times but the progress bar is back. 

Now if I could get this machine to come out of suspend it would be perfect...lol

---

### Post by beastrace91 on 2010-02-09
> **gabreal2k said:**
> Now if I could get this machine to come out of suspend it would be perfect...lol

Eh, Ubuntu boots so quickly I don't bother with suspend - it is buggy I've found regardless of operating system...

~Jeff

---

### Post by edmondt on 2010-02-09
> **beastrace91 said:**
> Eh, Ubuntu boots so quickly I don't bother with suspend - it is buggy I've found regardless of operating system...

~Jeff

That's a very silly response... suspend is only buggy on ubuntu, works perfect on OSX and Windows 7.

My rating on Suspend/Resume 
Ubuntu - 5.5/10
OSX - 10/10 (really quick resume!)
Windows 7 - 9/10 (works very well)

---

### Post by gabreal2k on 2010-02-10
Maybe this will help? 

If I click the upper right hand user name and select shutdown, as expected, the computer shuts down. 

If I right click a panel and: add to panel> add shutdown button>

 then click said button and choose shutdown the monitor freezes, with garbled colored lines, and the system hangs. 

System ALWAYS hangs if I use this panel button to suspend.

Could be a different way of executing a shutdown; I don't know. 

I haven't tried using the suspend from the upper right corner of the screen yet. 

In puppy linux, I have a line I add to Menu.lst to make it boot properly: acpi=force irqpoll

I'm wondering if perhaps something like this isn't needed in the suspend scripting to force the system to query the hardware thus updating any kind of hardware state=???

I'm not a programmer/developer though, so I don't know if I'm talking out my A** or not.

I do know without "acpi=force irqpoll" I get the dreaded "kernel panick: unable to mount virtual file system" syndrome.

---

