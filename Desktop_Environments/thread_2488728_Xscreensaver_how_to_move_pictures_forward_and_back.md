---
title: "Xscreensaver how to move pictures forward and back using keyboard"
date: 2023-07-13
forum: Desktop Environments
---

### Post by edson-andrade on 2023-07-13
Hi Everyone,
When screensaver (xscreensaver) is triggered and pictures showing up I'd like to understand if there is any option to use keyboard (right and left arrows for instance) to move pictures fwd and back without deactivating screensaver.
Thx

---

### Post by ajgreeny on 2023-07-13
Not that I'm aware of I'm afraid.

A screensaver is initiated specifically (or was in the past for CRT screens) to help reduce the risk of screen damage caused by very extended displays of static images and have always stopped running when the keyboard or mouse is used.

Perhaps you need to make use of something other than a screensaver, eg an image display application which you can configure to move the images forward/backward using the keyboard, though I do not know how easy or even if it's possible to initiate such an application automatically if the mouse and keyboard are not used for a specific period.

---

### Post by guiverc on 2023-07-13
I agree with @ajgreeny, as that would defy its purpose.

Myself I'd use another app; eg. `gpicview` (GTK2) used by older Lubuntu allows slideshows (*with keys allowing you to control the slideshow)*, modern Lubuntu provides `lximage-qt` (Qt5) that likewise allows it. There are others too (*what I've mentioned are those used by Lubuntu only*)

The upstream page for xscreensaver can be viewed here - [https://www.jwz.org/xscreensaver/](https://www.jwz.org/xscreensaver/) , with a FAQ also present.

The package is usually left unchanged, as the original creator/maintainer does not appreciate people using it making changes downstream, so that package in usually unaltered.

---

