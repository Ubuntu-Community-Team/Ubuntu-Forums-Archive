---
title: "Start X app from terminal"
date: 2009-03-23
forum: Desktop Environments
---

### Post by jnusa on 2009-03-23
Hey

I have an Ubuntu machine hooked up as a HTPC with Boxee installed. I manage the system via putty from a windows machine and often i see the need to start an X application on the tv from the putty ssh session - is this possible?

Scenario:  Boxee crashes - too lazy to start x11vnc and just want to redeploy from terminal :)

---

### Post by Bachstelze on 2009-03-23
For example

```
DISPLAY=":1.0" filezilla&
```

The value you have to set the DISPLAY variable to might differ. Fire an xterm and do [font="monospace"]echo $DISPLAY[/font] to find out what it is.

---

### Post by jnusa on 2009-03-23
Excellent! Just need to be the same user as logged into the X server. Thanks!

---

### Post by rolandrock on 2009-03-23
It is worth noting that starting apps remotely that depend on display configurations can be problematic (e.g., try running glxinfo on a remote terminal).  

I have a simple script that starts vlc with ncurses interface in a screen session so I can line up films from my netbook to play on my telly without getting off my shiny metal ****.  If I ssh to my main computer and run the script, it fails:

> paul@eeepc:~$ ssh newpc.local
[email]paul@newpc.local[/email]'s password: 
Linux newpc 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64

paul@newpc:~$ vlc_rem

malloc: ../bash/dispose_cmd.c:241: assertion botched
free: called with unallocated block argument
Aborting...Aborted


But if I fire it up from inside a screen session, it is fine.  Thought I would share that.  BTW, here is a version of that script designed to run at startup (polls for automounting of nas to keep vlc happy) if anyone is interested.  Curiously, when starting screen like this from inside screen, it does not complain - presumably because the vlc screen session starts detached (-d) - screen really is a work of true genius.

> export DISPLAY=:0.1
browse='/home/paul/gvfs/public on wdstorage.local/Videos'
wait=5
maxtry=5
x=0
while [ $x -lt $maxtry ] ; do
  if [ -d "$browse" ] ; then
    ps -ef |grep -v grep |grep -q VLC || \
    screen -S VLC -d -m vlc -Incurses --browse-dir="$browse" -f >> ~/.xsession-errors
    x=$maxtry
  else
    sleep $wait
    x=`expr $x + 1`
  fi
done


---

