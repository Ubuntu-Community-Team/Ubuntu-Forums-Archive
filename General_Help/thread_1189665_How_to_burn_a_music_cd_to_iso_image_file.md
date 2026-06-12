---
title: "How to burn a music cd to iso image file"
date: 2009-06-17
forum: General Help
---

### Post by jcadam on 2009-06-17
hello, 

Is there possible to burn some wav files to an image file as iso format? It seems cdrecord could do the similiar thing with following lines; I want to know can I burn CD within loopback device such as /dev/loop1.

# cdrecord -pad -v dev=1,0 -dao speed=12 ./L_FFFF_R_A3C5.wav

The 'dev' option specify a SCSI device point to my CD-RW driver.

---

### Post by synapsys on 2009-06-17
Are you trying to make an iso of a cd or make an iso of some music files you have?

---

### Post by jcadam on 2009-06-17
I am trying to create an iso of some musica files I got.

---

### Post by synapsys on 2009-06-17
I believe there is a gui tool for this called isomaster.

```
sudo apt-get install isomaster
```

---

### Post by jcadam on 2009-06-17
Thank you snapsys. This tool just packed up wav files into iso rather than turned them to CD tracks which could be played back on an ordinary cdplayer. Actually, AFAIK, this may need some thing called CD-DA format to write a new CD. However, I just want to create a iso file instead a real CD. How can I do this?

---

### Post by Gallienus on 2009-06-17
If I understand you correctly, jcadam, you want to create an ISO of a standard audio CD. Unfortunately, as far as I know, that's impossible. Audio CDs are multi-track (one track for each song), but ISO image files don't support multi-track formats.

[http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)

---

### Post by niteshifter on 2009-06-17
Hi,

If you're looking to create an ISO that is mountable (via looping): No.

If you're looking to make a file set (data and TOC files) suitable for later burning / archiving then the program cdrdao is useful. See this [post]("http://ubuntuforums.org/showthread.php?t=795181"), and spend some time with man cdrdao.

---

### Post by hissyfut on 2009-08-10
> **Gallienus said:**
> If I understand you correctly, jcadam, you want to create an ISO of a standard audio CD. Unfortunately, as far as I know, that's impossible. Audio CDs are multi-track (one track for each song), but ISO image files don't support multi-track formats.

[http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)

According to the following article, in the second part,
it is possible:
[https://help.ubuntu.com/community/CreateIsoFromCDorDVD](https://help.ubuntu.com/community/CreateIsoFromCDorDVD)

Edit: After reading the article again, both parts are exactly the same (unlesss Sound Juicer has some different way of creating an iso). The command line dd if=/dev/cdrom of=file.iso would apparently work for data or music audio. Please verify and correct if needed.

---

