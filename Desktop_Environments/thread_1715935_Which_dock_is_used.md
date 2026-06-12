---
title: "Which dock is used"
date: 2011-03-27
forum: Desktop Environments
---

### Post by RagC on 2011-03-27
Hey,  does someone by chance know which dock is used in this picture (bottom left):  [http://gnome-look.org/content/preview.php?preview=1&id=133892&file1=133892-1.jpg&file2=133892-2.jpg&file3=133892-3.jpg&name=Divergence+IV+-+%22A+New+Hope%22](http://gnome-look.org/content/preview.php?preview=1&id=133892&file1=133892-1.jpg&file2=133892-2.jpg&file3=133892-3.jpg&name=Divergence+IV+-+%22A+New+Hope%22)

---

### Post by Enigmapond on 2011-03-27
That is Avant Window Navigator with one of it's themes. I highly recommend this. Here is mine..:

---

### Post by Krytarik on 2011-03-27
Yeah, that's AWN (Avant Window Navigator), it's in the official repos, and you can get a more recent version by adding their PPA (the package is then called "avant-window-navigator-trunk" instead of just "avant-window-navigator" in the official repos):
[https://launchpad.net/~awn-testing/+archive/ppa]("https://launchpad.net/%7Eawn-testing/+archive/ppa")

Greetings.

---

### Post by Enigmapond on 2011-03-27
> **Krytarik said:**
> Yeah, that's AWN (Avant Window Navigator), it's in the official repos, and you can get a more recent version by adding their PPA (the package is then called "avant-window-navigator-trunk" instead of just "avant-window-navigator" in the official repos):
[https://launchpad.net/~awn-testing/+archive/ppa]("https://launchpad.net/%7Eawn-testing/+archive/ppa")

Greetings.

+1 That's the one I use. Couldn't do without it.

---

### Post by jonbwilson on 2011-03-28
I can never get those themes to work like they're supposed to in AWN. I can't figure out what they're doing differently. I install the theme as instructed, but then when I select it, all it does is change the dock color and nothing else. I'm on Maverick, and I have the latest version of AWN. Maybe I'm missing some other integral piece of software?

---

### Post by Copper Bezel on 2011-03-28
Shouldn't be, but if you mean the loopy curvy new(er) Lucido style, it's a "style," not a "theme." You can get to it under the main tab in Dock Preferences. The default is Flat, and the loopy "Chrome tab" one is Lucido. 

Also, do you have the latest version from the AWN PPA, or just from the Ubuntu repos (which is much older?)

And, of course, +1 for AWN being the best damned panel available on any system. The Transparency Intellihide is brilliant, especially with just a touch of alpha blur from Compiz.

---

### Post by Krytarik on 2011-03-28
@jonbwilson: Those themes are mostly about the colors. You need to change AWN's settings to modify its general look. But I don't have it installed currently, so I can't tell you more specifics.

**EDIT:** Ah, damn! It happened again, concurrent posting. ;-)
You should hinge to Copper, he knows AWN very well, see here:
[http://ubuntuforums.org/showthread.php?t=1714111](http://ubuntuforums.org/showthread.php?t=1714111)

---

### Post by jonbwilson on 2011-03-28
> **Copper Bezel said:**
> Shouldn't be, but if you mean the loopy curvy new(er) Lucido style, it's a "style," not a "theme." You can get to it under the main tab in Dock Preferences. The default is Flat, and the loopy "Chrome tab" one is Lucido. 

Also, do you have the latest version from the AWN PPA, or just from the Ubuntu repos (which is much older?)

Yeah, it's the Lucido style I'm talking about. It doesn't show up on the main tab under preferences. Whenever I choose a theme that uses Lucido, the style shows up blank. I have the latest version from the AWN PPA. I r confused.

---

### Post by Rasa1111 on 2011-03-28
> **jonbwilson said:**
> Yeah, it's the Lucido style I'm talking about. It doesn't show up on the main tab under preferences. Whenever I choose a theme that uses Lucido, the style shows up blank. I have the latest version from the AWN PPA. I r confused.

It usually shows under the "Style" menu, in the main preferences tab. 

 Also,
You (OP) can download the same theme that is in the link you posted.
It is here, in this package!
\It comes with the rest of the theme. 
[http://jurialmunkey.deviantart.com/art/Divergence-IV-quot-A-New-Hope-quot-183377193](http://jurialmunkey.deviantart.com/art/Divergence-IV-quot-A-New-Hope-quot-183377193)

One of my favorite themes ever.

---

### Post by jonbwilson on 2011-03-28
> **Rasa1111 said:**
> It usually shows under the "Style" menu, in the main preferences tab. 

 Also,
You (OP) can download the same theme that is in the link you posted.
It is here, in this package!
\It comes with the rest of the theme. 
[http://jurialmunkey.deviantart.com/art/Divergence-IV-quot-A-New-Hope-quot-183377193](http://jurialmunkey.deviantart.com/art/Divergence-IV-quot-A-New-Hope-quot-183377193)

One of my favorite themes ever.

Yeah, I already have the theme installed. But Lucido doesn't show up under styles on the main tab. It's just not there at all.

---

### Post by Rasa1111 on 2011-03-28
hmm..

 Maybe try removing it,
Using this~[http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)
and re-installing, using the same link.

First command removes all AWN.
Second adds PPA, 
third installs everything. 

 Ive never seen it not show up before,
except in AWN version in the repos. 

:???:

---

### Post by Copper Bezel on 2011-03-28
Now, this is probably a silly question, but even if it's from the PPA, you did install avant-window-navigator-trunk, not avant-window-navigator, right? The application still runs from the same command (avant-window-navigator,) but the entry in synaptic is different. If you do have avant-window-navigator installed, you can just go into synaptic, remove it, install trunk, and then restart AWN.

I have the two "extras" packages installed, but IIRC, they actually installed as dependencies for AWN despite being labeled as "extras," and looking at them now, they only provide additional applets, not styles.

---

### Post by jonbwilson on 2011-03-28
> **Rasa1111 said:**
> hmm..

 Maybe try removing it,
Using this~[http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)
and re-installing, using the same link.

First command removes all AWN.
Second adds PPA, 
third installs everything. 

 Ive never seen it not show up before,
except in AWN version in the repos. 

:???:

Thank you thank you thank you!  I figured out where I went wrong after putting your post together with all the other stuff I found online. I installed AWN from the software center when I first setup Ubuntu, and I added the PPA later. I had version 0.4.0, which is the stable version and not the latest. Now the Lucido style shows up. Sweet.

---

### Post by Rasa1111 on 2011-03-28
> **jonbwilson said:**
> Thank you thank you thank you!  I figured out where I went wrong after putting your post together with all the other stuff I found online. I installed AWN from the software center when I first setup Ubuntu, and I added the PPA later. I had version 0.4.0, which is the stable version and not the latest. Now the Lucido style shows up. Sweet.

haha! No problem, Glad it helped. :) 
Easy enough mistake to make for sure. 
have fun!

---

