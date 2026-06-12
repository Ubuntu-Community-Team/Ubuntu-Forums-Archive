---
title: "get rid of mysterious boxes"
date: 2014-09-02
forum: Desktop Environments
---

### Post by jgw on 2014-09-02
For some reason I now have 2 boxes on the lower left hand of my desktop.  I have no idea where they came from or what they do.  I have right and left clicked on them and nothing happens.  I have, hopefully, attached a photo of my desktop.  The first box starts with "New Folder" and the second (3d) starts with "Always on Top"[ATTACH=CONFIG]256075[/ATTACH] 

I would like to get rid of them but don't know how.

I made another run at clicking on things.  I found that if I right clicked, on the desktop itself that the top box appears and another desktop right click gets rid of it.  I have no idea what is going on.

Thank you................

---

### Post by deadflowr on 2014-09-02
No clue.
But by chance you didn't accidentally click on the prntscrn button and then also by chance set the image as the wallpaper?
Maybe open up system settings >> appearance and see if it's actually a screenshot or something.

If not, then we can rule that out...

---

### Post by jgw on 2014-09-02
Thanks for the reply.  If you check the attachment (picture of desktop) you will notice two dark boxes, in the lower left hand of the desktop.  You can double click on the attachment for a bigger view of the photo.   Oh, I did nothing.  The machine is never turned off (but restarted every couple of days.  I have not restarted since these appeared).  I just turned on the screen, this morning, and there those boxes are.  They are also always on top which means I have to move the screen out of their way.  As far as I can see they are not functional - just there.

I just took another look at your posting and apologize for telling you about the attachment size.  Seems a big egregious, on my part, give that you are a moderator (which I did not notice)

Thanks again...............

---

### Post by Frogs Hair on 2014-09-02
The top box is the context menu that appears upon right click or with Shift + F10 . It can be used to create a desktop folder ,  gedit text document , or open appearance preferences to change wallpaper . The second is a window title bar context menu , but I don't how it is appearing with no open window.

---

### Post by jgw on 2014-09-02
thanks for the reply.

This is strange.  If I click anyplace on the desktop the top box appears (and goes away).  The bottom box, however, just appears and stays no matter what I do.  I think I will restart the machine and see what that does.  (it remains a mystery <g>)

---

### Post by vasa1 on 2014-09-02
How many file managers do you have? There are at least two items in your launcher that look like icons for file managers.

My suspicion is that you've installed some software that is messing things up. You could run **dpkg --get-selections** and paste the contents here **between code tags** for people to take a look.

---

### Post by vasa1 on 2014-09-02
The Ubuntu Software Center may also help show what software you've installed. Some versions ago, it had a "history" version allowing you to see what software was installed and when. I don't know if that feature still exists and, if it does, how the output can be provided here.

Caveat: if you've installed software just by uncompressing tar files, they won't be registered in the system, AFAIK.

---

### Post by deadflowr on 2014-09-02
> **vasa1 said:**
> How many file managers do you have? There are at least two items in your launcher that look like icons for file managers.

My suspicion is that you've installed some software that is messing things up. You could run **dpkg --get-selections** and paste the contents here **between code tags** for people to take a look.

The orange looking file cabinet with multiple levels, is for the launcher program Drawers.

Still no clue as to the overall problem, though.
The fact that the one dialog box disappears depending on the user clicking on the desktop tells me at least that it isn't an accidental setting of a screenshot as wallpaper, as i earlier proposed, so we can eliminate that as a possibility. 
So, sadly, I'm back at zero.:(

---

### Post by vasa1 on 2014-09-02
The reason I'm suspecting something to do with a file manager is that several common file managers also "manage" the desktop. OP hasn't mentioned the file manager(s) in this thread or here: [http://ubuntuforums.org/showthread.php?t=2229171](http://ubuntuforums.org/showthread.php?t=2229171)

I've seen people recommend alternative/additional file managers without cautioning people about possible conflicts.

---

### Post by jgw on 2014-09-04
thanks for all the replies!!

I solved this one by simply rebooting.  I should have done that from the getgo and I apologize for not doing that.  I think the confusion on file manager is that I also have drawers which has a similar icon.   I have rebooted twice, just to see what would happen, nothing happened and everything is now dandy.  I am writing this off to "mysterious happening" and moving on until it happens again.

Thanks again for all the replies!!

---

