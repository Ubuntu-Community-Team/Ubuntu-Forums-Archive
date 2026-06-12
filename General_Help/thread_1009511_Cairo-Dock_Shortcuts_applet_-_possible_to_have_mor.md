---
title: "Cairo-Dock Shortcuts applet - possible to have more than one?"
date: 2008-12-12
forum: General Help
---

### Post by Ng Oon-Ee on 2008-12-12
The shortcuts applet is cool, but I think they tried to pack too many things into it, right now it can display my nautilus bookmarks, my mounted/unmounted drives, and my network drives. The problem is, in parabolic view this basically fills up the entire height of my wide-screen monitor (yes, I have quite a few bookmarks and multiple partitions).

My question is, is it possible to have more than one copy of the Shortcuts applet on my cairo dock? Then I can use one for bookmarks and one for the drives.

---

### Post by fabounet on 2008-12-15
it is not designed to be launched many times, as I didn't think there could be so many icons in it ^_^
for the moment the best you can do is adopting another view for the sub-dock, until a patch is made.

---

### Post by Ng Oon-Ee on 2008-12-15
> **fabounet said:**
> it is not designed to be launched many times, as I didn't think there could be so many icons in it ^_^
for the moment the best you can do is adopting another view for the sub-dock, until a patch is made.
Ah, the man himself speaks :)

Thanks for the reply. I'm no dev, but doesn't seem to me like it would be extremely hard to patch this? Thanks for the great work though. We really appreciate it.

And yes, the reason there's so many icons in it is a combination of widescreen limiting the height of my display, using this laptop as a general-purpose machine therefore many Nautilus bookmarks corresponding to different areas of work/play, and a dual-boot system with separate /home and /data partitions. Doubt I'm similar to the norm, but again, doubt I'm totally unique as well.

---

### Post by fabounet on 2008-12-15
patch is done :-)
if you're using the SVN, it will be available tomorrow.
seems to work fine, but if you experience some new bugs with it, thanks to report them ;-)

---

### Post by Ng Oon-Ee on 2008-12-15
Ah, I'm actually using stable version from repos. But I guess since you've taken the trouble, I will go compile SVN and test out the latest.

Thanks again.

---

### Post by Ng Oon-Ee on 2008-12-16
> **fabounet said:**
> patch is done :-)
if you're using the SVN, it will be available tomorrow.
seems to work fine, but if you experience some new bugs with it, thanks to report them ;-)
Have just tested the patch, works just fine, thanks =). The opengl option is cool, but yesterday's animations were totally screwed, though, didn't really activate, just see one frame of animation and then it stops, mouse move causes a few more frames of animation.

To note, the version prior to the current (1439) version I'm using, the icon animations worked perfectly. Not sure what you've changed, and unsure where to contribute on your forums as well (don't understand French, sorry =) )

---

### Post by fabounet on 2008-12-17
our forum is opened to english speakers of course :-)
yep animations are screwed right now, I'm moving them to plug-in (merging cairo animations and openGL animations is quite tricky, but I plan to finish this in a few days)

---

### Post by Ng Oon-Ee on 2008-12-17
I know its open to English speakers, but navigation is quite a challenge. Makes me feel out-of-place :). So I just browse to see if similar issues to mine have been raised. Or use babelfish.

Thanks so much for your work on this dock, and for replying on all those different forums (I see your nick quite a bit around the forums)

---

