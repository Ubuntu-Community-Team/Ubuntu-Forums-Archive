---
title: "can't get simple bash script working"
date: 2009-02-04
forum: General Help
---

### Post by ray field on 2009-02-04
I'm trying to put together the simplest of bash scripts to insert a text file into the system clipboard using xsel.

	xsel --clipboard < /home/public/clipxy 

works just fine.

however, when I try to run it in a bash script called clipfromxy.sh located in /.gnome2/nautilus-scripts

	#!/bin/sh
	xsel --clipboard < /home/public/clipxy 

nothing happens.  other shell scripts from that directory work just fine.  what am I missing?

---

### Post by ray field on 2009-02-04
I should add, I've chmod 777'd the file, and other scripts in the nautilus-scripts directory work just fine.

---

### Post by mixmaster on 2009-02-04
A shot in the dark ...

/bin/sh points to dash, not bash.  There are some incompatibilities.

Try it with 
#!/bin/bash 
as the first line and see if it makes any difference.

---

### Post by Barriehie on 2009-02-04
> **ray field said:**
> I'm trying to put together the simplest of bash scripts to insert a text file into the system clipboard using xsel.

    xsel --clipboard < /home/public/clipxy 

works just fine.

however, when I try to run it in a bash script called clipfromxy.sh located in /.gnome2/nautilus-scripts

    #!/bin/sh
    xsel --clipboard < /home/public/clipxy 

nothing happens.  other shell scripts from that directory work just fine.  what am I missing?

Hmm, I start my bash scripts off like this, might make a difference.
[php]
#!/bin/bash
[/php]Barrie

---

### Post by ray field on 2009-02-04
> **mixmaster said:**
> A shot in the dark ...

/bin/sh points to dash, not bash.  There are some incompatibilities.

Try it with 
#!/bin/bash 
as the first line and see if it makes any difference.

nope!?

running it from Midnight Commander in an xterm window gives

[1]+  Stopped                 clipfromxy.sh

---

### Post by Slim Odds on 2009-02-04
Redirect the output to a file and see if it's telling you what the problem is.

---

### Post by sedawk on 2009-02-04
In the script add a line "env" to list all environment variables defined.
Compare that list to the one you get when running "env" from command
line.

My (wild) guess is that  "DISPLAY" is not defined, so xsel cannot
run properly.

---

### Post by Slim Odds on 2009-02-04
> **sedawk said:**
> In the script add a line "env" to list all environment variables defined.
Compare that list to the one you get when running "env" from command
line.

My (wild) guess is that  "DISPLAY" is not defined, so xsel cannot
run properly.

Which xsel will tell you if you redirect the output and look at it.

---

### Post by ray field on 2009-02-04
> **Slim Odds said:**
> Redirect the output to a file and see if it's telling you what the problem is.


newbish here.

when I run 

    clipfromxy.sh > hal

the script terminates, and I wind up with an empty file named hal.

---

### Post by ray field on 2009-02-04
stranger still:

  sudo clipfromxy.sh > hal
  ...
  sudo: clipfromxy.sh: command not found

ls lists it in the very same directory.

---

### Post by Slim Odds on 2009-02-04
> **ray field said:**
> stranger still:

  sudo clipfromxy.sh > hal
  ...
  sudo: clipfromxy.sh: command not found

ls lists it in the very same directory.

Try:```
sudo ./clipfromxy.sh > hal
```

---

### Post by ray field on 2009-02-04
> **Slim Odds said:**
> Try:```
sudo ./clipfromxy.sh > hal
```

here are the contents of hal:

```
sudo ./clipfromxy.sh > hal
```

???

and once again, the contents of /home/raphael/.gnome2/nautilus-scripts/clipfromxy.sh:

```
#!/bin/bash
xsel --clipboard < /home/public/clipxy 
```

---

### Post by Slim Odds on 2009-02-04
> **ray field said:**
> here are the contents of hal:

```
sudo ./clipfromxy.sh > hal
```???

and once again, the contents of /home/raphael/.gnome2/nautilus-scripts/clipfromxy.sh:

```
#!/bin/bash
xsel --clipboard < /home/public/clipxy 
```

What do you think should happen?
What happens?

---

### Post by ray field on 2009-02-05
okay, here is where I am after a good night's sleep and a reboot or three: if I'm in Midnight Commander and I select clipfromxy.sh and press enter, the terminal window opens up with clipfromxy.sh

```
./clipfromxy.sh
```

the command executes and returns to a blank prompt.  

a subsequent paste shows that xsel has successfully read the contents of the file into the clipboard.  which is great!

however, when I select clipfromxy.sh from the desktop popup, nothing happens.  for that matter, if I'm in Nautilus and I click on the script, nothing happens.

here is the output of the script with env:

```
SUDO_GID=1000
USER=root
HOME=/home/raphael
SUDO_UID=1000
LOGNAME=root
USERNAME=root
TERM=xterm
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
DISPLAY=:0.0
LANG=en_US.UTF-8
XAUTHORITY=/home/raphael/.Xauthority
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
SUDO_COMMAND=./clipfromxy.sh
SHELL=/bin/bash
SUDO_USER=raphael
PWD=/home/raphael/.gnome2/nautilus-scripts


clipfromxy.sh
```

what do I need to do to be able to run this script from the desktop popup?

---

### Post by Slim Odds on 2009-02-05
Now I'm starting to understand.

the xterm clipboard is not the same as the clipboard used by GNOME.

You might want to do some research. I'm not all that familiar with the topic.

Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=8868](http://ubuntuforums.org/showthread.php?t=8868)

---

