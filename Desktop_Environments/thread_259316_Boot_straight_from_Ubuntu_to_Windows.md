---
title: "Boot straight from Ubuntu to Windows?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by MaveZ on 2006-09-17
Hi.

A quick question.

I have a dual boot system with Ubuntu and Windows XP. I like to keep Ubuntu as my #1 boot option, so that I dont need to do anything except to turn the power on to boot up in Linux.

However, I do like to use Windows XP as well.

Is it possible to have some sort of a boot option or a script, that boots the computer from Ubuntu desktop straight to Windows?

The Quit button in Gnome has the options for logoff, restart and shut down, but I'd like to see a option for "Boot to Windows" in there too.

Now I need to wait the system to shut down and select the corresponding operating system from Grub menu. Its not a big deal, but automating the process would be a nice feature.

So, can it be done, and how? ;)

---

### Post by missmoondog on 2006-09-17
what do you think restart is for? boot to windows. how else do you think it could be done? you can not do what you want to do!

---

### Post by Lord Illidan on 2006-09-17
I think the only solution is to stay there when it restarts and chose Windows from grub...but that would be too much work :)

---

### Post by PvSinNL on 2006-09-17
Well, the only thing I can think of would be to have a script that modifies your grub boot settings before rebooting the system. I'm no expert here, but I think that should be possible. Whether something like that could be incorporated into the GNOME "Quit" menu I don't know...

---

### Post by tturrisi on 2006-09-17
Just make xp the first choice in the grub menu.

---

### Post by Lord Illidan on 2006-09-17
> Just make xp the first choice in the grub menu.

Impossible ->

> 
I have a dual boot system with Ubuntu and Windows XP. I like to keep Ubuntu as my #1 boot option, so that I dont need to do anything except to turn the power on to boot up in Linux.

> Well, the only thing I can think of would be to have a script that modifies your grub boot settings before rebooting the system. I'm no expert here, but I think that should be possible. Whether something like that could be incorporated into the GNOME "Quit" menu I don't know...

Possible, but if something goes wrong?? And how will you restore grub.conf after you reboot??

---

### Post by MaveZ on 2006-09-17
Exactly.
Afterall, the startup happens with Grub, which I recon as a Linux bootloader.. Isnt everything possible with Linux? ;)

*edit
And doesnt grub do something after you have hit the enter key to select the operating system? That would be the place to restore the original config to run Ubuntu as #1 operating system in next startup.*


And because it might be "too much work", I decided to ask here first before trying it alone...

---

### Post by lha on 2006-09-17
I hope [this PC World article]("http://www.pcworld.com/article/id,118200-page,1/article.html") helps.

---

### Post by dpoole on 2006-09-17
Pc world article excelent ! Thank you.:)

---

### Post by -deadcats on 2006-09-17
Another option--unless your want Windows mostly for gaming--might be VMWare Workstation. I run Ubuntu, period. But from within Ubuntu, I run Win98, Win2K, and WinXP--and a standard selection of software, including Office Professional--all from within VMWare. I do this to test my wife's Windows software (she's an ISV). 

What makes it handy is that all I have to do is click on the VMWare or VMPlayer icon, select whatever flavor of Windows I want to run, and click on it. No more having to shut down Ubuntu, restart my machine, then load Windows. Just do it all from within Ubuntu. (Or SuSE, or Mandriva, or whatever.) It runs Windows in whatever resolution I want, and incredibly it seems faster than Windows standalone. I guess that's because it only has to load a select set of drivers, libraries, etc.

Anyway, that's another option. Unless you're much of a gamer. VMWare doesn't do well in 3-D gaming yet. But if that's all that's holding you back, then may I suggest Cedega?

regards,
-dc

---

