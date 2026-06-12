---
title: "No &quot;Write To Disc&quot; option"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Biased turkey on 2005-11-02
In the ubuntu starter guide (ubuntu wiki ) it says that to write a file to a CDROM , just right-click on it and select "Write to disc".
I don't see that option when right clicking on the file.
Does Ubuntu install any CDROM burning  program out of the box ?
I don't see any in Applications->Sound & Video.

Sorry to ask such simple question, but I'm a very recent "turncoat" ( for 5 years I used KDE exclusively )

---

### Post by aysiu on 2005-11-02
It should have a "write to disc" option.
Oh, well. You can easily install a CD burning program (Gnomebaker, Graveman, K3B), though.
Read more here:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by frenkel on 2005-11-02
Go to burn:// in nautilus and add the files. Then click on the write button and you're done!

---

### Post by SickTwist on 2005-11-02
[QUOTE=Biased turkey]In the ubuntu starter guide (ubuntu wiki ) it says that to write a file to a CDROM , just right-click on it and select "Write to disc".
I don't see that option when right clicking on the file.
Does Ubuntu install any CDROM burning  program out of the box ?
I don't see any in Applications->Sound & Video.

Sorry to ask such simple question, but I'm a very recent "turncoat" ( for 5 years I used KDE exclusively )[/QUOTE]

You'll only see the "Write to disc" option for ISO files (CD images, like the one you downloaded for the Ubuntu installation CD).

[Nautilus]("http://www.gnome.org/projects/nautilus/") (the file manager) has a built-in utility for creating data CDs. Just open a Nautilus window (Places --> Home Folder) and select "CD/DVD Creator" from the "Go" menu item. Drag files you wish to burn to this window then click "Write to Disc" on the toolbar when you are ready to burn.

Or, as aysiu has suggested, [Graveman]("http://graveman.tuxfamily.org/index.php"), [GnomeBaker]("http://biddell.co.uk/gnomebaker.php"), and [K3B]("http://www.k3b.org/") are programs specifically for burning discs. You can use Synaptic to install any/all of these easily.

Also, just so you are aware, Ubuntu comes with [Serpentine]("http://s1x.homelinux.net/projects/serpentine/") installed by default as well. This is a burning program for creating audio CDs. It is under Applications --> Sound and Video --> Serpentine

Have fun!

---

### Post by Biased turkey on 2005-11-02
Thanks to all of you for taking some of your time to reply.
I finally found the G0->CD/DVD Creator in Nautilus.
I don't have any ISO file on my hardisk right now so maybe that's why the right-click option doesn't work. I thought that right-click option was working with any kind of file.
I know about K3b ( good stuff imho ) and have been using it for a couple of years with KDE, but my thought was: If Nautilus has a default CD burner, why not try it instead of installing K3b.

---

