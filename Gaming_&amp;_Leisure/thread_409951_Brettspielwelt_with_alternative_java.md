---
title: "Brettspielwelt with alternative java"
date: 2007-04-15
forum: Gaming &amp; Leisure
---

### Post by engla on 2007-04-15
Brettspielwelt.de is a really great boardgaming website (available both in german and english). They are so friendly so that they provide linux, windows and mac downloads for their java gaming client.

Now, I have a problem since I'm on ppc and sun-java is not available. I need help, tips or hints on getting the brettspielwelt client to work with another java runtime like gcj or kaffe.

Ideas?

If nothing else, go and try out [brettspielwelt]("http://www.brettspielwelt.de")! They offer lots of different popular board games that you can play.. Me myself is a great fan of Carcassonne.

---

### Post by engla on 2007-04-15
By the way, [here is the client tarball]("http://www.brettspielwelt.de/Data/brettspielwelt.tar.gz") from their website.

---

### Post by MonkeyBoy on 2007-04-15
Awesome link!

I love boardgames!

Danke schon!

---

### Post by MonkeyBoy on 2007-04-15
I just got the client but I am not sure how to change the language to english.  I changed the client preference in the profile part of the website but the client is still in german which I am not too good at.

Any ideas?

---

### Post by MonkeyBoy on 2007-04-15
I found it.   

Sorry to be singlehandedly Bogarding this thread BTW.  :p

---

### Post by engla on 2007-04-16
Beautiful!

I found this in a blog today and it works!:

[How to install java for powerpc]("http://peter.makholm.net/2007/04/16/java-on-linuxppc/").

I used his instructions exactly (with the rename, install 'java-package' to get the make-jpkg tool) and it works fine with the brettspielwelt client!

---

### Post by EvilBro on 2007-09-05
The following is an account of the steps I took to get a working brettspielwelt client on Feisty. I hope it will help others if nothing else...

WARNING: this is not a step by step guide. It is merely what I remember doing to get the final result.

I downloaded the client and unpacked. I ran the start.sh from a terminal, but it failed due to missing some AWT-thing. I installed libgcj7-awt to rectify this (using synaptic).

This stopped the fail-message, but the client still wouldn't start. It would hang on the opening picture. 

I installed the java-common package next (to get update-java-alternatives or something) and immediately after that I installed sun-java6-jre (and all dependencies of course). From this point on the client worked.


I should note that the behaviour of the client is somewhat different than in windows. One thing that is hugely annoying is not being able to resize the playing area. You can affect this though by editing the Brettspielwelt.prop file. 

Well that's it for now. Pretty useless I know, but it might help someone (it would have helped me at least :) ).

---

