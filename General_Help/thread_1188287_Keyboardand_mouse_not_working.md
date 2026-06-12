---
title: "Keyboardand mouse not working"
date: 2009-06-15
forum: General Help
---

### Post by Stugol on 2009-06-15
Okay, I've been told I have to be more polite, apparently, and start my thread again. Apparently complaining about Ubuntu committing suicide all by itself is a big no-no. So here goes.

Last night I installed Ubuntu 9.04 and - after several other problems I won't go into - it asked permission to install official updates. I agreed. After a couple of minutes the screen went black, and stopped responding. It wasn't the screen saver or anything silly like that. I hit reset.

It loaded up again. I entered the username and password. The password box did not go away; nor could I type into it anymore. The mouse still moved and the shut down menu was still accessible. However, selecting shut down or restart merely caused the same featureless black screen as I mentioned earlier.

I went into recovery mode and repaired the graphics settings. This didn't help. I then asked it to repair damaged packages. When it loaded back into Ubuntu, the keyboard and mouse didn't work. They were USB, but I tried a PS/2 one and it still didn't work.

I'm running on a 64-bit AMD dual-core processor. I will post full specs when I can (I'm not at the machine just now).

Would anyone be so kind as to suggest a solution?

---

### Post by CatKiller on 2009-06-15
Do you happen to remember what was in the process of being updated?

Keyboard and mouse are handled by X when you're in a graphical environment. If your keyboard works OK when you're in the Recovery mode's root shell, then I'd look at X being broken. If your keyboard doesn't even work there then I'd imagine that it's some kind of problem with your Synergy install, although I've never used it so I couldn't help you much there. I just looked at what it did on Wikipedia.

---

### Post by Stugol on 2009-06-15
> **CatKiller said:**
> Do you happen to remember what was in the process of being updated?

Uhh...just a bunch of stuff. I dunno. It was an automated process that presumably would have terminated with a restart, so I wasn't paying much attention.

> **CatKiller said:**
>  Keyboard and mouse are handled by X when you're in a graphical environment. If your keyboard works OK when you're in the Recovery mode's root shell, then I'd look at X being broken. If your keyboard doesn't even work there then I'd imagine that it's some kind of problem with your Synergy install, although I've never used it so I couldn't help you much there. I just looked at what it did on Wikipedia.

Well, the USB keyboard was no use in the recovery mode either; but the PS/2 worked. So it's an X problem. But I don't know how to fix it.

Should I just give up and put 8.04 on there and hope it doesn't happen again? It doesn't really inspire me with confidence to know that an automatic update can totally sod up my OS without any hope of repair.

---

### Post by CatKiller on 2009-06-15
> **Stugol said:**
> Well, the USB keyboard was no use in the recovery mode either; but the PS/2 worked. So it's an X problem. But I don't know how to fix it.

Should I just give up and put 8.04 on there and hope it doesn't happen again? It doesn't really inspire me with confidence to know that an automatic update can totally sod up my OS without any hope of repair.

These things can happen. Whatever the OS. You appear to have been the victim of a freak occurrence with the interruption to your update. No one can say it won't happen again, since we haven't established what caused it yet.

8.04 is a Long Term Support release (supported till April 2011) and doesn't have some of the more experimental things in; each release only gets security updates with new features coming out with new releases. You might find that it works better for you, and since it only takes about half an hour to install you might find it quicker to do that than to isolate your problem. I understand that this is a fairly fresh install, so you won't be losing any customisation.

Otherwise, from the root console, you could run ```
dpkg-reconfigure xserver-xorg
``` to try to reconfigure X's keyboard and mouse settings. You might also find it helpful to remove synergy temporarily in case that's messing things up at all.

For the record, it's only kernel updates that require a restart. Occasionally you'll need to restart an application if that application has been updated.

---

### Post by Stugol on 2009-06-15
> **CatKiller said:**
> These things can happen. Whatever the OS. You appear to have been the victim of a freak occurrence with the interruption to your update. No one can say it won't happen again, since we haven't established what caused it yet.

You don't think it might be a good idea to analyse my system to find out what went wrong; to help The Powers That Be to fix the update to avoid it happening again?

> **CatKiller said:**
> 8.04 is a Long Term Support release (supported till April 2011) and doesn't have some of the more experimental things in; each release only gets security updates with new features coming out with new releases. You might find that it works better for you, and since it only takes about half an hour to install you might find it quicker to do that than to isolate your problem. I understand that this is a fairly fresh install, so you won't be losing any customisation.

Yes, you might be right. Although, if I do that, there won't be any going back - we will never know what happened.

> **CatKiller said:**
> Otherwise, from the root console, you could run ```
dpkg-reconfigure xserver-xorg
``` to try to reconfigure X's keyboard and mouse settings.

Okay, I'll try that. How do I get to the root console without using the keyboard or the mouse? Is it something to do with the recovery mode offered by the GRUB boot menu?

> **CatKiller said:**
> You might also find it helpful to remove synergy temporarily in case that's messing things up at all.

Remove Synergy? Without using the keyboard or the mouse? I'd be interested to know how that might be achieved.

---

### Post by CatKiller on 2009-06-15
> **Stugol said:**
> You don't think it might be a good idea to analyse my system to find out what went wrong; to help The Powers That Be to fix the update to avoid it happening again?

Yes, you might be right. Although, if I do that, there won't be any going back - we will never know what happened.

It's not like they trawl through the forums with us proles. Unless you file a bug report, they'll never know. It's only of academic interest to you and I at this point.

> Okay, I'll try that. How do I get to the root console without using the keyboard or the mouse? Is it something to do with the recovery mode offered by the GRUB boot menu?

That's right. It used to only offer single-user mode, which just dropped you into a root shell without starting any of the services. I understand there's a menu now, but one of the options still gives you a root shell. I can't tell you what it's called, because I've not had to use it, but it's there.

You'll be running as root, so any command that would normally need sudo won't. Obviously don't do anything silly like rm -rf /. When you want to reboot the computer to try out your changes, you can use ```
shutdown -r now
```

> Remove Synergy? Without using the keyboard or the mouse? I'd be interested to know how that might be achieved.

Ah, but you've already said that you can use the keyboard in single-user mode. So you won't need to either ssh into that machine or use mount/chroot from the live cd to affect the installed packages on the hard drive whilst using the live cd's configuration, which are the two solutions that occurred to me off the top of my head for ways that you could accomplish the task without using the broken configuration on that machine.

```
aptitude remove synergy
``` should do it, if you installed it through the package management system.

---

### Post by Stugol on 2009-06-15
> **CatKiller said:**
> Ah, but you've already said that you can use the keyboard in single-user mode

Actually, I don't remember saying anything of the sort.

It does, however, work in single-user mode. And I tried your suggestions. And it didn't help at all.

Although I appreciate your advice anyway.

I'm currently in the process of installing 8.04 over the top of it; so I'll see how that goes.

---

### Post by CatKiller on 2009-06-15
> **Stugol said:**
> Actually, I don't remember saying anything of the sort.

It does, however, work in single-user mode. And I tried your suggestions. And it didn't help at all.

Single-user mode and Recovery mode are synonymous in my head. There may be circumstances where they differ in practise, but I don't know what they are.

Shame it didn't help, really.

> Although I appreciate your advice anyway.

I'm currently in the process of installing 8.04 over the top of it; so I'll see how that goes.

I hope you have more luck this time out. Hopefully it was just one of those things - cosmic rays or whatnot - and you won't have any trouble with updates in the future.

I forgot to say; welcome to the community. I hope you have a better experience in the future after your rough start.

Lots of hope there but, hey, it's late.

---

### Post by Stugol on 2009-06-16
[SIZE=4]Okay, I installed 8.04 over the top of it. Installed Synergy. Added 1280x1024 to the xorg.config. Installed all the updates. Installed the printer.

So, exactly how stable IS this "older, more stable" build of Ubuntu? Well...

[/SIZE][INDENT][SIZE=4]- The automatic updates window won't show - clicking the arrow in the system tray shows a window for a fraction of a second, then it disappears again. All I see is a flicker. I can right-click and choose to install the updates, but not view them beforehand.
[/SIZE][/INDENT][INDENT][SIZE=4]- Firefox won't run  - selecting it from the Applications menu does nothing.
[/SIZE][/INDENT][INDENT][SIZE=4]- The .deb installer for TrueCrypt won't install - double-clicking on the file does nothing.
[/SIZE][/INDENT][INDENT][SIZE=4]- The .tar.gz installer for TrueCrypt (that contains the .deb installer) won't install - complains about a screwup in python.
[/SIZE][/INDENT][INDENT][SIZE=4]- Installing the EasyCrypt package through Synaptic doesn't help either - it won't run after it's installed, complaining about a python problem.
[/SIZE][/INDENT][INDENT][SIZE=4]- The last straw was when the entire system FROZE UP completely. For the second time, I might add.
[/SIZE][/INDENT][SIZE=4]
I'm gonna try Fedora and see if it's any more stable. Honestly guys, could Ubuntu be any more unstable, awkward and frustrating?? I mean, how much of a masochist do I have to BE?
[/SIZE]

---

### Post by Stugol on 2009-06-16
Right, well, Fedora is too unhelpful. I'm gonna try Ubuntu WITHOUT any updates.

---

### Post by Stugol on 2009-06-16
Nope, still crashes. Any ideas on how to find out what's causing it? Any kind of log, maybe?

---

### Post by CatKiller on 2009-06-16
dmesg has kernel logs.

There is a utility at System -> Administration -> Log File Viewer that will let you easily see the standard system logs.

---

