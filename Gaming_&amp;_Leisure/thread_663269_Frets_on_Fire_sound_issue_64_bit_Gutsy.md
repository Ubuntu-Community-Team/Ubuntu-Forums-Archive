---
title: "Frets on Fire sound issue 64 bit Gutsy"
date: 2008-01-09
forum: Gaming &amp; Leisure
---

### Post by silverhammermba on 2008-01-09
I downloaded FoF from sourceforge (the version via Add/Remove doesn't work for me) and it works great except that I can only hear the background playing. That is, I don't hear guitar.ogg at all. The weird thing is, the game seems to think that the background music _is_ the guitar line, because if I screw up it stops playing. Any ideas?

---

### Post by silverhammermba on 2008-01-10
I just confirmed this. I renamed guitar.ogg to song.ogg and now I hear the guitar line and no background. Has anyone else had this problem?

---

### Post by petzworld999 on 2008-01-10
Yes, I have. Chances are, it's not your imported songs, because I just gave my imported songs to my friend who runs FoF in Vista. He has no problems except for the fact that as Jurgen would say, he sucks.

---

### Post by petzworld999 on 2008-01-10
I solved the problem for me. What you need to do is download FoF 1.2.451 from here: [http://sourceforge.net/project/showfiles.php?group_id=182199&package_id=211274&release_id=501448]("http://sourceforge.net/project/showfiles.php?group_id=182199&package_id=211274&release_id=501448")
Just extract that on your desktop, cut and paste your songs folder from 1.2.512 to 1.2.451 and you should be good to go.

---

### Post by kolbycrouch on 2008-02-17
on 32-bit it works fine but on 64-bit it dosnt play guitar.ogg part. it just plays song.ogg which is the background music. how should i fix this

---

### Post by nicepants on 2008-02-22
this seems like a common problem, and one i'm having as well, unfortunately. using 1.2.451 doesn't work, though running 1.2.451 + rfmod does lower the background track volume properly instead of completely cutting out all sound. the guitar track still does not play.

after checking the logs, it seems like frets not seeing pyogg is the problem, even though it's installed on my system. from everything i've read on several forums, it seems to be a 64-bit issue.

i'm going to continue to mess around, but does anyone have any ideas?

---

### Post by haletd on 2008-03-10
I'm having the same issue, is there a fix?

---

### Post by k0rv3n on 2008-04-09
I hope someone have got a solution to this.
I just downloaded FoF and I too hear no guitar.
Works fine with windows on my laptop though :/

---

### Post by Jonny Two Shoes on 2008-04-27
Hi there,

I seem to be having the same issue on 64Bit 8.04 Hardy.  The sound is fine everywhere but as soon as I start a round and press a key to play a note then all sound disappears.  Even that guy's voice in the tutorial disappears.  It comes back if I press escape twice though.

Any ideas?  I would like to get this game working as it is the first time I have tried it.

---

### Post by Ag_Smith on 2008-05-10
me too I have hardy 64 bit and I have the same problem ...

and more: package from repository didn't work, i must use last version from frets on fire official site

someone fix this!!

at moment I must merge with audacity all file in song.ogg, but that workaround sucks...

please fix it I want :guitar: !!

---

### Post by kbitz on 2008-05-10
I can confirm this problem in 8.04 64-bit.

There is a thread over at the Frets On Fire boards about this:
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=20732;st=0](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=20732;st=0)

There is also a sourceforge bug tracker item about it:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1781073&group_id=182199&atid=900254](http://sourceforge.net/tracker/index.php?func=detail&aid=1781073&group_id=182199&atid=900254)

Maybe we should pool our resources at the FoF site or on the bug item at SFnet and see if we can't figure something out.

kbitz

---

### Post by kbitz on 2008-05-10
I can confirm this problem in 8.04 64-bit.

There is a thread over at the Frets On Fire boards about this:
[http://www.fretsonfire.net/cgi-bin/i...3;t=20732;st=0](http://www.fretsonfire.net/cgi-bin/i...3;t=20732;st=0)

There is also a sourceforge bug tracker item about it:
[http://sourceforge.net/tracker/index...99&atid=900254](http://sourceforge.net/tracker/index...99&atid=900254)

Maybe we should pool our resources at the FoF site or on the bug item at SFnet and see if we can't figure something out.

kbitz

---

### Post by Perfect Storm on 2008-05-10
Thread merged

---

### Post by Exteris on 2008-05-21
A simple solution (at the cost of sound quality however), is setting the bitdepth to 8 instead of 16.
It works flawlessly here now.

(d'oh for not noticing this earlier)

---

### Post by glit on 2008-06-21
i can confirm that. reducing sound quality from 16 to 8 bits really did the trick. FoF works like in the old days when I had the 32bit version of ubuntu in use. The game doesn't even sound bad on 8 bit sounds.. game on!

---

### Post by snowniak on 2008-10-31
I am on a Ubuntu 8.10 Intrepid Ibex AMD 64 bits,

I've searched for many ways to solve this, and found a good way.

Change the Audio Settings, and change the "Sample Frequency" to 22050,

Its a workaround actually, but very useful, and keep the game as it is.

Hope this helps...

:guitar:

---

### Post by doorknob60 on 2008-10-31
I used to have this problem, 'till I tried FoFix (AKA MFH mod or Alarian Mod). It's like 20x better anyways, and it didn't have problems, w00tness [http://code.google.com/p/fofix/](http://code.google.com/p/fofix/)

---

