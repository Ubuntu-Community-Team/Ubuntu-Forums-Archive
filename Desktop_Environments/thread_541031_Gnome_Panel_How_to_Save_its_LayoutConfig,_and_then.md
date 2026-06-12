---
title: "Gnome Panel: How to Save its Layout/Config, and then Restore it?"
date: 2007-09-02
forum: Desktop Environments
---

### Post by OzzyFrank on 2007-09-02
OK, now I've seen it said that ~/.gnome2/panel2.d is where the config file for your Gnome panels is stored, but all I see are all the launchers in ~/.gnome2/panel2.d/default/launchers. Ubuntu and Gnome are great, but they aren't MAGIC, hehe... and c'mon, someone must know the answer as to what file records the positions! So please share your wisdom, as I'd like to be able to save the panel in case Gnome mucks it up again. Would also appreciate an example of how to write a little script to restore it from a backup. Cheers!

---

### Post by OzzyFrank on 2007-09-05
Answer me, damn you, or I'll go jihad on your asses, and smack a fatwa upside your heads in the name of Jesus Allahstein! And someone be a nice dear and go to my other thread and answer the one about where the desktop icons layout is kept...

...NOW!

---

### Post by komputes on 2007-12-13
Try this:

Alt+F2

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Reboot and enjoy the default panels. And don't be mean, we all try our best.

:popcorn:

---

### Post by bharkins on 2008-04-01
> **komputes said:**
> Try this:

Alt+F2

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Reboot and enjoy the default panels. And don't be mean, we all try our best.

:popcorn:

Tried that code line, get error line "Can't exec gnome-panel": no such file or directory.

Any ideas?

---

### Post by komputes on 2008-05-20
These instructions were written for Gutsy (7.10) and no longer work in Hardy (8.04).

The new instructions (please note **this will [COLOR=Red]DELETE[/COLOR] files **which in turn will reset the panel): 

```
rm -fr .gconf/ .gconfd/ .gnome2/ .gnome2_private/ 
```

---

### Post by OzzyFrank on 2008-05-30
> **komputes said:**
> And don't be mean, we all try our best.

I thought I was being funny to an audience that wasn't there, hehe (can't really be mean when no-one is there to be mean to, hehe). [Though if you are referring to instilling absolute fear by use of Islamic words in this age of Bushian terrorism paranoia: Sorry!]

So, can I use any of this to restore my Gnome panel from a "backed-up" folder? I say "backed-up" because I had to rename .gconf, .gconfd and .gnome2 as I couldn't get into Gnome... so everything is back to default, but I still have those folders with my previous settings.

---

### Post by OzzyFrank on 2008-05-30
> **komputes said:**
> These instructions were written for Gutsy (7.10) and no longer work in Hardy (8.04).

The new instructions (please note **this will [COLOR=Red]DELETE[/COLOR] files **which in turn will reset the panel): 

```
rm -fr .gconf/ .gconfd/ .gnome2/ .gnome2_private/ 
```

Thanks on the update re Feisty vs Hardy. But I don't need to know how to reset the panel to its default, but rather back up the one I have, and then be able to restore it later. I've just had my panel reset to the default and it sucks, hehe! I want the reverse of this.

---

### Post by komputes on 2008-06-02
I'm guessing, set your panels the way you want them, then backup those folders instead of removing them. By the way if you remove those folders with "rm -fr" you will not be able to recover them through the trash. Concerning the language on the forums, just read the guidelines of the forums and try to be more courteous. Alas you did not succeed in instilling fear into me through words, the media has already made me numb to this (Re: Paris Hilton on CNN :roll: being covered over real news, that was the last straw). But better luck next time, as the arab peeps would say: "Incha Allah" (God willing).

:) Imagine world peace, or just go out to B&J's. Can't we all just get along? :)

Sorry Ozzy if the end of my message doesn't make sense, must be the sugar rushing to my head.

---

### Post by drs305 on 2008-06-04
> **OzzyFrank said:**
> Thanks on the update re Feisty vs Hardy. But I don't need to know how to reset the panel to its default, but rather back up the one I have, and then be able to restore it later. I've just had my panel reset to the default and it sucks, hehe! I want the reverse of this.

To save the panel settings (example to a desktop file called panel_settings):
```
gconftool-2 --dump /apps/panel > **~/Desktop/panel_settings**
```

To restore saved panel settings and refresh the panel:
```
gconftool-2 --load **~/Desktop/panel_settings** && killall gnome-panel
```

This won't save all the panel applets but it will save most of them.

---

### Post by OzzyFrank on 2008-06-26
OK... I would have thought this one would be solved by now. So, seriously, no takers? And if you're a developer looking for a small but useful app to make, this could be it! I personally think one should be included with the next Ubuntu and/or Gnome, as the panel can get destroyed with upgrades, and all those drawers full of launchers go to limbo. But I'd settle for a terminal command, or even a definitive answer on which file(s) to back up. I assume many others out there would welcome the info too. Cheers

---

