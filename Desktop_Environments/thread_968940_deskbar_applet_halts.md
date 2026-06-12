---
title: "deskbar applet halts"
date: 2008-11-03
forum: Desktop Environments
---

### Post by odzx on 2008-11-03
Since I upgraded to intrepid, deskbar applet turns gray after a while and stays that way after.
I cant say what triggers it really. It seems completely random. Every time it happens i need to kill the process and reload the applet. It is then functional for a while and then halts again. 
I tried to tick off  some plugins like tracker, google , yahoo, searches, but nothing changed.
ideas?
thanks

---

### Post by Blackwolf_Oz on 2008-11-03
Synaptic search deskbar-applet
remove & reinstall

---

### Post by odzx on 2008-11-04
> **legend1264 said:**
> Synaptic search deskbar-applet
remove & reinstall

thanks for the reply.
Tried that already. did not work.

---

### Post by ben2talk on 2008-11-08
> **odzx said:**
> thanks for the reply.
Tried that already. did not work.

SEARCH and find ANYTHING with linux GNOME desktop:
[http://farm4.static.flickr.com/3174/3013817775_5089f04c99_b.jpg](http://farm4.static.flickr.com/3174/3013817775_5089f04c99_b.jpg)
[http://farm4.static.flickr.com/3040/3014654964_618971f716_b.jpg](http://farm4.static.flickr.com/3040/3014654964_618971f716_b.jpg)

I hope this makes you smile - BUMP - the tracker might work one time, and it works REALLY well - launching with ALT F3 works the first time for me - I have to launch it with the panel applet for it to work after that.

your post is 3 days old - did you fix it or are you living with it?

---

### Post by odzx on 2008-11-09
The problem is still here. no solution yet.

---

### Post by nekr0z on 2008-11-27
odzx, I've had the same problem on my system, and have managed to solve it. In case you're still suffering:

1. Remove your old deskbar-applet configuration (it is stored in ~/.gnome2/deskbar-applet/ so I just did ```
rm -r ~/.gnome2/deskbar-applet
```
2. Remove the applet itself from the panel, and after that put it back again (so as to reload it without reloading the whole panel).

The folder ~/.gnome2/deskbar-apple is not created anew, so it looks like deskbar's config was moved to some other place, and the remaining old config causes trouble. All my deskbar settings remained intact after the above procedure, so I figure deskbar should have moved the config by itself, but failed to remove the old copy.

---

### Post by mgmiller on 2008-12-11
> **nekr0z said:**
> odzx, I've had the same problem on my system, and have managed to solve it. In case you're still suffering:

1. Remove your old deskbar-applet configuration (it is stored in ~/.gnome2/deskbar-applet/ so I just did ```
rm -r ~/.gnome2/deskbar-applet
```2. Remove the applet itself from the panel, and after that put it back again (so as to reload it without reloading the whole panel).

The folder ~/.gnome2/deskbar-apple is not created anew, so it looks like deskbar's config was moved to some other place, and the remaining old config causes trouble. All my deskbar settings remained intact after the above procedure, so I figure deskbar should have moved the config by itself, but failed to remove the old copy.

The above solution did not work for me.
What I found is that if I use deskbar, I must search for something and then use the search results, otherwise, deskbar fails to a blank screen the next time it is run.

For example:
1) do a search and find something useful.  Click on the found item and view the results.  >  All is fine and deskbar will continue to work.

2) do a search and whether it finds something useful or not, do nothing and close the search.  > Deskbar will no longer work, it displays a grey screen on subsequent runs.

3) Activate deskbar either from alt F3 or by clicking on the panel icon.  Don't enter anything in the search field and close the search.  > Deskbar will no longer work, it displays a grey screen on subsequent runs.

So, it seems deskbar gets mad unless you actually use it.

---

### Post by nekr0z on 2008-12-11
mgmiller, sorry to say that, but I failed to reproduce "gray failure" using the methods you've given. Whatever I do to my Deskbar, it works just as it is supposed to.

---

### Post by odzx on 2008-12-11
The above fix did not work for me either. I can get deskbar to turn grey by closing it using the the X on the top right of the window (works every time).It also turns grey  just randomly for no apparent reason every few times i turn it on/off (with ESC,F3,Clicking the applet icon).

---

### Post by nekr0z on 2008-12-11
Closing with X works for me too, thanks, odzx! (By "works" I mean "reproduces the bug".)

---

### Post by mgmiller on 2008-12-11
I should have been a little more explicit.  I am closing the search window by clicking the x on the top right of the window.  

At least it's reproducible.  How else do you close this window without clicking the "x"?

---

### Post by nekr0z on 2008-12-11
Well, I usually stick to keyboard while using Deskbar, and it's convenient to close the search window the same way you open it (i.e. Alt+F3). Esc works, too. Closing the window this way I cannot reproduce the bug, but using X in the corner reproduces the bug perfectly (and so does Alt+F4).

---

### Post by mgmiller on 2008-12-12
I just tried alt/F3 and esc to close the window and deskbar continues to work normally.  

I have entered a bug report on this.

[https://bugs.launchpad.net/ubuntu/+source/deskbar-applet/+bug/307421](https://bugs.launchpad.net/ubuntu/+source/deskbar-applet/+bug/307421)

Since you also experience it, could you please confirm the bug at the above link.

---

### Post by nekr0z on 2008-12-12
Done, and added one more way of non-buggy window closing.

---

### Post by mgmiller on 2008-12-12
Thank you.  
I confirm that clicking on the deskbar icon to close the app does not trigger the bug in my system as well.

---

