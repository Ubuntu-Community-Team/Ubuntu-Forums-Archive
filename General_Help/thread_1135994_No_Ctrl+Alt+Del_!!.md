---
title: "No Ctrl+Alt+Del ?!?!"
date: 2009-04-24
forum: General Help
---

### Post by steinaro on 2009-04-24
Alright, I have been using Ubuntu/Linux for a few months now but I have never understood what to do if the computer locks up. In Windows you just hit Ctrl+Alt+Del and you get a list of non-responsibe applications running that you can shut down. You know what I'm talking about, the Task Manager (I had to run to my wifes computer to get the name just now). 
Anything like that in Ubuntu? What are my options for a locked up computer or application?

Oh, and someone please respond. No one ever responds to my threads. :-k

---

### Post by letmekilluplz on 2009-04-24
Type in ```
Top
```

You can kill programs from there thats what I do

---

### Post by steinaro on 2009-04-24
> **letmekilluplz said:**
> Type in ```
Top
```You can kill programs from there thats what I do

I went to it and it looks good but I can't figure out how to use it. The arrow keys don't work. Is there a help manual or something?

---

### Post by m_2009 on 2009-04-24
Although not accessed via CTRL - ALT- DELETE, The ubuntu equivalent of task manager can be found by going to SYSTEM > ADMINISTRATION > SYSTEM MONITOR.

You can right click on any process and can do a number of things such as "Stop Process", "End Process" and "Kill Process" etc..

Another option is to add the "Force Quit" applet to the gnome panel.

---

### Post by ninjapirate89 on 2009-04-24
What can be done if it completely freezes (I've had times when I couldn't use mouse or keyboard)?

---

### Post by Monotoko on 2009-04-24
Use Alt Gr, SYSRQ and K (funny combination i know) to restart Xorg

---

### Post by letmekilluplz on 2009-04-24
To use top command press k and enter the PID(Listed on the left I think) of the program you want to kill(equivalent of "End Now")

---

### Post by steinaro on 2009-04-24
> **letmekilluplz said:**
> To use top command press k and enter the PID(Listed on the left I think) of the program you want to kill(equivalent of "End Now")

It worked! Thanks.

---

### Post by dazzlindonna on 2009-04-24
Well if you can't use the keyboard, then ctrl-alt-del wouldn't help anyway.

Right click a panel, Add To panel, Choose Force Quit applet.  That makes it super easy to kill a frozen window.  Just click the applet icon, and then click the frozen window.  That fixes 99% of my problems.

The other .9% of the time when that doesn't work, Ctrl-Alt-Backspace kicks me out to let me login again, solving the problem.

People often say to use the combination of Alt/PrtScr/REISUB (pressing those letters slowly) to get out of the worst freezes, but it's never worked for me.

If all else fails, and I absolutely can't do anything at all, I close my eyes, cross my fingers, and press the power button.

---

### Post by Monotoko on 2009-04-24
ahh, but hes running 9.04, ctrl+alt+backspace no longer works, its now ALTGR+SysRq+K

---

### Post by dazzlindonna on 2009-04-24
Ack! I'm running 9.04 too, but didn't notice that ctrl-alt-backspace disappeared.  Grrr...

Ok, what is ALTGR?

---

### Post by Monotoko on 2009-04-24
Its the right ALT key

---

### Post by dcstar on 2009-04-24
> **dazzlindonna said:**
> Ack! I'm running 9.04 too, but didn't notice that **ctrl-alt-backspace disappeared**.  Grrr...


Read the release notes, it is trivial to re-enable.

---

### Post by HotForLinux on 2010-05-25
[B]Enough is Enough...

Maybe it is high time desktop environments included an icon and a call to the system monitor in the window that pops up when you press Ctrl+Alt+Del[/B]

---

### Post by radite on 2010-05-25
Ok i'm new on using ubuntu,...there's no Ctrl+Alt+Del
but Alt + SysRq + K, how if my pointing device totally freeze?

---

### Post by pzkfw on 2010-05-26
This was one of my biggest problems when I switched over to Linux.  A full screen application would lock up the desktop enviornment (Gnome/KDE) and I couldn't kill it.  However, I found out a few "tricks" that make handling crashes in Linux 500000x better than in Windows.  Windows has decent management when something crashes, but yet again it's usually when your application is full screen and completley locks up, even ctrl+alt+del won't switch focus or alt-f4 won't end it.

Here is how to "recover" from any kind of crash in Linux that goes full screen and you can't get focus:

```
First, press **CTRL+ALT+F1**.
```This brings you to one of your six terminals.  The others are ctrl+alt+[f2,f3,f4,f5,f6].  Ctrl+F7 brings you back to your desktop but we're not interested in that because the problem is still going to be there.

It will ask you to log in.  Log in as your typical name.  This is linux so you can be logged in as the same user twice.  
You probably remember what process/thing is causing the problem.

Type:
```
$ps aux | grep processname
```"ps aux" is your entire process list and |grep processname filters it by the name.  It should return a name along with a process ID  (PID).  Next type:
```
$killall pid
```where pid was the PID of the process.  You may have to type sudo before killall.

If none of that works, just restart X.
You can do so by hitting **CTRL+ALT+BACKSPACE**
or log into one of your terminals with the above ctrl+alt+f1 and type
```
#sudo /etc/init.d/gdm stop
#sudo /etc/init.d/gdm start
```which restarts gnome.  (replace gnome with kdm if you're using kde)


You'll find that if you restart your desktop or restart X server then you won't ever have to do a hard reset due to a crash.

I'm not familiar with this forum's policies on sudo so replace sudo with sudo -i or su or whatever you like to use if that's the case.

---

