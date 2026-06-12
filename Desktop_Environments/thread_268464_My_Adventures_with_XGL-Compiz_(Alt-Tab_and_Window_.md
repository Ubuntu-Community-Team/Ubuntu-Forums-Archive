---
title: "My Adventures with XGL-Compiz (Alt-Tab and Window Decorations--Ahh!)"
date: 2006-09-30
forum: Desktop Environments
---

### Post by aysiu on 2006-09-30
**Back story**
I've heard the buzz about XGL/Compiz for a long time now--months. I've seen the videos and been wowed by them.

Every time I tried to follow a HowTo, I never got it to work, though. I usually ended up breaking my X server (and, no, it wasn't the faulty update from last month).

**Front Story**
Well, I finally found a tutorial that worked for me. It was simple, didn't require me to edit the /etc/X11/xorg.conf file, and it worked... well, mostly.

For the curious, it's called [Howto: Compiz, XGL on Ubuntu for the morbidly lazy](http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2)

It basically just has you install Compiz and XGL and then add a small config file to your home directory. That's it.

**What I Think**
First of all--my assessment of XGL/Compiz at first glance: it's not that great. Things wobble, zoom in and out and such... but (I know people will hate me for saying this) prefer Mac OS X's Expose to XGL/Compiz's zoom. The animation just looks a lot cleaner on OS X. The two things that *did* bowl me over were:

1. The speed at which everything responds. I can actually use Gnome, and it's not sluggish! The animation switching desktops (the cube effect) is fast and smooth.

2. Control-Alt-Mouseclick-Move Around With Mouse is just about the coolest (and most useless) effect I've seen.

**What I Could Use Some Help With**
That said, I'm still encountering a few problems. I did Google around, and it seems there are other people experiencing these problems, but no actual solutions.

1. I can't Alt-Tab. On a related note, I do not appear to have the switcher plugin in GConf-Editor, even though--as per that tutorial I linked to--I have *switcher* specified in the ~/.Xsession file. And I've even tried changing it to --replace. No go there.

2. My window decorations are funky. They appear only if I click on the window or maximize the window.

3. I can't resize or move windows. I can maximize and minimize, though.

Any tips? I'll probably end up still using IceWM, but I thought I'd play around with this just to see what it's like. It's one thing to watch a video online. It's another thing to actually see it on your own computer.

**Edit**: Never mind. I fixed it. Don't know why it didn't work in the first place, but I just went to *gconf-editor* > apps > compiz and edited the *general* key and added the necessary plugins.

---

### Post by Ramses de Norre on 2006-09-30
The howto is pretty old and uses vanilla compiz.. I'm afraid that's quite the reason for your problems.
A few days ago Beryl was released (formerly known as compiz-quinn) and it's A LOT better than vanilla compiz!
So I'd suggest you to try that out, I just did and I like it a lot =)

I can't find the howto I used now (I did it few months ago) but I think the best method is to create a new session in gdm so that you've still got a regular gnome-session on xorg too. And you'll need to change a couple of files to get the best performance but they have no influence on xorg.

---

### Post by aysiu on 2006-09-30
Thanks for the recommendation, Ramses de Norre. I think I figured out what went wrong. The HowTo is formatted in HTML so that if you highlight the text to paste in it creates separate lines for the last bits: ```
rotate zoom scale move resize place menu switcher &
``` It's been fixed on my computer.

If anyone has a working and easy-to-follow HowTo for Beryl, please post a link. There seem to be hundreds of XGL/Compiz HowTos on the web. Many are old, many are complicated, and many just don't appear to work for me.

The "morbidly lazy" one was the easiest one I could find that also worked.

---

### Post by djRobbieF on 2006-09-30
> **aysiu said:**
> If anyone has a working and easy-to-follow HowTo for Beryl, please post a link. There seem to be hundreds of XGL/Compiz HowTos on the web. Many are old, many are complicated, and many just don't appear to work for me.

[http://ubuntuforums.org/showthread.php?t=268036]("http://ubuntuforums.org/showthread.php?t=268036")

---

### Post by aysiu on 2006-09-30
> **djRobbieF said:**
> [http://ubuntuforums.org/showthread.php?t=268036]("http://ubuntuforums.org/showthread.php?t=268036")
I tried that, and it borked my X-server. Thanks for the suggestion, though.

---

### Post by djRobbieF on 2006-09-30
> **aysiu said:**
> I tried that, and it borked my X-server. Thanks for the suggestion, though.

So why not post your problem and get it working?  Just a suggestion.

---

### Post by aysiu on 2006-09-30
Too much work. I'm lazy... morbidly lazy, apparently.

---

### Post by djRobbieF on 2006-09-30
> **aysiu said:**
> Too much work. I'm lazy... morbidly lazy, apparently.

Haha, well... then there's those of us who are running Beryl.  And we laugh at you.  LOL  (not really)... but it's your call  :)

Great thing about community is, you post your problems and others "do the work" while you sit around being lazy... ;)

Anyways... here to help if we can.

Cheers.

---

### Post by aysiu on 2006-09-30
I guess it comes down to this: if it comes to getting a printer working or a proper screen resolution or some other "basic" functionality, I'm willing to work hard (ironically, haven't really had to--most of those "basic" things seem to work just fine without extra tweaking).

If it's just some fun extra GUI effects, I'm not going to put the energy into it unless it's easy. Troubleshooting for frills... not my bag, especially when my whole X server crashes.

---

### Post by djRobbieF on 2006-09-30
But Beryl is so much more than frills.  It's productivity in a beautiful way  ;)  I use it at work, and my goodness it helps me out.  I love it.

But again; personal preference.  It shouldn't be too hard to get you up and running, if you wanted to post your problems in the thread.  But your call.

---

### Post by aysiu on 2006-09-30
Thanks for the offer, djRobbieF. I may take you up on it some day.

---

