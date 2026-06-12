---
title: "gdesklets for 64 bit"
date: 2007-06-13
forum: Desktop Environments
---

### Post by adityakavoor on 2007-06-13
Hi,

I'm not able to get gdesklets working in my core2duo 64 bit PC.
The gdesklets shell just doesnt open. 
Please help

---

### Post by jrocket on 2007-06-14
Actually I'm having a problem with that as well.  I start it from the command line with 'gdesklets' and it says 'starting daemon', and eventually times out and the daemon still isn't started.  It says to check the log file, but I haven't found anything on the command line that tells me where the log file is located.  Eventually I just gave up.

---

### Post by Elipsn on 2007-06-14
I'm also having problems, it just won't start...

---

### Post by morghi76 on 2007-06-14
You're not alone. I have a x64 processor and gDesklets doesn't work... Any idea?

---

### Post by orb9220 on 2007-06-14
32bit kernel?

That still works and unfortunately the Devel team for gdesklets are like:

Programmer's on Valium.

1) They don't answer post in their forums or respond to emails.
2) The code is old and slow and there is no progress on upgrading or addressing bug issue's
3) They don't Care?

I wish there were but gdesklets and a few other's is why I still use 32 kernel on my 64 system.

Is Adesklets getting anywhere? Last time I checked it was a pain to setup.

---

### Post by morghi76 on 2007-06-19
I found a number of interesting threads which helped me to make the gDesklets working. Funny that, now they I manage to get them working I'm not using them... by the way, look at bug 110103 posted on lauchpad: [https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)

I used Dizzi file attached to the following comment and they worked! [https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103/comments/10](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103/comments/10)

Unfortunately the installation wiped out the link between files and apps but I restored it following the instructions given in these other post:
[http://ubuntuforums.org/showthread.php?p=2599591](http://ubuntuforums.org/showthread.php?p=2599591)

They actually consist in reinstalling few packages via synaptic.
Then, I must also report that I lost 3 of the 4 workspaces I use with Compiz cube but I don't know if there is any relation. By the way, I solved this issue installing the compiz manager via synaptic and setting the number of workspaces with this tool.

Sometimes is not easy to go for a x64 installation but if we (happy 64-bit processor owners) don't support the guys who are porting the system to our platform, they will never make it!

Thank you programmers out there!

---

### Post by adityakavoor on 2007-06-21
i went back and installed an i386 version of feisty ;)

---

### Post by ubonetu on 2007-07-01
You need to remove (and the .gdesklets directory in ~/  ) and re-install the original package.  I got it from a link here somewhere.  You may want to try sourceforge.net if you can't find it.

Edit (sorry to be so uninforming...  I don't know how I did this.  I worked on it for a couple of hours in a recent re-install with no luck.  I found it somewhere in this forum, I'll find it!)  Hey (I have a problem with parenthesis [if you get my drift (say no more, okay?)])!

If I can find that post I'll be back to edit...

ta, da!

[http://http://ubuntuforums.org/showthread.php?t=486693&highlight=gdesklets]("http://http://ubuntuforums.org/showthread.php?t=486693&highlight=gdesklets")

This wasn´t the one I was thinking of but it's marked as solved and makes reference to a deb package.

I'm on a really old machine now and am going to try to configure some effects but I don't expect much.  I hope that helped.

Be good!

---

