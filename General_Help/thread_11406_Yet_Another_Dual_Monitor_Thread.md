---
title: "Yet Another Dual Monitor Thread"
date: 2005-01-16
forum: General Help
---

### Post by confusionhere on 2005-01-16
I apologize for posting yet another thread on this topic but I am about at my wit's end. Recently I switched to Ubuntu (my first experience with Linux) and I have been trying unsuccessfully for several hours to get my dual monitor setup working.

My custom /etc/X11/XF86Config-4 file is [here.](http://www.ece.ualberta.ca/~bacarter/cmp/XF86Config-4.custom) 

When I boot using my custom XF86Config-4 file, I just get a command prompt and an error message that X cannot start because it is not configured properly. It also says that no screens are found.

My video card is a ATI Radeon 9000pro (with DVI and VGA outputs). My primary monitor is the "NEC FE771SB" plugged into the VGA port, and my secondary monitor is the "Apple 15" (an ancient, but working, 15" Apple CRT) plugged into the DVI port with an adapter.

I was told by somebody in another forum that you cannot enable dual monitors by merely copying over the new config file to /etc/X11 since Ubuntu checks the md5sum on bootup and X will fail to start if it has changed. If this is so, what is the "proper" way to enable a new config file?

Where am I going wrong? All comments are appreciated.

---

### Post by shrike on 2005-01-24
Hello,

Being a newbie - I'm in a similar situation.  I have a PC hooked up to a Sony G400 19" CRT and a Dell 1901fp DVI flatpanel Monitor hooked up respectively to a Asus Nvidia 4200 Graphics card.  I too have edited my XF86Config-4 file to what I believe is propper, but I too am mistified as to what else I need to do.  I replaced the Checksum in the var folder as indicated by the comments in the XF86Config-4 and it still hasn't worked for me either...

log in root console and type the following to do so

md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum

---

