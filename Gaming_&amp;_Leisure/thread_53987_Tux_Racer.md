---
title: "Tux Racer"
date: 2005-08-03
forum: Gaming &amp; Leisure
---

### Post by obx-jdt on 2005-08-03
Ok, here's the deal....My little girl is here for a month, and I was telling her about Tux Racer. Well, we went to install it so she could try it, but after insalling it, it didn't show up anywhere. I tried a file search for tux racer, tuxracer, and just tux (/home, /root, /) but nothing showed up. So I went to reinstall it, and it said it was already installed. 
Where does Tux Racer live, and how do I access it?

---

### Post by jyank on 2005-08-03
I've noticed some games like the hide when their installed :)

But, does the game load from the terminal?

Load up a terminal and type 'tuxracer'

If you want to make it easier on her, make a shortcut for it on a panel.  Right click > add to panel > custom application launcher > add > name it whatever, just make sure the command area says 'tuxracer'

Simple enough ;)

edit: realized you might have been searching for the wrong thing, theres actually a tuxkart and tuxracer, not sure which you want - but either should work through the terminal

---

### Post by amohanty on 2005-08-03
If you installed it via synaptic, just do a search on it and look at the installed files tab in the lower pane.

/usr/games/tuxracer

alternately 
>> locate -u
>> locate tuxracer

AM

---

### Post by ishtvan222 on 2005-08-03
When I want to find where it is located I just do 

which tuxracer

That will tell you where the binary is.
Hope this helps.

---

### Post by RicgorE on 2005-08-09
Methinks   /usr/games/tuxracer is the default path to tuxracer.

---

### Post by neowhale on 2005-08-09
You can find using the command line (shell) by typing:

whereis tuxracer

It will return the directory of the executable tuxracer ;)

---

### Post by jobezone on 2005-08-09
[QUOTE=obx-jdt]Ok, here's the deal....My little girl is here for a month, and I was telling her about Tux Racer. Well, we went to install it so she could try it, but after insalling it, it didn't show up anywhere. I tried a file search for tux racer, tuxracer, and just tux (/home, /root, /) but nothing showed up. So I went to reinstall it, and it said it was already installed. 
Where does Tux Racer live, and how do I access it?[/QUOTE]
 Try running ppracer? In my debian system it's now called planet penguin racer, or something like this.

---

### Post by xmastree on 2005-08-10
Run tuxracer from a terminal, that ought to do it. Works for me.

If you don't like terminals all over, add the mini commander (right click on a panel> add to panel>command line

Like this:

[IMG]http://www.xmastree.34sp.com/ubuntu/minicom.png[/IMG] 

Then type in any command you want which opens a new program.

Or you can install smeg and add it to the menu manually.

---

### Post by xmastree on 2005-08-10
> My little girl is here for a month, and I was telling her about Tux Racer.
[IMG]http://www.xmastree.34sp.com/sandy/sandytuxracer.jpg[/IMG]

**[COLOR=Red]If she's anything like mine, she'll love it![/COLOR]**
 :grin: 

(sorry about the focus though...)  :roll:

---

