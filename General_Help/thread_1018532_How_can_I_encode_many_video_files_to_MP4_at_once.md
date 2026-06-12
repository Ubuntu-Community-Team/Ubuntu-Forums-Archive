---
title: "How can I encode many video files to MP4 at once?"
date: 2008-12-22
forum: General Help
---

### Post by dorkdork777 on 2008-12-22
I've got a new PC (yay!), which I've been waiting on to convert my extensive media library to MP4, compatible with iPods and PSPs. I found HandBrake, and the world is a better place; however, I cannot select multiple videos to input at once. I'm using 64-bit 8.10.

Is there a way to do this? Or is there another app I should use that supports many files being inputted at once with the same output settings? (That supports encoding to iPod-compatible MP4, of course. :P)

Any help at all would be much appreciated! :)

---

### Post by ajcham on 2008-12-22
Try iriverter - as the name suggests it is designed with iRiver players in mind, but it does encode using MP4, so should still be compatible. You can choose to convert a single file, directory or from a DVD source.

EDIT: iriverter can be found in the multiverse repo, BTW.

---

### Post by dorkdork777 on 2008-12-22
Fantastic, I'm using it now and it seems good. Any advice on which preset is best for iPods? (I have a Classic.) There's a lot of them and they're confusing me. :)

---

### Post by dorkdork777 on 2008-12-22
Bumpy bump? I've tried a few of them; my PSP detects them as corrupt data. Handbrake does a good job but it can't process more than one file at a time. Any script that uses Handbrake's CLI perhaps?

Any help of any kind would be much appreciated :)

---

### Post by graabein on 2008-12-29
How do I launch handbrake with GUI? Nothing happens when I hit the menu item under *Audio & Video* and from command line I can only find **HandBrakeCLI**.

I installed *GTK GUI (Ubuntu 8.10 x86 Binaries)* from [here]("http://handbrake.fr/?article=download"). 

I want to convert some divx or avi files (same thing?) to mp4 for my Nokia N800 internet tablet.

---

### Post by MartyBuntu on 2008-12-29
> **dorkdork777 said:**
> Bumpy bump? I've tried a few of them; my PSP detects them as corrupt data.

Have you tried WinFF? I use it to transcode all my video for PSP.

---

### Post by mc4man on 2008-12-29
> How do I launch handbrake with GUI

I use 8.04 so I had to build vs. a .deb, anyway the gui is opened by ghb

Try looking in /usr/bin and see if it's there. If not look in /usr/local/bin

---

### Post by graabein on 2008-12-29
> **mc4man said:**
> I use 8.04 so I had to build vs. a .deb, anyway the gui is opened by ghb

Try looking in /usr/bin and see if it's there. If not look in /usr/local/bin

I get an error when I run **ghb** from command line. That's probably why I didn't get any response when I launched it from the menu.

```
$ ghb 
ghb: error while loading shared libraries: libgtkhtml-3.14.so.19: cannot open shared object file: No such file or directory
```

I've decided it's too much work to convert and transfer movies for the eight hour trip. I'll just stick with a book and some tunes and enjoy the scenery.

---

