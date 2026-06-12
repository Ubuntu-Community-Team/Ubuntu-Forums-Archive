---
title: "System Shutdown timer"
date: 2009-02-15
forum: General Help
---

### Post by benjamin.s.vaccaro on 2009-02-15
Hello,

Is there a program that closes all running programs then shuts down the computer at a set time? 

The reason I ask is I like to listen to music when I sleep, but obviously I do not need it playing when I am asleep. So instead of keeping my computer running all night and wasting electricity or getting up to turn it off I would like for it to automatically close running programs and then shut down.

---

### Post by dcstar on 2009-02-16
> **benjamin.s.vaccaro said:**
> Hello,

Is there a program that closes all running programs then shuts down the computer at a set time? 

The reason I ask is I like to listen to music when I sleep, but obviously I do not need it playing when I am asleep. So instead of keeping my computer running all night and wasting electricity or getting up to turn it off I would like for it to automatically close running programs and then shut down.

```
man crontab
man cron
```

---

### Post by 3rdalbum on 2009-02-16
Meh, you don't need to set a Cron job just to turn off your computer.

```
at now + 8 hours
```

or

```
at midnight
```
or
```
at 9:30am
```

Then you get a prompt like this: at>

Type in the command you want to run at the specified time, and press Enter. You can add another command in, or as many commands as you want. When you have input all the commands you want to run, press Control-D to save your changes and quit At.

If you want to shut down your computer, there is an extra little step. Shutting down requires root privileges, so you must use something like this:

```

chris@chris-desktop:~$ sudo at midnight
[sudo] password for chris: 
warning: commands will be executed using /bin/sh
at> halt

```
Press enter and then Control-D. Your computer will shut down at midnight.

You should also learn the "atq" command, which lists all the scheduled jobs, and "atrm" which removes a particular job. Remember that you created the job as root, so you must use "sudo atq" or "sudo atrm" to list or remove this job.

Another tip: At jobs are persistent after shutdowns, and if At misses any jobs it will run them on next boot. So if you schedule a shutdown for midnight and then at 11pm you decide to turn off your computer manually, make sure you remove the At job! Otherwise, the next time you turn your computer on, it will boot up and then shut down :-)

---

### Post by avsilesh on 2009-02-16
There is a small program for auto shutdown. I don't remember the name of the but just try searching in synaptic manager.I used it recently, quite convenient, can set what time or a time period later to shut down.Will post you the name when I recall it.

---

### Post by ivikas on 2009-02-16
Hello benjamin,

              I usually plays music at night while sleeping and power down system using a shell script.I don't know whether the script is safe or not but it helps me and hope the same for you.

suppose you are playing some music using totem player and wants to play (say 45 minutes) and after that you want the sytem should shut down after stopping totem player.Open a text editor and  you can write a shell script like this.

```

#!/bin/bash
echo "System shutting down within 45 Minutes"
sleep 45m
killall -9 -e totem
poweroff

```

 Copy the above code and save it as shutSys or give any name into your home directory.To run the script open a terminal Application-->Accessories-->Terminal and type:
```

sh shutSys

```
You can use any user account(need not be root to do this).Now a little explanation 
about the script.

First line of code tells which shell to use.
Second  displaying a message to tell you  what the script is serving.
sleep 45m [m-minutes,h-hour-see sleep manual(man sleep from terminal)-->delaying the system for 45 minutes(u can set this value)
killall -9 -e totem --To force kill application exactly by name totem
Then poweroff --->shut down the system after the time limit of 45 minute expires

This is a simple Shell script and they are very handy if you learn it(do googling).You can use this type of script to copy large files which takes hours and 
on

Hope this works for you.

---

### Post by benjamin.s.vaccaro on 2009-02-16
Very cool, thanks guys. I will try these different methods out.

---

### Post by geirha on 2009-02-16
The following will shutdown the computer in 60 minutes. It will also give warnings to all users.
```
sudo shutdown -h 60
```

---

### Post by benjamin.s.vaccaro on 2009-02-16
Just out of curiosity, we are talking about programs or scripts that tell the OS to shut down, but we are not telling programs to close; we are essentially force quitting them? In general these commands are harmful to the programs being ran, no? Because the point of the timer is that I can use it every night. 

Note: Amarok is playing the music from my ipod.

---

### Post by geirha on 2009-02-16
The shutdown command sends all processes [SIGTERM](http://en.wikipedia.org/wiki/SIGTERM). Basicly allowing the process the chance to close down properly.

---

### Post by benjamin.s.vaccaro on 2009-02-16
Thank you everyone for all your help and attention. I think Geirha's method works best for my needs.

---

### Post by avsilesh on 2009-02-16
"GShutDown",a small gui program will do the auto shutdown.

---

### Post by dcstar on 2009-02-17
> **3rdalbum said:**
> Meh, you don't need to set a Cron job just to turn off your computer.
........

No you don't, but if you see what these basic Linux things are capable of (when it is obvious that you don't know about them) then you can firstly achieve you initial goal and then have more knowledge about the capabilities of system you are now using.

Some people prefer to "throw people fish", I prefer to let them know where they can "find a fishing line" so that they may well benefit from it in the future.

---

### Post by JoshRobertson92 on 2009-05-15
Sorry so late
Just something that really annoys me is the beeping sound every 10 minutes and every minute for the last 10.
To get rid of this type **sudo shutdown -q +10 minutes **[I]to shutdown without bleeps in 10 minutes
[/I]or** sudo shutdown -q 9:07 ***to, you guessed it shutdown at 9:07 :D*

---

### Post by JoshRobertson92 on 2009-05-15
Sorry so late
Just something that really annoys me is the beeping sound every 10 minutes and every minute for the last 10.
To get rid of this type **sudo shutdown -q +10 minutes **[I]to shutdown without bleeps in 10 minutes
[/I]or**sudo shutdown -q 9:07 ***to, you guessed it shutdown at 9:07 :grin:*

---

