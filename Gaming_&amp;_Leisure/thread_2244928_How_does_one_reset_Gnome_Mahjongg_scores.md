---
title: "How does one reset Gnome Mahjongg scores?"
date: 2014-09-19
forum: Gaming &amp; Leisure
---

### Post by WB0HYQ on 2014-09-19
I've done a ton of searching here as well as using Google and can only come up with VERY old threads that give locations that don't exist in Ubuntu/Xubuntu 14.04.  My list of Mahjongg scores is very long now and I'd like to reset it back to as installed (I.E. no scores).

How does one go about that?  I can find files named such as 'gnome-mahjongg-difficult.scores' but there are no entries in it (using the file manager or SUDO gedit).  Even if I temporarily rename the file and start up Mahjongg I still see my previous scores.  It has to be getting them from somewhere, I just can't find out where.

There is a bug issued in Bugzilla addressing the possibility of a 'Clear' button, but that went nowhere according to the discussion.

Bill

---

### Post by R33D3M33R on 2014-09-20
To locate the file with the scores, try running the game with:

```
strace -e trace=open,read -o output.txt change-this-to-mahjongg-executable
```

Don't forget to open the list with the highscores to trigger event. In the output.txt file you will see which files were opened/read from.

---

### Post by vasa1 on 2014-09-20
What about ~/.local/share/gnome-mahjongg/history?

When I played a game and finished it, I immediately ran ```
find ~/ ! -path "*mozilla*" ! -path "*google-chrome*" ! -path "*cache*" -mmin -5 -type f -ls
```and got```
3803325    4 -rw-rw-r--   1 vasa1    vasa1          34 Sep 20 13:00 /home/vasa1/.local/share/gnome-mahjongg/history
2884260   16 -rw-rw-r--   1 vasa1    vasa1       12564 Sep 20 13:00 /home/vasa1/.config/dconf/user
```Edit: deleting the history file removes all previous scores, at least for me.

---

### Post by WB0HYQ on 2014-09-20
Both answers are right on the money.  I don't iknow enough about Linux, that's for sure. But I am learning.

The 'strace' command, offered by R33D3M33R, is a command that worked just fine - and can be used to figure out disk accesses by any program. This was useful not only in finding the History file, but can be used again and again with other tracing activities.

And, Vasa1, your answer was also correct.  I had been looking into various hidden files in my own 'home' folder, but I am still in the mindset of Windows and when I see a file with no extension, I leave it alone.  I have now learned that it is possible to double-click a "extensionless" file and have it open in a text editor (gedit).  In the History file I did find just what I was looking for.

My happy thanks to both of you for your valuable help.

Bill

---

### Post by vasa1 on 2014-09-20
> **WB0HYQ said:**
> ...
The 'strace' command, offered by R33D3M33R, is a command that worked just fine - and can be used to figure out disk accesses by any program. This was useful not only in finding the History file, but can be used again and again with other tracing activities.
...

I'm going to keep note of that. Its advantage is that it doesn't presuppose where the file is or isn't. If it's somewhere in the system as opposed to in being one's home folder, running find could take a long, long time.

In the context of your question, grepping output.txt for "O_RDWR" would clean things up.

---

### Post by WB0HYQ on 2014-09-20
Actually, I kind of enjoyed scanning through the output of the trace file.  Until one does something like that, you never really know just how much a given program interacts with your OS.  Now, at least for that program, I do.  If the file is simply opened with Gedit, then the Ctrl-F (Find) command works well also - and if you 'find' what you're looking for, there is a "find next" function that moves you to the next instance of the search term.

The first time I tried a command-line 'find', it took almost 30 minutes before the command completed.  I thought at the time that there HAD to be a better way.

Thanks again,

Bill

---

### Post by vasa1 on 2014-09-20
> **WB0HYQ said:**
> ...
The first time I tried a command-line 'find', it took almost 30 minutes before the command completed. ...Yes, that's why it's important to limit the scope of **find** by specifying paths or excluding folders, etc whenever that's possible.

---

### Post by WB0HYQ on 2014-09-21
Given the size of hard drives now (my 64-bit system has two 1Tb drives - one for Linux and one for Windows 7) searches can take literally hours and hours so your statement definitely holds true.

Thanks for the input (here also).

Bill

---

### Post by jhon8 on 2015-08-24
My thanks to [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar773818_3.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=773818") 				 				 					 						 	[**[COLOR=#000000]R33D3M33R[/COLOR]**]("http://ubuntuforums.org/member.php?u=773818") for putting me wise to 'strace'. Debian Jessie user here. Long story short, mahjongg was dying in a cloud of Gtk errors, and I couldn't figure out why. Strace showed me that it was trying to load a defective tileset I had deleted. (Half the fun of mahjongg is making new tilesets.) I copied a good tileset to the name of the bad one, and mahjongg started up normally! (I'd still like to know where gnome-mahjongg keeps its preferences...) Anyway, problem solved! 8-D

---

