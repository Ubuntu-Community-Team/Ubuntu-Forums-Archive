---
title: "Hi i am a beginner to ubuntu .... and would want to install prince of persia warrior"
date: 2007-07-06
forum: Gaming &amp; Leisure
---

### Post by 12hello on 2007-07-06
hi guys need help in installing prince of persia warrior within ....what should i do i have discs which work in windows if aany one could help me with detailed steps would be of great help

---

### Post by mig5 on 2007-07-06
You could try to run it in wine, which is a compatibilty layer for Windows programs, but it doesn't seem to work for this game according to: [http://appdb.winehq.org/appview.php?iVersionId=7231&iTestingId=9830](http://appdb.winehq.org/appview.php?iVersionId=7231&iTestingId=9830) .  To get wine you'll need to add the multiverse and universe repositories to your sources, if you haven't already done so and then search for 'wine' in synaptic.
Another, more realistic option, would be to run Windows in a virtual machine.  You can do this with [VMware Server]("http://www.vmware.com/products/server/") or [Virtual Box]("http://www.virtualbox.org/wiki/Downloads").  Both of those programs are free, but only virtual box is open source.  Virtual Box also provides easy-to-install .deb packages.

---

### Post by 12hello on 2007-07-06
Hmm ... okie where can i get the complete list of hugh end games that can work on ubuntu 7.04.....

---

### Post by stuart.crouch on 2007-07-06
Ok. Do people know something I don't know here?

This is the second thread I've seen today that suggests using virtual machines to run games that require high levels of 3D acceleration.  Virtual machines only provide 2D acceleration at present, so the games will install, maybe even run but won't be playable.  

This is just bad advice, which is worse than no advice at all IMO.  People will read this thread, try it and have wasted their time on a suggestion that we already know will go nowhere.

@12hello: I'm afraid to say you are out of luck with Prince of Persia.  That game still needs windows - at the moment.

---

### Post by 12hello on 2007-07-06
hey stuart.crouch thanks for ur help ... on this topic could u just tell me a website or sumthing where i would come to know which games can be played on linux .... i mean using wine or sum other stuff

---

### Post by azraelck on 2007-07-06
> **12hello said:**
> hey stuart.crouch thanks for ur help ... on this topic could u just tell me a website or sumthing where i would come to know which games can be played on linux .... i mean using wine or sum other stuff

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by Dinchamion on 2007-07-06
You can also try Cedega, though you have to pay for it. [According to the wiki](http://cedegawiki.sweetleafstudios.com/wiki/Prince_of_Persia:_Warrior_Within) Warrior Within works.

Also, for another list of games: [cedega games database](http://www.cedega.com/gamesdb). Again, you have to pay for Cedega, but if there are many games you wanna play and you have no luck with wine, it can be a good investment.

---

### Post by hikaricore on 2007-07-06
I wouldn't trust Cedega any further than I can throw a dead bear.

And according to the **UNOFFICIAL** wiki you posted:  _Supported by TransGaming - **No**_

Unless you find a good source with screenshots saying the game runs and runs well don't bother with Cedega.

---

### Post by Dinchamion on 2007-07-06
> **hikaricore said:**
> I wouldn't trust Cedega any further than I can throw a dead bear.

And according to the **UNOFFICIAL** wiki you posted:  _Supported by TransGaming - **No**_

Unless you find a good source with screenshots saying the game runs and runs well don't bother with Cedega.

I didn't say it was supported by Transgaming: I said that according to the wiki it works. And according to my experience the wiki works as well :) (meaning if they say something works, it does - as far as my experience goes, the wiki was never ever wrong about issues or anything)

Screenshots... I would have to install it and try...

And no, I don't like cedega either, but when it comes to playing, it's a nice thing to have something else to try before booting up Windows. I like Windows even less than Cedega. :) (For example the only way for me to run SWG with usb joystick support is through cedega :()

---

### Post by mig5 on 2007-07-06
> **12hello said:**
> Hmm ... okie where can i get the complete list of hugh end games that can work on ubuntu 7.04.....

Search [http://appdb.winehq.org/search.php?sSearchQuery=+](http://appdb.winehq.org/search.php?sSearchQuery=+) to see programs that have been tested in wine.  There are programs that aren't on there that do work, not every program is listed.

As for 3D acceleration you could watch ReactOS ([http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)), maybe one day that operating system will be able to play Prince of Persia.

---

