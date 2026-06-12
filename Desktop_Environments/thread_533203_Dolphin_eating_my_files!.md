---
title: "Dolphin eating my files?!"
date: 2007-08-23
forum: Desktop Environments
---

### Post by saggio on 2007-08-23
Hi there, 

I'm an amateur musician, and, as such, I have a rather large collection of music. I've digitized most of what I have (encoded as FLAC), and I've been using audacious to play them (amarok messes with the way I categorize my music). So far, it's been going great, and I've had no issues. k3b is perfect for my needs (not as fancy as EAC, but still pretty good), and, up until now, Dolphin was very effective as a simple file manager.

However, I've recently run into a BIG problem. As I was re-arranging some of my albums and moving them into over-arching artist folders (artist-album-track is how I organize), some of them disappeared.

Gone. The folders I created are empty, and I can't find the missing album folders anywhere! There's nothing in the 'trash' icon in Dolphin, and I'm getting very worried. Around 5 gigs of music I can't seem to find - and they happen to be some of my favourite albums, too! On top of this, I just moved and I don't have all of my CDs with me, so I can't just re-rip. :( 

If anybody knows anything about this issue, please let me know! I'm having a hell of a time.

---

### Post by Happy_Man on 2007-08-23
How were you moving them? Dragging and dropping, or using the command line? you could have entered the wrong command by mistake......


You can always install an application like Beagle/Kerry and search for it using that.... or use the inbuilt search capabilities of Linux:

For beagle/kerry:
```
sudo apt-get install kerry
```

For the inbuilt search ```
sudo updatedb
find <search terms here>
```

Hope some of this helps!

---

### Post by saggio on 2007-08-23
Thanks for the tip! 

Turns out, Dolphin moved all my stuff to completely random folders. x\ I don't know if that's a bug of the software, or my fault. Regardless, I'm just glad to have found my music again!

Thanks.

---

