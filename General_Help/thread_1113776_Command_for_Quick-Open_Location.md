---
title: "Command for Quick-Open Location?"
date: 2009-04-02
forum: General Help
---

### Post by e.m.fields on 2009-04-02
Allo!

It's a trifling thing, but it's going to drive me crazy:** What is the command-line to run the open-location dialog in Ubuntu/Gnome? ** 

***Not*** the command ***to open a location***, but **to open the "open location" dialog** you'd see if you clicked on the desktop and hit "Ctrl-L".


Purpose being, I'm looking for a quick keyboard shortcut to open location via Compiz / Metacity.  More efficient to go straight to location than open nautilus. 

Thanks!!

--
e.m.fields
chapel hill, nc

---

### Post by Elfy on 2009-04-02
```
gnome-open <url>
```

eg gnome-open ~/ would open your home

mmm - me reads again now I've woken more - if you try the command with out a location it asks for one, so perhaps that's not what you want.

That is the command so try using it in whatever shortcut you choose

---

### Post by e.m.fields on 2009-04-17
Hi ... thanks for reply, but....

This
[IMG]http://i674.photobucket.com/albums/vv108/emfields/open_location.png[/IMG]

is actually what I'm looking for. 

Anyone know how to run this dialog from command-line?
Thanks!

---

### Post by Yashiro on 2009-04-17
gnome-run used to open the old run dialog. Not sure about the location popup.

---

### Post by Brucevdk on 2009-04-18
There is no relatively easy way to invoke this "Open Location" dialog (ALT + F2) as it is part of Nautilus (the desktop is a Nautilus view). However, perhaps you'll settle for the "Run Application" dialog. The thread [Add Gnome Run Dialog to Main Menu](http://ubuntuforums.org/showthread.php?t=512290) was helpful in finding a solution to bring up the dialog as it is part of the gnome-panel.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=110177&d=1240048198[/IMG]

You'll have to compile the attached gnome-run.c using the command below and put it in ~/bin (if it's in your path) or /usr/local/bin. Then you'll be able to bring it up using the command: gnome-run. The gnome-run.c attached is a slightly modified version of the one from [http://darkness.codefu.org/wordpress/2004/07/24/152](http://darkness.codefu.org/wordpress/2004/07/24/152) so the dialog is focused. 

```

gunzip gnome-run.c.gz # Ubuntu Forums doesn't allow you to attach .c files
gcc gnome-run.c -o gnome-run -L/usr/X11R6/lib -lX11

```

Another solution might be to compile panel-run-dialog.c from gnome-panel directly which uses panel-run-dialog.glade for its interface definition.

You might also be interested in [GNOME Do](http://do.davebsd.com/).

---

