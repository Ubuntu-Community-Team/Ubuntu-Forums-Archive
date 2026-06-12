---
title: "Deluge hagns up the whole computer."
date: 2009-03-20
forum: General Help
---

### Post by emshains on 2009-03-20
Lately, I've been checking out how well does deluge work. I prefer it to the transmission because of the gui. But, when I leave it over-night to download/upload something, it hangs up after downloading about 200mb. It's like, I wake up, the fan is running, but the screen is blank and there is no response to any keyboard commands. And this occurs exclusively with deluge, transmission is working just fine. Is this a problem with my computer or deluge ? I can get about 250 kb/s top speed with my connection, and I use wi-fi to connect my box.

I am running ubuntu 8.04.2.
My specs:
1,6 ghz sempron
768mb of ram
7300Gt.

---

### Post by bruno9779 on 2009-03-20
I had similar problems with deluge, and wasn't able to make sense of them.
I have happily switched to KTorrent, that works just great nowadays (kind of buggy back in 7.04)and perfectly suites my needs.

---

### Post by emshains on 2009-03-20
> **bruno9779 said:**
> I had similar problems with deluge, and wasn't able to make sense of them.
I have happily switched to KTorrent, that works just great nowadays (kind of buggy back in 7.04)and perfectly suites my needs.

Could you describe them ? 

And won't ktorrent be slower than deluge in a gnome environment ?

Emm, is there a way to import all the torrents from transsmission or deluge to use with another torrent ?

---

### Post by Dr Small on 2009-03-20
> **emshains said:**
> And won't ktorrent be slower than deluge in a gnome environment ?


You can run KDE apps in GNOME; It just pulls in all the qt4 and kdelibs, but I don't think it will make it *that* slow.

---

### Post by emshains on 2009-03-20
> **Dr Small said:**
> You can run KDE apps in GNOME; It just pulls in all the qt4 and kdelibs, but I don't think it will make it *that* slow.

When I ran it on my p3 500mhz box, the difference in performance was ENORMOUS. :)

---

### Post by bruno9779 on 2009-03-20
Mainly I had the same problem you had, plus some kind of bug, where some torrents would stall with no apparent reason, also when having 1000s of seeds and nothing else downloading.

If you switch to ktorrent, importing torrents is easy:

1 - re-open (or re-download) the torrent file in ktorrent
2 - chose the same download location you had in deluge

and it is done: Ktorr will check automatically for downloaded chunks.

Concerning speed: Deluge boots a bit faster, but i get better download speeds with ktorrent

---

### Post by Dr Small on 2009-03-20
> **emshains said:**
> When I ran it on my p3 500mhz box, the difference in performance was ENORMOUS. :)
Well, yes, of course. It certainly depends on your system. For me, I am completely GNOME and KDE dependencyless. I run pure Openbox ;)

---

### Post by emshains on 2009-03-20
Ok, so ktorrent it is. 


Emm, I thought about using a lighter WM, but then I realised that the WM wasn't the one lagging my bootup.

---

### Post by sisco311 on 2009-03-20
What version are you using? The one in the Ubuntu repos is rather outdated.  

Try the latest; it's in the PPA repo: [https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/~deluge-team/+archive/ppa")

---

### Post by mb_webguy on 2009-03-20
+1

I use the version from the Deluge PPA, and I don't have any problems with it whatsoever.

---

