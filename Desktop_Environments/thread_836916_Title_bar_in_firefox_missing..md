---
title: "Title bar in firefox missing."
date: 2008-06-22
forum: Desktop Environments
---

### Post by mail2kvasanth@yahoo.co.in on 2008-06-22
I can't see my title bar in firefox. somebody help to [IMG]http://www.flickr.com/photos/click-it/2598927441/[/IMG]

---

### Post by lisati on 2008-06-22
I get that sometime too when I accidentally bump F11..... pressing F11 again usually brings it back again.

---

### Post by rdshaw on 2008-09-17
I am having the same problem. Firefox starts without a title bar visible. It is not running in full screen mode, because when I press f11, it goes into full screen mode where moving the mouse to the top of the screen causes the title bar to slide down. I am running the latest version of Firefox (3.0.1) and Ubuntu Gutsy current on all updates. It is more annoying than anything else, but I would like to correct it because my father is driving me crazy about it.  

Any help is appreciated. 
Thanks, 
Ron

---

### Post by MoebusNet on 2008-09-25
Just came up with same exact problem with FF3.0.2. I submitted a bug report, so we'll see.

Until I can figure this out, I've installed Opera through Synaptic.

---

### Post by zedstrange on 2008-10-16
ditto,  and it happens from time to time with other application windows, but lately it is just firefox.

Pain in the neck,  sometimes a new session fixes it, but mostly not.

---

### Post by BGrigg on 2008-10-16
This is a problem that apparently is a conflict with FF and Compiz. Try "Alt-F2" to bring up the "Run Application" box and type in (without the quotes): "metacity --replace" and see if that restores the title bar. "compiz --replace" restores the eye candy and unfortunately the problem.

---

### Post by mouseware on 2008-11-04
wow, i've been looking for a fix all night! that fixed it, thanks! so when i went back into visual effects and bumped it up to extra and its back the way it was...

happened after upgrading to intrepid, btw!

---

### Post by BezNalogov on 2008-12-10
The strange thing is that this happened to me after some pop-up (that wasn't blocked somehow) appeared. This pop-up deliberately came up without the title bar, so it was very hard to close. 

I pressed alt+tab to move to another window, then I close the pop-up via the gnome panel (via right mouse click and then exit). 

Ever since firefox starts without a title bar, and I have to press F11 twice to get the title bar back. It's like FF has set this as the default for a window to appear.

I removed .mozilla in my home directory and that solved the problem for me. Unfortunately I forgot to backup my bookmarks, so I lost those. So be aware when you will do this, to backup your bookmarks and understand that you will have to do all your settings again.

---

### Post by lori on 2009-02-25
> **BezNalogov said:**
> The strange thing is that this happened to me after some pop-up (that wasn't blocked somehow) appeared. This pop-up deliberately came up without the title bar, so it was very hard to close. 


Same thing happened to me. 
It was a download from **gnome-look.org which had the popup add window (third party site)** which couldn't be closed, after that I had the same problem with Firefox not having a titlebar.
BGRIGG's solution worked for me except that I ran "compiz --replace" **after** running "metacity --replace", problem was resolved and compiz was back.

---

### Post by black-max on 2009-03-02
Thanks BGrigg! Had just installed sexy new compiz themes and was going to blame them. Worked a treat.

---

### Post by duo001 on 2009-04-04
It has been a while but I got this problem again. This time I didn't want to loose all of my data, ie saved passwords, so I found the one file that is the cause. Go into your `/.mozilla/firefox/profile folder/ and remove the localstore.rdf file.

Now I'm sure with some more time someone could go in and find the exact line in that file that causes this. I just don't have that much patience.

---

### Post by zika on 2009-04-04
problem is solved with (this is the place were I learned that) [http://ubuntuforums.org/showthread.php?p=6206588#post6206588](http://ubuntuforums.org/showthread.php?p=6206588#post6206588)

---

