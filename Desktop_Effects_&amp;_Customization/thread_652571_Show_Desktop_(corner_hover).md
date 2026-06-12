---
title: "Show Desktop (corner hover)"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by dumplinknet on 2007-12-28
using ubuntu GUTSY-
Problem: I want to be able to move my mouse into the upper right hand corner of my screen and have it minimize everything till i see the desktop. I dont know how to get this working on gutsy with compize fusion (if possible in anyway)


for now, i have the desktop icon (from the list of panel icons) moved to the upper right hand corner. I have to click it to minimize all my windows. is there anyway that i can just move my mouse to the right hand corner and let it minimize all my windows without clicking anything?

ive been trying to get this to work,,, no luck. any help would be great!!!

---

### Post by Forlong on 2007-12-29
Run
```
gconf-editor
```
And navigate to **apps &#8594; compiz &#8594; general&#8594; allscreens &#8594; options &#8594; show_desktop_edge**
Double-click the entry and add **TopRight**

---

### Post by dumplinknet on 2007-12-29
uh, sorry to be a noob but what is gconf-editor and how do i run it?

---

### Post by Forlong on 2007-12-29
No need to be sorry.
Everytime somebody posts a command in CODE tags, it's something you can run in the terminal.

Additionally if it's an application, you can run it via [Alt]+[F2] as well (which I'd recommend in this case).

---

### Post by dontcopymusic on 2008-01-16
Hi

Is there any way I could get al my running applications appear the way widgets appear when I move my mouse to for example the top right corner? I saw it on ubuntu 6.10 with beryl. I use ubuntu 7.10.

Thanks in advance!

---

### Post by Huss on 2008-03-31
Great.

Thank you!

---

