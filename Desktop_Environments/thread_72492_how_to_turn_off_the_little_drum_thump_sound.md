---
title: "how to turn off the little drum thump sound"
date: 2005-10-06
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2005-10-06
I've been searching all over for this and I haven't been able to find a way to do this.  I want to turn off the little drum thumpy sound that happens when I open a program.  It's very annoying after awhile.  Either that or I want to change it to something more interesting so if anyone knows how to;

1.  turn the bloody thing off
2.  change the sound (ideal)

I've changed all of the system sounds in the System>Preferences>Sounds and that didn't do it.  I even tried turning off the system bell.  No luck.  eh how come this sound isn't listed on the sound prefs! 

Just to be clear, I've already changed ALL of the sounds in an effort to turn it off. and it didn't work (Although all of the other sounds changed fine).  I want the sounds, I just want that one to be different or to be none at all.  So please don't tell me to go to System>Prefs>Sounds and change it there cause it's NOT there.

It's driving me looney.  Ideas?  Thanks!!

Aaron

---

### Post by Zelut on 2005-10-06
To turn off the drum sound at login go to System > Admin > Login Preferences (I believe it is, not at my Breezy box right now).  It'll have options for different login/splash screens, changing or removing audio options at login (prompt, success & failure).

---

### Post by 11hjpphty76lkjj on 2005-10-06
Thanks for the reply.  Sorry I didn't mention that I'm using Hoary.  But I did check in the System>Admin>Login Screen Setup and I found nothing about sound options..  thanks for the idea though!

Aaron

---

### Post by Muhammad on 2005-10-06
**System -> Preferences -> Sound**

The Un-check the "Enable Sound Server Startup"

or try this:  [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

If neither worked, then your only option is to update... ;)

---

### Post by 11hjpphty76lkjj on 2005-10-06
Muhammad,

I want the sounds to work, I just don't want the drum beat sound. :(  And I'd like to upgrade to breezy however my current setup is complicated, I have hoary booting from a usb hard drive, and I haven't figured out how to get breezy to work with that.  I just want the drum beat that is played with I open a program to not to do that...

grr

Aaron

---

### Post by Alexander Kirillov on 2005-10-06
[QUOTE=kalosaurusrex]Thanks for the reply.  Sorry I didn't mention that I'm using Hoary.  But I did check in the System>Admin>Login Screen Setup and I found nothing about sound options..  thanks for the idea though!

Aaron[/QUOTE]
It is under accessibility tab.
However, it only controls the drum beat when login window is shown - not *after* you login.

---

### Post by 11hjpphty76lkjj on 2005-10-06
Thanks for everyone for reviewing this.  I restarted gdm and it seems to be working correctly.

Aaron

---

### Post by nicco on 2005-10-11
Hey, I just stumbled upon this thread. I can't read from your last reply if you actually fixed the issue or not, but in any case, I found out that the .wav file you're looking for can be found at:

/usr/share/sounds/gtk-events/clicked.wav

You can remove, rename, or replace this file manually (requires sudo of course.) You might have to restart some processes (or reboot) before it takes effect, though.

Nicolay

---

