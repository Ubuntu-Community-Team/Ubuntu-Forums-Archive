---
title: "No thumbnails ubuntu 7.04"
date: 2007-06-10
forum: Desktop Environments
---

### Post by drunya on 2007-06-10
After uprgrading ubuntu 7.04 all thumbnails have disappeared... Deleting ./thumbnails didn't help. I've tried to change thumbnail options in Nautilus, but it also doesn't help. :( Can you help me?

---

### Post by khulbert on 2007-06-17
I am having the same problem, and have been unable to get anything to work :(

I think my problem has something to do with the fact that for some reason on my system applications aren't automatically associated with filetypes.  Before I can open any file I have to choose a program to open it.

---

### Post by CupofDice on 2007-06-19
I ran into a video thumbnail problem last week, so I came across this info from [here]("http://ubuntuforums.org/showthread.php?t=204380&highlight=No+thumbnails") .Type "gconf-editor in the terminal and check apps/gthumb/browser and make sure 'show thumbnails is checked. If you can't get video thumbnails, [mplayer-video-thumb]("http://me2030581.googlepages.com/") helped me out.

---

### Post by khulbert on 2007-06-19
It is the jpg thumbs that I'm trying to fix, but the video thumbs don't work either.  The options were already set correctly in gconf, I'm still stuck.

---

### Post by The Caped Crusader on 2007-08-18
I'm having exactly the same problem. Happens with PNG, JPG and all image files I currently work with. I had to re-associate image viewer/gthumb to them to be able to open them.

Happens with video files too. AVI, etc.

Tried to reinstall Nautilus but to no avail. I can't remember if this happened after some kind of update of new package install... damn :(

I've also deleted Desktop's .thumbnails folder but Nautilus didn't generate a new one, as expected.

Mp3's sound preview works fine, which means this is image-related exclusive problem.

Any ideas of other packages I can purge and/or reinstall? jpglibs maybe?

This is my first post here on Ubuntu forums. Ubuntu is great, BTW! :D

---

### Post by The Caped Crusader on 2007-08-19
I tried to uninstall some graphic packages i installed recently but the porblem continues. Nautilus doesn't generate .thumbnails folders.

Is there some way to safely uninstall Nautilus and reinstall it with default settings? I suspect that it might do the job.

If not, i guess it's reinstall-ubuntu all over again :P

---

### Post by whomever21 on 2007-10-20
I'm having this problem in 7.10. Did anyone ever figure out how to fix it in 7.04?

---

### Post by whomever21 on 2007-10-20
I figured this out about ten seconds after I posted--just in time to embarrass myself in front of the techies.

Anyway, I installed the following and my video thumbnails just...worked.

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 
gxine ffmpeg ogle ogle-gui
```

---

### Post by zavius on 2007-11-24
I'm still not getting this to work. None of my images are showing previews. A few vid files are but the ones I'm worried about are images. 

Anyone figure this out???

---

### Post by rune0077 on 2007-11-24
I had kinda the same problem. Check out this: 

[http://ubuntuforums.org/showthread.php?t=619121]("http://ubuntuforums.org/showthread.php?t=619121")

It solved most of my problems, though for some odd reason, a few of the files didn't get fixed. The rest is back to normal.

Hope that helps:)

---

### Post by zavius on 2007-11-24
That fixed it!!!! Thanks so much!!!

However my .jpg's and other pictures are only showing thumbnails when I click on then. How do I get them to automatically show up??

---

### Post by rune0077 on 2007-11-25
Okay, I think i found a solution, but you're not going to like it. If you erase the extension of the filename (like .png or .jpg etc) I actually think its going to work. I did this by accident with one of my non-fixed images, and it has shown up fine since then. I tried doing it with a few more, and lo and behold, they behave normally as well. 

This is a stupid solution. I have something like 800 photos in my Picture folder, and as far as I can tell, this is the only way to get them back to normal. It's going to be a long night...

---

### Post by zavius on 2007-11-25
Actually I believe the solution is to delete a file in the ~/.local directory. I can't find the post that I found and I'm not on my Linux box right now. I believe it was something like this:

~/.local/applications/mimetypes.cache

It solved my problem. I will post if I can find that post again.

---

### Post by t0n1 on 2008-07-13
I have the same problem in Hardy.
None of the methods posted here worked.
Has anyone got a solution?

---

### Post by whomever21 on 2008-07-18
Deleting $HOME/.local/share/mime/mime.cache worked for me, but usually all I have to do is add the medibuntu repository and install ubuntu-restricted-extras.

---

