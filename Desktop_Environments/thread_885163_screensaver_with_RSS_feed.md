---
title: "screensaver with RSS feed"
date: 2008-08-09
forum: Desktop Environments
---

### Post by allankelly on 2008-08-09
Hi, I've seen various chat about configuring a text screen saver with a live RSS feed. This is a HOWTO for a clean install of Hardy.

1. Install xscreensaver. You are NOT going to execute it but you need the components.

2. Edit ~/.xscreensaver. In the section for textProgram, change it as below:
```
textProgram:	xscreensaver-text --url http://rss.slashdot.org/Slashdot/slashdot
```
Obviously that's the slashdot RSS feed, use any URL you want.
What this does is to configure the xscreensaver-text program to return the plaintext of the specified URL.
xscreensaver-text is the default text source for these screensavers.

3. Select Phosphor or fliptext as your screensaver via Gnome screensaver. (Note that unfortunately xscreensaver also installs a System->Preferences->Screensaver link with the same icon. You have to find the Gnome one!)

4. To adjust the behaviour of the screensavers phosphor or fliptext, alter the /usr/share/applications/screensavers/fliptext.desktop or /usr/share/applications/screensavers/phosphor.desktop file setting Exec=
The settings I find useful are:
fliptext.desktop:
```
Exec=fliptext -root -fps -delay 5000 -speed 4.0 -lines 16
```
phosphor.desktop:
```
Exec=phosphor -root -delay 30000 -scale 4
```

Hope that's of assistance.

Cheers, al.

---

### Post by allankelly on 2008-08-10
Folks, in addition to the instructions above:

You need to install xscreensavers extra packages to get phosphor and fliptext.

You need to execute xscreensaver once from the commandline (or from the xscreensaver config window) to get a copy of ~/.xscreensaver

As well as changing the textProgram: line in .xscreensaver you need to change the textMode: line:

```
textMode:       program
textProgram:    xscreensaver-text --url http://rss.slashdot.org/Slashdot/slashdot
```

Should work now!

Cheers, al.

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by krokosjablik on 2008-10-02
Thank you very much, it works!

The problem is only if there is a proxy...

xscreensaver-text expects HTTP_PROXY environment variable to be setted. 
I have tried to set this variable local (~/.profile), system wide (/etc/profile) and for the X-Server (created /etc/X11/Xsession.d/90environment). But it didn't work for me...

The only solution I actually have is to write a wrapper shell script (xscreensaver-url.sh):
```
#!/bin/sh

if [ $2 ]; then
	export HTTP_PROXY=$2
fi

if [ $1 ]; then
	xscreensaver-text --url $1
else
	echo "An URL must be specified!"
	echo "    For example:  xscreensaver-url.sh http://fridge.ubuntu.com/node/feed"
	echo "    With a proxy: xscreensaver-url.sh http://fridge.ubuntu.com/node/feed proxy:3128"
fi
```

copy this script into a PATH directory (for example /usr/local/bin) and use this one in the ~/.xscreensaver:
```
textProgram:	xscreensaver-url.sh http://fridge.ubuntu.com/node/feed proxy:3128
```

---

