---
title: "Auto Right Align Icons?"
date: 2007-11-25
forum: Desktop Environments
---

### Post by staticvoid on 2007-11-25
Hi, I've seen **8 posts **asking this *same* exact question and none have an answer. 
How do you make the right click option "clean up by name" throw all the icons to the right instead of the left? Like Mac OS, they are on the right side, not the left. Is there a way in Gnome?? I saw one post asking about it in KDE, and it is still unsolved.

default desktop icons alignment: right side, howto?

Anybody?? Its driving me nuts :P hehehe

S void

---

### Post by staticvoid on 2007-11-26
bump...

---

### Post by staticvoid on 2007-11-28
bumping again

---

### Post by staticvoid on 2007-11-29
i'm still curious....


sorry for the triple bump

---

### Post by toxin on 2007-11-30
I would like to know, too.
But maybe people you see with right aligned icons in the screenshots move them manually?

---

### Post by staticvoid on 2007-11-30
Yes they align them manuelly .

 I think if we can figure out where the files are to the actions of the right click menu we can some how tweak the commands....

sv

---

### Post by staticvoid on 2007-12-04
well I'll post here and right a big howto if I find out how....

:(

sv

---

### Post by Levant on 2007-12-04
I don't have access to my linux machine at this exact moment, but have you tried the gconf-editor under apps -> nautilus (which draws the icons). Careful screwing around with that (you can break something!), but if there's a way to change the alignment, that is where it would be.

If you don't know how to launch it, just type "gconf-editor" into the terminal =)

---

### Post by staticvoid on 2007-12-04
i tried this and couldn't find anything.

where are the commands for the desktop right click menu?

If I can see the command for "clean up by name" then maybe I can tweak it or the file it uses

sv

---

### Post by skyjacker on 2007-12-04
> **staticvoid said:**
> Hi, I've seen **8 posts **asking this *same* exact question and none have an answer. 
How do you make the right click option "clean up by name" throw all the icons to the right instead of the left? Like Mac OS, they are on the right side, not the left. Is there a way in Gnome?? I saw one post asking about it in KDE, and it is still unsolved.

default desktop icons alignment: right side, howto?

Anybody?? Its driving me nuts :P hehehe

S voidIn kde under System settings,Desktop/ Behavior/File/Icons... Uncheck  Automatically Line up icons. Move them where ever you want. They should stay there. Don't know about Ubuntu though.

---

### Post by sethvath on 2007-12-04
I am certain I saw a fix for kde in one of the arabic forums. They read from right to left and it was a hack to align everything from right to left, including the desktop icons. Googling doesnt give any useful links. 

Gnome I'm not sure, can it even be customized as much as kde?

---

### Post by staticvoid on 2007-12-04
i guess gnome can be customized just as much, depending on what tools you use. perhaps not with the preinstalled ones...


so... the right click menu actions?


sv

---

### Post by sethvath on 2007-12-04
You want the right click menu options to read right to left?

---

### Post by staticvoid on 2007-12-04
No,

I mean I want to know what commands the menu options are exucuting. Then maybe I can narrow it down and change the file its executing or something... just a thought.

Then maybe I could change it to tell the icons to be on the right.

Just a thought... :D

sv

---

### Post by sethvath on 2007-12-04
My first thought is to locate a desktop.ini file and modify its attributes. That probably will not work in gnome like xfce

---

### Post by tcommbee on 2007-12-04
this is the nautilus bug: [http://bugzilla.gnome.org/show_bug.cgi?id=42479](http://bugzilla.gnome.org/show_bug.cgi?id=42479)
if you download the source you can look at it yourself: currently tbrl (top-bottom-right-left,  the ordering you want) isn't implemented and just uses tblr instead. so you have to hack it yourself or wait for an official fix. there seems to be not much progress in it though.

---

### Post by staticvoid on 2007-12-05
ok. to bad about the bug...

i'll see if I can make a fix


sv

---

