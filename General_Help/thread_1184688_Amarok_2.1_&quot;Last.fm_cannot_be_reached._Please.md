---
title: "Amarok 2.1: &quot;Last.fm cannot be reached. Please check your firewall settings&quot;"
date: 2009-06-11
forum: General Help
---

### Post by cfogelberg on 2009-06-11
Hi all,

I'm running Jaunty on my Dell XPS M1330. I've just upgraded my Amarok installation to 2.1 from 2.0.2, following the instructions here: [http://sathyasays.com/2009/06/07/amarok-21-is-out-installing-amarok-21-on-ubuntu-904-jaunty/](http://sathyasays.com/2009/06/07/amarok-21-is-out-installing-amarok-21-on-ubuntu-904-jaunty/)

This has mostly worked, and I can run Amarok 2.1, play all my music and listen to last.fm radio stations.

However when I start last.fm I get the warning message "Last.fm cannot be reached. Please check your firewall settings" and the lyrics applet doesn't work: "Lyrics were unable to be downloaded. Please check your internet connection: Unable to contact server." This all happens even as I'm streaming a last.fm station.

I'm not sure what could be driving this, but any suggestions much appreciated!

Christo

---

### Post by Chronon on 2009-06-11
I don't have any solution for you, unfortunately.  It's odd that you can stream music from last.fm but can't get lyrics.

If you don't have any luck here maybe the Amarok forums would have a higher population of people who could help.

---

### Post by nilarimogard on 2009-06-11
Try this: [http://webupd8.blogspot.com/2009/05/fix-amarok-2-and-lastfm-scrobbing-in.html](http://webupd8.blogspot.com/2009/05/fix-amarok-2-and-lastfm-scrobbing-in.html)

---

### Post by carljung on 2009-06-11
I get the same message when I try to test login. I'm pretty sure I don't have a firewall :confused:

---

### Post by cfogelberg on 2009-06-11
Yes, what makes this very odd is that when I had amarok 2.0.2 I think (IIRC) I could test the login fine (but of course nothing scrobbled due to a change at last.fm) - now I can't even do that :/ xto

---

### Post by cfogelberg on 2009-06-15
OK, I'm dumb.

Thought things through and realised that the mess of errors suggested something hadn't been updated. Initially I had only installed amarok from the kubuntu PPA and not installed the other changes to kdebase etc. Upon installing all of the patches in kubuntu PPA amarok now seems to work: I can fetch lyrics and successfully test my login to last.fm. I guess the scrobbling works but I only just made the changes and restarted amarok, so I haven't checked yet.

Christo

---

