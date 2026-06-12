---
title: "One translucent window"
date: 2009-12-23
forum: Desktop Environments
---

### Post by warfacegod on 2009-12-23
I was wondering (hoping) if there is a way to make only one window translucent and leave every other window the same. Specifically, Amarok 1.4. I'd like to be able to see my desktop through it.

Basically, I'd like to have these two screenshots overlaing each other.
Thanks.

---

### Post by CHW on 2009-12-24
Hi,

Maby this might help:

[http://ubuntuforums.org/showpost.php?p=8242769&postcount=6](http://ubuntuforums.org/showpost.php?p=8242769&postcount=6)

Regards,
CHW

---

### Post by warfacegod on 2009-12-24
Thanks for replying. I read the post and it looks like that's for just the window borders themselves, I'm running the meta-city opacity theme already. I'm looking to make the entire window translucent so that I can see through the middle of it.

---

### Post by CHW on 2009-12-25
You have to try the compiz solution.
There you can define any window class to be translucent, not only limited to the borders.

---

### Post by warfacegod on 2009-12-25
All right! I got it figured out. In CompizConfig Settings Manager I created a new window specific setting. Type was window title, named it title=Amarok, set the value to 65 and... well, see for your self. This is exactly what I was looking for. Thanks for the assistance.

---

### Post by CHW on 2009-12-26
You are welcome.

---

### Post by Pablo Pablovski on 2009-12-26
Wow, that looks very like my Amarok, which is also translucent using Compiz (80%) and is the only application whose window I make translucent.

---

### Post by warfacegod on 2009-12-26
Cool looking. Is that 1.4? And how did you get all that info onto the right of the window? I'd like to try that myself. I dig the dark theme you've got too.

---

### Post by Pablo Pablovski on 2009-12-27
Yep, 1.4 - I haven't tried 2.x since the original 2.0, which was entirely horrible. 

I got 1.4 from a PPA somewhere - it runs perfectly on karmic - but I might try 2.2, now that it's less than entirely horrible.

And the system status stuff on the RHS is Conky. See the megathread in the Community Cafe for everything you'd ever EVER need to know about Conky - that's where I got most of my configuration from. I've attached my conkyrc file as a starting point. You'll need to rename it to "conkyrc" without the .txt extension, then configure it to suit your system. Install conky-all from the repos. 

```
sudo apt-get install conky-all
```



Edited: Speeling errirs...

---

### Post by warfacegod on 2009-12-27
Yeah, 2.0 was so bad, I dumped it after 5 minutes and spent the rest of the day with a boom-box next to my laptop. Unless 2.2 or anything after is just making 1.4 more excellent, I'm not going anywhere near it.

This conky thing looks very interesting all of a sudden. I'd seen it mentioned in the forums before but just ignored it. This is always the way with me. I get my computer set up perfectly then five minutes later, bam!, I find something cool looking and I'm back to tinkering.

Anyway, thanks for the file. I'll post again in a few days with what I come with. Now, off to make another backup!

---

### Post by hariks0 on 2009-12-28
> **Pablo Pablovski said:**
> Yep, 1.4 - I haven't tried 2.x since the original 2.0, which was entirely horrible. 

I got 1.4 from a PPA somewhere - it runs perfectly on karmic - but I might try 2.2, now that it's less than entirely horrible.

And the system status stuff on the RHS is Conky. See the megathread in the Community Cafe for everything you'd ever EVER need to know about Conky - that's where I got most of my configuration from. I've attached my conkyrc file as a starting point. You'll need to rename it to "conkyrc" without the .txt extension, then configure it to suit your system. Install conky-all from the repos. 

```
sudo apt-get install conky-all
```



Edited: Speeling errirs...
But what is that thing in the LHS? Are they only icons aligned as two sets or what ? And where did the Top panel go?

---

### Post by Pablo Pablovski on 2009-12-28
I use kubuntu which has only one panel by default, and the icons on the LHS are contained within two instances of the desktop folder plasma widget, configured to show my favourite applications and mounted drives.

Could achieve the same thing using icons directly on the desktop, but conky's transparency means they get overwritten by it.

---

### Post by warfacegod on 2009-12-28
I can't find the thread. > See the megathread in the Community Cafe for everything you'd ever EVER need to know about Conky...

---

### Post by Pablo Pablovski on 2009-12-28
Here it is - 11k posts and still going stong! 

[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

I first came across it when it had a few hundred posts, and I've followed it ever since.

Also, the Sourceforge page for Conky is a useful resource.

[http://conky.sourceforge.net/]("http://conky.sourceforge.net/")

and the documentation page will be useful in configuring Conky to your  specification:

[http://conky.sourceforge.net/docs.html]("http://conky.sourceforge.net/docs.html")

Good luck!

---

### Post by warfacegod on 2009-12-28
Thank you my good man.

---

### Post by warfacegod on 2009-12-28
So I've spent some time messing with conky and I like it allot. Unfortunately the changes I'm making to the file aren't sticking. I'm going to drop it for awhile until I'm more comfortable with the "language" or until I find a conky for idiots book.

> In CompizConfig Settings Manager I created a new window specific setting. Type was window title, named it title=Amarok, set the value to 65 and... well, see for your self. This is exactly what I was looking for. Quoting myself here.

I spoke too soon. Firefox started randomly turning translucent too! Took me a bit to realize that I was looking at Amarok pages when it happens. So now I have to change Compiz settings to fix it. Aargh!

---

### Post by Pablo Pablovski on 2009-12-29
The .conkyrc file (the . may or may not be important) needs to be in your home folder by default, unless you launch conky with a switch pointing it to a named config file elsewhere. 

If you haven't put it in your home folder, and launch conky without a named config, your changes won't be in the config file Conky opens, so they won't appear, or "stick".

As regards your Compiz translucency settings, you need to delete the Window Title = Amarok setting, because - as you've found - that will mean Web pages, documents etc. whose title is "Amarok" will be transparent too.

The best way to do it is set Window Class = Amarok to your preferred transparency in CCSM. Good luck!

---

### Post by warfacegod on 2009-12-29
> As regards your Compiz translucency settings, you need to delete the Window Title = Amarok setting, because - as you've found - that will mean Web pages, documents etc. whose title is "Amarok" will be transparent too.

The best way to do it is set Window Class = Amarok to your preferred transparency in CCSM. Good luck!

Yeah that's what I tried right after my last post, worked like a charm.

> The .conkyrc file (the . may or may not be important) needs to be in your home folder by default, unless you launch conky with a switch pointing it to a named config file elsewhere.

If you haven't put it in your home folder, and launch conky without a named config, your changes won't be in the config file Conky opens, so they won't appear, or "stick".

I'll double check on this but I'm pretty sure everything is where and how it should be. Thanks.

---

### Post by warfacegod on 2010-01-01
> Yep, 1.4 - I haven't tried 2.x since the original 2.0, which was entirely horrible.

I got 1.4 from a PPA somewhere - it runs perfectly on karmic - but I might try 2.2, now that it's less than entirely horrible.

I just installed 2.2. It is virtually as bad as 2.0 ergo, entirely horrible.
Messed with it for 20 min. and got rid of it (or tried to at least). I had fits trying to uninstall it. Put 1.4 back and it remembered all of my settings, no configuring required. Good thing I didn't mark it for complete removal.

---

