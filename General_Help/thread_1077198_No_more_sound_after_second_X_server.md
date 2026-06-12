---
title: "No more sound after second X server"
date: 2009-02-22
forum: General Help
---

### Post by cactux on 2009-02-22
Hello

My Kubuntu (8.04) has no more sound after I started a second X server. How can I get it back?
I tried a full reboot: no effect.
If I boot on the live CD, the sound works fine.

To get a second X server, I logged as another user in a console (CTRL+ALT+F1), than I run:
startx -- :1

How can I correct this?
Why does this happened? How can I prevent this?

Thanks for your help

---

### Post by stratman1988 on 2009-05-07
Hey I get the same thing when I boot up a new X server using:
```
X :3 -ac & nvidia-settings --load-config-only
```
to run fullscreen games with Wine.  Worked fine just yesterday in Hardy and now there's no sound with my fresh install of Jaunty.
I've tried using both ALSA and OSS(tested fine on main desktop) driver's with wine to get around the problem and have fully working sound on my main desktop, but no luck on the other X server. 
I get this error when running wine on the separate X server:
```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: Permission denied
```

---

### Post by bensabin on 2009-06-05
I've found a solution:

edit /etc/group

```
sudo vi /etc/group
```

Next, search for audio, you shoud find somethink like this:

```
audio:x:29:pulse
```

Add a coma and your username afther pulse

```
audio:x:29:pulse,username
```

Save and restart ubuntu, it should work.

[SIZE="1"]ps: Sorry for my English, I'm French speaker[/SIZE]

---

