---
title: "Which version of Fluxbox does feisty have?"
date: 2007-04-06
forum: Desktop Environments
---

### Post by RedSquirrel on 2007-04-06
Hi,

Does feisty have the lastest Fluxbox (1.0rc3) or is it still 1.0rc2? Just wondering whether I should upgrade to feisty for the new Fluxbox or compile rc3 myself...

Thanks.

---

### Post by tbroderick on 2007-04-06
0.9.15.1+1.0rc2-1

You can check at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by RedSquirrel on 2007-04-06
Thanks for the reply.

Funny enough, I was looking at that site and I thought I saw "Last Modified: Mon, 20 Nov 2006" on the *X Window System* software page, but that was in fact the date for the main *Software Packages* page. The *X Window System* page says "Last Modified: Fri, 6 Apr 2007". I think I need some fresh air! :)

---

### Post by yabbadabbadont on 2007-04-06
I thought you always used the SVN version?  Of course, that doesn't preclude you from wondering which version is included in feisty...  :D

---

### Post by kerry_s on 2007-04-06
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29133&stc=1&d=1175896432[/IMG]

---

### Post by RedSquirrel on 2007-04-06
> **yabbadabbadont said:**
> I thought you always used the SVN version?  Of course, that doesn't preclude you from wondering which version is included in feisty...  :D

I was hoping to keep up to date with the SVN version, but I've just been a bit too busy with other projects. However, now that there's a new rc, I feel I should check it out. At the very least, I like the thought of a better rendering job on those rounded window corners!

Thread drift: who are the two ladies in your avatar and what happened to the fancy Fluxbox icon? :)


> **kerry_s said:**
> [IMG]http://ubuntuforums.org/attachment.php?attachmentid=29133&stc=1&d=1175896432[/IMG]

Thanks. You sure have fun with screenshots, don't you? ;)

---

### Post by yabbadabbadont on 2007-04-06
> **RedSquirrel said:**
> I was hoping to keep up to date with the SVN version, but I've just been a bit too busy with other projects. However, now that there's a new rc, I feel I should check it out. At the very least, I like the thought of a better rendering job on those rounded window corners!

Thread drift: who are the two ladies in your avatar and what happened to the fancy Fluxbox icon? :)


I just installed svn-4841 today.  The only thing I've found wrong (so far) is that the issue with excessive space around the clock is back.  They did fix the problem with the clock being justified wrong until the style was reloaded though.  So I guess you win a few, lose a few.  :D  Oh, they also added en_US NLS files, but I ran into strange characters being displayed when I compiled with NLS support.  So I rebuilt without it.  However, I've since discovered that the menu is now supposed to include character encoding settings, so that was probably the problem...

Thread drift response:  They are from the short-lived (2 seasons) Showtime series, "Dead like me".  Fuscia caught so much flak over having an avatar of an actress portraying a dead person, that I decided to switch to one that shows two actresses portraying dead people...  :twisted:

I was getting tired of the old one anyway.  (besides, those ladies are hot ;))

---

### Post by kerry_s on 2007-04-06
I got to use scrot for something. :) 
Plus people like to see things, sometimes i'm just to lazy to type much or my hands just hurt. :(

---

### Post by yabbadabbadont on 2007-04-06
> **kerry_s said:**
> I got to use scrot for something. :) 
Plus people like to see things, sometimes i'm just to lazy to type much or my hands just hurt. :(

I just wish that you would use proper thumbnails.  Not everyone can run resolutions higher than 1024x768 and your screenshots mess up the forums display for me.  :(

---

### Post by kerry_s on 2007-04-06
> **yabbadabbadont said:**
> I just wish that you would use proper thumbnails.  Not everyone can run resolutions higher than 1024x768 and your screenshots mess up the forums display for me.  :(

No problem, i'll use select or resize it for you from now on. :)
PS: remind me if forget.

---

### Post by RedSquirrel on 2007-04-07
> **yabbadabbadont said:**
> I just installed svn-4841 today. 

I just installed 4842! Thanks for your comments regarding the SVN version; they were just the little push I needed. :)

By the way, you mentioned a while ago that you back up the essential Fluxbox system files as a tarball (I did that too, just in case), and then remove Fluxbox, then extract those files in the tarball.

What command are you using when you remove Fluxbox (the Fluxbox from the repos, I mean)? Did you use autoremove? The reason I ask is that /etc/X11/fluxbox/ and /etc/menu-methods/fluxbox were not removed when I did:

```
sudo apt-get remove fluxbox
```Just curious.






> *Thread drift response:  They are from the short-lived (2 seasons) Showtime series, "Dead like me".  Fuscia caught so much flak over having an avatar of an actress portraying a dead person, that I decided to switch to one that shows two actresses portraying dead people...*  :twisted:Clever. 

I had a look at the show's website and it looks pretty good. I'm really not watching enough TV. :lolflag:

> *I was getting tired of the old one anyway.  (besides, those ladies are hot* ;))Yeah, they do kind of jump out at me when I see your posts, especially since they were looking directly at the camera when the shot was taken.

---

### Post by yabbadabbadont on 2007-04-07
> **RedSquirrel said:**
> I just installed 4842! Thanks for your comments regarding the SVN version; they were just the little push I needed. :)
Doh!  Now I have to update just to keep up with the Jones.  :lol:

> **RedSquirrel said:**
> By the way, you mentioned a while ago that you back up the essential Fluxbox system files as a tarball (I did that too, just in case), and then remove Fluxbox, then extract those files in the tarball.

What command are you using when you remove Fluxbox (the Fluxbox from the repos, I mean)? Did you use autoremove? The reason I ask is that /etc/X11/fluxbox/ and /etc/menu-methods/fluxbox were not removed when I did:

```
sudo apt-get remove fluxbox
```Just curious.
That's because I am sometimes frighteningly stupid.  (Out of habit, I always use the "--purge" option)  :oops:

---

### Post by RedSquirrel on 2007-04-17
> **yabbadabbadont said:**
> I just installed svn-4841 today.  The only thing I've found wrong (so far) is that the issue with excessive space around the clock is back.  


In case anyone wants to know, the excessive space is gone in svn 4855. ;)

---

### Post by yabbadabbadont on 2007-04-17
> **RedSquirrel said:**
> In case anyone wants to know, the excessive space is gone in svn 4855. ;)

Thanks for the info.  Since I ditched Feisty and reinstalled Edgy, I've been "drinking the Kool-Aid" and using Gnome.  ;)  This is just the impetus I need to switch back to Fluxbox.  :D

---

### Post by kerry_s on 2007-04-17
> **yabbadabbadont said:**
> Thanks for the info.  Since I ditched Feisty and reinstalled Edgy, I've been "drinking the Kool-Aid" and using Gnome.  ;)  This is just the impetus I need to switch back to Fluxbox.  :D

How come you ditched feisty?

---

### Post by yabbadabbadont on 2007-04-17
> **RedSquirrel said:**
> In case anyone wants to know, the excessive space is gone in svn 4855. ;)

Actually, I just checked a bug I had open in the Fluxbox tracker and it was fixed in SVN 4844.
> Date: 2007-04-07 19:00
Sender: rathnor
Logged In: YES 
user_id=603593
Originator: NO

The trick is that we are trying to avoid constantly resizing the clock
window. So we don't ask for the size of the actual text that is being
rendered, rather the size of this zero-filled string. Mind you, the clock
sizing has changed a bit over the years, so it might not be worth it any
more.

Most (all?) other text buttons are relatively static text. The clock is
the only one that changes very regularly (esp if someone has "seconds" in
there somewhere). Having it change width affects the whole toolbar, so we
really want to minimise that.

However, since the words in the clock change at most once a day, I think
the following would be a far better approach: get the current time string.
replace all numbers with zeros, get its width, and use that as the width.
This allows it to be precise for proportional fonts etc. spaces, colons and
other "thin" characters won't be misspaced - the numbers in the string are
the only things that'd change "often".

... in fact, I like that so much that I've done it (svn 4844).

Closing bug.

Cheers,

 - Simon (observe how idea starts out silly and a bit overcomplicated, but
eventually gets there ;-)  )

You can all thank me for (politely) complaining to the Fluxbox devs about it...  :lol:

---

### Post by yabbadabbadont on 2007-04-17
> **kerry_s said:**
> How come you ditched feisty?

A bunch of little issues (though still annoying) and a couple of big issues.  All of which have been reported and discussed (on and on and on) elsewhere.  I'm going to do what I did with Edgy.  Wait two or three months after release so that all the suckers^H^H^H^H^H^H^Hearly adopters can work out the bugs and find work arounds.  ;)

---

### Post by RedSquirrel on 2007-04-17
> **yabbadabbadont said:**
> Thanks for the info.  Since I ditched Feisty and reinstalled Edgy, I've been "drinking the Kool-Aid" and using Gnome.  ;)  This is just the impetus I need to switch back to Fluxbox.  :D

Hey, great! (considering your comments were the kick to get me to keep on top of the svn revisions) :)

I used enlightenment for a day (E16) but it crashed X while I wasn't doing anything too strenuous and that sent me right back to Fluxbox, which _never_ crashes. <looks-around-for-wooden-surface>

I really like that pager with thumbnail previews in enlightenment, but Fluxbox is still king. Maybe I'll try E17, but it may be even worse for stability (?).

> **yabbadabbadont said:**
> Actually, I just checked a bug I had open in the Fluxbox tracker and it was fixed in SVN 4844.

You can all thank me for (politely) complaining to the Fluxbox devs about it...  :lol:

Well done. I noticed it wasn't at the top of the Changelog for 4855, so I figured it was actually fixed in an *earlier* revision, but I could only state that 4855 was fine since that was the one I installed. Sorry for being so vague about it. :)


> **yabbadabbadont said:**
> A bunch of little issues (though still annoying) and a couple of big issues.  All of which have been reported and discussed (on and on and on) elsewhere.  I'm going to do what I did with Edgy.  Wait two or three months after release so that all the suckers^H^H^H^H^H^H^Hearly adopters can work out the bugs and find work arounds.  ;)

I'm pretty tempted to give it a try (the server edition). OTOH, my edgy works so well, there's really no big rush.

---

### Post by yabbadabbadont on 2007-04-17
> **RedSquirrel said:**
> Maybe I'll try E17, but it may be even worse for stability (?).
Whenever I managed to get E17 compiled, I never had any problems with it taking down X or the system.  Every once in a while it would crash, but it immediately restarted itself and all my open applications were still there.  Nice feature for an alpha window manager.

> **RedSquirrel said:**
> Well done. I noticed it wasn't at the top of the Changelog for 4855, so I figured it was actually fixed in an *earlier* revision, but I could only state that 4855 was fine since that was the one I installed. Sorry for being so vague about it. :)
No problem.  If you hadn't have mentioned it, there's no telling how long it would have been before I would have bothered to check that bug...

---

### Post by RedSquirrel on 2007-04-17
> **yabbadabbadont said:**
> Whenever I managed to get E17 compiled, I never had any problems with it taking down X or the system.  Every once in a while it would crash, but it immediately restarted itself and all my open applications were still there.  Nice feature for an alpha window manager.



That does sound nice. I seem to recall that E17 has a fair number of dependencies. Is it tough to compile?

---

### Post by yabbadabbadont on 2007-04-17
I believe there is a thread here in the forums about an E17 repository that someone maintains.  Otherwise, I would suggest searching for an "easy-e17" type script that will pull down and build the CVS code in the correct order.  I've used the script from [http://omicron.homeip.net/](http://omicron.homeip.net/) before successfully.  However, I can't remember if I used it while I was on Gentoo or Ubuntu.  Either way, it shouldn't matter.

---

### Post by RedSquirrel on 2007-04-19
Thanks for the info.

PS - I'm still grinning at that "drinking the Kool-Aid" remark you made earlier. Well put. :)

---

### Post by RedSquirrel on 2007-05-13
It turns out that backing up all of the Fluxbox system files and then restoring them is a good idea. :)

I discovered that the file /etc/menu-methods/fluxbox lost its execute permissions so my Debian menu wasn't updating. 

It took me a while to notice there was a problem because I rarely use the menu. Lately, I have been using only a handful of apps which all have handy keyboard shortcuts.

Anyway, I fixed the file and all is well. (sudo chmod a+x /etc/menu-methods/fluxbox)

---

### Post by @vijay@ on 2007-09-02
> **RedSquirrel said:**
> In case anyone wants to know, the excessive space is gone in svn 4855. ;)
what is the theme that u r using???

---

### Post by RedSquirrel on 2007-09-02
That one is Vista Black. You can get it here:

[http://ubuntuforums.org/showthread.php?t=320104](http://ubuntuforums.org/showthread.php?t=320104)

---

### Post by @vijay@ on 2007-09-03
> **RedSquirrel said:**
> That one is Vista Black. You can get it here:

[http://ubuntuforums.org/showthread.php?t=320104](http://ubuntuforums.org/showthread.php?t=320104)

thanx .... very good theme :)

---

### Post by RedSquirrel on 2007-09-03
> **@vijay@ said:**
> thanx .... very good theme :)
You're welcome. At the moment, I'm using [Noir]("http://customize.org/fluxbox/themes/49534"). :)

---

### Post by @vijay@ on 2007-09-04
> **RedSquirrel said:**
> You're welcome. At the moment, I'm using [Noir]("http://customize.org/fluxbox/themes/49534"). :)

Cool Website dude ............... im really thankfull that u pointed me thr ........ godlevel

---

### Post by @vijay@ on 2007-09-04
.

---

