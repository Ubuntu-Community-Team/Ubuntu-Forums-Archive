---
title: "Extreme CPU Usage"
date: 2009-03-21
forum: General Help
---

### Post by Aflack on 2009-03-21
i have ubuntu 8.10 32bit running on my 

5gb ram
amd64bit quad core 2.2ghz 
geforce 9300

and all the time my cores take turns running 100 percent, and it slows everything down. Here is a screenshot: [http://www.yfrog.com/0gmaxedcpup]("http://www.yfrog.com/0gmaxedcpup")

---

### Post by taurus on 2009-03-21
Open a terminal and run top to see which process is offender.

Applications -> Accessories -> Terminal
```
top
```
Or install **htop** from the repos if you want a GUI top.

---

### Post by Aflack on 2009-03-21
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6528 root      20   0  214m 135m  18m R   83  3.8 269:52.81 Xorg               
 7538 alex      20   0 21904  11m 7816 S    9  0.3  64:19.63 cairo-clock        
 9329 alex      20   0 70672  24m  15m S    5  0.7   7:09.41 gnome-system-mo    
 7458 alex      20   0  104m  55m  21m S    3  1.6  10:59.23 compiz.real        
 7549 alex      20   0 53700  25m  12m S    2  0.7   8:06.25 alarm-clock        
14170 alex      20   0  312m 117m  28m S    1  3.3   0:44.95 firefox            
14244 alex      20   0  112m  24m  13m S    1  0.7   0:00.70 gnome-terminal     
 7520 alex      20   0 59712  32m  10m S    0  0.9   0:26.30 GlobalMenu.Pane    
 7522 alex      20   0 26296  12m 9476 S    0  0.4   1:26.02 multiload-apple    
 7280 alex      20   0 31336 4940 3432 S    0  0.1   4:01.01 pulseaudio         
 7740 alex      20   0 3058m  68m  21m S    0  1.9   1:38.84 pidgin             
    1 root      20   0  1960  872  576 S    0  0.0   0:01.64 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.92 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.84 ksoftirqd/1        

xorg?

---

### Post by taurus on 2009-03-21
Yip.  Looks like X server is maxing out your CPU.  What kind of graphic card do you have anyway?

---

### Post by Aflack on 2009-03-21
Nvidia GeForce 9300 + 8300 

256mb dedicated and 2gb shared.

forgot to mention, xorg never used to do this. for a few months ubuntu worked perfectly.

---

### Post by taurus on 2009-03-21
Try this test.  Reboot your machine.  Then at the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Login with your username and password.  Now, have a look at the outputs of these two commands.

```
uptime
top
```
If you want to get out of top, just hit q for quit.

---

### Post by Aflack on 2009-03-21
> **taurus said:**
> Try this test.  Reboot your machine.  Then at the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Login with your username and password.  Now, have a look at the outputs of these two commands.

```
uptime
top
```
If you want to get out of top, just hit q for quit.

ill try that in a little bit, then ill post.

---

### Post by Cruncher on 2009-03-21
Which programs are you running when this happens? In the Processes tab of the System Monitor you can see the amount of CPU time each process uses (sort by CPU usage descending).

Edit: Woops, didn't read the recent replies. But the Processes tab might still be useful for you.

---

### Post by Aflack on 2009-03-21
ok so for uptime i got: 1 min and the avg load was .52 .28 and .10

and the top process range from top  init and xorg maxing at 1% cpu usage.

(my cores go to 100 percent a minute or so after log in)

---

### Post by Cruncher on 2009-03-21
And it is always xorg that uses this 100% CPU time (according to "top")? Can you append the output of "dmesg", as well as the file /var/log/Xorg.0.log once this happens?

---

### Post by Aflack on 2009-03-21
> **Cruncher said:**
> And it is always xorg that uses this 100% CPU time (according to "top")? Can you append the output of "dmesg", as well as the file /var/log/Xorg.0.log once this happens?

what do you mean to do with the xorg file? im kinda new

and yeah its always xorg like rigght now its using 86% on the 'top' list.

---

### Post by Cruncher on 2009-03-21
Please open a Terminal and run this command when your CPU has this problem:
```

dmesg > boot.messages

```
Then attach the files "boot.messages" (should be in your home directory) and /var/log/Xorg.0.log to this thread.

---

### Post by Aflack on 2009-03-21
it says invalid files when i try to upload

---

### Post by Cruncher on 2009-03-21
Does the problem also arise when you DON'T use/start Firefox?
Do you visit facebook.com? There seems to be a similar issue, workaround is here:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251700](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251700)

re the files: Apparently you have to zip them before the forum engine allows you to attach them. So please create a zip archive containing the two files, using your favorite file browser or with this command:
zip -j logfiles.zip boot.messages /var/log/Xorg.0.log
Then attach logfiles.zip to the thread.
...unless the above link already solved your problem.

---

### Post by Aflack on 2009-03-21
i do visit facebook all the time, but even without that it still rises to 100 percent taking turns with my other cores.

---

### Post by Cruncher on 2009-03-21
> **Aflack said:**
> i do visit facebook all the time, but even without that it still rises to 100 percent taking turns with my other cores.
Then you should try blocking [http://www.facebook.com/swf/SoundPlayer.swf](http://www.facebook.com/swf/SoundPlayer.swf) with Adblock, or downgrade to Flash 9, as proposed in the bug report.

Concerning your logfiles, I can't see any obvious problems in them.

---

### Post by Aflack on 2009-03-21
i blocked that and its still 100 percent D:

---

### Post by Cruncher on 2009-03-21
I assume you restarted Firefox after you blocked it? Logging out or rebooting might also be a good idea, in case the problem causing the 100% CPU doesn't stop by itself after closing Firefox.

---

### Post by Aflack on 2009-03-21
restarted ff and its still 100 percent

---

### Post by Aflack on 2009-03-22
whered you go D:

---

### Post by Cruncher on 2009-03-22
Sorry, out of ideas :-/

You did reboot?

---

### Post by Aflack on 2009-03-22
no but i did indeed find out it was facebook. after i closed the tab it took a whioe for my cpu usage to go back to normal. then on facebook it shot up.

---

### Post by Aflack on 2009-03-22
actually its not facebook i dont think because when i shut off firefox i still use 100 percent :o

---

### Post by mishaokami on 2009-08-04
short answer go to preferences->appearence and turn visual effects to none

long answer:


I've had the same experience with my nvidia 9300/730i.
I would doubt that the problem is with compiz.  My experience is this:

I use nvidia 180 from the repos

Turn on compiz (and thereby the compositor) = crash or on a good day Xorg (nvidias user space X binary) goes to 100%

Turn off compiz and turn on metacitys compositor = same

Turn off both compositors and im stable.

That is alot of suck.
Unfortunately it looks like nvidias own closed source xclient or kernel drivers are suspect.  I'm not quite sure where this functionality is coded.

This said, i have not as yet tried to use blender or something else that stresses other features of the chip.  Perhaps all 3d stuff is a loss.

m

---

