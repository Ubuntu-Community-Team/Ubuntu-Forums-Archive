---
title: "ctrl+alt+f1 does nothing - please help!"
date: 2005-12-30
forum: Desktop Environments
---

### Post by tentimes on 2005-12-30
Hi,

I'm trying to get a command line so I can install the latest nvidia drivers I downloaded. Pressing ctrl+alt+[any Function key] does nothing. I thought this was supposed to drop you into command line?

Getting really frustrated as I can't figure this out at all :( It won't tun in terminal as it won't install with X running.

Appreciate any help I can get (and yes I have read through the nvidia howto's ;))

---

### Post by thekiller on 2005-12-30
it should work the way you are tryin to do it. Try to see if CTRL+ALT+BACKSPACE kills your xserver and brings you back to the login screen. Then press CTRL+ALT+F1.

---

### Post by tentimes on 2005-12-30
ctrl+alt+BACKSPACE blanks the screen, then it appears to restart at login screen, I am trying to use ctrl+alt+f1 (f anything tbh) during this process, and again at login. Nothing happens. It is as if it is dissabled in some way.

Any ideas? I just need to get out of X so i can run commands, but there is no safe boot or commandline boot in the bootloader...
Just can't understand this at all :(

Thanks for any help :)

---

### Post by thekiller on 2005-12-30
ok lets do another thing, lets remove gdm from the startup script. Log back in and type this :

```

sudo update-rc.d gdm remove

```

Then reboot, and you should be able to see the login prompt. Log in and install NVIDIA drivers.

---

### Post by tentimes on 2005-12-30
Nope. the nvidia installer (remember I'm running the .run file from thier website) says "you appear to be running an x-server, please exit x before installing....

This was why I was trying ctrl+alt+f1, but it doesn't work. I need to shutdown x and operate from command line...

---

### Post by thekiller on 2005-12-30
[QUOTE=tentimes]
This was why I was trying ctrl+alt+f1, but it doesn't work. I need to shutdown x and operate from command line...[/QUOTE]

Yeah i know that. But since you said ctrl+alt+f1 doesnt work I suggested you to remove gdm from the startup script and reboot. When it wont see any gdm, it wont bring up a login screen, and hence it will only show what you are supposed to see on pressing ctrl+alt+f1.

EDIT : Once you are done, you can again add gdm on the startup, by swapping [COLOR="Red"]remove[/COLOR] with [COLOR="Lime"]add[/COLOR] in that command.

---

### Post by tentimes on 2005-12-30
I still got the login prompt after using the remove line :( It executes ok in a terminal when I run it though, and says:

update-rc.d: /etc/init.d/gdm exists during rc.d purge (use -f to force)

I reboot and still I get the login window as normal :( I remember with other linux versions I have been able to use ctrl+alt+fX to get terminal - not sure why it won't work oin Ubuntu.

Definitely seems like it's diabled somewhere! :)

---

### Post by az on 2005-12-30
I don't think it's a GDM thing.  It is probably an xorg thing.  Please file a bug report at bugzilla.ubuntu.com.  The package would be ( I guess) xserver-xorg.  Please take a look first to see if this bug has already been reported.

---

