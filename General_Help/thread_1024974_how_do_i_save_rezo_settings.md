---
title: "how do i save rezo settings"
date: 2008-12-29
forum: General Help
---

### Post by kevil99 on 2008-12-29
[[IMG]http://i140.photobucket.com/albums/r25/kevil99/th_Screenshot-6.png[/IMG]](http://s140.photobucket.com/albums/r25/kevil99/?action=view&current=Screenshot-6.png)


how do i save theses settings i want to run a hiher rezo than 1024x768 default. the rezo always goes back to default when i restart the pc

---

### Post by kevil99 on 2008-12-30
Is my question unclear? i need to try and keep the rezo high.

---

### Post by kevil99 on 2009-01-01
thx ppl

---

### Post by stderr on 2009-01-01
Rezo? There's an abbreviation I've never heard of before :)

Firstly, check System -> Preferences -> Screen Resolution.

Secondly, I would have a look in /etc/X11/xorg.conf

Are there any resolutions specified in there?

---

### Post by gopgioclub on 2009-01-01
Online magazines like ak47.tv and BlueEyes Magazine, along with the more established ZoneZero, may be the most vital (and cost-effective) showcases for contemporary photography outside the hot names of the gallery circuit, and I hope they keep thriving and growing. Influence was probably my single favorite art-photography magazine in 2004, but they could only get one amazing issue out...with the second one scheduled for publication in the first quarter of 2005.  I can't wait.

---

### Post by loomsen on 2009-01-02
Save it to another path. You dont have write permissions in /etc/X11 which is rather good.

Just change the path to save the file to your home folder.

Assuming you saved the file to 
**~/xorg.conf**
open up a terminal and do this to backup your default xorg.conf and replace it with your new one:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup && sudo rm /etc/X11/xorg.conf && sudo cp ~/xorg.conf /etc/X11/

```

If you choose to copy and paste, make sure you get the whole line at once.

---

