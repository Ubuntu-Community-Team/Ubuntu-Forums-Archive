---
title: "Custom bash shells..."
date: 2022-12-22
forum: Desktop Environments
---

### Post by dbee on 2022-12-22
I want to create two bash custom command line shells...

Shell 1: Localhost

Background color: white
Text Color: black
Prompt: localhost>

Shell 2: Webhost

Background color: black
Text Color: white
Prompt: webhost>

I need to access both these cmd lines from local desktop. Webhost is my server on hostinger. 

How do i create two different profiles in the one X-window on my desktop? 

How do i access those two shells easily?

How do i open them automatically?

---

### Post by ActionParsnip on 2022-12-22
You can set text colours with the PS1 shell value. You can set the background colour in the saved session (in PuTTY for example).

---

### Post by TheFu on 2022-12-22
Google "ABSG bash" for how to create bash scripts.  Don't let the name bother you.  It is for beginners too.

X/Windows stuff depends on your specific setup.  More and more systems are running Wayland, not X/Windows, so I suspect completely different methods are needed for that.  
```
$ inxi -Gz
```
should be able to provide sufficient details about the graphical environment for someone knowledgeable to guess.

How run any program at login is also specific to the environment.  Different WMs and different DEs handle it differently.

bash is a program (shell), running inside a terminal.  There are 30+ different terminals, so how to invoke each and what the allowed options are different for each.  I use "xterm"s, and I'm happy to show how I open those to specific places with specific colors for letters and background, but you'll need to read the manpage for your terminal of pain/choice to figure out which options it supports.  Many of the fancier terminals have terrible manpages, so the available options may not be specified or may vaguely point to some toolkit's standard options, like Qt or GTK+.   Some program teams also might prefer the 'info' format, that the GNU people won't drop even though it is clear they lost that contest.

Anyways, here's a few lines from my initial GUI startup script:
```
#!/bin/bash

XTERM_OPTS="-u8 -fs 12 -fa Monospace -sb -fg green -bg black"
/usr/bin/xterm  $XTERM_OPTS -geometry 78x9+78+0 &
/usr/bin/xterm  -geometry 80x25-23+199 $XTERM_OPTS -e ssh -X istar &

```
That should be sufficient for you to figure out what's possible.

Where

a) istar is known via local DNS

b) ssh-keys have been exchanged from the current host to istar.  The first time the ssh keys are used in a login, they must be unlocked.  How long that unlock lasts is controlled by ssh-agent on my systems. Others might use different methods like a "key store".  I've never used those after deciding they weren't what I wanted.

c) If you don't have DNS, you can use the IP address or setup a ~/.ssh/config stanza for each host. All ssh-based tools will honor these settings. If you need multiple, but different connections, into the same remote system, use a different stanza with a unique name.  The manpage for ssh_config spells out the possible settings, but usually, sometime like:
```
host spam1
  user joe43209
  hostname 192.168.55.65
  port 20022

```
is sufficient.
By saying "ssh spam1", the command for any ssh-based tools, will automatically user the different username, IP address, and non-standard port, to make connections.  No more trying to remember if -p or -P are used for each command like ssh, sftp, scp, rsync, x2go, freenx, sshfs, and about 50 other tools.

Hope this is helpful.

---

### Post by dbee on 2022-12-25
thanks

---

### Post by ActionParsnip on 2022-12-25
Well, yeah it's going to open all those terminals. Think about it.
The terminal launches and the shell reads the config file and runs the commands. You have two which say "run xterm" so they are ran, the file is ran again and in these two new terminals..... Run xterm twice. So in those 4 new xterms the config files are read again and 2 xterms are spawned in each terminal.... And so on.

Its a fork bomb.

---

