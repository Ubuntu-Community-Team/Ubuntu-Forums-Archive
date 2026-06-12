---
title: "Error showing Vista folder content in Ubuntu"
date: 2009-05-30
forum: General Help
---

### Post by tripod on 2009-05-30
Hello everybody

I have tried to search the net for an answer to this question, but no luck so far.

I've partitioned my harddisc into two parts, one containing Windows Vista 32-bit, and one containing Ubuntu (the newest).
When I mount my Vista-filesystem (NTFS) by clicking it in the dropdown menu at the top of my screen "Locations", it mounts without errors.

But when I'm trying to acces my music files, saved in Vista and mounted in Ubuntu at /media/Windows/username/Music, and clicks the folder "Music", it shows no content. No files at all, and more critical, no errors. 
But when I start my PC (ThinkPad T61)in Vista, I can see, that the music files exist.

The music is stored in mp3, and I have the suitable codecs installed.
My guess is, that I don't have the rights do view the content of the folder, but since I get no errors I'm stuck.
Ask me if you need postings of my fstab or something else.

Thank you in advance, Tripod.

---

### Post by kmitnick on 2009-05-30
try to access it from terminal using sudo
```
sudo /media/Windows/username/Music
``` then ```
ls -al
```

---

### Post by merlinus on 2009-05-30
Are you certain that your music folder is being mounted.

Try the mount command in a terminal and see what comes up.

Also, posting fstab wouldn't hurt.

---

### Post by tripod on 2009-05-30
Allright, think I've solved my own problem.
It turned out that I've used Wubi to install Ubuntu, so the info given before is wrong (my files are in /host/Users/username instead).

The solution was to enable sharing for everyone in Vista, and then switch back to Ubuntu. Just as simple as that.

Sorry for taking your time (but thank you for your fast answers, you guys rock!), sometimes life is more easy than you think. 
Maybe it's not the definitive solution, but for a newbie as me, it's a suitable workaround.

Greetings, Tripod.

---

