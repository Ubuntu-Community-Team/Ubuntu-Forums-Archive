---
title: "Xorg is getting on my nerve!"
date: 2005-06-15
forum: Desktop Environments
---

### Post by DFreeze on 2005-06-15
What is it with Xorg (or whatever is causing the stalls)? System lockups were one of the major reasons for me to ditch Windows, but having to reboot twice every evening is too familiar to be funny.

I'm not good enough yet with the CLI to kill the right process to get my Gnome desktop back, so I just manually reboot every time the desktop stops responding. 

Can it be something I do? I don't do anything out of the ordinary. Just internet and email, and working through some HOWTO's. Are you experiencing the same thing? Should I just wait until Xorg gets upgraded to a more stable level, or what else can I do to keep my computer working? Maybe some handy tips for the CLI to prevent having to reboot?

---

### Post by sethmahoney on 2005-06-15
Control + Alt + Backspace should restart Gnome without having to reboot your whole computer, but there's something else going on that should be taken care of, cuz it shouldn't be doing that.  So...  Are you using Ubuntu or Kubuntu?  Hoary or Breezy?  What graphics card do you have?  Sound?  Network adapter?  Any unusual hardware or software installed?

---

### Post by Penguin Man on 2005-06-15
[QUOTE=DFreeze]What is it with Xorg (or whatever is causing the stalls)? System lockups were one of the major reasons for me to ditch Windows, but having to reboot twice every evening is too familiar to be funny.

I'm not good enough yet with the CLI to kill the right process to get my Gnome desktop back, so I just manually reboot every time the desktop stops responding. 

Can it be something I do? I don't do anything out of the ordinary. Just internet and email, and working through some HOWTO's. Are you experiencing the same thing? Should I just wait until Xorg gets upgraded to a more stable level, or what else can I do to keep my computer working? Maybe some handy tips for the CLI to prevent having to reboot?[/QUOTE]
 I've been having trouble with Xorg locking up in Hoary as well (which I never had with XFree in Warty, SuSE or Mandrake on this same machine).  I updated my nvidia drivers last night thinking it might be a driver issue, we'll see if it helps.

In this case, Ctrl-Alt-Backspace wouldn't even do anything, Xorg had locked up completely and was stealing all my keystrokes/mouseclicks.  I had to login remotely and do a /etc/init.d/gdm restart to get X friendly again.

---

### Post by desdinova on 2005-06-15
If you're getting driver lockups with the Nvidia drivers,

1) its not xorg's fault - its nvidia's ;-)

2) try removing or commenting out the "RenderAccel" option in your xorg.conf

---

### Post by speedsix on 2005-06-15
I'm getting the same problem in Hoary using an Ati Radeon.

Have replaced 'ati' for 'vesa' in the /etc/X11/xorg.conf for now and its running fine.

---

### Post by afonic on 2005-06-15
[QUOTE=Penguin Man]I've been having trouble with Xorg locking up in Hoary as well (which I never had with XFree in Warty, SuSE or Mandrake on this same machine).  I updated my nvidia drivers last night thinking it might be a driver issue, we'll see if it helps.

In this case, Ctrl-Alt-Backspace wouldn't even do anything, Xorg had locked up completely and was stealing all my keystrokes/mouseclicks.  I had to login remotely and do a /etc/init.d/gdm restart to get X friendly again.[/QUOTE]
 Not much to help here, but I can suggest an easier way to restart Gnome.

Just press Control - Alt - F2, login and then sudo /etc/init.d/gdm restart

I have various problems too, but after tests I found out that the Ati drivers created them. I am not turning them off though, I need that 3D acceleration... :-)

---

### Post by sethmahoney on 2005-06-15
[QUOTE=Penguin Man]In this case, Ctrl-Alt-Backspace wouldn't even do anything, Xorg had locked up completely and was stealing all my keystrokes/mouseclicks.  I had to login remotely and do a /etc/init.d/gdm restart to get X friendly again.[/QUOTE]

Dunno if it helps or not, but I had the same problem when I was running aMule 2.whatever.  I went back to 1.whatever and there weren't any more problems.

---

### Post by DFreeze on 2005-06-16
[QUOTE=sethmahoney]Control + Alt + Backspace should restart Gnome without having to reboot your whole computer, but there's something else going on that should be taken care of, cuz it shouldn't be doing that.  So...  Are you using Ubuntu or Kubuntu?  Hoary or Breezy?  What graphics card do you have?  Sound?  Network adapter?  Any unusual hardware or software installed?[/QUOTE]

I'm on Hoary, Ubuntu. Sound is an old SoundBlaster Live but I haven't even checked if it worked. Network adapter are two: one regular 3com ethernet card and a WiFi (D-Link g520+) which I also still have to get going (not much time and so many options). My graphics card is an NVidia 200 something (very old).

I recently went to the k7 kernel, having used the regular one with NVidia package. But I get visuals and accelleration in k7 too, so I figured I didn't need to reload the NVidia with the new kernel. Should I?

I knew about the CTRL-ALT-Backspace, but then the login would stop right before the GDM splash would appear. But now I read a way to stop the GDM. 

Thanx for any other info.

---

### Post by xmastree on 2005-06-16
[QUOTE=DFreeze]I'm on Hoary, Ubuntu. Sound is an old SoundBlaster Live but I haven't even checked if it worked. Network adapter are two: one regular 3com ethernet card and a WiFi (D-Link g520+) which I also still have to get going (not much time and so many options). My graphics card is an NVidia 200 something (very old).

I recently went to the k7 kernel, having used the regular one with NVidia package. But I get visuals and accelleration in k7 too, so I figured I didn't need to reload the NVidia with the new kernel. Should I?

I knew about the CTRL-ALT-Backspace, but then the login would stop right before the GDM splash would appear. But now I read a way to stop the GDM. 

Thanx for any other info.[/QUOTE]
 So, you were getting lock-ups with Windows and now you're getting them with linux too?

Are you sure it's not a hardware problem? Are all your fans working?

---

### Post by wvslkr on 2005-06-16
I can't help you on the specific issue, but I tend to agree with xmastree.  I have used X in about all of it's iterations since 3.3.2  and the only time it has totally locked the machine it has been hardware or crappy driver related.  If you, as we both gathered, were having problems in windows also, I would suspect you have a hardware problem.

Other than that all I can suggest is to throw up some logs and see if some eyeballs can help.

---

