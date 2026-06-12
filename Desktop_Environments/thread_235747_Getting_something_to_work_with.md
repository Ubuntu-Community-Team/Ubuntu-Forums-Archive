---
title: "Getting something to work with"
date: 2006-08-13
forum: Desktop Environments
---

### Post by driller on 2006-08-13
It is now two weeks since I loaded Ubuntu and I have achieved nothing.
  Each time I switch on the computer, i get the Ubuntu desktop with a large magnified section top center.  There is a program in the tray called "Gnopernicus" I can of course switch this off, but it will be back next time as I have no idea how to get rid of it.
   I have tried to load a printer, (HP Laserjet 4000N) but to no avail. I go through the:"Add a Printer" routine, as for a PP printer. Step 1 - I select a Local Printer in port LPT#1, then click Forward. Select HP as the manafacturer and either Laserjet 4000 or 4000 Series Postscript recommended)then when I hit the Select Driver button, it goes to something called "Select a PPD file"  WHAT IS THIS? It wants me to open a file, but I have no idea what or why.
   I have never used the command line as I do not know how.
Is there any point in keeping on keeping on?

---

### Post by em3raldxiii on 2006-08-13
Hi Driller,
 
Well, I can't answer ALL your questions, but I can help a little.  I assume you are using Gnome.  In your system preferences menu, there should be an icon for sessions.  In there, you should be able to find Gnopernicus and remove it from the session boot options.  Unfortunately, I am going purely from memory, so you may have to hunt a little ... someone who's at a gnome computer should be able to give you more concise directions.
 
With regards to your printer, first off is it a parallel-port printer, or a USB printer?  This may make a difference.  Under most circumstances, printers are recognized pretty much immediately if they are plugged in (and possibly turned on).
 
As for a PPD file, this I don't know off hand, but perhaps if you do a search of this forum for PPD file, you may find something of use.
 
I hope this helps a little.  I'll keep an eye on this thread and maybe check it when I get home from work tonight and I can give you more precise directions.
 
Now, as far as using the command line - it's actually easier than you think, and you'll likely be a command-line-interface (CLI) pro in no time.  Here's the basics (assuming you are in Gnome.  If you use KDE, this may be slightly different).
 
First, open your favorite terminal program.  For example:  Applications>Accessories>Terminal.
 
There you can type commands.  Most commands that affect your system (such as installing programs) will start with "sudo".  Here's an example:
 
```

sudo apt-get remove gnopernicus

```
 
This will UNINSTALL the program.  **Apt-get** is a program that allows you to administer the programs that are installed on your comptuer.  For example, if you come across a program you want ... say the K3B CD burning program (which was built for KDE but works beautifully in Gnome), you could do one of the following:
 
```
sudo apt-get install k3b
 
**OR**
 
sudo aptitude install k3b

```
 
aptitude is roughly the same thing as apt-get, but it handles "dependencies" slightly differently and may make uninstallation later somewhat easier or more complete (I have to read up on that one of these days actually).
 
Anyhoo ... that should get you started.  The beauty of using the CLI is that it is incredibly fast and usually painless.  No hunting for buttons or for checkboxes.  You just type in the command and it does it.  Fast.
 
Now, JUST about every program can be STARTED with the command line too (though it will require that the terminal window stay open until you are done with the program).  For example, you could try this:
 
```

gedit

```
 
which would start the gnome text-editor, which is handy if you can't find the icon for it.
 
Also, you can kill processes this way too.  For example:
 
```

killall gnopernicus

```
 
and as long as you spell everything right, you'd kill the program pretty much instantly.
 
There you are ... now you are dangerous hahaha.  Don't break anything!  Good luck.

---

