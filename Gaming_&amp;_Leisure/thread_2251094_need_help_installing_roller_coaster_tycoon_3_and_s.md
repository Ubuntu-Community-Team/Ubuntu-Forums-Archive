---
title: "need help installing roller coaster tycoon 3 and sims"
date: 2014-11-01
forum: Gaming &amp; Leisure
---

### Post by hmart902 on 2014-11-01
so i have had continuous problems with getting roller coaster tycoon 3 and sims life stories to run on ubuntu. everything installs jsut fine, but then when i go to run it i get an error that says please insert original disc or files may be corrupted. i was hoping that someone has the solution to the problem. input on how to solve this problem would be greatly appreciated. tia

---

### Post by lisati on 2014-11-02
When I used to run the SIMs on Windows a few years ago, it needed the original installation disk sitting in the disk drive, even though I'd gone through the installation process. Perhaps the copy you have has a similar requirement.

---

### Post by oldrocker99 on 2014-11-02
Most Windows games which came on disk did require the disk to be mounted before the game would run. The least obtrusive was probably Oblivion, which ran fine as long as you had a disk named 'OBLIVION" mounted. When Sacrifice, Shiny's crazy diamond, came out, it got praise for requiring only the code to be entered, and then would run without the disk. That was a big deal in 2000.

---

### Post by hmart902 on 2014-11-02
how do i go about mounting the disk though?

---

### Post by oldrocker99 on 2014-11-04
When the disk is inserted, it should be mounted automatically. There's a program you need to know about called acetoneiso, which handles .iso files. It can make an .iso file, and mount it, so you don't have to search for the disk:
```
sudo apt-get install acetoneiso
```
Acetone is a free, open source version of the much-pirated Windows program Alcohol, which does the same thing, just as GPartEd does everything Partition Commander does.

---

