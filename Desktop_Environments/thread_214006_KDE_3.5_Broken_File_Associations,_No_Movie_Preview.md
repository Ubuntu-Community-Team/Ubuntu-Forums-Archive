---
title: "KDE 3.5: Broken File Associations, No Movie Previews, and No View Icons"
date: 2006-07-12
forum: Desktop Environments
---

### Post by palsyboy on 2006-07-12
I've been using Kubuntu for a year or two now, and it's blown away any other distro I've used.  6.06 has been better than ever on many fronts, but for some reason, KDE or the particular build Kubuntu is using aren't working well for me.

For one, no matter what I do to change file associations, all video files open in Kaffeine.  Happily, I prefer Kaffeine, so this would be my ideal setting, anyway.  Nonetheless, it could prove to be a problem down the road.

Second, XMMS has been set time and again to open mp3 and m3u files, yet Amarok always opens them up.  And considering how much I dislike Amarok, this is a bad thing.  I always have to remember to use "Open with" when playing music.

Third, no video file of any type has a preview, no matter what settings I play with.  This makes navigation much more difficult for my massive media archive.

Lastly, Konqueror's icons for switching between icon and list views isn't present, and I can't find a way to get them back.  Thus, jumping around my hard drive requires lots of gratuitous mouse-clicking.

I'm *really* into usability and require my interface act in certain ways; the curent situation makes me feel crippled.  I even reinstalled the system after wiping /home, and the same things occurred.

Does anyone have fixes to these problems?  I don't want to switch to Gentoo or Debian.  Or is there a way to install KDE 3.4 on 6.06 without massively affecting the system (so many metapackages)?

---

### Post by croak77 on 2006-07-12
For video previews I think you need libarts1-xine installed. Not sure though.

For file associations, you can go to the Control Center (kcontrol), under KDE Components -> File Associations. 

Not sure about icon and list view switching.

---

### Post by palsyboy on 2006-07-16
Thank you, thank you, and thank you. :)

I don't know why I didn't think to try the File Associations thing.  Just for others who might read this thread later, I'll note that I had to play around with mp3 and m3u associations a lot before it would work.  Specifically, I couldn't remove amaroK's association at some places; I could simply deprecate it and move XMMS to the top of the list.  Maybe it's just a bug, but I'm getting kind of scared that KDE's trying to force me towards using their native apps.

As for the movie previews, you're entirely correct.  Thanks for the tip.

So far, I haven't run into anything yet to fix the view-switch problem.  I'll probably try out [Dolphin](http://www.kde-apps.org/content/show.php?content=40491) whenever I get the time.

---

