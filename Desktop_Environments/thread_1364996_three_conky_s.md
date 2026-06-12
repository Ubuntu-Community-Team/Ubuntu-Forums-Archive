---
title: "three conky ?s"
date: 2009-12-26
forum: Desktop Environments
---

### Post by robertrose6 on 2009-12-26
How do I change the color of the font?

How do I restart conky without having to restart the computer?

How do I and something to the list?  (battery status maybe)

I have already added wireless but that was pretty easy

Thanks for the help

---

### Post by taurus on 2009-12-26
If you have your own version of ~/.conkyrc, you change the color of your font in there.  And if you want to restart it, just kill the current one and restart it again so it would read the new ~/.conkyrc.

---

### Post by robertrose6 on 2009-12-26
here is a  sample
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

So were it says {color orange}CPU 
that makes the word CPU come up orange.
So If I wanted it green I just change the word orange to green.
and if I wanted to change the out put color were do I change that? Right now it is gray.

when killing conkrc do I just type kill conkrc in CLI? If so how do I restart the programe?i

I am very new to Ubuntu and Linux.

---

### Post by taurus on 2009-12-26
You could add these lines to the beginning and change the color to whichever one you want.

```

# Default colors and also border colors
default_color **white**
default_shade_color **white**
default_outline_color **white**

```
And if you want to kill the current conky, just run

```
sudo killall conky
```
Then, start a new one with 

```
conky &
```

---

### Post by robertrose6 on 2009-12-26
The kill all works great. But the restart command does not. But I did get the colors to change.


Thanks for the help

---

### Post by 5BallJuggler on 2009-12-26
> **robertrose6 said:**
> How do I change the color of the font?

How do I restart conky without having to restart the computer?

How do I and something to the list?  (battery status maybe)

I have already added wireless but that was pretty easy

Thanks for the help

I know that this link I'm passing to you has well over 1000 pages, but if you have the time and the inclination there are some fantastic things that you may want to try, including adding rings, images, direct links to web pages etc. etc. 

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

start from the 1st page, or just search the thread for anything that takes your fancy, it's all there in some form or other.

Phil (previous conky virgin)

ps the command to start conky is.....

```
conky
```

---

### Post by robertrose6 on 2009-12-26
I have looking at that thread for about 3 hours on and off. 

I am going to try that command right now

thanks


ok I just trused that command and it brings up a conky but not the same one that runs after startup. Any ideas?

---

### Post by stinkeye on 2009-12-26
> **robertrose6 said:**
> I have looking at that thread for about 3 hours on and off. 

I am going to try that command right now

thanks


ok I just trused that command and it brings up a conky but not the same one that runs after startup. Any ideas?
The config that comes with conky is in 
```
/etc/conky/conky.conf
```
If you run conky in terminal with
```
conky
```
it will load ~/.conkyrc

If you don't have a ~/.conkyrc it will load /etc/conky/conky.conf
To load a specific conky in terminal name a conky config whatever you like eg...conky1
```
conky -c ~/[COLOR="Magenta"]path to your config[/COLOR]/conky1
```
See [_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by robertrose6 on 2009-12-26
Thank you very much. Now I dont have to log off every time I make a change. And I have been looking for that thread. I used it to get started but I lost it on one of the log outs

---

### Post by stinkeye on 2009-12-27
> **robertrose6 said:**
> Thank you very much. Now I dont have to log off every time I make a change. And I have been looking for that thread. I used it to get started but I lost it on one of the log outs
To easily stop/start your conky use this ```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky -c ~/[COLOR="DarkRed"]path to/your conky[/COLOR] &

 fi
```
Save as tooggleconky
Make executable
Create a laucher in your panel.

You can add more conky configs later
eg I run 7 conkys
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
sleep 1 &&
 exec conky -c ~/conky/conkypanel &
sleep 3 &&
 exec conky -c ~/conky/conkycal &
#sleep 3 &&
# exec conky -c ~/conky/conkyclocklua2 &
sleep 4 &&
 exec conky -c ~/conky/conkyplaytime &
sleep 5 &&
 exec conky -c ~/conky/conkysb &
sleep 6 &&
 exec conky -c ~/conky/conkysro &
#sleep 7 &&
 #exec conky -c ~/conky/conkytide &
sleep 9 &&
 exec conky -c ~/conky/rottoswellmini &
sleep 10 &&
 exec conky -c ~/conky/conkygmail &
fi
```

If your using compiz have a look here for a startup script
[_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8102716&postcount=20[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=8102716&postcount=20")

---

### Post by robertrose6 on 2009-12-27
Thanks everyone for there help. Now for the new question.
Can someone point me to how to get the temps for my hard drive and cpu to show up. Allso how to get the battery life info to conky.

I read something about needing to wright a shell script. I have no idea what that is.

---

### Post by stinkeye on 2009-12-27
[[COLOR="DarkRed"]_http://conky.linux-hardcore.com/?page_id=427_[/COLOR]]("http://conky.linux-hardcore.com/?page_id=427")

---

