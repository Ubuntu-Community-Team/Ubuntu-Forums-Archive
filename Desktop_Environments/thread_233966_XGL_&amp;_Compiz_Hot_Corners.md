---
title: "XGL &amp; Compiz Hot Corners"
date: 2006-08-10
forum: Desktop Environments
---

### Post by DarkNemesis618 on 2006-08-10
I have XGL and Compiz working beautifully...however there are hotcorners that have been annoying me.  I'm sure it's just a plugin somewhere.  Anyone know which plugin it is and how to disable it?

---

### Post by hopstah on 2006-08-10
i, too, find this to be a less-than-useful feature to compiz.  let me see if i can figure out how to disable it for us.

ok, found it.  open up gconf-editor, and navigate to apps > compiz > plugins > scale > allscreens > options > and delete the values that say things like bottomleft and topright, etc.

---

### Post by hopstah on 2006-08-10
to eliminate the bottom-right 'show desktop' corner, that's under showdesktop > allscreens > options, but i think i'm going to keep that one.

---

### Post by murataht on 2006-08-11
top right, buttom left is for scale plugin.

run gconf-editor and go apps>compiz>plugins.

find scale plugin and disable top-right and bottom-left mouse shortcut. you can preserver the shortcut key. which may become handy sometimes.

bottom-right is for showdesktop plugin. you can repeat the above method to disable it.

---

### Post by hopstah on 2006-08-11
> **murataht said:**
> top right, buttom left is for scale plugin.

run gconf-editor and go apps>compiz>plugins.

find scale plugin and disable top-right and bottom-left mouse shortcut. you can preserver the shortcut key. which may become handy sometimes.

bottom-right is for showdesktop plugin. you can repeat the above method to disable it.

pssst... read my posts right above yours ;)

---

### Post by cptnapalm on 2006-08-11
Speaking of hot corners, I do like the show desktop and whatever the bottom left action is called, but I find myself puzzled as to why the bottom right corner shows the desktop when the stock Gnome configuration has the show desktop icon in the bottom left.  Would it not make more sense if the show desktop hot corner was in the same location as the show desktop icon?  While it might be because that is how OS X does it, it makes little sense when in Ubuntu.

---

### Post by hopstah on 2006-08-11
interesting point.  it's pretty easy to switch it, if you're so inclined.  i never got used to using the button in the bottom left, because i typically remove that bottom bar right away after an install.

---

### Post by murataht on 2006-08-11
> **hopstah said:**
> pssst... read my posts right above yours ;)

you got it first man. i found the only question that i can answer in the forum, so i was busy with replying .... :D 

cheers

Murat

---

### Post by hopstah on 2006-08-11
haha, it's cool.  it's not a competition, i just thought it was funny. :D

---

### Post by murataht on 2006-08-11
it is not a competition. but you can imagine the feeling that to be able to answer the question, instead of not being a linux geek. "yeah i am contributing .. " :-D 

so i was hurry to answer, instead of reading down the replies. :p
next time, i should check the replies first.  

cheers

murat

---

