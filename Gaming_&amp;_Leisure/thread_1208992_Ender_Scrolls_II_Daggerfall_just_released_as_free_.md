---
title: "Ender Scrolls II: Daggerfall just released as free download"
date: 2009-07-09
forum: Gaming &amp; Leisure
---

### Post by ishii255 on 2009-07-09
I'm downloading it right now, should work fine with dosbox. The official site is really slow right now due to all the traffic. Get it from [fileshack]("http://www.fileshack.com/file.x/14752/The+Elder+Scrolls+II:+Daggerfall+Free+Client").

Here's the url if the link doesn't work:
[http://www.fileshack.com/file.x/14752/The+Elder+Scrolls+II:+Daggerfall+Free+Client](http://www.fileshack.com/file.x/14752/The+Elder+Scrolls+II:+Daggerfall+Free+Client)

Nice to play a free crpg other than ultima

---

### Post by Grishka on 2009-07-11
> **ishii255 said:**
> I'm downloading it right now, should work fine with dosbox. The official site is really slow right now due to all the traffic. Get it from [fileshack]("http://www.fileshack.com/file.x/14752/The+Elder+Scrolls+II:+Daggerfall+Free+Client").

Here's the url if the link doesn't work:
[http://www.fileshack.com/file.x/14752/The+Elder+Scrolls+II:+Daggerfall+Free+Client](http://www.fileshack.com/file.x/14752/The+Elder+Scrolls+II:+Daggerfall+Free+Client)

Nice to play a free crpg other than ultima

nice. =D> that's five years since they're released Arena for free. Daggerfall is good, some people still prefer it to Oblivion. still, fileshack may not be the best way to get it. so, an [official link](http://www.elderscrolls.com/downloads/downloads_games.htm).

edit: scratch that, I'm getting 3 KB/s transfer from Bethesda. :lolflag: fileshack it is. :)

---

### Post by del_diablo on 2009-07-11
Its a good game to anybody who likes:
*RPG
*Hack & Slash a tad
*Loves a good atmosphere
*Can read

---

### Post by malrost on 2009-07-11
A quick how-to, as much for myself as anyone else, since this is my first use of dosbox and the instructions on the Bethesda and the /. links aren't quite right for 9.04. The instructions I've seen are based on a later release of dosbox then is in the repositories, which apparently changes things a bit.


[LIST=1]
[*]Download the game. [http://bethblog.com/index.php/2009/07/09/daggerfall-now-available-for-free/]("http://bethblog.com/index.php/2009/07/09/daggerfall-now-available-for-free/")
[*]extract the downloaded archive to a folder location that you will map to dosbox as your C: drive. I'm using /home/beb/dos/c
[*]install dosbox
```
sudo apt-get install dosbox
```
[*]in a *_gnome_* terminal, run dosbox
```
dosbox
```
[*]The rest of the code listed below is entered into the *_dosbox_* terminal. Mount the directory you made as C:, using the recommended settings.
```
mount c /home/beb/dos/c -freesize 1000
```
[*]Notice that dosbox starts you out by default in the Z:\ drive. Change to the C:\ drive.
```
C:
```
[*]If you mounted the folder to which you'd extracted the Daggerfall game, the DIR command should list the following directories.
```
dir
.
..
DAGGER
DFCD

```
[*]dosbox has to think that Daggerfall is installed and run from a virtual CD. The DFCD file included in the download is the fake CD. Map this directory to dosbox as the D: drive.
```

mount d /home/beb/dos/c/DFCD -t cdrom -label Daggerfall

```
[*]switch to the D: drive, and install Daggerfall.
```
D:
install

```
[*]At this point you should see the install graphics (see attached), and your mouse should be able to access Daggerfall by clicking inside the dosbox window. To toggle to/from fullscreen --and to free your mouse pointer if it gets stuck in dosbox-- press ctrl+enter. More detailed install instructions are available from this point [here]("http://www.shacknews.com/onearticle.x/59477"), step 13 on.
[*]Once the installation finishes it will kick you back to a dos terminal. Disregard the commands the install program told you to enter. Instead type this:
```
fall z.cfg
```
[/LIST]

---

### Post by humandraydel on 2009-07-11
Anyone have any luck actually playing it?  I got it to install, but when I try to play, it says "You must have the wrong CD inserted into your CD-ROM.  Please insert the Daggerfall CD and try again."

It's obviously mounting it fine because I went through the whole install sequence.

---

### Post by lnxnut on 2009-07-11
I'm at the exact same roadblock.  Somebody will figure it out soon hopefully :)

---

### Post by humandraydel on 2009-07-11
It works if I type "fall z.cfg"

---

### Post by Falcorian on 2009-07-11
> **humandraydel said:**
> It works if I type "fall z.cfg"
Same problem as above, this solves it.

However now my mouse doesn't control the dosbox mouse unless I'm in fullscreen mode... In which case half the screen is off the edge. :-/ Anyone got any ideas?

I was able to get the mouse to grab by setting up a configure file for dos box, and setting autolock=false.

---

### Post by del_diablo on 2009-07-12
Abuse Ctrl+F10, to solve the mouse problem :P

---

### Post by Sand &amp; Mercury on 2009-07-12
I'm really digging it. I played the demo years ago, but it doesn't even hint at the expansiveness of the full game. It's also nice to see something from Bethesda before they turned into a bunch of prudes. :D Though Morrowind to my mind, remains their crowning achievement, with the perfect balance of size, depth and simplicity.

---

### Post by bodyharvester on 2009-07-12
> **Sand & Mercury said:**
> Though Morrowind to my mind, remains their crowning achievement, with the perfect balance of size, depth and simplicity.

so true, i played morrowind and oblivion but i do think oblivion should have been more like morrowind, not the other way around

---

### Post by Pressondude on 2009-07-25
I can't use my arrow keys in DOSbox...at least not in the installer when I need to setup my soundcard. I'm using a Zboard with the standard keyboard layout chipset attached. The USB version.

---

### Post by Grishka on 2009-07-25
> **Pressondude said:**
> I can't use my arrow keys in DOSbox...at least not in the installer when I need to setup my soundcard. I'm using a Zboard with the standard keyboard layout chipset attached. The USB version.

I think it's fixed in 0.73. or use [DBGL](http://members.quicknet.nl/blankendaalr/dbgl/), and turn off the 'use scancodes' option. this will help for sure.

---

### Post by Pressondude on 2009-07-25
How do I turn off scancodes?

---

### Post by Grishka on 2009-07-25
> **Pressondude said:**
> How do I turn off scancodes?

there's a 'use scancodes' option in DBGL profile's I/O tab.

---

