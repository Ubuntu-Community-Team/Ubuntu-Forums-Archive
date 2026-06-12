---
title: "Lives Video Editor Hangs on Startup"
date: 2006-08-22
forum: Desktop Environments
---

### Post by mister_p_1998 on 2006-08-22
Hi guys,
Im trying to install Lives video editor, which installs ok, but hangs on startup. The Website says, if it does this you should do the following:
edit ~/.lives, and change:

<jack_opts>
0
</jack_opts>

to:

<jack_opts>
16
</jack_opts>


Then restart LiVES as normal.

Trouble is, I cant find "~/.lives" where is it?

Steve

---

### Post by Alexander Grundner on 2006-08-27
**~/** <-- Refers to your **Home directory**. And when you see **.**lives or **.**whatever, this refers to a hidden folder/settings. To see the .lives folder in the File Browser (Nautilus) just click menu item VIEW > SHOW HIDDEN FILES

BTW, I installed LiVES using the dapper repo [they setup](http://lives.sourceforge.net/index.php?do=downloads). 


> **Ubuntu dapper.** Add the following to /etc/apt/sources.list:

deb http://people.ubuntubrasil.org/~rclbelem/lives/dapper/   binary/ 

Unfortunately, I'm having the same problem as you. It doesn't want to launch.

---

### Post by mister_p_1998 on 2006-08-28
if you leaVE IT ABOUT TWO MINUTES, IT FINALLY LAUNCHES!

---

### Post by Alexander Grundner on 2006-08-28
Here's the solution I found (not pretty):
[http://ubuntuforums.org/showthread.php?t=241330](http://ubuntuforums.org/showthread.php?t=241330)
> **matty_x said:**
> 
##Run the following after starting LiVES from the command line

jackstart --driver=oss


---

### Post by Binfarteen on 2006-09-01
To get this working with alsa, I installed automake 1.9 (which installs autoconf).  It also requires gettext and gettext-devel 0.12.1+, which were already on my system.

I then added the following to /etc/apt/sources.list:

deb [http://people.ubuntubrasil.org/~rclbelem/lives/dapper/](http://people.ubuntubrasil.org/~rclbelem/lives/dapper/)   binary/

Then "apt-get update" and "apt-get install lives" 

Then "apt-get install jackd"

Then edit ~/.lives (hidden file in home folder), and change:

<jack_opts>
0
</jack_opts>

to:

<jack_opts>
16
</jack_opts>

Then prior to running, from a command prompt:

jackstart -d alsa

Took a couple seconds to load, no delay.  Sound and video both ok.

---

### Post by Tehrasha on 2006-09-09
I have altered the 'jack_opts' line in my ~/.lives file as above, and I get this in a terminal when launching LiVES.

>  # lives
LiVES 0.9.6
Copyright 2002-2006 Gabriel Finch (salsaman@xs4all.nl) and others.
LiVES comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.

[B]jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
`default' server already active[/B]


The part in bold then repeats over and over, forever.

I get this whether I start JACK with ALSA or OSS, there is no difference.

Anyone else?

---

### Post by danielph on 2006-09-14
Well I just need a video editer to chop some bits out of several mpg file. This evening I have tried to get Cinelerra, Lives, GOPchop (beware of using chopped files with dvdauthor), Diva, Jahshaka and Pitivi to work with varied success, but none of them could do the job or I couldn't find a way of getting them to do the job. I normally just use Avidemux but this seems to have a problem with AV sync with mpg files. 

OK rant over. As for your problems, well as I type I am still sitting waiting for Lives to load. The CPU is running at 100%. I pulled this down from the same repostitory. I very interested in your findings for Lives or getting any of these editors working.

---

