---
title: "How do I bring my Fluendo Codecs into a clean install"
date: 2009-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by starcannon on 2009-03-26
My Mini 9 shipped with Ubuntu 8.04 preloaded and has the Fluendo Codecs.
I want to do a fresh clean install of 8.10 on my Dell Mini 9; and, I want to bring the Fluendo Codec Pack into my fresh clean install.
Is there a tutorial that would help me salvage the Codecs from my restore DVD? 

Thanks for looking, 
starcannon

---

### Post by starcannon on 2009-03-30
This is a shameless bump, can anyone help me?

---

### Post by amendt on 2009-03-30
The problem is Fluendo doesn't know that you bought these codecs so you can't redownload them from Fluendo's website and it is only one click to enable the same (ilegal) codecs from mediubuntu.

---

### Post by anjilslaire on 2009-03-30
I've been trolling through my Dellbuntu Mini 9 restore DVDs as well out of curiosity. The "Dell Drivers and Utilities" disc is full of .exe's, so that's likely the Windows drivers. 
The Dell Ubuntu 8.04+ LTS DVD included with the Mini 9 includes a 1.1gb rootfs.img that I'm going to poke around in to see what I can find.

I remember a thread somewhere where someone pointed out where to find teh codecs on the Dell LTS restore disc shipped with systems, but I can't find the thread anymore.

---

### Post by starcannon on 2009-03-30
amendt;
Thanks for the reply, yeah I know I can medibuntu them; but where I have Fluendo, I prefer to use them if I can, indeed I would like to do this for the 1420n that I bough my mother as well, I upgraded her to 8.10, and lost her Fluendo codecs in the process, would love to restore them for her (I have her on medibuntu at the moment)

anjilslaire;
Thanks, I looked at my restore DVD, but have not solved the location of the codecs yet either, I had hoped they were packaged, but I'm betting they are installed and I would need to find out wich files to copy from the disk and into the correct locations on the hdd after I install 8.10; if you find that old posting I'd be very interested, and of course I'll continue digging. I know the answer must be out there some where.

---

### Post by anjilslaire on 2009-03-30
Yeah, it appears the Dell LTS DVD consists primarily of a 1.2GB rootfs.img that refuses to extract easily. My guess is that its installed in the OS image as well. That's unfortunate.

---

### Post by fballem on 2009-03-30
Actually, the medibuntu codecs _almost_ provide the equivalent of the fluendo codecs. The fluendo codecs play Windows Media Lossless, which I don't think the medibuntu codecs do.

You may want to contact fluendo and see if there is something that can be done to help you in your circumstances.

Hope this helps,

---

### Post by notbitmonk on 2009-04-05
I received a Dell Inspiron two days ago and there was link on the desktop to make a recovery DVD.  If you check the DVD you will find the Fluendo codecs and the DVD playback software (in .deb files).  Now, I tried watching some H.264 files (.mov Quicktime) without luck.  Fluendo does provide the codecs on their website so I thought that I shouldn't have any problem.  I asked the Dell representative and haven't got an answer back.  Until I hear from Dell, I'll have to suppose that the Dell codecs from Fluendo do not have all the codecs advertised on Fluendo's website.

---

