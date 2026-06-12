---
title: "CPU constantly at 60% even though System Monitor/htop shows no programs using cpu"
date: 2009-05-27
forum: General Help
---

### Post by ihaveabu on 2009-05-27
I'm running jaunty 9.04

after playing a video from hulu in firefox, my cpu has been running at 60% with no programs running, even after i restarted a few times. i've tried uninstalling adobe flash, java jre and even with these 2 completely uninstalled the cpu is still at 60% consistently.

i tried using the system monitor and htop to view cpu load, and both show the same thing. 60% cpu load, but no programs that are actually using the cpu beyond 5-10%.

my cpu temp is consistenly 10-15C over it's idle temp at 35C now because of this.

how do i fix this? i only started having this problem after i played a video on hulu. youtube didn't have this problem before, just hulu for some reason...

my desktop specs:
P4 2.4C oced to 2.8
2GB DDR2 PC3200 running at 320mhz
120GB HDD
ATI Radeon 9600

---

### Post by ihaveabu on 2009-05-27
and here's another screenshot showing this root X11R6 thing running 60% cpu when i'm not doing anything...

---

### Post by mojorising on 2009-05-27
Hi, 

You can try the top utility in the command line to identify the process consuming CPU. Just type "top" (without quotes) in a command window to run it. Type "man top" to see the top documentation with lots of different options. 

It may take you a little while to find the culprit this way but it's probably the most effective way to identify the process you're looking for. 

I'm wondering if you have this issue all the time or only when Firefox is running -- sounds like all the time. Regardless, the issue seems odd. I can't think of a reason why such a thing would happen. It's likely the increased CPU usage change since you watched the Hulu video is coincidental, though, I suppose one can't be certain until exhaustively checking. 


Mike

---

### Post by ihaveabu on 2009-05-27
> **mojorising said:**
> Hi, 

You can try the top utility in the command line to identify the process consuming CPU. Just type "top" (without quotes) in a command window to run it. Type "man top" to see the top documentation with lots of different options. 

It may take you a little while to find the culprit this way but it's probably the most effective way to identify the process you're looking for. 

I'm wondering if you have this issue all the time or only when Firefox is running -- sounds like all the time. Regardless, the issue seems odd. I can't think of a reason why such a thing would happen. It's likely the increased CPU usage change since you watched the Hulu video is coincidental, though, I suppose one can't be certain until exhaustively checking. 


Mike

i have used the top utility.

here's a scrnshot:

---

### Post by mojorising on 2009-05-27
Just saw your second screen shot there. X11R6 is X Window -- you need that. It looks like you do have quite a few things running. Maybe shut some of those down to see if you see any changes in X' CPU usage (a possibility, I believe). 

Another neat tool you might be interested in is rcconf, you can use it to prevent unnecessary services from starting at boot. Just Google a given service before disabling it so you know what you're disabling. 


Mike

---

### Post by mojorising on 2009-05-27
Using top too, that's great. I see your usage is now at forty-something percent. Progress!


Mike

---

### Post by ihaveabu on 2009-05-27
this is interesting. i stopped x session manager using system monitor, and all of a sudden my cpu load dropped from 70% to 15%...

i resume x session monitor and it all of a sudden jumps up to 70% again

---

### Post by ihaveabu on 2009-05-27
> **mojorising said:**
> Using top too, that's great. I see your usage is now at forty-something percent. Progress!
 
 
Mike
 
yea, htop is basically top but with a better gui.
 
after turning off x session manager, my cpu load is down to 5%, and my temp's are down to 36C. wtf??
 
wtf is x session manager, and why is it being stupid?
 
the weird thing is that system monitor shows it as sleeping, but only using 2% cpu. the moment i turn it on, cpu load jumps to 60%
 
 
oh and i forgot. if i try to restart or shutdown, it pops up a window that says an unknown program is trying to run, should i lock the screen, cancel, or log off.. this started happening today after playing hulu too...
 
and now, for some reason, all my desktop icons are gone, i can't right click the desktop, and it's not letting me restart. the restart countdown is stuck at 59 sec and i can't start a terminal or anything. 
 
this is freakin weird

---

### Post by doas777 on 2009-05-27
try rkhunter and chkrootkit. they are both in the repos. you are running htop as root, right?

---

### Post by ihaveabu on 2009-05-27
> **doas777 said:**
> try rkhunter and chkrootkit. they are both in the repos. you are running htop as root, right?
 
i thought linux didn't have viruses... ???

---

### Post by ihaveabu on 2009-05-27
ok so i sudo apt-get 'ed rkhunter
 
now how do i use it?

---

### Post by ihaveabu on 2009-05-27
what exactly is x session manager?

---

### Post by doas777 on 2009-05-27
> **ihaveabu said:**
> i thought linux didn't have viruses... ???

Rootkits and viruses are very different types of malware, and ubuntu can be susceptible to rootkits (as could any os).  its hard to get one, but not unheard of. rootkits are usually used to hide actions from the system itself, and could explain processing that isn't visible in the process list.  many of the botnet command and control servers around the world are linux and unix servers that were comprimised by an attacker, and subsequently rooted, to maintain long term control. the failure is usually the operator or administrator (or a weak ssh cert...), but the result is the same .

another thought is it could be interupt handler processing, and I'm not sure that would show in top. do you have any dying hardware?

---

### Post by doas777 on 2009-05-27
> **ihaveabu said:**
> ok so i sudo apt-get 'ed rkhunter
 
now how do i use it?

this shoudl do ya
```
sudo rkhunter --check
```

---

### Post by doas777 on 2009-05-27
according to wikipedia, the x session manager, allows you to save session state (load the windows/apps that were open at last shutdown/logoff) when you log in next. it also controls the applications that you launch at login. 
you can configure this stuff in System -> Preferences -> Start Up Applications (in jaunty; called "Sessions" in hardy-).

you may wanna check each of your startup application entries, and if you have the check box on the options tab checked, uncheck it, and reboot. it may help.

---

### Post by ihaveabu on 2009-05-27
> **doas777 said:**
> according to wikipedia, the x session manager, allows you to save session state (load the windows/apps that were open at last shutdown/logoff) when you log in next. it also controls the applications that you launch at login. 
you can configure this stuff in System -> Preferences -> Start Up Applications (in jaunty; called "Sessions" in hardy-).
 
you may wanna check each of your startup application entries, and if you have the check box on the options tab checked, uncheck it, and reboot. it may help.
 
i don't have that checked. I tried having it checked earlier cuz i was having trouble getting last.fm to start automatically. then i eventually disabled the "check for running programs" thing. i opened start up apps, and the box to monitor apps is unchecked...
 
 
i did do the rootkit scanner, and it came up with no rootkits, but a few warnings on 
```

[21:04:09] /usr/sbin/unhide [ Warning ]
[21:04:09] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
 
[21:04:10] /usr/sbin/unhide-linux26 [ Warning ]
[21:04:10] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
 
[21:10:04] Info: Starting test name 'passwd_changes'
[21:10:04] Checking for passwd file changes [ Warning ]
[21:10:04] Warning: Users have been added to the passwd file:
 
[21:10:04] Info: Starting test name 'group_changes'
[21:10:04] Checking for group file changes [ Warning ]
[21:10:04] Warning: Groups have been added to the group file:
[21:10:04] clamav:x:126:
 
[21:10:05] Checking for SSH configuration file [ Found ]
[21:10:05] Info: Found SSH configuration file: /etc/ssh/sshd_config
[21:10:05] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[21:10:05] Info: Rkhunter option ALLOW_SSH_PROT_V1 set to '0'.
[21:10:05] Checking if SSH root access is allowed [ Warning ]
[21:10:05] Warning: The SSH and rkhunter configuration options should be the same:
[21:10:05] SSH configuration option 'PermitRootLogin': yes
[21:10:05] Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
 
[21:10:07] Checking /dev for suspicious file types [ Warning ]
[21:10:07] Warning: Suspicious file types found in /dev:
[21:10:07] /dev/shm/pulse-shm-1170254521: data

```
 
these are the warnings that showed up... hmm....

---

### Post by ihaveabu on 2009-05-27
they are reporting the exact same symptoms here as well:
[https://bugs.launchpad.net/ubuntu/+bug/368631](https://bugs.launchpad.net/ubuntu/+bug/368631)
 
when you try to log off, it'll say "A Program is still running Application name is " Unknown".
 
hmm....

---

### Post by doas777 on 2009-05-28
> **ihaveabu said:**
> i don't have that checked. I tried having it checked earlier cuz i was having trouble getting last.fm to start automatically. then i eventually disabled the "check for running programs" thing. i opened start up apps, and the box to monitor apps is unchecked...
 
 
i did do the rootkit scanner, and it came up with no rootkits, but a few warnings on 
```

[21:04:09] /usr/sbin/unhide [ Warning ]
[21:04:09] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
 
[21:04:10] /usr/sbin/unhide-linux26 [ Warning ]
[21:04:10] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
 
[21:10:04] Info: Starting test name 'passwd_changes'
[21:10:04] Checking for passwd file changes [ Warning ]
[21:10:04] Warning: Users have been added to the passwd file:
 
[21:10:04] Info: Starting test name 'group_changes'
[21:10:04] Checking for group file changes [ Warning ]
[21:10:04] Warning: Groups have been added to the group file:
[21:10:04] clamav:x:126:
 
[21:10:05] Checking for SSH configuration file [ Found ]
[21:10:05] Info: Found SSH configuration file: /etc/ssh/sshd_config
[21:10:05] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[21:10:05] Info: Rkhunter option ALLOW_SSH_PROT_V1 set to '0'.
[21:10:05] Checking if SSH root access is allowed [ Warning ]
[21:10:05] Warning: The SSH and rkhunter configuration options should be the same:
[21:10:05] SSH configuration option 'PermitRootLogin': yes
[21:10:05] Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
 
[21:10:07] Checking /dev for suspicious file types [ Warning ]
[21:10:07] Warning: Suspicious file types found in /dev:
[21:10:07] /dev/shm/pulse-shm-1170254521: data

```these are the warnings that showed up... hmm....

those are basically teh same ones I get, except I havn't seen the passwd and group warnings before. did you enable the root account perhaps? not that it matters for this issue.

---

### Post by drs305 on 2009-05-28
> **ihaveabu said:**
> i don't have that checked [saved session]. I tried having it checked earlier cuz i was having trouble getting last.fm to start automatically. then i eventually disabled the "check for running programs" thing. i opened start up apps, and the box to monitor apps is unchecked...

To me, this is a bit counterintuitive, but it seems to work clearing out everything stored in saved sessions. The next time you are about to shut down or reboot:
Close every app you have running.
Go to System, Preferences, Startup Applications (formerly StartUp), Options tab. 
Enable "Automatically remember" (tick it).
Shutdown.
On restart, return and deselect the "Remember" option so it is unchecked.

It seems that just deselecting the option doesn't completely clear the list. You have to 'force' it to remember that nothing is running by the method I described above.

---

### Post by ihaveabu on 2009-05-28
> **drs305 said:**
> To me, this is a bit counterintuitive, but it seems to work clearing out everything stored in saved sessions. The next time you are about to shut down or reboot:
Close every app you have running.
Go to System, Preferences, Startup Applications (formerly StartUp), Options tab. 
Enable "Automatically remember" (tick it).
Shutdown.
On restart, return and deselect the "Remember" option so it is unchecked.
 
It seems that just deselecting the option doesn't completely clear the list. You have to 'force' it to remember that nothing is running by the method I described above.
 
 
is there a way to manually clear all the things stored in the saved session? because i just tried logging off with the box checked, and the coutdown screen for logout froze at 60 seconds, and it wouldn't let me close it or anything. i couldn't shutdown... wtf??

---

### Post by drs305 on 2009-05-28
> **ihaveabu said:**
> is there a way to manually clear all the things stored in the saved session? because i just tried logging off with the box checked, and the coutdown screen for logout froze at 60 seconds, and it wouldn't let me close it or anything. i couldn't shutdown... wtf??

I think it is $HOME/.gconfd/saved_state but as I don't know what else is stored in the file I've never tried to delete it.

I've not seen it freeze the logout and I've played with the setting a lot trying to determine exactly how it worked.

---

### Post by ihaveabu on 2009-05-28
yea it's really annoying cuz right now my computer's running really slow with this thing running in the background. did all this happen when i checked the box to monitor each session? is this some kind of bug with that option, or did i just do something weird?

---

### Post by ihaveabu on 2009-05-28
hmm this is interesting
 
if i disable Remote desktop server on startup, my cpu load goes way down. i'm looking at the file .xsession-errors in my home folder, and it repeats teh line Warning **: Remote Desktop server alread running; exiting ... over and over
 
i disabled auto startup of remote desktop server and the cpu is normal again...
 
is remote desktop server supposed to use a lot of cpu?

---

### Post by ihaveabu on 2009-05-28
ok i seem to have gotten this to work. turns out it probably had nothing to do with hulu or flash player

i deleted the saved state file in gconfd, deleted the xsession errors file, and turned off the auto start of:
Evolution Alarm Notifier
Remote Desktop

and so far so good. 

there has to be a way to manage different sessions right? when i'm in the login screen, i can click options and pick the session i want to log into. but is there a way to delete certain sessions?

---

### Post by ihaveabu on 2009-05-28
i tried googling around, and so far nothing on how to delete saved sessions in jaunty...
 
anyone?

---

### Post by ihaveabu on 2009-05-30
> **ihaveabu said:**
> i tried googling around, and so far nothing on how to delete saved sessions in jaunty...
 
anyone?

help?

---

