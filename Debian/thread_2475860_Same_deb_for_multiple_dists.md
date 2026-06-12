---
title: "Same deb for multiple dists"
date: 2022-06-10
forum: Debian
---

### Post by jonasb-to on 2022-06-10
[COLOR=#333333][FONT=Verdana][FONT=&quot]This is a copy of my post in the Debian forums, hence the references to buster & bullseye - the actual question is still valid for Ubuntu though.
 
Hello!

I'm maintaining a local repo with some deb's that we need for our company, it's run in a JFrog artifactory server.

What I can't seem to grasp is the 'deb.distribution' property of the pkgs.

According to JFrog's own docs I'm supposed to be able to upload pkg.deb with both buster AND bullseye as deb.distribution, however from testing I can see that it doesn't work.

What's really the best practice for maintaining the same pkg.deb for multiple distributions (in my case both buster and bullseye)?
Do I have to upload them multiple times, one for each dist? If so, I've realised that the filenames have to be unique, so I have to copy pkg.deb to pkg-buster.deb and pkg-bullseye.deb. Am I correct in that?[/FONT]





[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][[CENTER][COLOR=#777777][FONT=FontAwesome][/FONT][/COLOR][/CENTER]]("https://forums.debian.net/viewtopic.php?f=5&t=151818#top")[/FONT][/COLOR]

---

### Post by coffeecat on 2022-06-10
*Thread moved to **Debian** sub-forum.*

---

