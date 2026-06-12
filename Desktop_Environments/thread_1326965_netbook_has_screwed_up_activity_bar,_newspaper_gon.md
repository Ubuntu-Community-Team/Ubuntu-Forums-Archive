---
title: "netbook has screwed up activity bar, newspaper gone"
date: 2009-11-14
forum: Desktop Environments
---

### Post by pwrcul on 2009-11-14
I screwed it up while trying to figure out stuff with little success.  In my trial and error I took the option to remove stuff, but I see no way to get them back.

So I no longer have the number applications running, newspaper button, applications button, and the binoculars are over on the left.  

I am still clueless on where this stuff is documented.  All I could find are videos/demos, reviews, overviews, of the desktop and the documentation for regular KDE.

Thanks in advance.

More:  background, more rant:

Let me mention I am only now seriously striving to switch to Kubuntu on my desktop machine and on my netbook.  So I don't know that much yet.

I wonder if I have to reinstall the whole Kubuntu netbook package?
I wonder if I can somehow repair or replace just the damaged activity bar?

Has anyone worked up any documentation for the netbook version?

I was having trouble with the newspaper, now I seem to have lost it.  Any clues on it?

---

### Post by pwrcul on 2009-11-15
I found a partial fix with a downside, 

I have a new default activity bar, but no applications and still no newspaper.  

Clicking on the buttons for Applications and Newspaper on the new activity bar shows a successful press but no result.

Good Part:
From this link I learned how to get the applications bar in post 7.
[http://kubuntuforums.net/forums/index.php?topic=3107347.0](http://kubuntuforums.net/forums/index.php?topic=3107347.0)

The relevant passage was this:
"if you want to get back to the default, you can delete .kde/share/config/plasma-netbook-appletsrc in your home directory and restart KDE."

I chose to mv the screwed up one to the same name plus .old

But then I got a totally white desktop with only my activity bar as the exception.

---

### Post by pwrcul on 2009-11-17
An update:
I tried in konsole
   kquittapp plasma
but was told no plasma app was running.

so in .kde/share/config/ I used mv to change the names of all that start with plasma to .old and restarted.
I got back most of what I had destroyed.  The newspaper came back without its containment though.

Right now I am still considering a reinstall of the regular Kubuntu or perhaps the remix.

---

### Post by Zorael on 2009-11-17
The processes' names are plasma-desktop and plasma-netbook, I believe.

And yes, removing/renaming everything rhyming with plasma in ~/.kde/share/config/ should make it fall back to using the default settings.

---

### Post by pwrcul on 2009-11-17
Zorael, thanks for the comment.

I still did not get back either the applications menu thing nor the newspaper so I decided to do a fresh install of the regular Kubuntu 9.10 desktop version and await the next release--or perhaps something interim that is further along.

Right now, the Kubentu netbook 9.10 technology preview is a little too cutting edge for me.  It is very interesting, and I learned some of the "plumbing" involved, but my main goals are pragmatic.

---

### Post by irelandmc on 2009-12-13
Just had to do this same thing with my Kubuntu 9.10 install. 
~/.kde/share/config/ mkdir old
~/.kde/share/config/ mv plas* old
restart
Everything was back where I started.
Thanks for the help.

---

