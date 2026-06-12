---
title: "GnomeBaker: Write Speed"
date: 2005-12-21
forum: General Help
---

### Post by Rev. Nathan on 2005-12-21
OK, I am a little confused in GnomeBaker. I am writing an audio disk, I click 'Create Audio Disk', and a question is asked:

[IMG]http://bigrevmedia.com/coronets/Screenshot-Create%20Audio%20CD.png[/IMG]
The default is for, and it goes up to 100. Are these porpotional to the speed on your burner (1 = 600 kbp/s, 2 = 1200 kbp/s, etc)? Or will an 8x burner burn at 100% when you set it to 100?

I have a 48x burner, and I want to burn that fast; should I use 48, 100, or what?

Also, it provides diffrent modes:

default
tao
dao
raw96p
raw16

Should I mess with any of these? What are they?

Thanks!

---

### Post by timfrost on 2005-12-21
The number is a measure of the speed at which recording can be done.  It is a multiplier factor. A speed of 1 means "write at the same speed that an audio (CD) or video (DVD) tarack is played".  A burn speed of 4 is a reasonable value for CD-RW or DVD-RW, and indicates that the device is capable of recording to a rewritable disc at 4 times the playback speed.

Different recordable media are capable of being written to at dfferent speeds.  For instance, I have Imation CD-R media capable of being written at speeds to 16x, but the CR-RW and DVD+RW say "1x-4x", which means that a speed of 4 is the highest safe recording speed for these media.

The modes control how the disk is written to.
tao = track-at-once
dao = disk-at-once

I don't know what the raw96p and raw16 options mean here.

tao makes it possible to add tracks if the media/drive supports that.  Beyond that, I have no ideas.


Tim

---

### Post by Rev. Nathan on 2005-12-21
Thanks, I tried to write a CD @ 48x, the highest my drive can go (52x for the CDs), and the disc instantly failed. However, when I used Serpentine using "Highest Speed Possible", it burned just fine. Odd? Or did I not catch something, here?

---

