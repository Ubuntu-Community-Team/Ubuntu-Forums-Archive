---
title: "Sword &amp; Sworcery No Sound"
date: 2012-06-01
forum: Gaming &amp; Leisure
---

### Post by monsieurdozier on 2012-06-01
I recently purchase the Humble Bundle V, and I install Sword and Sworcery through the Ubuntu Software Center on Ubuntu 12.04.  I started up the game, and I have no sound.

My sound works fine for Firefox, as well as the Speaker Test in the System Settings.  The volume is up in the game, and on my speakers.  Am I missing something?

I've tried uninstalling and reinstalling the game.  Any help would be greatly appreciated.

I went through the Sound Troubleshooting on this page:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and Passed Everything.

I'm running an Asus G50V Republic of Gamers Laptop.

I ran the game in a window, and opened Sound Settings.  Under the applications tab, it tells me:
No application is currently playing or recording audio.

So it seems that Ubuntu is for some reason not detecting the game as playing audio.  Any ideas?

---

### Post by filsd on 2012-06-01
> **monsieurdozier said:**
> I recently purchase the Humble Bundle V, and I install Sword and Sworcery through the Ubuntu Software Center on Ubuntu 12.04.  I started up the game, and I have no sound.

My sound works fine for Firefox, as well as the Speaker Test in the System Settings.  The volume is up in the game, and on my speakers.  Am I missing something?

I've tried uninstalling and reinstalling the game.  Any help would be greatly appreciated.

I went through the Sound Troubleshooting on this page:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and Passed Everything.

I'm running an Asus G50V Republic of Gamers Laptop.

I ran the game in a window, and opened Sound Settings.  Under the applications tab, it tells me:
No application is currently playing or recording audio.

So it seems that Ubuntu is for some reason not detecting the game as playing audio.  Any ideas?

I'm also having this problem.
Totaly diferent PC. But I have a asus motherboard to.
Never had a problem with sound on this machine.

---

### Post by peterbat on 2012-06-02
I solved the problem on my 64-bit macbook by installing libpulse0:i386 (apt-get install libpulse0:i386).

---

### Post by wbed on 2012-06-02
I had this same problem (having also just purchased an astounding bundle of games). In particular, I am running a 64-bit system. The Sword and Sworcery binary is 32-bit, but the package does not appear to depend on pulseaudio. Sound worked for me after `apt-get install libpulse0:i386'.

---

### Post by monsieurdozier on 2012-06-02
Running apt-get install libpulse0:i386 fixed the problem for me.  Thanks!

---

### Post by filsd on 2012-06-04
Running apt-get install libpulse0:i386 fixed the problem for me too! =D
Thanks!

---

