---
title: "The Annoying Alert Sound"
date: 2009-02-07
forum: General Help
---

### Post by photon_man62 on 2009-02-07
Welcome fellow Ubuntu users! This is my first help post :D
---
So you're annoyed when an extremely loud BEEEEP sound goes off when you do something "wrong", for example:

-try to scroll down in Firefox when you have scrolled to the very bottom
-press Backspace when there is nothing left to clear (this happens in the terminal, in small alert boxes etc.)

Yeah. I was annoyed too. And I finally figured out how to solve it!

In GNOME:

Go to System>Preferences>Sound
Go to the "Sounds" tab.
Uncheck "Play Alert Sound".

And you're done! Simple as that!

.:*EDIT*:.
This does **NOT** work with the virtual terminal. To turn it off there, type "xset b off" without the quotes into the prompt. Thanks to **Patsoe** for pointing that out.

.:*EDIT*:.
I'll just quote **Temujin**'s suggestion here:

> **Temüjin said:**
> Another possible solution for those who want the PC speaker to shut up without opening their case: Add:
```
blacklist pcspkr
blacklist snd_pcsp
```
to /etc/modprobe.d/blacklist
Not sure if it works on laptops.
This is if you're using headphones and sound leaks out of your speakers for some reason.

---

### Post by sune_cph on 2009-02-08
This should really be turned off by default, it's so damn annoying!

Thanks for the tip.

/Sune

---

### Post by photon_man62 on 2009-02-09
> **sune_cph said:**
> This should really be turned off by default, it's so damn annoying!

Thanks for the tip.

/Sune

Yeah, I know :D

It's particularly annoying when you're using headphones, because it IGNORES that you're using headphones and beeps through the speakers (or motherboard, I honestly don't know).

---

### Post by Patsoe on 2009-02-09
> **photon_man62 said:**
> 
.:*EDIT*:.
This does **NOT** work with the virtual terminal.

For that, you can try "xset b off" at the prompt.

---

### Post by 3rdalbum on 2009-02-09
Why not just disconnect the PC speaker?

It's also possible to redirect the speaker sound to instead play a sound file (or run any other command) but in my experience the effect tended to wear off after a few hours and start beeping the speaker again! Still, you can always give it a go; there's instructions on the Gentoo wiki.

---

### Post by photon_man62 on 2009-02-09
> **3rdalbum said:**
> Why not just disconnect the PC speaker...

Maybe because I was using a laptop? :D

---

### Post by Yellow Pasque on 2009-02-09
> **photon_man62 said:**
> Maybe because I was using a laptop? :D
Another possible solution for those who want the PC speaker to shut up without opening their case: Add:
```
blacklist pcspkr
blacklist snd_pcsp
```
to /etc/modprobe.d/blacklist
Not sure if it works on laptops.

---

### Post by photon_man62 on 2009-02-09
Thanks, people, for adding to this tip :D

---

