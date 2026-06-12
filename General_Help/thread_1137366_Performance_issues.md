---
title: "Performance issues"
date: 2009-04-25
forum: General Help
---

### Post by AlexisMclovin on 2009-04-25
I have been having some slowdown problems with my ubuntu system (newest version) lately i really dont know what the cause is. When i first starting using ubuntu is was working fairly well. I was wondering if their is something i can tweak to improve performance. Like windows has disk cleanup , you know something like that

---

### Post by soro2005 on 2009-04-25
Do you hear/see that the CPU works at high load? (Fan spinning a lot) How exactly is it slow? All the time? Or on logon, when you perform certain tasks, etc. When it's going slow, open a terminal window and enter "top" (without the quotes). What are the first few entries?

Also, you can add the System Monitor Applet to a Gnome panel and observe a little what exactly is going on there. How's the state of the memory?

---

### Post by CradLeRcker on 2009-04-25
this thread also concerns me as well, though i just installed ubuntu
i can say that the cpu runs at full speed constantly ever since it was installed. im also running on a laptop, a compaq cq50.
it lags everywhere, from the moment the login screen appear to firefox lagging at each page. it seems like its refreshing the entire screen everytime i move or change the screen.

---

### Post by soro2005 on 2009-04-25
So tell us what you see if you enter
```
top
```
into a terminal window. I'm pretty sure, though, that your problem is different from the OP's.

---

### Post by TURBO_TURBINA on 2009-04-25
> **AlexisMclovin said:**
> I have been having some slowdown problems with my ubuntu system (newest version) lately i really dont know what the cause is. When i first starting using ubuntu is was working fairly well. I was wondering if their is something i can tweak to improve performance. Like windows has disk cleanup , you know something like that


Yes, there is a very powerfull cleaner app called "bleachbit". Google it. Thank you

---

### Post by CradLeRcker on 2009-04-25
i see a list of things ...
is there anything specific that you want to know?
Xorg and gnome-system-mo are constantly the top 2 and are the ones usually taking up most of the cpu

---

### Post by soro2005 on 2009-04-25
The gnome-system-monitor is the panel applet with the graphs indicating the system load. Does it get better if you remove that from the panel? Are there any other programs/process with a consistently high CPU usage?

You may want to try and reconfigure your X-server. Boot into recovery mode, and enter into a console
```
sudo dpkg-reconfigure xserver-xorg
```
It'll run you through a series of screens. You will want to keep the defaults. It may look intimidating, and it's a bit tricky. So don't do it if you're not adventorous.

In any case, it seems to me that your problem is different from the original poster's, and it's not nice to hijack a thread with a different problem. You say you have permanent CPU 100%, the original poster seems to have collected some cruft.

---

### Post by CradLeRcker on 2009-04-25
nvm i seem to have fixed it.
i nvr installed the gfx driver... lol my bad...

---

### Post by Yeti can't ski on 2009-04-28
I had the same problem of slowly decaying performance on each upgrade. Please find below some things that really boosted performance for me: 

- clean the CPU ventilation fan (no joke); 

- release some free space in the harddisk; 

- change the memory swapping ratio if you have 2GB of RAM or more;

- eliminate from the Startup unnecessary programs/processes by going on System -> Administration -> Startup Applications (don't eliminate anything whose purpose you don't know!); 

- eliminate one or two virtual consoles (you have as a defalt four of them, but you probably don't need so many particularly if you - just like me some weeks ago - don't know what they are);

- tweak Open Office in order to allow it use more resources. 

There also other things that I stil didn't try out (because I am lazy and the computer is fast now) such as concurrent boot. 

Remember to make a back up before adventuring with configuration stuff and be careful. 

For the last three suggestions you can find information here:

[http://www.chinwong.com/index.php?/site/comments/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php?/site/comments/ubuntu_speed_up_tips/)

[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

Good luck!

---

### Post by Yeti can't ski on 2009-04-28
P.S. - I also used the new system janitor of Jaunty, but watch out because it "cleans" also packages that may be useful, such as skype. Control carefully its deletion list before letting it do its work.

---

### Post by AlexisMclovin on 2009-04-30
sorry for the late reply i have been busy, but it seems it runs slow only when im running an application that demands the computer's attention. I just got the new upgrade to Jaunty Jackelope so im going to use the computer a little bit before i see if there is anything potentially wrong.

 umm here is what happens when i insert "top" in terminal it had a bunch more programs but they were not taking up any memory  
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3618 alex      20   0  3156 1600  848 R 27.9  0.3  55:51.64 dbus-daemon        
 2524 root      20   0  177m  26m 9352 R 18.6  5.5   1:13.34 Xorg               
 3693 alex      20   0 27872  12m 6440 S 16.6  2.5  39:18.20 python             
 3741 alex      39  19 30584  12m 4668 R 15.3  2.6  33:43.00 tracker-indexer    
 3681 alex      39  19 53708 9836 4356 S 12.3  2.0  29:14.56 trackerd           
 9353 alex      20   0 51060  14m 9872 R  7.3  2.9   0:03.26 gnome-terminal     
 9049 alex      20   0  177m  56m  21m S  1.0 11.6   0:34.11 firefox            
 3721 alex      20   0 79656  30m  12m S  0.3  6.2   0:02.79 deskbar-applet     
    1 root      20   0  3084  556  500 S  0.0  0.1   0:01.33 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.44 ksoftirqd/0

---

### Post by LoneWolfJack on 2009-04-30
it'S the tracker deamon again. go figure.

```
sudo killall trackerd
```

---

### Post by AlexisMclovin on 2009-05-03
umm i dont know what that does, could you tell me before i just get rid of it?

well i tried to use the command above but it still says that dbus-daemon is still running

---

