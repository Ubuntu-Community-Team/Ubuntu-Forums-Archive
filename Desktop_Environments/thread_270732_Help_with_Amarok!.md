---
title: "Help with Amarok!"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Zargoon on 2006-10-03
Ok, so I've installed amarok and put some files in my play list but when I click them to play them it just says it's paying for a few seconds and then skips to the next song. I'm using a xine engine.  Any ideas what the problem might be?

---

### Post by dwasifar on 2006-10-03
> **Zargoon said:**
> Ok, so I've installed amarok and put some files in my play list but when I click them to play them it just says it's paying for a few seconds and then skips to the next song. I'm using a xine engine.  Any ideas what the problem might be?
You need the libxine extra codecs.  Look here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mitch.c on 2006-10-03
> **Zargoon said:**
> Ok, so I've installed amarok and put some files in my play list but when I click them to play them it just says it's paying for a few seconds and then skips to the next song. I'm using a xine engine.  Any ideas what the problem might be?
What format are the files... mp3, ogg? Does it play anything at all, or does it just say it's playing before advancing? Have you installed the restricted format codecs (see [https://help.ubuntu.com/community/RestrictedFormats)?](https://help.ubuntu.com/community/RestrictedFormats)?) If you are trying to play mp3 files, you need libxine-extracodecs from the multiverse repository.

---

### Post by Zargoon on 2006-10-05
I followed the instructions and it worked.  However, amarok will play exactly two songs and then it will freeze.  Any ideas why?  I tried this with different music and it's always two songs.  These files are .mp3

---

### Post by Zargoon on 2006-10-06
And ideas?

---

### Post by altonbr on 2006-10-06
I had the exact same problem.. the thread is deliciously called "[amarok won't play music]("http://www.ubuntuforums.org/showthread.php?t=245132")"

I found that I had to physically go into /home/brett/music and drag and drop the files for them to populate and play. Nothing else worked.

---

