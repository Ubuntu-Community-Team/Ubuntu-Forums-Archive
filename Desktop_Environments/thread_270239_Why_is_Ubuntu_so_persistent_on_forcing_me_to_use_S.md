---
title: "Why is Ubuntu so persistent on forcing me to use SoundJuicer?"
date: 2006-10-02
forum: Desktop Environments
---

### Post by lucis on 2006-10-02
I liked being able to rip CD audio to Ogg Vorbis right from Nautilus in previous versions of Ubuntu. Now, however, every time I try viewing the contents of my CD drive SoundJuicer is loaded. I got nothing against SoundJuicer, really, but whatever happened to the ability to choose? What is this, Windows?

I try opening the mount point from Nautilus's address bar and SoundJuicer is loaded. I try ls'ing the mount point and get an empty directory. What is going on? How do I disable SoundJuicer from handling CD audio?

---

### Post by aysiu on 2006-10-02
System > Preferences > Removable Drives and Media

---

### Post by meng on 2006-10-02
lucis, I admire your attitude, i.e. wanting to customize the OS to your preferences; but I don't much care for your other attitude, i.e. assuming that it can't be done when it can.

---

### Post by lucis on 2006-10-03
> **aysiu said:**
> System > Preferences > Removable Drives and Media

Nope, tried that aLready. After disabling SoundJuicer from opening when an audio CD is inserted, I now get an error when I try to open an audio CD. 

[QUOTE=meng] lucis, I admire your attitude, i.e. wanting to customize the OS to your preferences; but I don't much care for your other attitude, i.e. assuming that it can't be done when it can.[/quote]

Meng, I'm sorry if I came off as rude. I've been a Windows user for far too long and trying to clear the default configuration is more trouble tban it's worth. :biggrin:

---

### Post by skymt on 2006-10-03
> **lucis said:**
> Nope, tried that aLready. After disabling SoundJuicer from opening when an audio CD is inserted, I now get an error when I try to open an audio CD.

What error?

---

### Post by lucis on 2006-10-03
> **skymt said:**
> What error?
[I]
"cdda:///dev/hdc" is not a valid location.[/I]

---

### Post by lucis on 2006-10-04
No ideas? Is this worthy of filing a bug over?

---

### Post by aysiu on 2006-10-04
Possibly. I'd bump it one more time in 24 hours. If you still don't get a response after that and can't find anything on Google, I'd file a bug report.

---

### Post by lucis on 2006-10-20
Bump... ](*,)

---

### Post by crumja on 2006-10-20
Just remove the app sound juicer.

If that doesn't work, make sure you have the right options selected in the removable drives and media preferences section. In the first tab, the first two boxes should be ticked and nothing else. In the second tab, the audio cd tab shouldn't be ticked.

---

### Post by lucis on 2006-10-21
> **crumja said:**
> Just remove the app sound juicer.

If that doesn't work, make sure you have the right options selected in the removable drives and media preferences section. In the first tab, the first two boxes should be ticked and nothing else. In the second tab, the audio cd tab shouldn't be ticked.

I don't think removing SoundJuicer would help. Besides, I like SoundJuicer for when I want to rip an entire CD, but prefer ripping right from Nautilus when I just want to rip a track or two.

I made sure the correct options were checked in the Removable Drives and Media configuration but to no avail. When I try to browse an audio CD in Nautilus it's still giving me the error. :(

---

### Post by mulder_edu on 2007-11-16
Did anyone ever figure out what this problem was?  I'm having the same problem in Gutsy. :(

I get that same error message:

"cdda:///dev/hdc" is not a valid location.

---

