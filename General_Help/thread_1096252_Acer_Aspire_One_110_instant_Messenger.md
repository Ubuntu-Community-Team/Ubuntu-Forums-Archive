---
title: "Acer Aspire One 110 instant Messenger"
date: 2009-03-14
forum: General Help
---

### Post by zypcu on 2009-03-14
Does anyone know if it is possible to install under Ubuntu the IM Messenger which comes with linpus linux lite? i think that is the only IM 
Messenger under linux which supports msn video call. there are some others (aMSN etc) but they only support webcam


Thank you

---

### Post by pjalegria on 2009-03-14
Yeh a would to like to now to...

---

### Post by mnk on 2009-05-14
Yes someone please tell me too!

---

### Post by 3rdalbum on 2009-05-14
Heh, I tried doing this a while back but my main system is 64-bit and I never ended off trying it on my 32-bit Ubuntu netbook!

I put the Linpus restore disc into my desktop and I think there was a .tar.gz file that was the default state of the SSD. I might have needed to loopback mount a squashfs filesystem that contained the .tar.gz file; I can't remember.

From there, I found the location of the binary and copied it to my hard disk. Then I did the following procedure:

1. Launch the program in a terminal.
2. It will complain about a missing library.
3. Copy the library from the .tar.gz disk image to the appropriate place on your hard disk.
4. Repeat.

(It might be quicker to extract the .tar.gz file first rather than keep cherry-picking libraries from it)

I eventually hit a brick wall; The messenger requires 32-bit Gstreamer, which I couldn't provide it as my desktop is on 64-bit.

If anyone can get it working, that would be really good. I might give the idea another try on my netbook. I don't think it would be realistic to distribute the program in a .deb file as it seems to rely on a hundred megabytes of slightly modified libraries.

---

