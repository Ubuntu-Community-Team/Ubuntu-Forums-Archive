---
title: "Setting Up Nethack"
date: 2005-12-28
forum: Gaming &amp; Leisure
---

### Post by James_Nostack on 2005-12-28
I'm having problems setting up [Nethack](http://www.nethack.org), in part because I'm an idiot when using Linux.

I unzipped the tar file into /usr/games, and now I have a Nethack shell script.  I click on it, and it gives me a text file in gedit, with code in it.

In /usr/games/lib/nethackdir there is a Nethack executable.  But when I click on it, nothing happens.

---

### Post by matthew on 2005-12-28
Hi, James,

Good news/bad news. 

The bad news is you are trying to install Nethack the hard way.

The good news is that it is in the Ubuntu repositories (universe)

First make sure you have [enabled the extra repositories]("http://www.psychocats.net/linux/sources.php")

Thenyou can install it from a terminal by typing
```
sudo apt-get install nethack
```
and run it by typing
```
nethack
```

---

### Post by Mikko Rautiainen on 2006-03-22
Thank you! I spent probably 3 hours wondering what I was doing wrong, installing Nethack.

To clear things out: I just installed Ubuntu on my laptop, and I feel so stupid sometimes trying to figure out how things are here. "This nethack.exe doesn't seem to work, what can I possibly be doing wrong", if you get my meaning. I had no idea what the guide was about (about packages and repositories) but it seemed to work. Thanks again! Now I need to get the tile-graphics to work...

One last thing. I have no idea where the nethack was installed. How can I create a shortcut to it? To the games menu or on the desktop.

---

### Post by matthew on 2006-03-22
[quote=Mikko Rautiainen]One last thing. I have no idea where the nethack was installed. How can I create a shortcut to it? To the games menu or on the desktop.[/quote]Applications->System Tools->Applications Menu Editor
This will let you create a menu item and choose where.

Nethack either installs or creates a link at /usr/games/nethack so you can use that for the link.

NOTE: There is a package called nethack-gnome that has a pretty nice graphic adaptation to the game. It uses the same game rules, etc., it just overlays it with a nicer looking display. You might enjoy it.

---

### Post by Mikko Rautiainen on 2006-03-22
Problems: 
1)want to use tiles instead of ASCII for graphics.
2)want to create a link for Nethack
( 3) Nethack-gnome doesn't start)

The game (Nethack) installed and can be run via the terminal. The link at

*usr/games/nethack*

doesn't work however, and putting it to the menu or desktop is of no use. Is it possible to have use the tile-graphics without installing nethack-gnome? Finding no solution to my problem, I then installed Nethack-gnome using

*sudo apt-get install nethack-gnome*,

a magic line that seems to install programs, and Ubuntu installed Nethack-gnome to an unknown place. I found there was a shortcut to it in 

*usr/games/nethack-gnome*, 
pointing to
*/usr/lib/games/nethack/nethack-gnome.sh*

Now Nethack-gnome won't start even from the terminal (link doesn't work). All I get is the message

[I]:~$ nethack-gnome

Gnome-ERROR **: Could not create per-user Gnome directory </home/mikko/.gnome/accels> - aborting

aborting...[/I]

Nethack.org ( [http://www.nethack.org/v343/ports/download-linux.html](http://www.nethack.org/v343/ports/download-linux.html) ) mentions the tile-file (I think it is this one) nh10.pcf, how can I set the game to use these tiles?

---

### Post by Longwing on 2006-04-15
Bestill my heart, a problem I actually know the answer to!

**First, a quick bit about apt-get from a fellow Linux noob:**
Apt-get's closest analogue in the non-Linux world would be windows update (ugh). Now mind you, I'm not trying to start a trash-on-microsoft thread, but Apt-get is so much more than Windows Update could ever be. The program connects to a bunch of databases online, these contain huge stores (called repositories) of programs. These databases don't just contain the programs themselves, but also information on where they go, and if they need anything else to run. When you type "sudo apt-get nethack-gnome", your computer connects to these databases and downloads/installs nethack, along with everything you need to run it.

**Now on to the real question, getting the darn thing to run: Here's what I managed to do.**
    1) Right-click on your "applications" menu and hit "Edit Menus".
    2) Select "Games" in the left-hand column.
    3) Hit the new entry button.
    4) Fill out the form which pops up, put in "/usr/games/nethack-gnome" into the Command section. The rest have no right answer, fill in what you want. For the icon, I chose the "rip.xpm" file from the "nethack" sub-folder (hit the icon button and browse the folder which comes up)
    5) Close the menu editor by hitting Okay until it goes away.

You'll now have nethack in your "games" menu, under applications. To put it on your desktop, right-click on it in the menu, there should be an option which says "Add this launcher to desktop". I'm running Ubuntu 5.10 and that worked for me.

---

### Post by dolny on 2006-04-15
[http://www.darkarts.co.za/projects/noegnud/](http://www.darkarts.co.za/projects/noegnud/) - anybody tried this?

---

### Post by Longwing on 2006-04-15
> [http://www.darkarts.co.za/projects/noegnud/]("http://www.darkarts.co.za/projects/noegnud/") - anybody tried this? I tried it a while back in windows, but ultimately got bored and went back to the pure text version. It's got a lot of options, particularly in the graphical-tiles department, really good for those who like LOTS of display options.

Ironically, one of my projects for the day is setting up [Vulture's Eye]("http://www.darkarts.co.za/projects/vultures/"), also from [DarkArts Studio]("http://www.darkarts.co.za/"). I've never tried Vulture's Eye, but I throughly enjoyed the (now defunct) [Falcon's Eye]("http://users.tkk.fi/%7Ejtpelto2/nethack.html") on which it's based. It gives Nethack a kind of dos-adventuregame feel, much more structured than a lot of the alternate-interfaces.

---

### Post by Mikko Rautiainen on 2006-04-18
I manage to get the shortcuts to the desktop but neither of them work.

I can run Nethack via the terminal but not from the Shortcut. Nethack-gnome doesn't start at all. Also, trying the sudo apt-get install nethack-gnome says I have the latest version.

---

### Post by Longwing on 2006-04-19
Something more at work then...

Unfortunately, I don't have a quick answer for you, and my Linux Box is currently spread across my dining room table. This makes it difficult to experiment. I'll see if I can come up with anything once I get everything rebuilt.

Based on the error you mentioned in your earlier post, it seems as though nethack doesn't have permission to mess with your home directory. Since the install was done as Root (that's what the "sudo" part of the command is for) it seems unlikely that it would be locked out.

One lazy solution would be to run it as root, just to confirm that the program itself is working. Try
```
sudo nethack-gnome
``` from a terminal, and let us know if the program can run. This will isolate wheather it's a permissions issue, or a deeper flaw in your current nethack instalation.

Please also note that I, like you, am a total noob. Doubtless a lot of guesswork will be involved here before we figure out what's happening.

---

### Post by Mikko Rautiainen on 2006-04-21
```
sudo nethack-gnome
```

tells me that *command not found*,

```
sudo apt-get install nethack-gnome
```

tells me that *nethack-gnome on jo uusin versio* which means that *nethack-gnome is already newest version* and

```
nethack-gnome
```

tells me that *Gnome-ERROR **: Could not create per-user Gnome directory </home/mikko/.gnome/accels> - aborting*.

---

### Post by The Grum on 2006-04-26
Im getting the same problem. I can run the program as root using

```
sudo /usr/games/nethack-gnome
```

The permissions for the .gnome folder are:

```
drw-rw-rw-  3 me   games  4096 2006-04-26 14:03 .gnome
```

Ive tried adding myself to the games group, but this has no effect.

---

