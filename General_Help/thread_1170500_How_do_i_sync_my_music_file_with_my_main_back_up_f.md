---
title: "How do i sync my music file with my main back up folder?"
date: 2009-05-26
forum: General Help
---

### Post by GirlofTime on 2009-05-26
Hello,

After helping my friend set up her new ubuntu box on her old dell she asked if she could use her Ipod with it.  I did some light research and ended up putting Banshee on her system.  After playing around with it i decided i wanted to give Banshee a try.

I usually keep all my music on one folder backed up on my external hard drive.  I have copied my entire collection over to my desktop in preparation for installing banshee.  But i was thinking....is there a way to keep my music folder on my external WD in sync with my folder on my desktop.  So i dont have to make two copys each time i buy a new album and/or figure out what things i didnt copy yet to my external hard drive.

So for example, what im looking to do is this....I buy an album lets say Radiohead Kid A.  Currently its sitting in my /home/music folder.  Then when i load up banshee if i remember correctly it should automatically read that new folder.  Now....if and when i decide to back up my music collection with my external hard drive i would connect the hard drive.  Western digital passport. And then at this point i would like some sort of option to "Sync" my external hard drive music file to my ubuntu desktop music file, so i could make a auto back up of that file.  Haha sorry for all the words just wanted to be as clear as possible.  If i can answer any more questions to further help you help me just let me know!...THANKS!!! :KS

---

### Post by maheshasolkar on 2009-05-26
rsync run in archive mode does a pretty good job at this:

```
  % rsync --verbose --progress \
          --archive \
          <source> \
          <destination>

```

For more information on rsync options:

```
  % man rsync
```

If you always update your local Music folder with Banshee, you'll need to use the local folder as source, and the external drive as destination.

If there's another application/computer that updates the external drive, you may need to run rsync with source and destination swapped, so that you get new updates from the external drive to your local folder.

---

### Post by GirlofTime on 2009-05-26
> **maheshasolkar said:**
> rsync run in archive mode does a pretty good job at this:

```
  % rsync --verbose --progress \
          --archive \
          <source> \
          <destination>

```

For more information on rsync options:

```
  % man rsync
```

If you always update your local Music folder with Banshee, you'll need to use the local folder as source, and the external drive as destination.

If there's another application/computer that updates the external drive, you may need to run rsync with source and destination swapped, so that you get new updates from the external drive to your local folder.

Thank you!  I found Grsync for anyone who wants a GUI for rsync.  Works perfectly.  Thank you, thank you, thank you!  I love COMPUTERS!!!

---

