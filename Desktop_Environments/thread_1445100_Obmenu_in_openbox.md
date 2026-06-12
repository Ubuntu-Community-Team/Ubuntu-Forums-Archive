---
title: "Obmenu in openbox :?"
date: 2010-04-02
forum: Desktop Environments
---

### Post by Fxy on 2010-04-02
Hi

I just recently installed obmenu inside openbox...  What i am trying to do is to show my applications in a menu, like whats in xfce...  Can anyone tell me the execute command that i would need to make this happen, or if not could you let me know on what i have to do before i can accomplish this...

Thanks in advanced ;)

---

### Post by burton247 on 2010-04-02
Im not 100% sure what your question was asking. Openbox menus are written in XML i believe. You have to create the structure of your menu yourself, either editing the XML or, as you have, using the GUI tool - obmenu. The tool itself is rather self explanatory to use i thought.

---

### Post by Jose Catre-Vandis on 2010-04-02
Open a terminal, type obmenu

Is that what you meant?

---

### Post by Fxy on 2010-04-02
Actually i know how to open and run obmenu [not stupid lol]...

I was talking about using obmenu to show my applications on/in the menu.  I have my button in the menu and all i need is the execute command so that my applications will appear on/in the menu under applications... 

You know the one like which is on the xfce menu :?  When you right click then applications is at the botton...

From what i have learnt to get things to show you create an item on the menu & then add its execute command in the execute command box given...

All i am looking for is the command that i can put in the execute command box :?

---

### Post by urukrama on 2010-04-02
You can use menumaker to automatically create a menu with all your installed applications. 

[Download the source code]("http://sourceforge.net/projects/menumaker"), unpack the archive and move into the extracted directory with the terminal

	tar xzvf menumaker-0.99.7.tar.gz
	cd menumaker*

You can install Menumaker with the usual commands (./configure, make and sudo checkinstall), but you can also run it without installing with the following command:

	./mmaker OpenBox3

(Note that Menumaker will not overwrite existing menu.xml files. If you have already changed your menu.xml file, you&#8217;ll need to back it up, remove it, and then add the changes to the new menu.xml file Menumaker created, or force Menumaker to overwrite any existing file with the -f flag (./mmaker -f OpenBox3).

You could also use the Debian menu in Openbox. To do so follow the instructions found [here]("http://icculus.org/openbox/index.php/Help:Menus#The_Debian_menu").

---

### Post by Jose Catre-Vandis on 2010-04-03
> **Fxy said:**
> Actually i know how to open and run obmenu [not stupid lol]...

All i am looking for is the command that i can put in the execute command box :?

OK, know where we are going now ;)

As urukrama says, menumaker will pull together all your applications, but you may wish to have a more discrete list, in which case you have to build one at a time.

When you open obmenu, it offers you the choice of adding a new menu or new item. The new menu will give you a sub menu in the right click list, so you could create one called "Applications". you can then create new items in this new sub menu clicking on the new item button. In the lower half of the obmenu window, add the name you want to appear, and the command line instruction to run the application. Click on the save button and test. Repeat ad-infinitum ;) The commands you can give can be quite complex and you can add arguments you might want. You won't get icons in the menu!

For example

In the name box:    Firefox
In the action box:  Execute
In the command box: /usr/bin/firefox  (or very often the app name will suffice)

Hope this helps

---

### Post by kerry_s on 2010-04-03
do you have "menu" installed? (sudo apt-get install menu)
if so run:> sudo update-menus

---

### Post by Jose Catre-Vandis on 2010-04-03
> **kerry_s said:**
> do you have "menu" installed? (sudo apt-get install menu)
if so run:> sudo update-menus

Does that work in Openbox Kerry_S ? - if so must try.....

---

### Post by Fxy on 2010-04-03
Thank you all for your replies :D

I have never heard of menumaker, sooo ill have to go give that a try right away...  Sounds very promising for what i want to accomplish...  Also have to take a look at that menu noted by Kerry_S, sounds like another thing worth taking a look at ;)...

Ill go try these stuff now and post my finds when im done :p

---

### Post by eriqjaffe on 2010-04-03
I'm using [obmenugen]("http://sourceforge.net/projects/obmenugen/") to dynamically create my menus in Openbox.  Just make sure it's executable and put it somewhere in your path (I put it in /usr/local/bin).  In your autostart.sh, just add "obmenugen -p &" somewhere in there, and you should have a dynamically updating pipe menu.

The only trouble I ran into was that the menu is empty if there are any broken symlinks in /usr/share/applications, but that was fairly easy to deal with once I knew what was happening.

---

### Post by kerry_s on 2010-04-03
> **Jose Catre-Vandis said:**
> Does that work in Openbox Kerry_S ? - if so must try.....

i guess not any more, i just tried it on mine & it didn't work, but i'm running lubuntu which uses openbox & tried with the right click menu on, then i got stuck with it, had to drop to command line to turn it back off. :lolflag:

---

### Post by Jose Catre-Vandis on 2010-04-03
> **eriqjaffe said:**
> I'm using [obmenugen]("http://sourceforge.net/projects/obmenugen/") to dynamically create my menus in Openbox.  Just make sure it's executable and put it somewhere in your path (I put it in /usr/local/bin).  In your autostart.sh, just add "obmenugen -p &" somewhere in there, and you should have a dynamically updating pipe menu.

The only trouble I ran into was that the menu is empty if there are any broken symlinks in /usr/share/applications, but that was fairly easy to deal with once I knew what was happening.

Looks like a good 'un if you want everything :)

---

### Post by rfithen on 2011-11-29
> **eriqjaffe said:**
> I'm using [obmenugen]("http://sourceforge.net/projects/obmenugen/") to dynamically create my menus in Openbox.  Just make sure it's executable and put it somewhere in your path (I put it in /usr/local/bin).  In your autostart.sh, just add "obmenugen -p &" somewhere in there, and you should have a dynamically updating pipe menu.

The only trouble I ran into was that the menu is empty if there are any broken symlinks in /usr/share/applications, but that was fairly easy to deal with once I knew what was happening.

This is the kinda stuff drives me nuts. Hey obox devs, get your heads out of the sand, you think users might want programs to appear in a menu somewhere when they install an app? This is why windows will always carry the market share!

---

### Post by qkzoo on 2012-01-08
I've tried installing menumaker, and now I'm just pulling my hair out.

I think I compiled it correctly, and run ./mmaker -f OpenBox3 and get:

```

andrew@andrew-HP-Mini-110-3000:~$ mmaker OpenBox3
  no terminal emulator specified; will use the default
no suitable terminal emulator found
andrew@andrew-HP-Mini-110-3000:~$ 

```

What am I supposed to do now?  I right click on my OB desktop and still don't have a menu like I thought menumaker would generate.  I must be missing something...?  Any help?

Q

---

### Post by qkzoo on 2012-01-09
Solved this issue on my own.  For those in my situation, I am using Lubuntu, and it comes with lxterminal or something like that.  Menumaker requires one of a few popular terminal programs to function properly.  I did this:

```

sudo apt-get install lxterm

```

...then...

```

mmaker -vft Xterm OpenBox3

```

Xterm is the terminal I downloaded.  The documentation for MenuMaker tells you which ones are allowed.  OpenBox3 is my WM now.

:D

---

