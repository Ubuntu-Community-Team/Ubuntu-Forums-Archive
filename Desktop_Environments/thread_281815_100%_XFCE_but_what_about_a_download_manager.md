---
title: "100% XFCE but what about a download manager?"
date: 2006-10-21
forum: Desktop Environments
---

### Post by TiredBird on 2006-10-21
I followed the instructions at [http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce") to get a pure xfce environment but one of the things that got wiped out was 'gwget', leaving me without a graphical download manager (I still have 'wget' which can be used from the command line). So what do I do now? I want a graphical download manager. Do I reinstall 'gwget' or is there something better?

---

### Post by taurus on 2006-10-21
Why not use apt-get/aptitude from a terminal.  Nice and easy...  ;)

---

### Post by TiredBird on 2006-10-21
I need more explanation. How do I use that for downloading a video or a lot of pictures? I'm pretty computer savvy but I'm a noob when it comes to Linux or Ubuntu.

If you've got a solution, I'm more than willing to try it but I honestly don't understand what you're suggesting.

---

### Post by taurus on 2006-10-21
What do you mean by downloading a movie or a lot of pictures?  :confused:

---

### Post by TiredBird on 2006-10-22
Say a video thats 200 MB or zip full of pictures, maybe 100 MB. Or lets say I want to download an ISO image - about 650 MB. Those are the kinds of things I would like to use a download manager for. Most of these things I find first with Firefox. When I tell Firefox to download it, Firefox hands it off to Flashgot, an extension I added to Firefox, then Flashgot sets up my download manager to take care of it. All of this used to happen automatically when I had gwget installed, but wget, which is still installed, doesn't do it by itself. It needs 'gwget' to interface between it and Flashgot.

Got any ideas?

---

### Post by taurus on 2006-10-22
Try using links or links2!!!

---

### Post by TiredBird on 2006-10-22
I appreciate the fact that you're trying to help but...

I just looked at a description of links and links2. Those seem to be web browsers. I already have one of those - Firefox - and I'm not planning to change that anytime soon. It looks like I'm not going to find an XFCE replacement for 'gwget'. Guess I'll just reinstall it. At least it was working.

---

### Post by MrWizard on 2006-10-25
taurus was suggesting you install gwget with aptitude in the Terminal, like so:
```
sudo aptitude install gwget
```

However, gwget is a Gnome front-end for wget and, although I do believe it should work from within XFCE, it will require that you install the Gnome dependencies.  This may or may not be objectionable to you.

If you want to stay away from that, I would suggest Downloader for X.  I haven't used it extensively, but it seems to work reasonably well and is comparable to something like GetRight on Windows.  It can also be installed from the Terminal:

```
sudo aptitude install d4x
```

Hope this helps.

**Edit:** Another option for you might be wxDownload.  This seems to be a feature-rich download manager.  It is not, however, in any of the Ubuntu repositories (as far as I know).  But an Ubuntu 6.06 package can be downloaded here:
[http://www.getdeb.net/search.php?keywords=wxDownload](http://www.getdeb.net/search.php?keywords=wxDownload)

---

### Post by TiredBird on 2006-10-26
MrWizard,

Thanks for your help. The suggestions you make are not ones I evaluated. I wanted to keep using flashgot, the firefox extension, so I went to their website to see what download managers they supported. gwget was the only one they supported that was in the Ubuntu repositories so I reinstalled it.

Yes, it drags a lot of Gnome dependancies with it and that is what I was trying to avoid. However, I let them come in.

Now, however, after some bad experiences with flashgot, (I can set the default location for a download but it puts everything in the same folder.) So, I ended up removing it and gwget and the dependancies.

Now I'm back to using the downloader thats a part of Firefox and although its not quite as efficient as some others, it does do what I want. And, if I have some serious downloads, (like full ISO images), I can still use 'wget'.

Thanks for the suggestions though.

---

### Post by kalikiana on 2006-10-27
What about using Freeloader? Should be in the repositories I think, it is able to load torrents as well. The only disadvantage is that it's perl.

I think I'm going to try d4x now. :)

---

