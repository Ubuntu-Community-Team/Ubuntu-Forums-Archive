---
title: "Ok quick question!"
date: 2005-11-19
forum: Desktop Environments
---

### Post by sevenrechlin on 2005-11-19
Well the question is quick, though probably not the answer :rolleyes: 

What I want to do is have the scroll lock LED either come on automatically when the computer is started, or (preferably) come on and off when I press the scroll lock key.  I _do not_ care if scroll lock is actually doing anything, I just want the light to turn on and off.

Looked everywhere and I cannot for the life of me figure this out....  Please help!!!!!

Lol thanks.:razz: 

P.S. Sorry for accidently posting in the other forum by mistake :(

---

### Post by manicka on 2005-11-19
My scroll lock doesn't even have an LED.

Does it still work anyway?

---

### Post by teaker1s on 2005-11-19
gnome-system-keyboard preferences will allow key modification other than that it's controlled by xserver-xorg files which are in xkb folder.
could use 'xbindkeys' program or 'bl' or 'tleds' 
xbindkeys can be altered but from personal experience unless you know exactly what to do you can end up with a system that won't boot gui or you get xkb config error and any help info on the subject is extremely poor

I'd try 'bl or 'tleds' as a safer bet

---

### Post by teaker1s on 2005-11-19
'gkrellm-leds' for labtops or wireless displays on screen

---

### Post by az on 2005-11-19
I cannot find anything for the scroll lock, but maybe you can hack numlockx?

tleds also blinks your scroll lock and numlock with network activity (cool!)

---

### Post by sevenrechlin on 2005-11-19
Well (I should've explained this) my keyboard lights up when the scroll lock LED is ON (don't ask why, weird I know) so I want to be able to turn it on/off or just be able to have it always on in the least. 

BTW: what did you mean "gnome-system-keyboard preferences"?

---

### Post by teaker1s on 2005-11-19
yes

---

### Post by GoLo on 2005-12-27
today I've bought an SunBeamTech keyboard:
[http://www.sunbeamtech.com/PRODUCTS/peripherals/multimedia_keyboard/multimedia_keyboard.htm]("http://www.sunbeamtech.com/PRODUCTS/peripherals/multimedia_keyboard/multimedia_keyboard.htm")

Oh!! big problem. Light is switched on/off with the scroll-lock key. And only on if scroll led is on.

If I enable scroll lock on term, I cant' do nothing. In X it ignores me.

Solution:

I found it [here,]("http://es.tldp.org/Manuales-LuCAS/AA_Linux_colegio-1.1/AA_Linux_colegio-1.1-html/x9696.htm") sorry it's in spanish.

In X: **xset led      3** , [B]xset -led 3
on, off.

[/B]

---

### Post by roostishaw on 2006-07-28
Don't cross post, thanks!
[http://ubuntuforums.org/showthread.php?t=92255](http://ubuntuforums.org/showthread.php?t=92255)

---

### Post by kdub432 on 2007-01-15
Thanks!

---

