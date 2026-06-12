---
title: "Royally ticked off by Synaptic"
date: 2009-02-25
forum: General Help
---

### Post by oaxacamatt1 on 2009-02-25
Hi all,
I spent several hours installing VLC 0.9.8 from the tarball.  I got all the dependencies and things went very well, until...  I got VLC started and then realized I needed a few more pieces of software, like vlc-nox and vlc-plugin-alsa.  So I went to Synaptic and installed the plugins, etc.  NEXT thing I realized,(Ubuntu or Synaptic) installed VLC ??0.8.6?? OVER my NEW installation of 0.9.8.  I was totally p-ed off. 

My question is how can I stop (Ubuntu or Synaptic) from doing this again?  For example, I want to make sure Exaile won't be written over.
Cheers,
Matt

---

### Post by taurus on 2009-02-25
Where did you install the new version of vlc?  Is it /usr/local/bin?  If it is, then just remove the older version from the repos either with synaptic or from a terminal.

---

### Post by doug1212 on 2009-02-25
Hi,
Building VLC has to be a PITA with all those QT4 development files, If it's any use there is a third party repo for Hardy here:

[HTML]http://ubuntufromscratch.wordpress.com/[/HTML]

It's in french but not difficult to find the way around.
Doug.

---

### Post by TwiceOver on 2009-02-25
Sorry I don't have the exact answer for you, but I remember seeing a "Don't ever update this package" type checkbox somewhere at one time.

I'll have to look for that.

---

### Post by mb_webguy on 2009-02-25
You actually tried to compile VLC?  Ouch.  I tried that exactly once, and gave up after an hour of crawling through dependency hell.

You can find debs for the more recent builds of VLC for Intrepid [here]("http://archive.getdeb.net/dump/intrepid/vlc/").

---

