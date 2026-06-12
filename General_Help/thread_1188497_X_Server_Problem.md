---
title: "X Server Problem"
date: 2009-06-15
forum: General Help
---

### Post by Thedjatclubrock on 2009-06-15
I installed a command-line system and then LXDE and xinit.

GDM doesn't work, and gets stuck on a black screen with a pointer in the middle.

When I try startx, LXDE starts, but the mouse doesn't work (and I'm not sure the keyboard works, either.). Any ideas? I have tried dpkg-reconfigure xserver-xorg without any luck. :(

Thanks in advance.

---

### Post by nolliecrooked on 2009-06-15
which base version did you install?

---

### Post by Thedjatclubrock on 2009-06-15
As in OS version? Jaunty.

(Thanks for the quick response :D )

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> As in OS version? Jaunty.

(Thanks for the quick response :D )

ok, did you use the alternate cd?

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> ok, did you use the alternate cd?

Yes, and used the install command line option.

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> Yes, and used the install command line option.

hmmmmmmm, never really done it that way. probably a dumb question, but did you install xorg?

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> hmmmmmmm, never really done it that way. probably a dumb question, but did you install xorg?

Yes. It installed when I installed lxde

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> Yes. It installed when I installed lxde

try;

sudo aptitude remove xorg

and then;

sudo aptitude install xorg

and report back here what happens :P

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> try;

sudo aptitude remove xorg

and then;

sudo aptitude install xorg

and report back here what happens :P

I tried that. It did install a few more packages, but I still can't use any input device.

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> I tried that. It did install a few more packages, but I still can't use any input device.

okkkkkkkkkkkk next try;

sudo aptitude install xserver-xorg-input-mouse
sudo aptitude install xserver-xorg-input-kbd

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> okkkkkkkkkkkk next try;

sudo aptitude install xserver-xorg-input-mouse
sudo aptitude install xserver-xorg-input-kbd

already done, they are (and were) installed.

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> already done, they are (and were) installed.

ummmmmmm

sudo aptitude install xserver-xorg-dev

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> ummmmmmm

sudo aptitude install xserver-xorg-dev

The development package? Okay...

---

### Post by Thedjatclubrock on 2009-06-15
> **Thedjatclubrock said:**
> The development package? Okay...

Still no luck

---

### Post by nolliecrooked on 2009-06-15
sudo aptitude install xorg xterm gdm synaptic

that may work.

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> sudo aptitude install xorg xterm gdm synaptic

that may work.

Nope. No luck

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> Nope. No luck

lmao. you have tried rebooting after installing that stuff right?

---

### Post by Thedjatclubrock on 2009-06-15
Yes sir. GDM still freezes at the pointer and the input devices still fail with startx

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> Yes sir. GDM still freezes at the pointer and the input devices still fail with startx

try;

startlxde

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> try;

startlxde
It just hangs on the CLI...

If this helps any - X over ssh works fine.

There are no obvious errors in the error log either. The mouse seems detected..

Also, I did something interesting. I purposely messed up X's config. It went into low-graphics mode, in which both the mouse and keyboard worked....

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> It just hangs on CLI...

ugh, then sorry bro, I dunno. your gonna need to ask someone with more experience with CLi base installs.

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> ugh, then sorry bro, I dunno. your gonna need to ask someone with more experience with CLi base installs.

Alright. Thanks for all the help anyway. :D

---

### Post by Thedjatclubrock on 2009-06-15
By magic it works now... But whenever I open Firefox, X crashes and brings me back to the xdm.

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> By magic it works now... But whenever I open Firefox, X crashes and brings me back to the xdm.

lol, maybe you should just install the normal Ubuntu and install LXDE from the repos. then remove what you dont want/need?

---

### Post by Thedjatclubrock on 2009-06-15
> **nolliecrooked said:**
> lol, maybe you should just install the normal Ubuntu and install LXDE from the repos. then remove what you dont want/need?

It might be a hardware issue. Everything is beginning to crash X

---

### Post by nolliecrooked on 2009-06-15
> **Thedjatclubrock said:**
> It might be a hardware issue. Everything is beginning to crash X

what graphics card do ya have?

---

