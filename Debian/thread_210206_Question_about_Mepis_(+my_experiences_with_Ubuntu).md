---
title: "Question about Mepis (+my experiences with Ubuntu)"
date: 2006-07-06
forum: Debian
---

### Post by Albi on 2006-07-06
Well, I've tried both Ubuntu, Xubuntu, and Kubuntu on my older computer, and the experience hasn't been that great.  The specs are 800mhz Celeron, 128mb ram (no idea what kind :\), and a 30gb hard drive, and it came prepackaged with Windows ME (*shudders*) back when I bought it.

Ubuntu:
I installed this back in 5.10.  I messed some things around (apt would give me a lot of errors) but eventually got everything working.  The only problem was that gnome was so slow, Firefox would take around 15 seconds to launch and would lag like hell when MSN was open at the same time.

Xubuntu:
This was faster, but nowhere near as polished.  It seemed that the window bar would only go halfway across the screen unless you used the default one, making an application launcher was a pain in the ***, and I still don't know how to make a shortcut on my desktop using xfce!
Eventually, I used nautilus instead of xfce as my desktop manager, and the speed difference wasn't noticeable.  However, it didn't feel very polished and user friendly, so I eventually ended up installing Kubuntu, hearing that it was faster than the regular.

Kubuntu:
The speed difference wasn't that great vs gnome, I had a lot of the same problems.  I do, however, like the user interface more than gnome when it's customized.

So my question would be:
Is Mepis3/6 noticeably faster than Kubuntu, or should I just go back to Xubuntu or seek another distro?

---

### Post by aysiu on 2006-07-06
Mepis will not be noticeably faster than Kubuntu on 128 MB of RAM.

You should go back to Xubuntu and learn to love it. 128 MB of RAM will get you little love on KDE or Gnome.

---

### Post by Albi on 2006-07-09
Hmm I tried Xubuntu for a while.  Although it's faster, it's still sluggish.
I'm using zenwalk right now.  It's faster, but I miss apt-get and automatix :(

---

### Post by aysiu on 2006-07-09
That's surprising, because Xubuntu flies on my 766 MHz 128 MB RAM machine.

Try [this](http://www.ubuntuforums.org/showpost.php?p=692882&postcount=8).

---

### Post by koshari on 2006-07-09
i was pretty happy with xubuntu on a 700athlon with 256 ram, 

we also run xubuntu on a p2 350 with 64 meg of ram exlusively to drive a shared scanner in out workplace, its a little sluggish but was a hell of a lot easier to get a scsi scaneer operational than puppy.

---

### Post by 3rdalbum on 2006-07-10
Xubuntu actually takes a bit of getting used to. I installed Xfce (the last stable version - I meant to install the development one) on my computer now and I appreciate it more than I did when I tried it months ago.

With Thunar, it's great... but don't throw out Xffm, you'll occasionally need its power.

---

### Post by dermotti on 2006-07-10
I love Xubuntu.

Yea Zenwalk is pretty damn fast, but it at a cost of alot of other things. Its easier to mess up, harder to administrate for a newb.

Xubuntu just works.

---

### Post by Albi on 2006-07-10
> **aysiu said:**
> That's surprising, because Xubuntu flies on my 766 MHz 128 MB RAM machine.

Try [this](http://www.ubuntuforums.org/showpost.php?p=692882&postcount=8).

How would I modify that to include xfce instead of icewm?

Zenwalk didn't require any modifications after I installed it, but I don't like the fact that it's slackware based but has little slapt-get compatibility.  You have to basically just find and install all libraries for a program you want yourself.

---

### Post by aysiu on 2006-07-10
*xfce4* instead of *icewm*.

---

### Post by Albi on 2006-07-10
> **aysiu said:**
> *xfce4* instead of *icewm*.

Yeah I know it seemed obvious but I just wanted to make sure.  I'll try it on my computer once I buy a new mouse.

---

### Post by brentoboy on 2006-07-10
you might consider going back down the distro tree to debian sarge instead of up it to mepis.  I just tired the new mepis over the weekend, and spent about two hours with it before going back  to ubuntu.  I just didnt see it as much of an improvment over ubuntu (once you have all the codecs setup on ubuntu)

the version of gnome (and kde) that works on debian is older, so it is more responsive on older PCs.  But, it is gnome  (or kde) and not a differnt desktop altogether that isnt as feature rich.

Once you have tried all the different ubuntu's, you probably have enough experience to get debian going without too much hassle.  Ubuntu is built on debian (a newer version of debian, but debian non the less)

---

### Post by jacksaff on 2006-07-11
> **brentoboy said:**
> 

the version of gnome (and kde) that works on debian is older, so it is more responsive on older PCs. 

This is not true at all. Every version of kde in the 3 series has been faster and required less resources than the one it has replaced in spite of increased functionality. I believe the same is true of gnome.
The difference between ubuntu's and sarge's versions of kde is that the former has more bug fixes and performance tweaks wheras the latter has been more thoroughly tested (by virtue of being around longer).
You really need 256MB+ of RAM to run either kde or gnome well and 512 would be better. XFCE runs well with 128 and is useable with 64 on one of my pcs as long as I don't try keep too many larger apps open. With 64MB of RAM you start wanting to avoid memory hogs like firefox but the desktop itself works fine.

---

### Post by brentoboy on 2006-07-11
That might all be true -- I dont know.

I do know that on an old PC I once tried to get working debian woody was the "newest" thing I could successfully install and not HATE how slow everythign was.  Woody installed KDE as the default desktop.

---

### Post by Albi on 2006-07-11
I found out why Xubuntu wasn't running as fast as it should be; it turns out that when I installed it from the server CD (following aysiu's guide at psychocats), I did not update the kernel afterwards.  This means I was using a server kernel instead of a 686 one, and the speed difference is noticeable and made it faster.

I did the minimal install; it worked for the most part, but it's missing a few essential things like thunar and sound control.

---

