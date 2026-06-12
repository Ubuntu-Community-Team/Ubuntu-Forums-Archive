---
title: "Auto-change terminal background color everytime connected to ssh"
date: 2008-12-08
forum: General Help
---

### Post by Tje on 2008-12-08
Hi All,

Is it possible to automatically change terminal background color every time we connected to ssh.

For example:
1. Open terminal, it will be our default background color, black for instance
2. then do $ssh [email]admin@host.com[/email]
3. Then automatically change to "white" background for host.com and "yellow" for host2.com, for instance.


Thanks in advance !!

---

### Post by jfanaian on 2009-06-09
This would be very useful, if anyone has any idea please share :)

---

### Post by francis.pilon on 2010-03-29
I am also looking for a answer to this!

---

### Post by dearingj on 2010-03-29
I just wrote a simple bash script that could be used to do this:
```
#!/bin/bash
if [ "$1" = "host1.com" ]; then
	setterm -term linux -back blue -fore white
else
	if [ "$1" = "host2.com" ]; then
		setterm -term linux -back black -fore white
	fi
fi
ssh "$1"

```

Just save it as a text file somewhere in your PATH (I used /home/username/bin/my-ssh.sh), mark it as executable, and remember to use it instead of ssh.

---

### Post by HermanAB on 2010-03-29
Hmm, what you got to do is change the configuration file of the terminal program immediately before you start it up using a launcher script.  If you would use lxterminal, then you could rewrite file ~./config/lxterminal/lxterminal.conf:

```

[general]
fontname=Monospace 10
selchars=-A-Za-z0-9,./?%&#:_
bgcolor=#000000
fgcolor=#aaaaaa
tabpos=top
scrollback=1000
```

It is fairly obvious.  

If you use gnome-terminal, then you got to dig in whatever gnome stores its data in and it is gnown to be gnot very friendly...

I hope that gives you some ideas!

---

### Post by nothingspecial on 2010-03-29
> **HermanAB said:**
>   

If you use gnome-terminal, then you got to dig in whatever gnome stores its data in and it is gnown to be gnot very friendly...


I`m finding that right gnow! haha

This would be incredibly useful though. I`m forever rebooting (or whatever) my server when I mean my laptop/netbook.

---

### Post by IanBlanes on 2010-11-01
I had been looking for something like this for a while, and since I couldn't fine any tool that suited my needs I made this one: [http://deic.uab.cat/~iblanes/colorize-0.1-src.tar.gz]("http://deic.uab.cat/%7Eiblanes/colorize-0.1-src.tar.gz"). It's a command that wraps another command in a pseudo-tty and translates the colors of its output so that default background and foreground colors are changed but other colors are preserved.

Here is an screenshot:
[IMG]http://deic.uab.cat/%7Eiblanes/colorize-example-small.png[/IMG]

I've been using it without trouble for a while with "alias ssh='colorize -- ssh'". There is an issue with the background color of lines already colorized and terminal width growing, but that seems to be the price to pay to have scroll back. Apart from that, feedback is welcome.

---

### Post by srigelsford on 2010-12-15
I created several profiles in gnome-terminal with the settings I wanted, then created aliases like the below example to ssh to ares.
The Ares profile has a red background.

alias -p ares='gnome-terminal --window-with-profile=Ares -x bash -c "ssh ares"; exit'

The pitfall of this is that it cannot be done in your existing terminal window, it launches another. My alias closes the existing one after launching the new one, but you can stop that by removing the ; exit from the end.

Just create as many profiles as you like, and associate each server to a profile in an alias. To launch just type the name of the alias
$ares

Sam.

---

### Post by guymauve on 2011-03-23
I needed to remove the -p in the line below :

> alias [COLOR="Red"]-p[/COLOR] ares='gnome-terminal --window-with-profile=Ares -x bash -c "ssh ares"; exit'


There is also a other way that works too and you can use Gnome Do to start your term with it...

Details :
You have to define a new profil into gnome-terminal then use this name in Gnome Do to start you term with this profil... When typing this name Gnome Do should reconize it as Terminal profile...

The goodies come in profile definition there is a tab called Title and command... Set the options available as follow :

check all the box under Command + write your command into the frame beside Personnal command. For example : ssh user@hostname

Then you are good to go... When start your term with your new profile name with Gnome Do your personnal command will be executed at startup. You can also make the title of the term to be replaced after the command executed and make the terminal closing when exit command is sent to the term. Like this you are sure that the term with wrong color will not be available for you on your own (or local) machine... Offcoarse it will be available if the initial command failed and you not exiting the term.

Everything should be obvious anyway... It works at least with 10.04. But I am pretty sure this tab is there since a wild

Please forgive my poor english

Goodluck

Guymauve ;-)

---

