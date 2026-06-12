---
title: "&quot;anibg&quot; is a frontend for animated wallpapers."
date: 2010-11-08
forum: Desktop Environments
---

### Post by clausismus on 2010-11-08
Hi,

I coded an application, which can put a movie or a screensaver on a desktop. It's a frontend for "Shantz-XWinWrap".

If you wanna see a video which shows it in action, then visit [http://www.youtube.com/watch?v=t4ggNlqhDIc]("http://www.youtube.com/watch?v=t4ggNlqhDIc").

You can download it under: [http://code.google.com/p/anibg/]("http://code.google.com/p/anibg/")

Or just type this in your terminal:
```
wget http://anibg.googlecode.com/files/anibg_v0.2.0.deb && wget http://anibg.googlecode.com/files/shantz-xwinwrap_v0.3.deb && sudo dpkg -i anibg_v0.2.0.deb shantz-xwinwrap_v0.3.deb
```

I would be happy, when you give me some feedback.

---

### Post by SlugSlug on 2010-11-11
This looks good!

could you help? When selecting 'Select Background' 
I dnt see screen savers
prefrences are set
Shantz-Xwinwrap: /usr/bin/xwinwrap
Scrennsaver: usr/share/xscreensaver

mplayer ffmepg also set

---

### Post by clausismus on 2010-11-11
Hi,

if you are using Ubuntu then the correct path to the xscreensaver folder would be "/usr/lib/xscreensaver".

I hope I could help you.

I'm coding the support to download videos from the internet.
Some improvements are coded, bugs fixes, one instance of "anibg" can just be runned and the GUI was little changed.

So, you may be curious.

---

### Post by SlugSlug on 2010-11-11
Thanks I'll change that tonight and try again,

Have you thought of a PPA.. maybe you could have a 'extras' package that would supply cool videos / effects you've found?

---

### Post by clausismus on 2010-11-11
Yes I thought about a PPA, but I don't really know how it works with "bzr".

I making now an education as a mechanic and I don't want to use my time just for coding, I have some other hobbies too, so it takes some to time to code the next release (3-4 weeks), and I don't think, that a person checks everday, if a new release was released.

A PPA would be very useful to update the application.

When somebody could help, then help, I think this is a good idea.

---

### Post by clausismus on 2010-11-11
I try to learn, how to manage a PPA.

I created a PPA a time ago, but I didn't knew how to upload my application. The link would be [https://launchpad.net/~clausismus/+archive/anibg]("https://launchpad.net/~clausismus/+archive/anibg").

The command to upload the application would be:

dput ppa:clausismus/anibg <source.changes>

I don't know how to create an "source.changes" file.

The site [https://help.launchpad.net/Packaging/PPA/Uploading]("https://help.launchpad.net/Packaging/PPA/Uploading") says that "debuild" creates this file.

But it seems that "debuild" needs a hierarchy, a folder called "debian" and in the folder there should be files called "changelog" and "rules".

I don't know which files are needed too and how to create these files.

I hope a person could help, who knows how to create a PPA.

---

### Post by SlugSlug on 2010-11-11
quite like the atlantis screen saver

---

