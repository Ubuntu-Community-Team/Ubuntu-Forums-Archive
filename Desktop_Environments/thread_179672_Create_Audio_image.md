---
title: "Create Audio image"
date: 2006-05-20
forum: Desktop Environments
---

### Post by Hellkid on 2006-05-20
Hi,
I have been searching high and low for this and can't quite seem to find a working solution. I want to create an image file (eg: ISO or whatever) from mp3 and/or OGG.

I have found very similar requests out there with no apparent solutions. The closest that I came to was with K3B where I created an audio project, dumped my files and then said burn. Here they had a "Create image only" checkbox, however it outputted wav files for each audio file which is not what I am after. I would like just one image file created, so that if I mounted it, it would appear as a CD drive to the system.

Any ideas?
Thanks.

---

### Post by meng on 2006-05-20
If you're going to use K3B, can you try creating a data project instead of audio?

---

### Post by Hellkid on 2006-05-20
Yeah I could. But that's not going to help me, because then I will just get a data image that contains the audio files...not exactly what I am after.

I intend to mount this image into my Windows Virtual Machine, so that I can write it to MiniDisc using an application that can only be used in Windows (doesn't work under wine).

So, to recap, I need an audio image file to be created. Many years back in the days of using windows, I used to use Nero for this purpose so I asssumed it was possible. However I am thinking that this may not be the case.

---

### Post by meng on 2006-05-20
Sorry I didn't understand from your first post what you were trying to achieve. I don't suppose you could get a similar effect by burning a data image with the wav files. I understand this would not really be what you're after.

---

### Post by Hellkid on 2006-05-20
I gave it a go but it didn't work. It just made an image whose content happened to be wav files.

I am thinking that to make an audio image requires something extra and special (TOC etc). I presume that if it was simple then all the burning apps (serpentine, Gbaker and K3B) would be able to do it.

I am convinced that there must be a way. Thanks for your suggestions none-the-less.

---

### Post by editrix on 2006-07-30
Hellkid, if you found a way, please post it, as I'm having the same problem.

---

### Post by Hellkid on 2006-08-08
Hey Editrix, sorry - still no joy for me on this. I have pretty much abandoned the efforts for now (may pick it up again in the winter time though). If you stumble across a solution, please drop the info in this thread. If I do find out how to do this then I will be sure to update the post.
Thanks.

---

### Post by bom28 on 2006-08-11
I think shntool can do what you want : create one wav file from multiple wav files, see "2b. join mode" in [http://www.etree.org/shnutils/shntool/doc/TUTORIAL](http://www.etree.org/shnutils/shntool/doc/TUTORIAL)
use mpg321 or oggdec to convert mp3 and ogg to wav
Of course these are all command-line apps, I don't know if a GUI exists to do this.
And there is bchunk for the reverse operation : breaking a wav in multiple wav using a .cue file.

---

