---
title: "Hanged"
date: 2006-03-14
forum: Desktop Environments
---

### Post by noumaan on 2006-03-14
I installed ubuntu few days ago. Every thing is working great, my internet, lan, chat, web, music, movies, etc. 

Since last two days I am facing a problem. [LIST]
[*]My applications are taking a little more time to start than the time they took before. 
[*]Whenever my browser (firefox) is loading a lengthy webpage the entire system gets hanged, I can not move mouse or do anything else. It also happens when I am browsing and running the Help application that comes with ubuntu.
[/LIST]

I would like to know

[LIST]
[*]What could possibly be wrong?
[*]What should I do to solve this problem and prevent it to occur frequently?
[*]In windows we use ctrl alt delete and go to task manager to close the non-responding applications/programs. How do we do such a thing in Ubuntu?
[/LIST]

---

### Post by Ramses de Norre on 2006-03-14
Did you made any changes to your system?
You can use top from the command line to watch processes, or sudo ps aux for a static output. free will show memory information. 
To stop a process: killall process_name or kill PID (PID is found in top or ps aux) or for non-willing processes: kill -9 PID, for more options: man kill
For a GUI: applications > system tools > system monitor

---

### Post by rjwood on 2006-03-14
need more info.
What version of ubuntu are you using?
what is your hardware?
what version of ff are you using?

---

### Post by cronholio on 2006-03-14
You can use Applications->System Tools->System Monitor. Or better, install the Force Quit appled on your upper taskbar (right-click on it and click "Add to panel...").

The System Monitor will also show you which program it is that is hogging all the memory/CPU. If the computer is too slow to run the System Monitor, press Ctrl-Alt-F1, login and run "top".

EDIT: w00t!!! Triple same-time post. :D

---

### Post by noumaan on 2006-03-14
I made several changes, I downloaded many packages, the last package I installed was an Educational software Kletters. I remember that the problem occured after installing Kletters but I don't think that it is due to that download. I also downloaded several other programs. 

How do I go to applications > system tools > system monitor when I can not even move my mouse. 

Ubuntu version is 5.10 
256 MB RAM 
800 MHZ processor (don't know exact because I don't know how to see my processor information in ubuntu) 
Firefox/1.0.7 (Ubuntu package 1.0.7)

---

### Post by cronholio on 2006-03-14
Well, press Ctrl-Alt-F1 and wait. It should switch to the text console eventually. Then type "top". It will show you the processes and how much CPU/memory they consume. You can kill the one that's blocking your system by "kill -9 <pid>". PID is the process ID (shown by the output of "top").

---

### Post by noumaan on 2006-03-14
and I tried the TOP thing but I didn't know how to switch back to the GUI so I had to restart. 

ok I can learn to use TOP but what is wrong with my system? How do I figure this out?

---

### Post by Ramses de Norre on 2006-03-14
To go back to the GUI do ctrl+alt+F7.
What's the output of top when it hangs? (open it in terminal in X and press q when the system hangs, you can then copy the output.)

---

### Post by cronholio on 2006-03-14
The program using the biggest amount of CPU will be on the top of top (pun intended).

---

### Post by noumaan on 2006-03-14
This is what I see right now when my system isn't troubling at all. I don't know what causes it to hang so that I could repeat it and get the log. 

 6767 root      15   0 51632  15m 5880 S  1.0  6.1   0:37.41 Xorg
 7310 dan       15   0 30784  12m 8052 S  0.3  5.0   0:01.42 gnome-terminal
 7330 dan       16   0  2132 1072  844 R  0.3  0.4   0:00.05 top
    1 root      16   0  1560  532  460 S  0.0  0.2   0:01.54 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.03 khelper
    5 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   84 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush
  113 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.04 kswapd0
  698 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1839 root      16   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2898 root      15   0     0    0    0 S  0.0  0.0   0:00.03 kjournald

---

### Post by Ramses de Norre on 2006-03-14
This indeed looks pretty normal.. look at it again when it's hanging (watch the top processes for cpu, memory, which process..)
Also give the output of dmesg|tail after a hang.

---

### Post by noumaan on 2006-03-16
I am totally unable to do anything productive on my Ubuntu. The system gets hanged whenever I am reading a PDF file, a lenghty web page, or doing anything that requires to work with larger files (more than 500 KB). This is what I have noticed so far. 

I am totally unable to switch to console, command line, terminal when my system gets hanged. 

I placed the force quite icon on my panel but clicking it doesn't work anything when my system is in trouble. 

During this time my Hard Disk works like crazy and little bulb in my CPU blinks at the speed of light, but still the situation doesn't get resolved even after 30 mins (last time I gave it 30 mins to workout). 

I never used linux before Ubuntu, I really love ubuntu and I really want it to work. I just can't figure out how. :(

---

### Post by noumaan on 2006-03-19
I found [these]("http://ubuntuforums.org/showthread.php?t=42873") [guides]("http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html"). I have a 256 MB RAM so I guess I should consider trying such a solution. But these guides are written for older versions of ubuntu I am currently using 5.1 Breezy Badger. How do I optimize my system to use little memory? Do you guys think that the guides mentioned above would work fine for breezy badger aswell?

---

