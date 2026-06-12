---
title: "[SOLVED] Trouble installing CountDown game"
date: 2008-03-08
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-08
[B][COLOR="Navy"]Hi ,
please help.
I have downloaded the countdown tv game for Linux.

Here are readme file contents[/COLOR]:[/B]

XCountdown - X version of the popular Channel 4 quiz show, for 2 players.

To configure:
	edit config.h - you will need to change this

To build:
	xmkmf
	make Makefiles
	make

[B][COLOR="Navy"]I have got to here. I did the above three commands in the terminal. I checked for the executable in src directory, it is there.
I have copied the OSPD_2-9.gz and xcountdown.xpm.gz files to the /usr/local/lib/ directory (I needed to login as root to do that). I presume the below instructions mean just to copy the individual .gz files and not the whole src directory of the game. Also I left them as .gz - is there a need to extract them?
The executable instill wont start. Also below it says ' executable with one argument ' - what does this mean?[/COLOR][/B]

There are two directories of source code. The first to be built is part of
Xc, the Control Panel Widget Set, v 1.3, copyright 1992 by Paul D.
Johnston.  The second is the main XCountdown code. This also contains the
CircPerc widget from the Free Widget Foundation, and an OS dependant
implementation of usleep(), if you need it, copyright 1991 by Patrick J.
Naighton.

If all goes well, you should have a executable xcountdown in the src/
directory. Most problems should be fixable by editing the Imakefile in the
appropriate directory. Copy the dictionary, src/OSPD_2-9.gz, to the location
you defined in config.h, and same for the logo, src/xcountdown.xpm.gz, and
then run the executable with one argument - the display of the second player.
Run it without any arguments for a short explanation.

NOTE: For the number round you need the bc command (basic calculator). This
must be pointed to by your $PATH variable. It is often in /usr/bin/bc.

Full help, and rules of the game, are available from within the program,
in the Extras menu.

**[COLOR="Navy"][COLOR="Navy"]If anyone out there has this working please explain in  a step by step(and clear)[/COLOR] way.[/COLOR]**
**[COLOR="DarkGreen"]It is so frustrating getting this to work.[/COLOR]**

---

### Post by Rytron on 2008-06-09
I'll settle for this online version instead.

[http://www.kountdown.co.uk/text/index.php]("http://www.kountdown.co.uk/text/index.php")

---

