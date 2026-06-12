---
title: "celestia, not working"
date: 2005-10-26
forum: Gaming &amp; Leisure
---

### Post by tukster on 2005-10-26
hi all
i've installed celestia-common and celestia-gnome with synaptic.
but when i try to run it with celestia-gnome, this error is shown:

"Unknown escape code in string
Error reading configuration file." :( 

And i can't locate any launcher for it
(haha noob, been using ubuntu for a week).

I then tried to compile it. Configure went ok till an error stating that i don't have "zlib". I've compiled zlib 1.2.3 from zlib.net, but no go. celestia configure still reports zlib missing.

pls, what am i missing here.:confused:

---

### Post by Perfect Storm on 2005-10-27
Works perfect here with a synaptic install. Try remove your compiled zlib install and reinstall zlib from the repo.

Then:
sudo apt-get install celestia-gnome

By the way are you on 386 system or amd64?

---

### Post by tukster on 2005-10-27
hello
did everything u wrote, but i still have the same error.
i'm running amd 64 box.

---

### Post by Perfect Storm on 2005-10-27
Ah, that may be the issue. Sorry I don't know how to solve it, I have no experience with a64 arcitecture.

---

### Post by tukster on 2005-10-27
well thx for helping,
i'm wondering why no one else reported this prob on 64 box,
maybe i just goofed things up

---

### Post by skylark on 2005-11-02
tukster, I'm also running AMD64 and have exactly the same problem. I'll post here if I can work out a solution.

---

### Post by skylark on 2005-11-02
Here is a partial solution for AMD64:
sudo cp /etc/celestia.cfg /etc/celestia.cfg.old

now edit /etc/celestia.cfg (eg sudo vim /etc/celestia.cfg)
go to end of the file and comment out labelled stars that start with:
"\u03b1...
by adding a "#" character to the beginning of those line.

This at least gets celestia working but on startup it still gives warnings:
"Error parsing solar system file"

and familiar places like Earth, Mars etc aren't loaded. So it's not a very good solution! 

The other solution might be to set up celestia-gnome in a 32-bit chroot, but I tried it and it "quit unexpectedly" - it might have something to do with setting up the video card drivers under the chroot which I haven't attempted. So no easy solution yet.

---

### Post by tukster on 2005-11-02
well good try anyway
i couldn't do much, but i'm thinking going 32bit for a while,
its not just celestia, but ati drivers, wine, cedega(lol).
i hate to have xp for gaming only.

---

### Post by reedlaw on 2005-11-02
I'm having a problem in Celestia too.  I can't see any of the space craft models.  I am running Breezy with linux-386.

---

### Post by manfo on 2005-11-03
Hi everyone, I'm on amd64 and I'm getting the same error told by tukster... Celestia worked fine when I was running Hoary, though... :( 

Bye!
.m

---

