---
title: "sudo aptitude install quak2 not working?"
date: 2007-05-24
forum: Gaming &amp; Leisure
---

### Post by blk03mitsues on 2007-05-24
i've read that i can install quake from "sudo aptitude install quake2" but i get this message "couldnt find any package whos name or description matched "quake2"

---

### Post by The Squig on 2007-05-24
edit:
Have you opened the multiverse repository?

top open closed repos edit this file
/etc/apt/sources.list (you can do this with the sudo gedit command)

then typ sudo apt-get update in terminal

-------------------
apt-cache show quake2:

```
Description: improved version of id Software's Quake II engine
 Quake II is a 3D action game engine in first-person perspective, commonly
 known as a ``first person shooter''.
 .
[B] This package contains no data files.  You will need to either install the
 commercial data from the Quake II CD-ROM with the ``quake2-data'' package,
 or install some free data files.[/B]
 .
 This game currently supports software rendering with X11, SDL, or SVGAlib,
 or hardware accelerated rendering with OpenGL (directly or via SDL).
 .
 NOTE: The network part of Quake II has several unfixed security problems.
 It should not be used in untrusted networks.

```

---

### Post by The Squig on 2007-05-24
edit: double psot

---

### Post by chrisLACHCIK5084 on 2007-05-24
> **blk03mitsues said:**
> i've read that i can install quake from "sudo aptitude install quake2" but i get this message "couldnt find any package whos name or description matched "quake2"



ya you do need the cd to install quake 2 and then you get the respoitory

---

