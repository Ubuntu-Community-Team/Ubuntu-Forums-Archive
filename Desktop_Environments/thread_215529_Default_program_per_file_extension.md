---
title: "Default program per file extension ?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by abelthorne on 2006-07-14
Hello,
Is it possible in Ubuntu to set a default program for a file extension, indepentdently of its content? AFAIK, Linux doesn't use extensions to recognize the type of a file (I guess it uses MIME).

My problem is that Scribus files (.sla) are plain text files (XML I think). So, when I double-click on one, it will open with the text editor. I can right-click on one and select "open with Scribus" in the menu, but that's not very user-friendly.
If I set the default program for this kind of file to Scribus, I get an error message saying "the filename says that its a Scribus file but the content says plain text" and doesn't let me open the file.
And BTW, if I add Scribus to the default programs list it will appear twice in the contextual menu and it will appear in the menu of plain text files, which I don't want to.

How do I - if possible - sort this out?

---

### Post by utnubu001 on 2006-07-14
yeah i also wanna know cause when i click on a movie it goes to totem-and totem needs a xine engien and im to lazy to download it
so i always have to right-click and say open with xine

HELP

---

### Post by abelthorne on 2006-07-14
> **utnubu001 said:**
> yeah i also wanna know cause when i click on a movie it goes to totem-and totem needs a xine engien and im to lazy to download it
so i always have to right-click and say open with xine

With video files, I don't think you'll encounter any problem by changing the default program (open properties of a file, go to "open with" tab and change the default program to the one you want).

My problem is slightly different (extension vs MIME handling).

---

### Post by philippe_carlo on 2006-07-14
You need to edit the /etc/mime.types to match extensions with programs. You can do this with sudo gedit /etc/mime.types. It's the only way I know. You would expect some better interface though.

---

### Post by abelthorne on 2006-07-14
> **philippe_carlo said:**
> You need to edit the /etc/mime.types to match extensions with programs. You can do this with sudo gedit /etc/mime.types. It's the only way I know. You would expect some better interface though.

That's perfect. Anyway, I'm not really aware of MIME type management : are there some things not to do if I don't want to screw my system ?
Is there a particular syntax to use ?

Shall it work fine if I add the MIME type "text/scribus    sla" or do I have to set it as application rather than text ? Is the program name case sensitive ?

---

### Post by philippe_carlo on 2006-07-14
(a) It's probably just a good idea to keep a backup of the original file.
(b) Everything is case sensitive. I'm not an expert on this. Play around with the file and see if it works. That's the best way of learning wether stuff works. Mind the backup though!

---

### Post by abelthorne on 2006-07-14
> **philippe_carlo said:**
> (a) It's probably just a good idea to keep a backup of the original file.
(b) Everything is case sensitive. I'm not an expert on this. Play around with the file and see if it works. That's the best way of learning wether stuff works. Mind the backup though!

In fact, it seems that a user can make a custom .mime.types files in his own directory, which content supercedes the one that's in etc.
I'll make tests with it.

---

### Post by visualdensity on 2006-07-14
How about right-clicking on the item, BUT select 'Others' option at the bottom of pop-up menu? I find that works for me for most of the items.

Just so that we don't always need to fire up the terminal. :) If you're not clear, try this [http://www.weekeat.com/linux/setting-default-players-in-ubuntu](http://www.weekeat.com/linux/setting-default-players-in-ubuntu)

---

### Post by abelthorne on 2006-07-14
> **visualdensity said:**
> How about right-clicking on the item, BUT select 'Others' option at the bottom of pop-up menu? I find that works for me for most of the items.

Just so that we don't always need to fire up the terminal. :) If you're not clear, try this [http://www.weekeat.com/linux/setting-default-players-in-ubuntu](http://www.weekeat.com/linux/setting-default-players-in-ubuntu)

My point is precisely that I'd like to avoid going through the contextual menu to launch my Scribus files. I'd like to simply double-click on them.

---

### Post by steveland? on 2006-08-21
Here's how I do it:

>	Open mime.types:	sudo gedit /etc/mime.types
>	Search for file extension:	<ctrl+f> “file type”
>	Copy Mimetype
>	Create a backup of defaults.list:	sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list.backup
>	Open defaults.list:	sudo gedit /usr/share/applications/defaults.list
>	Search for Mimetype:	<ctrl+f> <ctrl+v>          (mimetype should still be on your clipboard)
>	List available applications:	ls /usr/share/applications/*.desktop
>	Change default application or Mimetype in the form	[mime-type]=[new-app].desktop
>	Save mime.types
>	Restart nautilus: killall nautilus

---

### Post by KeybladeSephi on 2008-06-25
An easy way that I did it was right click on the *file* that has the corresponding extension you want to change default programs to and click on Properties. Go to the Open With tab and choose which program you want to open it with. You can also add and remove options. Hope this is what you were trying to accomplish =]

Oh and by the way, this is on Ubuntu 8.04 Hardy Heron; I don't know if this will work on Feisty Fawn or Gutsy Gibbon. Sorry if it doesn't =\

---

