---
title: "iPod Video Trouble with Amarok and gtkpod"
date: 2006-03-13
forum: Desktop Environments
---

### Post by happyponcho42 on 2006-03-13
I just got an iPod video and am having trouble transferring music.  Initially, I connected it to a Windows computer and transferred a bunch of mp3's over successfully.  Now, I'm over on Linux and problems are arising.

I've installed gtkpod and followed many how-to's on the web including the one on these forums.  I can mount my iPod Video successfully and gtkpod reads my iPod and lists the songs on there.  However, when I add songs to my gtkpod local and attempt to Sync, the database updates but nothing is transferred over.

I tried reinstalling gtkpod, with different versions each time and still run into the same problem.  I hit Sync, but no songs are transferrered at all.

And so...I moved to Amarok...

With Amarok, I can successfully connect to my iPod Video and list the songs.  I then click on a few albums in my Amarok Collection and select "Add to Media Device Transfer Queue".  Ok, so that went well since it appears under the URL in my Media Device tab.  But...when I click Transfer, and it appears to finish transferring, I unmount my iPod and look through it to find that the songs do not appear anywhere.

And so...I tried retransferring the songs.  When I try to transfer, Amarok prompts me and asks whether I wish to overwrite the songs since they already exist on the iPod, stating the exact location of the song on the iPod with the file name.  So now I guess Amarok did transfer the songs over, but why are they not appearing on my iPod?  I did notice that my free space on my iPod jumped down to 25.00GB so I am pretty sure that the files transferred, but for some reason, do not appear on my iPod Music list.

Any takers?

---

### Post by dpaint4 on 2006-03-13
I wonder if you're using an iPod compatible codec, or if you've set any kind of transcode option. My first quess from what you're saying is that you imporeted some CD's into Amarok in the default Vorbis format, and that you've transferred thost files to your iPod, but aren't able to see or play them from your iPod because they're not in MP3 or AAC or ALAC.

But that's only a guess. If you're dealing with a library of one of the above three formats, or have your program set to transcode to them before transferring to your iPod, then my guess is no good for you.

I just switched to Ubuntu from XP, and I'm currently avoiding my iPod Video and pretending it dosen't exist because I just KNOW it's gonna be trouble to get the thing working.

---

### Post by happyponcho42 on 2006-03-13
Well, problem solved...half of it anyways.

I followed the tutorial on compiling amarok svn from source (apparently, 5G iPod support is broken in Amarok 1.3x), and I can now successfully transfer music to my iPod with it showing up.  The only concern I have now is the wasted room from the previous Amarok installation uploading the music to wherever on my iPod (the amarok version that uploaded, but songs did not show up)...but hey, 30GB is a lot to use, so I doubt I'll come across any capacity issues.

Now being that I have an iPod Video, I should be able to put videos on there.  gtkpod, however, still refuses to send anything to my iPod, after attempting to 'Sync' it many times (all it does is update database, and nothing else).  Any takers for the gtkpod issue?  I'd really like to get it to work so I can start using the video feature of my video iPod.

Thanks

---

### Post by alecjw on 2006-10-14
> **happyponcho42 said:**
> Well, problem solved...half of it anyways.

I followed the tutorial on compiling amarok svn from source (apparently, 5G iPod support is broken in Amarok 1.3x), and I can now successfully transfer music to my iPod with it showing up.

Where did you find this tutorial?

---

