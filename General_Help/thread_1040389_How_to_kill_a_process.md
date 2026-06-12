---
title: "How to kill a process?"
date: 2009-01-15
forum: General Help
---

### Post by UranUtan on 2009-01-15
Hi,

Just added SuperTux2 on Ubuntu 8.10 (up to date), computer is P3, 1GHz, 750 MB Ram, video card is a low end 6 years old nVidia card 32 MB (forgot the model).

When the game started, it is awfully slow and the graphics mode took the full screen (Ubuntu desktop is not visible). I would like to know a way to kill the process quickly. 

Generally, how to know the process of a particular application and how to kill a specific process?

Thanks in advance for any help.

---

### Post by wolfen69 on 2009-01-15
do alt-F2 to open a run dialog bog. then you can type in "xkill" without the quotes. it will turn your cursor into an x. just position the x anywhere in the open application and click. it will kill it.

---

### Post by drs305 on 2009-01-15
There are a lot of ways to terminate an app:

GUI:
1. System > Administartion > System Monitor.  Processes tab, highlight the app, RtClk, End Process. If it doesn't end, right click again and select Kill.

2. Force Quit (Add to Panel, Force Quit): Click on Force Quit icon, then click on app

3. xkill, as previously mentioned.

4. Find the PID  and then kill the process (wth the *less* pipe, hold the ENTER key to scroll): 
```
ps aux | less # or "ps aux | grep *appname*"  if you know the name  
*or *
ps -u *yourusername*  # example: ps -u *dave*

```
Then:
```
sudo kill -9 PID  # example  sudo kill -9 8876
```
or
5. ```
killall *appname*
*or*
killall -9 program
```

6. Open a terminal: htop
Highlight the process, F9 Enter (kill)

---

### Post by UranUtan on 2009-01-15
Thank you gentlemen for your quick help. In particular drs305 for your very complete answer.

Please note that in my particular case, the entire screen is in graphic mode (SuperTux2) there is no way for me to click on any Ubuntu menu.

This SuperTux game is terrible, I wonder how it could be rated 4 stars in the Add/Remove Application. It is so slow, it is not even able to move a mouse. I want to learn ow to kill such crappy application if even the next time this occurs again.

Can you please confirm that Alt-F2 would open a terminal or something to allow me to type in the commands?

---

### Post by drs305 on 2009-01-15
Yes, normally ALT-F2 will open a window. You can enter the command and run it. 'Tick' the 'Run in Terminal' box to display a terminal window so you can see the results.

---

