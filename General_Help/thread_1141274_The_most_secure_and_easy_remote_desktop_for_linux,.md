---
title: "The most secure and easy remote desktop for linux, for the windows user :)"
date: 2009-04-28
forum: General Help
---

### Post by k-bl on 2009-04-28
Let me just start out by saying I've searched long and hard for a secure remote desktop environment for linux (specifically ubuntu in my case) and was finding nothing with the exception of vnc/vino/x11, which leaves something to be desired.

Then one day I tried a new search, something a bit different on Google and found nx-server, downloadable at [http://www.nomachine.com](http://www.nomachine.com) (guys, this needs added to the repositories!).

Now I was a windows user since I was probably 8 (I'll be 25 in may) and have always used RDP, and thought to myself "Why hasen't anyone adapted RDP-server to linux?"  Well, the search is over!

nx-server is out of the box, simple, secure, and easy.  All you have to do is download nx-server and it's prerequisites (nx-client, nx-node).  Install client, node, and then server (in that order) using gdebi package installer and make sure ssh-server is installed ("sudo apt-get install openssh-server") and you are set.

Nx-server uses an amazing compression rate to give you a super-speedy desktop environment over an ssh connection.  It supports multi-session and is much more secure than a single session vino vnc remote desktop.

I have had a few issues with nx-server about the initial creation of the credentials file (this is created when you install nx-server), you might have to do a chown on them (check the error log, it will show you which ones), but after that you are free and clear.

In fact, I'm using nx-server right now on an ubuntu system (9.04) from a windows xp pro system.

Thanks for bridging the gap guys!

K-BL

---

### Post by lykwydchykyn on 2009-04-28
nx-server is proprietary, so just adding it to the repos may present some licensing problems.  There's freeNX, which is a FOSS clone of the server, but I don't know why it's not in Universe, at least.  You can get it from some ppa repos though.

It's good stuff, though, for sure.

---

### Post by k-bl on 2009-04-28
Well, it's still amazing :)

---

