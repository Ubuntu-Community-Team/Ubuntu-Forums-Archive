---
title: "Creative Zen Touch"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Aurdal on 2006-07-10
Hey, I've a Creative Zen Touch mp3 player which I can't get to work with ubuntu, I tried[ this ](http://ubuntuforums.org/showthread.php?t=93810&highlight=Zen+Touch) tutorial, but nope.

Basically Gnomad won't recognize it.

---

### Post by Aurdal on 2006-07-11
Anyone?

---

### Post by Thund3rstruck on 2006-07-11
I thought I read that 
[Amarok]("http://amarok.kde.org/index.php?full=1&set_albumName=album03&id=amarok13&option=com_gallery&Itemid=60&include=view_photo.php") had added support for the creative line of mp3 players..

---

### Post by bluenova on 2006-07-11
> **Thund3rstruck said:**
> I thought I read that 
[Amarok]("http://amarok.kde.org/index.php?full=1&set_albumName=album03&id=amarok13&option=com_gallery&Itemid=60&include=view_photo.php") had added support for the creative line of mp3 players..
I think the Zen touch is supported by Amarok now. I have the Zen Xtra which does not have support yet :(

---

### Post by Aurdal on 2006-07-13
Thanks guys, however Amarok can't find it either, it tells me to mount it. How exactly do I mount it?

---

### Post by Aurdal on 2006-07-14
Found the problem, the newest firmware uses MTP and is not supported. And it can't be downgraded.

So, how screwed am I? Will libnjb support MTP at a later time?

---

### Post by bluenova on 2006-07-17
Take a look here, there is a wishlist report for MTP:
[http://bugs.kde.org/show_bug.cgi?id=128532](http://bugs.kde.org/show_bug.cgi?id=128532)

I'm sure they are going to implement it, but vote for it to bump it up the list of things to be added.

---

### Post by Aurdal on 2006-07-19
I run gnome... But thanks, :)

---

### Post by goobers on 2006-07-19
Yeah, I installed the MTP firmware too, but I can still use windows to sync it, so all is not lost...

---

### Post by bluenova on 2006-07-20
[quote=Aurdal]I run gnome... But thanks, [/quote]

So? I don't understand.

---

### Post by Aurdal on 2006-07-22
Isn't that a KDE site? Will it help me if MTP is implented in KDE if I run gnome?

---

### Post by msak007 on 2006-07-22
Aurdal, I wrote a how-to on how to get MTP-enabled Creative MP3 players to work with Gnomad. Just follow the link in my sig, and let me know if it works for you. If you have any problems, just post them in that thread. You're using a Zen Touch, so you may want to note post # 40 if you have problems after following my instructions. Hope this helps!

---

### Post by bluenova on 2006-07-24
> **Aurdal said:**
> Isn't that a KDE site? Will it help me if MTP is implented in KDE if I run gnome?
Amarok uses the KDE libs to run, which is why it's on the KDE bug tracker. There is nothing wrong with running a KDE app in Gnome or the other way round.

---

### Post by Aurdal on 2006-07-24
Aah I must have missed that it was for amarok, I thought it was KDE spesific.

---

### Post by paulyche on 2006-08-09
Since amarok 1.41 experimental libmtp support has been added to amarok. You'd have to compile from the SVN source. This script here might be helpful if you want to do this as you'll have to choose to compile libmtp support in.

[http://www.kde-apps.org/content/show.php?content=27313]("http://www.kde-apps.org/content/show.php?content=27313")


I found all this out because I was loooking up MTP and amarok 'cos I recently had my Zen Touch (With MTP firmware) replaced by a Zen Sleek by an insurance company.

Then I discovered that the Sleek comes with the old PDE firmware and I don't have to muck around with MTP at all if I don't upgrade the firmware.

So I'm pleasantly suprised. :-)

---

