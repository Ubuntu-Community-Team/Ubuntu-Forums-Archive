---
title: "How should I launch Unity gui from the command-line?"
date: 2015-05-03
forum: Desktop Environments
---

### Post by typhen on 2015-05-03
Hi hi,

I'm running 14.04 and Unity desktop here. I had a weird set of issues that I managed to get fixed, but I'm looking for more understanding of my Linux system -- I want to know what went wrong!


I recently had strange issues in my gui environment:
 - shutdown/restart from the gui required authorization
 - suspend was not available from the gui -- but still worked perfectly if i incanted: sudo dbus-send --system --print-reply     --dest="org.freedesktop.UPower"     /org/freedesktop/UPower     org.freedesktop.UPower.Suspend
 - sound didn't play at all -- sound drivers weren't loaded


I eventually realised that this was caused because I'd set Grub to launch Ubuntu in text mode. specifically, I replaced this:
 - GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
with this:
 - GRUB_CMDLINE_LINUX_DEFAULT="text"


and when the system started up, I'd login as my non-root user, then i'd say
 - sudo lightdm start
to get unity up.



A notable symptom: my sound card wasn't detected at all:
aplay: device_list:268: no soundcards found...

but sound plays fine if i let grub start the gui. Is that weird? It sure looks weird to me.


I have two questions about the situation:
 1) why was I seeing these symptoms? Is there a common thread between them? It seems like maybe they are all related to authentication/permissions?
 2) is there a correct way to launch the gui from a grub text launch?

---

### Post by mc4man on 2015-05-03
I don't know if adding a text argument to the kernel boot parameters would cause such issues but if you wanted a 'text' boot display then simply removing quiet splash & updating grub  would do that with no issue (I do that here, ex. screen shot

---

### Post by alex375 on 2015-05-03
>  is there a correct way to launch the gui from
 lightdm
From dropout terminal No other way

---

### Post by v3.xx on 2015-05-04
> **alex375 said:**
> lightdm
From dropout terminal No other way
I prefer using xinitrc to launch a gui from console.  This can also be done manually with the startx command.
[https://wiki.archlinux.org/index.php/Xinitrc](https://wiki.archlinux.org/index.php/Xinitrc)

Have you tried nomodeset?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by alex375 on 2015-05-04
> This can also be done manually with the startx command.
that turns on one window with X
Where gui man?

---

### Post by deadflowr on 2015-05-04
> **alex375 said:**
> that turns on one window with X
Where gui man?


No, startx starts an X session which includes whatever desktop the user has defined, in the xinitrc file or elsewhere.
lightdm is just the display manager, from which an X session can be chosen from. Or a non-X session, such as wayland or mir.

But that is neither here nor there as the real issue is why certain settings are running for the OP as they do.

Like why the user needs to auth for shutdown from the gui...

That one seems like a user permission error, but that is a general guess.

---

### Post by alex375 on 2015-05-04
> No, startx starts an X session which includes whatever desktop the user has defined, in the xinitrc file or elsewhere.
and as result you'll see plain empty window with x sign

> @Nick You can. With a plain X server as  'session' without a window manager you can run exactly one application  full screen (without borders or other decoration). This is how these  minimal XBMC distributions work for example. I did this with Chromium  once a few years ago in 10.04 - but I didn't save the exact  configuration
[http://askubuntu.com/questions/310671/start-ubuntu-without-a-desktop-environment-but-start-an-x-application](http://askubuntu.com/questions/310671/start-ubuntu-without-a-desktop-environment-but-start-an-x-application)

Or you'll see this

---

### Post by v3.xx on 2015-05-04
The OP has not requested how to run without a window manager or desktop environment. Why bring it up? This (again) is neither here or there.

---

### Post by alex375 on 2015-05-04
i wanna say that 'startx' isnt cool idea
if you know how to tune it up maybe you can do somethin worth with it
But if you run it 'as is' ....

---

### Post by typhen on 2015-05-05
> 
I don't know if adding a text argument to the kernel boot parameters would cause such issues but if you wanted a 'text' boot display then simply removing quiet splash & updating grub would do that with no issue


So you're saying removing the word "text" and just leaving it blank will still boot into text mode? Interesting; I'll give it a shot.



> 
No, startx starts an X session which includes whatever desktop the user has defined, in the xinitrc file or elsewhere.
lightdm is just the display manager, from which an X session can be chosen from. Or a non-X session, such as wayland or mir.


Let me clarify these points to see if I understand: [assuming a default install of Ubuntu 14.04, with no changes to xinitrc etc]
I would expect the normal flow of events (on a fresh install with no config changes) to be:
 - grub starts ubuntu with "quiet splash"
 - with these kernel params, ubuntu directly invokes "lightdm start" as root
 - lightdm uses X (but not xinitrc) to display a login screen
 - the user enters credentials
 - lightdm calls "startx", using the given user account

Do I have some wrong assumptions in this sequence?
If the above assumptions are correct, then I'd expect that "sudo lightdm start" should be the correct way to start my gui (to mimic what grub/linux would normally do upon a non-text boot)?
If so, then it looks like we should assume there's some local weirdness in my install that wouldn't be reproducible on a fresh ubuntu install.


> 
Have you tried nomodeset?

> 
 Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. 

As far as I can see, nomodeset would fix graphical glitches, but shouldn't be related to the issues I'm experiencing?




I'm doing further research on kernel parameters (I think that's what they're called) to find out what "text" actually achieves. Haven't found it yet.
I'm also seeing suggestions to do this:
sudo service lightdm start

Is it possible that my error has been invoking lightdm directly instead of using service/upstart?

---

### Post by v3.xx on 2015-05-06
> As far as I can see, nomodeset would fix graphical glitches, but shouldn't be related to the issues I'm experiencing?
Yes, you are correct.  I mention it because of you needing to boot from console (text).  And although this is not a video problem, this can be a symptom of nomodeset being required.  So probably not a fix.

---

### Post by deadflowr on 2015-05-06
Well first, have you considered creating a second user to see if the problems are system problems or user problems.

And second, I think the lightdm command is wrong.
should be
```
sudo start lightdm
```
when I try it your way, it hangs...

You can see the output of the command by running ctrl + alt + F1.
This should bring you back to the text screen.
Press ctrl + alt + F7 to get back to the gui login screen.

The proper output should be some thing like
lightdm: starting/running: process:XXXX.
and it should return to the username@ubuntu~$ prompt.

The output of the command you gave was it hung with no return to the prompt...

---

