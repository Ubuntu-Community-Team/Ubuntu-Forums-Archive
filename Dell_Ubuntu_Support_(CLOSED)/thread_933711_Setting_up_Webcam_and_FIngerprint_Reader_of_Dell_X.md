---
title: "Setting up Webcam and FIngerprint Reader of Dell XPS M1530"
date: 2008-09-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zephyrcat on 2008-09-29
I just recieved a Dell XPS M1530 with Ubuntu pre-installed. So far, it is great, but I am having a few problems.

EDIT: Problems seem to be rapidly changing.

**Current: (See below for how this evolved.)**

1. In Cheese, webcam works, no sound.

2. Fingerprint: SOLVED.

3. Spell checker: SOLVED.

4. The eject button above the keybaord does not work. The light around the button lights up, the drive feels like it is spinning, but the disc does not come out. Choosing eject from nautilus works just fine.

5. After suspend and hibernate, windows turn white.

**Original:**
1. In Cheese, all I see are some colored lines and some static at the bottom. How can I get my webcam working?

2. What do I do to set up my fingerprint reader?

3. Every word I have typed so far in this message except for I, just, a, Dell, Ubuntu, so, am, and all have a red underline, indicating they are misspelled. What is with that?

**Update:**

I figured the fingerprint issue out. See [this]("https://wiki.ubuntu.com/ThinkFinger") guide.

Found a forth issue: The eject button above the keyboard does not work.

**Update 2:**

The webcam seems to be working now, even though I did nothing. Unfortunately, Cheese is still not recording sound.

**Update 3:**

paddy1978 solved the spelling problem

**Update 4:**

Suspend and hibernate cause windows to turn white.

Thanks!

---

### Post by paddy1978 on 2008-09-30
For the spellings in Firefox, have you got the correct dictionary installed? It doesn't use the same settings as OpenOffice, it has its own dictionaries.

You can select the correct dictionary by right-clicking on a textbox in Firefox, and going to the 'Languages' option on the menu. (You'll need to have the 'Check spelling' option enabled on this menu first).

---

### Post by zephyrcat on 2008-09-30
Ok. Great. That solved the spell check problem. Anyone know anything about the rest?

---

### Post by kentonspr on 2008-10-01
I'm pretty sure the eject button issue is a feature. It wont eject a CD / DVD that is mounted. When you put a CD in the drive it auto mounts the CD and doesn't unmount until you use the eject option in nautilus or manually unmount it and hit your eject button the the computer.

If you dont have a CD in, should be able to it the eject button and listen to the drive try and eject something that isn't there. Nothing is mounted so it will allow the drive the mechanical function of attempting to eject.

---

### Post by zephyrcat on 2008-10-01
I wondered about that, and it appears to be true. Seriously, though, why would I go to nautilus, right click on the CD, choose unmount (when the very next option is eject which does both) and then click on the eject button.

Is it possible to change the function of the eject button to unmounting and ejecting?

---

### Post by zephyrcat on 2008-10-02
Unfortunately, I have noticed another problem. After resuming from hibernate or suspend, the inside of menus and windows are just white.

Any ideas?

Thanks!

---

### Post by gunthr on 2008-10-18
Did you find anything out about the eject button? I bought a XPS M1530 with Ubuntu and I'm pretty sure it worked out of the box. Now I have reinstalled with a 64 bit version of Ubuntu Ultimate 1.9 and it doesn't eject.

There must be a way to tell it to unmount the disc before ejecting. Does anyone know where the settings for these keys are? Can we modify the command and add umount or something?

---

### Post by zephyrcat on 2008-10-19
No, not really. I did find a solution for the mic, though:
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=15286](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=15286)

---

### Post by gunthr on 2008-10-19
I did find a solution for the eject issue. I added

```
dev.cdrom.lock=0
```

to the end of /etc/sysctl.conf and it seems to have resolved the eject issue. I found it in

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530")

---

### Post by gunthr on 2008-10-19
Although, it does leave the cd icon on the desktop after it is ejected, but that's better then having to unmount it first.

---

