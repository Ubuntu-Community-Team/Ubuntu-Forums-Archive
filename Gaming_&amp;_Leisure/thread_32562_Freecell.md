---
title: "Freecell"
date: 2005-05-08
forum: Gaming &amp; Leisure
---

### Post by lmellen on 2005-05-08
:? Is freecell available to Kubuntu users. I do a "aptitude search freecell" and I get:

"p   freecell-solver-bin                            - Library for solving Freecell games"
"p   libfreecell-solver-dev                       - Library for solving Freecell games (Development files)"
"p   libfreecell-solver0                            - Library for solving Freecell games"
"p   vdr-plugin-freecell                            - Plugin to vdr that implements the card game "Freecell"

If I install the above will that give me freecell?
                                                                         Thanks -- Larry :)

---

### Post by JonahRowley on 2005-05-08
**Pysol** is an amazing solitaire game for Linux.  It has a million features, a million games, I haven't found anything else quite like it.

---

### Post by Marquis_de_Carabas on 2005-05-08
Ace-of-penguins has a Freecell game (along with seven other games - Minesweeper, Solitaire, Taipei etc.). It's not as pretty as Windows Freecell and it doesn't have the stats or anything, but it's cool nonetheless.

With Synaptic (Kynaptic? I don't use KDE) it's sometimes worth searching "Name and description" Just searching in the name misses out any programs which have "This Freecell-like game" or "This program consists of Freecell, Solitaire and..." in the description.

On second thoughts, I just took JonahRowley's advice and tried PySol. Great program, I'm sure you won't be disappointed.

---

### Post by lmellen on 2005-05-09
](*,) Gentlemen, I tried to install pysol, it removed all my kde games, and now it just sits in a usr/games folder. I'm running Kubuntu, do I need gnome? What is going on?? Thanks -- Larry

---

### Post by Marquis_de_Carabas on 2005-05-09
[QUOTE=lmellen]](*,) Gentlemen, I tried to install pysol, it removed all my kde games, and now it just sits in a usr/games folder. I'm running Kubuntu, do I need gnome? What is going on?? Thanks -- Larry[/QUOTE]

If you open a terminal and type "pysol" does it run? Not all programs will create menu items unfortunately, you have to do that bit yourself. I don't use KDE, as I said, but a quick Google turned up [this page](http://home.fnal.gov/~dawson/howto/kde/index.html) which has sections on "Adding items to the menu" and "Adding items to the panel".

---

### Post by lmellen on 2005-05-09
[QUOTE=Marquis_de_Carabas]If you open a terminal and type "pysol" does it run? Not all programs will create menu items unfortunately, you have to do that bit yourself. I don't use KDE, as I said, but a quick Google turned up [this page](http://home.fnal.gov/~dawson/howto/kde/index.html) which has sections on "Adding items to the menu" and "Adding items to the panel".[/QUOTE]

 :smile: Thanks Marquis_de_Carabas, I didnt know it ran from terminal.
 Do you know how to fix the sound. I get this error message:
                                         "PySol: pysolsoundserver module not found, sound disabled."

I still would like to know why installing pysol would remove my kde games??
Pysol creators wouldn't do that intentionally would they??
I can fix it, but I'll have to use aptitude install to do it! 
           Thanks for the reply -- Larry

---

### Post by Marquis_de_Carabas on 2005-05-10
[QUOTE=lmellen]:smile: Thanks Marquis_de_Carabas, I didnt know it ran from terminal.
 Do you know how to fix the sound. I get this error message:
                                         "PySol: pysolsoundserver module not found, sound disabled."

I still would like to know why installing pysol would remove my kde games??
Pysol creators wouldn't do that intentionally would they??
I can fix it, but I'll have to use aptitude install to do it! 
           Thanks for the reply -- Larry[/QUOTE]

You don't *have* to run it from a terminal, you can add an item to your menu yourself.

With regards to your KDE games, are they definitely removed? Not just the menu items? Have a look in /usr/games. I don't see how installing Pysol could have actually removed other programs, but I guess it's possible it messed up the menu somehow. If you use Kynaptic and mark the KDE games package for (re)installation then it should solve the problem, although I'm sure you'd like to know how and why it happened in the first place!

Also, you might want to look at Kpat. I've never used it but it's a specifically KDE program and includes a version of Freecell.

Good luck!

---

### Post by Anonii on 2007-02-06
I'm reviving this dead thread to ask which game of FreeCell is that normal solitaire game installed by default in Windows.

---

### Post by Marquis_de_Carabas on 2007-02-06
> **Anonii said:**
> I'm reviving this dead thread to ask which game of FreeCell is that normal solitaire game installed by default in Windows.

Klondike, I believe. Although technically it's not a version of Freecell, rather Freecell is another version of Solitaire. (Forgive me for being anal, I can't help it)

---

### Post by frog3764 on 2007-02-25
Greetings to the Group - I found the Freecell and solitare games I like in the KPatience program.  I found it in the Freespire site.  It's KDE.  So, now can someone tell me in detail as I'm a newbie/dummy how to get it and install it in my Ubuntu?  The are much better than the Aisleriot?  group.  All help will be appreciated.

The Frog

---

### Post by tubasoldier on 2007-02-25
I used to use PySol before I found KPatience. I like KPatience much more.

---

### Post by frog3764 on 2007-02-25
I am trying to find out how to get it and install it to my Ubuntu OS.  I am a newbie/dummy to Linux so I need a step by step.

Frog

---

### Post by tubasoldier on 2007-02-25
```
sudo apt-get install kpat
```

---

### Post by frog3764 on 2007-02-25
So I need to find Sudo, then what?  I need some help here.  What is the rest of the  apt-get install kpat?  What do I do with this?

---

### Post by tubasoldier on 2007-02-25
open a terminal. It is under acessories in the startup menu. That is where you type in that exact phrase. it will ask for a password. You put in your admin password that you input when you installed the OS and then it will install the program for you along with any dependencies you need.

---

### Post by frog3764 on 2007-02-26
OK Great!  Then do I need to download the Kpat Solitare game and install it?
I can't get past the $.  It doesn't like my name or password I use to log-in.  Now what?

---

### Post by tubasoldier on 2007-02-26
you don't need to log-in to anything. just type in the code exactly like this:
```
sudo apt-get intstall kpat
```

Then it will ask for your password. And after you give it the correct password, (the one that you put in as the admin user in the install) then it will install it all for you automatically. It is really that simple.

---

### Post by frog3764 on 2007-02-26
Hey tubasoldier - It took a few times as I kept getting a invalid command, but it finally worked and I have the games.  Thanks for your patience and help.

Frog

---

### Post by tubasoldier on 2007-02-26
no problem. 

Just for future reference: Whenever you see a little grey box with the word "code" above it then it means you should input that into your terminal.

---

### Post by Marquis_de_Carabas on 2007-02-26
Hey Frog, for future reference you can also use the Add/Remove Programs ([See here for info]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/gnome-app-install.html")) or Synaptic ([Info here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/synaptic.html")) to install programs rather than using the terminal. It does the same thing, just in a nicer looking way :)

---

### Post by go_beep_yourself on 2010-04-04
I'm not having any sound from KPatience. Is it not supposed to have any sound? Is anybody else getting sound from it?

---

