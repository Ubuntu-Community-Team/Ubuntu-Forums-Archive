---
title: "Slow Desktop"
date: 2009-05-02
forum: General Help
---

### Post by Kubular on 2009-05-02
I've been getting weird lag since I updated to 9.04. The framerate seems quite slow - mouse doesn't move smoothly and it _feels_ slow. It's not a great deal, maybe a few milliseconds but it definitely doesn't feel right.

Having trouble typing too, I'm typing a lot faster than the chars are actually being rendered. And no, I'm not that fast a typist.
It keeps missing chars too, and again, I'm not missing them, the OS must be. Which is making me wonder if something's interfering somehow.

I've had some video issues - was having trouble with the proprietary ATI driver (using a Radeon HD4850) ubuntu recommends so disabled that, still seems slow. What's interesting is that Gnome actually seems faster than the X script interface thing.

If I disable the proprietary driver it seems even slower but then I can't even open the Display Manager or the Hardware Test app. Display manager opens a window but it's empty (apart from a weird green rectangle in the middle). Then it takes forever to close after I ask it.

Hardware manager never seems to get round to opening a window at all, have once received a "this app is not responding - force quit?" type message, but that's it.

Installing ATI's drivers from their website fixed this - they work a lot better, it is faster but things still do feel noticably slow. I get a weird message on restart too when the OS loads. Something about soft-restarts or something? I'll come back and update this with the actual message later.

I missed out 8.10, haven't really touched Ubuntu in the last year, so it's a fresh install.

I have managed to set up my dual monitors/resolutions up properly though, which is a first for ubuntu. ;) At least this easily.

Every cloud has a silver lining!

---

### Post by Kubular on 2009-05-02
Issue i actually a lot simpler than I've made out. The desktop/apps are running fine, it's only the input devices that seem slow (mousend keyboard).

Suspect it's an I/O issue but don't know nearly enough to fix it myself. Have to type slowly otherwise I lose chars (ubuntu seems to not hear my keypresses).

Mouse also feels slow, as stated above.

I've reported this on launchpad, as it seems similar to a bug reported a few months ago. In the meantime though, does anyone have any ideas where to start?

---

### Post by Mikkee on 2009-05-05
I got the same problem as for the mouse beeing laggy. This happen mostly when Downloading torrent or loading a huge webpage. 

Note that i use a wifi card and a wireless mouse on a new computer but i didn't had this problem in my old computer with Ubuntu 8.10 with the same mouse and wifi card.

Should i start a new thread ?

---

### Post by Kubular on 2009-05-05
Possibly, I managed to fix my issue, here:

[http://ubuntuforums.org/showthread.php?p=7220406&posted=1#post7220406](http://ubuntuforums.org/showthread.php?p=7220406&posted=1#post7220406)

Sounds like you're machine's just struggling to cope. Could be related though. Have a read through that and see if it sounds familiar.

---

### Post by Mikkee on 2009-05-20
I fixed my problem by connecting my computer directly to the rooter via cable. No more lag at all.

Tks anyway.

---

