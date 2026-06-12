---
title: "nautilus is passing smb:// uri's to my applications on launch"
date: 2010-01-10
forum: Desktop Environments
---

### Post by adante on 2010-01-10
I rebooted my computer. This turned out to be a bad idea because now when I start it, the ubuntu x splash screen comes up then it drops me back to a terminal. Once I log in, run startx, it prompts me for a keyring password which I give it, and then it kills X and restarts it and gives me the gdm prompt. Ok, whatever.

Now when I try to browse my smb:// shares, nautilus tries to launch my applications by passing them a smb:// uri.

So for instance if I double click on a fish.avi file, it seems to launch "vlc smb://host/share/path/to/fish.avi".

VLC is pretty confused about this. In fact most apps are. Given that this *used* to work I assume that nautilus *used* to translate the smb:// uri into a ~/.gvfs/share/path/to/fish.avi so that it would appear as a regular old file to most applications.

Of course this is mainly speculation. The end result is that some fairly fundamental behaviour, that is graphically browsing network shares, is now fairly fundamentally broken for me. 

Unfortunately nowadays I lack the 99 requisite hours to figure out what is happening so I am posting here in the hope that I will get some sort of satisfactory answer.

Is there a way to fix this?

---

### Post by pavi_elex on 2011-11-04
so does it mean when you open your video file through share, it does not open with vlc.
It tries to open it with text editor or any other application?
is it correct?

---

