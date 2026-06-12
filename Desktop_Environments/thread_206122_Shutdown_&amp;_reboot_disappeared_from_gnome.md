---
title: "Shutdown &amp; reboot disappeared from gnome ?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by GoBieN on 2006-06-29
Hello everybody

I'm not sure how it happend, but shutdown & reboot is no longer an option when i click on the icon to shutdown.

See for yourself here:
[http://ares.gobien.be:8080/ubuntu/shutdown.jpg](http://ares.gobien.be:8080/ubuntu/shutdown.jpg)

Anybody know how I can resolve this ?

---

### Post by Maggot on 2006-06-29
Is the "Show Actions Menu" checked in System, Administration, Login Window?

---

### Post by GoBieN on 2006-06-29
[QUOTE=Maggot]Is the "Show Actions Menu" checked in System, Administration, Login Window?[/QUOTE]
Yes it is, I checked.

ps: Maybe important information. I'm running on gnome on XGL. 

Can choose at login (GDM), for Gnome XGL of Gnome default.

---

### Post by jonboy99 on 2006-06-29
This happened to me after installing kubuntu desktop on ubuntu, and booting into gnome.  Had to log out to gdm to shut down.  They reappeared after uninstalling kubuntu.

---

### Post by GoBieN on 2006-07-04
[QUOTE=jonboy99]This happened to me after installing kubuntu desktop on ubuntu, and booting into gnome.  Had to log out to gdm to shut down.  They reappeared after uninstalling kubuntu.[/QUOTE]
Well i don't have kubuntu installed, i just installed XGL/compiz using this thread:
[http://www.ubuntuforums.org/showthread.php?t=194993&page=1](http://www.ubuntuforums.org/showthread.php?t=194993&page=1)

---

### Post by Crosbie on 2006-07-08
I have the same problem since installing Xgl via method A on the wiki.  I seem to remember it happening when trying out Kubuntu, too, as per jonboy99.

---

### Post by Crosbie on 2006-07-09
Update for you:  I fixed my situation by switching to method B.  As long as Xgl is working for you, why not?  Be careful to add the 50sec timeout tweak as suggested in someone's note on that page.

I have a feeling it's not possible to fix it whilst using method A.

---

### Post by GoBieN on 2006-07-10
Let me clear up the situation a bit more.
I have a Gnome XGL session, and a Gnome standard session.
In the Gnome standard session, the reboot and shutdown buttons appear as normal. In the Gnome XGL session the buttons are not there, i can only choose  log out and switch user.

There must be an easy way to fix this ?

---

### Post by Dubbayoo on 2006-07-10
I have the same problem and I don't use XGL (although I may have attempted to get it working, can't recall). It comes and goes. Sometimes if I just log back in or reboot I get the icons back.

---

### Post by tturrisi on 2006-07-10
afaik, the reboot shutdown components are a part of gdm, so you must use gdm to have those choices, else use a term & type sudo reboot or sudo halt.

---

### Post by Dubbayoo on 2006-07-10
I know how to reboot and shutdown the system. I would prefer a solution to a workaround. The fact is the buttons should always be there.

---

### Post by tturrisi on 2006-07-10
> **Dubbayoo said:**
> I know how to reboot and shutdown the system. I would prefer a solution to a workaround. The fact is the buttons should always be there.
I figured as much.  But I believe that gdm must be being used for those buttons to be there.  I had a similar issue when I installed an older app that removed gdm and I lost those buttons, so I had to reinstall gdm set as the default login manager and the buttons came back.

You could create a launcher to shutdown and add it to the panel:
example:
Name: Shutdown
Generic name: Shutdown
Comment: See ya later...
Command: sudo /sbin/shutdown -h 0

You could even create launchers to shutdown, reboot & logout so that sudoers do not need to type the password:
[http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/07/linux-desktop-how-to-shutdown-restart.html](http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/07/linux-desktop-how-to-shutdown-restart.html)

---

### Post by jimmygoon on 2006-07-10
If you run gdm from a command terminal or startx or xinit (or is it initx?) from the command line when it loads I don't have the icons either. Thats why I install XGL the right way!

---

### Post by Dubbayoo on 2006-07-10
I tried and failed to get xgl working with ATI. The method I used went thru gdm anyway and I'm still using gdm now. The typical method is I boot up in the am, the icons will be missing, I will reboot or maybe even just log out/in and they'll show. AFAIK no xgl-related processes are starting normally.

---

### Post by Dubbayoo on 2006-07-11
It happened again this morning. I booted up normally into Gnome; there where no shutdown/hibernate buttons; I rebooted the system right away then had all three buttons.

---

### Post by GoBieN on 2006-07-11
You guys all talk about GDM beging used, for the buttons. But maybe its me because i'm to newb, but i do use GDM. In GDM I can choose for XGL session, so it don't get the part where you guys say i don't use GDM ?
> stan@Ubuntu-drake:~$ ps aux | grep 'gdm'
root      4691  0.0  0.2  11300  1824 ?        Ss   18:32   0:00 /usr/sbin/gdm
root      4703  0.0  0.3  11704  2668 ?        S    18:32   0:00 /usr/sbin/gdm
root      4725  0.4  1.6  21540 12836 tty7     SLs+ 18:32   0:03 /usr/bin/X :0 - br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
stan      8545  0.0  0.1   2880   812 pts/0    S+   18:43   0:00 grep gdm


---

### Post by Ratzilla on 2006-07-18
did you undo what you did in method A before doing method B?  I did Method B after Method A and I got nothing...

---

### Post by Dubbayoo on 2006-07-18
I don't have compiz/xgl installed at all so I don't think that is the problem.

---

### Post by Deus42 on 2006-08-15
I have this same problem running XGL/compiz on an ATI card. In my case, I think it is because the howto for ATI cards has you create a separate display (:1) and connect to that with a new gnome session.

---

### Post by GoBieN on 2006-08-21
Still no easy solution :(

---

### Post by sazabi on 2006-08-22
I had the same problem too(no shutdown/restart buttons)
Reinstalling compiz and compiz-gnome solved it for me.

---

### Post by Lunar_Lamp on 2006-08-22
I did a bit of a dirty hack to give me this functionality.  Whilst I could probably make a bit nicer by putting a graphical front-end on it, this script does the job nicely for me.  To use it:

 - copy the code into a blank gedit document
 - save the file somewhere (e.g. /home/usr/scripts/shutdown.sh
 - exit gedit, and open a terminal and navgiate the directory where you saved it
 - type "chmod +x shutdown.sh"
 - create a launcher on your toolbar somewhere (right click, add to panel, custom launcher)
 - choose an icon and name and comments, the "command" should be the path to the file we have just created

```
#!/bin/bash

# script to shutdown or restart laptop
# for a nice icon use icon from /usr/share/icons/Human/48x48/apps 

OPTIONS="Shutdown Reboot Cancel"
echo "Type the number of the option you wish to perform"
select opt in $OPTIONS; do

        if [ "$opt" = "Shutdown" ]; then
                sudo shutdown -h now
        elif [ "$opt" = "Reboot" ]; then
                sudo shutdown -r now
        elif [ "$opt" = "Cancel" ]; then
                exit
        else
                clear
                echo bad option
        fi
done

```

---

### Post by pizpot on 2006-08-24
---

---

### Post by pizpot on 2006-08-24
---

---

### Post by hraposo on 2006-08-24
You can type:
sudo halt -p  to shutdown
sudo reboot   to reboot

---

### Post by hraposo on 2006-08-24
You can type:
sudo halt -p  to shutdown
sudo reboot   to reboot

---

### Post by GoBieN on 2006-08-24
Yes ofcourse i can, as i've said here, but i liked the icons :s they dindt require a password to shutdown.

---

### Post by gottferdamnt on 2006-08-25
And what about logout? What is the command line to? ](*,)

---

### Post by mikuskuikku on 2006-09-13
Has anybody got the 'shutdown' button back??? Still missing my!

---

### Post by boakes on 2006-09-15
Missing mine also.

---

### Post by cookfromfrozen on 2006-09-16
Mine are gone after installing Xgl/Compiz on method 2 also.  There has to be a fix for this.

---

### Post by bbarrons on 2006-09-16
all, I have seen this mentioned several times here. I am not sure why it happened to me, I do have ubuntu and kubuntu installed but I did get an answer on this thread. try here [http://www.ubuntuforums.org/showthread.php?t=254269](http://www.ubuntuforums.org/showthread.php?t=254269)
if it works please post back and let everyone know. I think this should be reported as a bug. I just havent done it yet......
Bill

---

### Post by mikuskuikku on 2006-09-18
Thanx for the suggestion... BUT, it didn't work for me! ](*,) 
Any more ideas?

---

### Post by scatyb on 2006-09-18
> **mikuskuikku said:**
> Thanx for the suggestion... BUT, it didn't work for me! ](*,) 
Any more ideas?

Try this:
sudo vi /etc/gdm/gdm.conf-custom

Change this:
RebootCommand=
to this:
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."

Save changes / Restart GDM:
sudo /etc/init.d/gdm restart

*Be sure "SystemMenu=true" exists and is uncommented in /etc/gdm/gdm.conf!!!

GL :wink:

---

### Post by eradicator_006 on 2006-09-18
[http://www.compiz.net/post-38921#p38921]("http://www.compiz.net/post-38921#p38921")

This is how I fixed it using compiz w/ AIGLX.

---

### Post by chuckyp on 2006-09-18
Problem is caused by XGL + Compiz installation.

---

### Post by mikuskuikku on 2006-09-24
Couldn't find anything about compiz.
This is what solved the problem for me (at least I think this is what solved it).

Removed the following rows in /etc/gdm/gdm.conf-custom
[xdcmp]
Enable=false
HonorIndirect=false
[greeter]
Browser=true
SystemMenu=false
[servers]
0=inactive

And removed the wollowing rows in /etc/gdm/gdm.conf
RemoteGreeter=/usr/lib/gdm/gdmlogin
SystemMenu=true

So now I got my 'Shutdown' button back!
Thanx for your support! :D

---

### Post by Chemical-X on 2007-09-23
Problem Solved :D

I tried to use beryl to have a cool desktop, but whatever method I tried to install it, it's main functions never seemed to work... So I uninstalled beryl and stayed with the Desktop Effects that feisty already brings... lamer than beryl, but still cool... The problem was that I changed some scripts and, at last, discovered the one that was bringing me problems... Thing it's the one with the xgl startup questions (dunno, not really sure... kinda noob here)...

Well, back to the main problem, the phantom shutdown&restart buttons... Use these command:

sudo emacs /etc/X11/Xsession.d/91Xgl 
(i like the emacs, but u can use any other editor)
Now just copy the following script to the 91Xgl file (don't forget to backup if the file already exists... just in case):


# This file is sourced by Xsession(5), not executed.

STARTXGL=
XGL="/usr/bin/Xgl"
XGL_OPTIONS=":1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer"

if grep -qs ^use-xgl "$OPTIONFILE"; then
  if [ -x "$XGL" ]; then
    STARTXGL=yes
  fi
  if [ -r /tmp/.X1-lock ]; then
    xglpid=`cat /tmp/.X1-lock`
    if [ -d /proc/$xglpid ]; then
      echo "Xgl already running"
      STARTXGL=
    fi
  fi
fi

if [ -n "$STARTXGL" ]; then
  $XGL $XGL_OPTIONS &
  DISPLAY=:1
	cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
fi

# vim:set ai et sts=2 sw=2 tw=80:


By the way, in the above script, the smiley face is ": and p" (without commas, without the blank spaces and without the and)... Just in case (I didn't know :P)...
Well. that's it... reboot, press CtrlÁlt+Backspace, whatever you're method is and voilá...
My shutdown and restart buttons are back in action, I still got my nice desktop effects, such as cube and "dizzy-dancing" windows...
Hope it worked for you

---

