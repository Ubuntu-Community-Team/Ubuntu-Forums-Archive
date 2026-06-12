---
title: "compiz fusion freezes after changing settings"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by atomkarinca on 2007-07-25
hi yall :)

changing preferences in the "compizconfig settings manager" causes my computer to freeze. enabling preferences on the main window (like opacify or desktop cube) doesn't affect anything but changing settings in the subpreferences (like enabling inner cube or changing keyboard bindings) causes to freeze. the mouse is still controllable or if some song or video is playing it goes on but mouse and keyboard controls are out of order. even ctrl+alt+backspace doesn't work.

has anybody had the same problem or any suggestions?
thank you.

---

### Post by Happy_Man on 2007-07-25
Does it stay like that forever? Perhaps it is just applying...... that takes a bit to enable plugins on my computer.

---

### Post by Nigel Goode on 2007-07-25
This is my problem too. Changed to allow desktop effects to see what they were like, and the screen went white and I can't see or do anything.  I guess that there's not an undo function.  I can get into 'native' unix/linux to run commands. N E boddy know a command I can use?
:(

Nigel Goode

---

### Post by atomkarinca on 2007-07-25
Happy_Man: it stays forever. when i boot with compiz i get this error and when i run it through alt+f2 i got no borders but i get rid of the freeze. for the life of me i couldn't figure it out.

and i just got a fresh new bug :) compiz doesn't recognize my super key. i think i will mess with this for a long time.

---

### Post by Happy_Man on 2007-07-25
> **Nigel Goode said:**
> This is my problem too. Changed to allow desktop effects to see what they were like, and the screen went white and I can't see or do anything.  I guess that there's not an undo function.  I can get into 'native' unix/linux to run commands. N E boddy know a command I can use?
:(

Nigel Goode
Did you have the proper drivers installed? The White Screen of Death is usually due to that.....

---

### Post by atomkarinca on 2007-07-26
unfortunately i don't get a white screen of death. it's just that everything freezes but the mouse cursor. in addition i am using beryl without a glitch but i want to be able to use that expo plugin in fusion :)

---

### Post by Nigel Goode on 2007-07-26
Unfortunately, no.  

I've been using Ubuntu for several months with no drivers installed, so didn't think that I needed them - working on the "ain't broke" principle.  Of course, now that I have all of my emails and documents unavailable, I need to know how to load drivers while the screen is white ...

Does anyone know a command line fix that I can use to get back to the original config (no desktop effects) so I can then install my drivers etc?

If I 'overload' ubuntu, will I lose my data/emails?  Really don't want to do that unless it's fan cleaning time.

:<(

---

### Post by Happy_Man on 2007-07-26
> **Nigel Goode said:**
> Unfortunately, no.  

I've been using Ubuntu for several months with no drivers installed, so didn't think that I needed them - working on the "ain't broke" principle.  Of course, now that I have all of my emails and documents unavailable, I need to know how to load drivers while the screen is white ...

Does anyone know a command line fix that I can use to get back to the original config (no desktop effects) so I can then install my drivers etc?

If I 'overload' ubuntu, will I lose my data/emails?  Really don't want to do that unless it's fan cleaning time.

:<(
Reboot your computer and go into recovery mode. If you have a nvidia card, type in ```
sudo apt-get install nvidia-glx-*
``` where * is either:

New if your card is fairly recent

Old if your card is really old

Just leave it as "nvidia-glx" if your card is about as old as a Geforce 4 MX 420 card. 

Then try rebooting and logging back in normally and see if it works. 


If, however, you have an ATI card, type ```
sudo apt-get install xorg-driver-fglrx
```

If none of that works.... your card may not be able to run Compiz.... or you don't have proper drivers. Sorry.

---

