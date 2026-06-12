---
title: "Enhance text boot process"
date: 2011-03-08
forum: Desktop Environments
---

### Post by HeinMueck on 2011-03-08
Hi all!

Still on lucid, I am trying to configure a decent console based boot process. I had to figure out some startup script errors and was upset what I had to fix just to see all messages properly. For me, having a 'talking' OS in favour of a Colourful-but-Black-Box-Liar without even one single record of a good logging policy is just one, but big plus of running Linux - please stop to windooze Linux ;-)

What I want: 
- add 'text' to the kernel parameters (fixed or grub editor)
- have all messages issued during the boot process on the console
- end up with a login prompt, no X
- beeing able to scroll back the messages

Why?
When I have trouble with booting, I want a simple and standard method to boot in the most transparent way. The 'text' approach seems great. In everyday use, of course I might not use this. On servers, I will use it all the time. 

What still makes me mad:

1: Somewhere within running the upstart-jobs and the rc-scripts the output gets mangled - new lines starting in the middle of the screen, all output is badly formatted using the "staircase approach". I have seen this on more machines than just mine, so I hope its a more general behavior.

Question: Who else has seen this and perhaps knows what little bugger is responsible for this effect and how to squash it?

What I found so far:

1: prevent gdm from being started
Add 'text' to the kernel parameters. You can add an extra menu item to the grub menu or just edit the grub entry during boot to have your machine start in text mode only once. This is nice, a very good template for a useful function can be found in the gdm upstart job.

2: Screen reset and deleted somewhere in the middle of the boot process:
Make sure Grub is setting the console resolution once and not resetting it again later by using
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep
in /etc/default/grub - select the resolution you want, not mine :) Even with this, the screen flickers on every 4th boot, however, the content stays. 

3: Splash screens pop up and dissapear
Only the hard way worked: remove plymouth. 
-> would love to get better ideas for this from the forum


Cheers,
Hein

---

### Post by deconstrained on 2011-03-14
You need to add the proper module(s) for a higher-resolution framebuffer (add it to /etc/initramfs-tools/modules) and remove "splash" from the command line in /etc/default/grub (assuming you haven't already). Adding "nosplash" might help too. Plus, in addition to setting GRUB_GFXMODE, you need to add "video=uvesafb:mode_option=[mode]" to GRUB_CMDLINE_LINUX_DEFAULT, where [mode] is a mode supported by your adatper;
```
sudo apt-get install v86d hwinfo
sudo hwinfo --framebuffer
```

The following has information that would be of use to you:
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)
The stuff regarding Plymouth you can ignore, but the rest of it is probably relevant.

Rebuild your initramfs when you're confident that you've configured everything properly.

---

### Post by Krytarik on 2011-03-15
First, I really like your attitude! I also like the more technical look, and having the possibility to check the output, when I disable the boot splash. But since my machine isn't a server or such, that isn't really necessary, and in the end the splash simply looks prettier.

1.) If that is enough to make GDM not run at startup, and it works for you, fine. Noted.

2.) I have it that way, "keep" didn't work for me:
```
GRUB_GFXMODE=800x600
GRUB_GFXPAYLOAD_LINUX=800x600

```3.) Put it that way, including your "text" fix:
```
GRUB_CMDLINE_LINUX_DEFAULT="text"

```Note: If you only remove "splash" there, you simply see *nothing* at boot.

But, unfortunately, I don't believe that there is a way to be able to scroll back the output text.

Greetings.

---

### Post by deconstrained on 2011-03-16
I concur, it's a thing of beauty when someone actually puts some effort into trying  to solve a problem on their own and puts detailed information about what they've gone through and exactly what the problem is, instead of the countless, spammy "this doesn't work" threads.

Depending on how it's set up (I wouldn't know) you may be able to scroll back text by holding shift and pressing page up (well, at least it works in bash).

---

### Post by Krytarik on 2011-03-16
> **deconstrained said:**
> 
Depending on how it's set up (I wouldn't know) you may be able to scroll back text by holding shift and pressing page up (well, at least it works in bash).
Are you sure? It doesn't work for me, at least not when switching to a console with Ctrl+Alt+F1.

---

### Post by deconstrained on 2011-03-17
Ah, maybe it's an Arch thing. The TTY consoles on my headless machine usually allow scrolling back.

---

### Post by HeinMueck on 2011-04-04
Hi!

Thanks for the hints you gave. I had some time this weekend to try around and made some progress.

The reason for the staircase effect was the getty on tty1 :) Cause of upstart it pops up somewhere among all other services starting and spits its prompt right into everything else. I disabled the getty on tty1 and everything was nicely readable again.

So I suggest - and will look for a solution - to put the getty on hold until you enter a console and press enter once. Or a way to postpone the start of the getty until everything else is done. Clear drawback of "event driven procedures".

I also started to make use of the fact that the gdm.conf keeps plymouth from staying when you start with the 'text' kernel param. The splash pops up for a fraction of a second and goes away, without purging the screen buffer, i.e., messages stay :)

Anyway, since the very old days of the kernel I remember it was possible to scroll back with shift-pageup, but only as long you did not switch to another console. Buffer gets deleted once you press Alt-Fx to switch. So starting X forces the output to a different tty and thus deletes the buffer before you even had a chance to use it. Pitty, but yet explainable.

Cheers,
Hein

---

### Post by Krytarik on 2011-04-04
> **HeinMueck said:**
> Or a way to postpone the start of the getty until everything else is done.
Although I don't really know how it's start up, how about running it either
a) as one of the last services in "/etc/rc*.d" or
b) through "/etc/rc.local" ?
> **HeinMueck said:**
> 
I also started to make use of the fact that the gdm.conf keeps plymouth from staying when you start with the 'text' kernel param. The splash pops up for a fraction of a second and goes away, without purging the screen buffer, i.e., messages stay

Even if you only remove the parameters "quiet" and "splash", the boot splash won't get shown, and instead all boot output. Setting "text" just additionally prevents GDM from starting.

Are you sure that it's the boot splash that flickers up, and not just a switch of the video mode? Because it really wouldn't make sense.

---

### Post by HeinMueck on 2011-04-04
> **Krytarik said:**
> Although I don't really know how it's start up, how about running it either
a) as one of the last services in "/etc/rc*.d" or
b) through "/etc/rc.local" ?

The getty's are usually a pure init job, as they are replaced by the shell once you login and respawned by init once you close the shell. Thus the tty's upstart job has the keyword respawn with included.

I guess that the way upstart works makes it impossible to predict when it would be the right time to have the getty spit out its prompt. You just dont know when all startup processes have finished and stop writing to the terminal. So the easy solution is not having a getty on the default terminal and the more sophisticated one is request a prompt once you need it.

> **Krytarik said:**
> Even if you only remove the parameters "quiet" and "splash", the boot splash won't get shown, and instead all boot output. Setting "text" just additionally prevents GDM from starting.

You are right. Although - funny enough - after all that playing around having quiet set or not makes no difference on my machine anymore; but that is for sure a completely different story ;-)

> **Krytarik said:**
>  Are you sure that it's the boot splash that flickers up, and not just a switch of the video mode? Because it really wouldn't make sense.

I'm sure the flicker is caused by a switch of video modes. As I understood it from the grub docs, there is one value 'before the flicker' [GRUB_GFXMODE] and one 'after the flicker' [GRUB_GFXPAYLOAD_LINUX].  It even flickers when you set a) both of them to the same value and b) the latter to 'keep', which should do something the valuename indicates. I could live with the flicker, but sometimes it the scrollback buffer gets deleted too and you cant access the 'before-the-flicker' messages anymore.

My problem is that I dont have much knowledge about KMS. Maybe reading will help here. Let me check ;-)

---

