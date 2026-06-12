---
title: "head over heels save problem"
date: 2007-04-05
forum: Gaming &amp; Leisure
---

### Post by smurphs on 2007-04-05
I've recently discovered a Head over Heels remake by retrospec which is fantastic.

However, it won't save for me. It's supposed to create a .hoh file in your home directory, but doesn't. Anyone know of a solution?

---

### Post by Perfect Storm on 2007-04-05
Do you have write/read permission of ~/.hoh folder and thie files within? Have you at anytime started the game with root permission (likely messing up permission)?

---

### Post by smurphs on 2007-04-05
I did install the game as root, as it wouldn't let me do otherwise. As for the .hoh files, they don't exist, as if the game isn't creating them (i've done a locate to no avail). The game installs to usr/local/bin & share, which seems a bit odd. Do you reckon i need to change the permissions of the data files? what is the command to check permissions by the way, using the right-click in nautilus seems a bit misleading to me.

---

### Post by Perfect Storm on 2007-04-05
Have you ever ran the game at anytime with sudo infront?

---

### Post by smurphs on 2007-04-05
Hooray, i fixed it. You put me in the right direction, I copied everything to my home folder and ran it from there, and it's now creating the saved games, so it must have been a permissions thing. Seems strange that no-one else has run into this (or maybe I'm the only one who enjoys playing 20 year-old games!! God that makes me feel older than i am!

Cheers.

Dyl.

---

