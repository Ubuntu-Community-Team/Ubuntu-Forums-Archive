---
title: "gtkpod and iPod - transfer podcasts to &quot;podcast&quot; directory help"
date: 2009-03-31
forum: General Help
---

### Post by golbez_88rule on 2009-03-31
I recently installed gtkpod 0.99.12 from the repositories (I'm using 8.04).  I am able to transfer podcasts that I downloaded with podget to my Ipod (Nano 3G, 8 GB video) using gtkpod, but they are always put into the Music category under genre Podcast, instead of the Podcast menu within the iPod interface.  In the gtkpod window all of the podcasts show up in the Podcasts playlist in my iPod's repository, and all of the podcast files have "Podcast" as the genre.  A similar problem was reported with Rhythmbox was reported in these forums [here]("http://ubuntuforums.org/showthread.php?t=944274&highlight=ipod+podcasts") but no response.  Has anyone successfully been able to use gtkpod to transfer podcasts correctly to the podcasts menu in the iPod?

---

### Post by jdforsythe on 2009-09-14
When you drag your files to the podcast playlist in gtkpod, do it to the podcast playlist on your ipod, NOT the one under Local, ipod... Does that make sense?

In other words, to the podcast playlist with the music notes icon, not the one with the hard drive icon.

That should make them show only in podcasts and not under music.

---

### Post by alienclone on 2009-09-14
nevermind

---

### Post by mr_luksom on 2010-10-03
Fully realising this has thread has been sleeping for a year, I am going to bump because I am having the same problem.

I am getting my podcasts from podget, and syncing with gtkpod. I copy them to the 'Podcasts' repository on the iPod. It syncs, I can see them and play them, however they are mixed in with music.

Any ideas?

---

### Post by mr_luksom on 2010-10-04
I've managed to solve it.

First, out of the README, add files and folders directly to the 'Podcasts' repository on th iPod. Don't drag n drop from any other libraries/ repositories.

Then, some manual post-processing is required. I'm sure this is just replicating iTunes. Select all of th podcasts in the iPod repository, then hit 'Edit Track Details.' Make sure you hit the edit multiple files checkbox (you may need to edit you preferences first). Then:
1. Change file type from 'Audio' to 'Podcast'
2. Select 'Skip when shuffling', 'checked', 'bookmarking'
3. Make sure there are albums for each 'feed'
4. Add a podcast URL (podcast tab)
5. Add the same URL as the rss feed.

If you do all of these things, then it will show up in Podcasts. I wonder if some sort of script could take care of this?

---

