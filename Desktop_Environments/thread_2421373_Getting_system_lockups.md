---
title: "Getting system lockups"
date: 2019-06-20
forum: Desktop Environments
---

### Post by bradleypariah on 2019-06-20
I'm wondering if anyone can tell me which logs I should be checking out.  My system has been infrequently freezing. All of a sudden the display  freezes and the mouse won't move. The only solution is resetting the PC.   

The system had been stable for months, and this started happening last  week. Sometimes I'll be reading a PDF when it happens, sometimes I'm  opening YouTube from Firefox.

Since I can't identify a pattern, I don't know what is at fault. Any advice?

My system specs are:
Kubuntu 18.04
i7 2600s 2.8 x8 GHz CPU
8 GB DDR3 RAM
gtx680 4GB DDR5 GPU, 430.26 driver 
SoundBlaster Audigy FX
Cleveland-GL8 Motherboard

---

### Post by TheFu on 2019-06-20
Do the system log files have any hints for the problem?
Are you certain it is a system lockup and not just a GUI issue?
** can you change to a different pty?
** can you ssh into the machine from a different device?

Is the system out of RAM?  What does top/vmstat show for RAM use?  Is the swap being fully used just before the crash?

---

### Post by bradleypariah on 2019-06-20
> **TheFu said:**
> Do the system log files have any hints for the problem?

Although I've been using Linux for ten years, I'm embarrassed to say  that I don't know how to check the system log files.  Would I just **cat  /var/log/syslog | grep **(the date that it happened)?  -or is there a  better log?  That's kinda the heart of my original post.  I simply don't know where to look.

> **TheFu said:**
>  Are you certain it is a system lockup and not just a GUI issue?

No, I'm definitely not certain.  In fact, I did a little test - when  the screen locks up and the keyboard stops responding, I've turned on  my wireless 360 gamepad twice, and both times it blinked then got assigned to Player #1,  which tells me the xpad or xboxdrv modules are still working, but I'm  not positive.

> **TheFu said:**
>  ** can you change to a different pty?

I don't know what that means.  The keyboard and mouse are completely unresponsive, so literally nothing works besides the hardware buttons on the tower.  

> **TheFu said:**
>  ** can you ssh into the machine from a different device?

I don't have SSH set up.  I've never learned how to log in via SSH.  I have another computer (laptop) running 18.04 on the network, but the only method I have ever used to have them interact with one another is KDE Connect.  I can run commands through there.  I suppose I could attempt to restart plasma.  Does restarting plasma reinitialize the GPU driver?

> **TheFu said:**
>  Is the system out of RAM?  What does top/vmstat show for RAM use?  Is the swap being fully used just before the crash?

At the moment, I'm at 4% CPU, about 30% RAM (I have lots of browser tabs with video open), 0% swap, and 0 kbs network.
I have a CPU load monitor in my dock, and it never shows any high usage at the times of crashes, but I'll swap out the widget for something with more information so I can monitor RAM and swap.

---

### Post by TheFu on 2019-06-20
We all use our computers differently. Whatever works is whatever works.

> **bradleypariah said:**
> Although I've been using Linux for ten years, I'm embarrassed to say  that I don't know how to check the system log files.  Woiuld I just **cat  /var/log/syslog | grep **(the date that it happened)?  -or is there a  better log?
```
sudo egrep -i 'error|warn' /var/log/*g
```
FYI, there are only a few reasons to **ever** use cat.  I use tac (reverse output) more than cat. grep can read syslog directly, BTW. Saving an extra process and pipe. I stress this with my students. For some reason, lots of book show the cat {some files}| grep {regex} methods - don't know why.
For HW stuff, need to check the **dmesg** output.

> **bradleypariah said:**
> 
No, I'm definitely not certain.  In fact, I did a little test - when  the screen locks up and the keyboard stops responding, I've turned on  my wireless 360 gamepad twice, and both times it blinked then got assigned to Player #1,  which tells me the xpad or xboxdrv processes are still working, but I'm  not positive.
Sorry, I have no idea what any of that means.

> **bradleypariah said:**
> I don't know what that means.  The keyboard and mouse are completely unresponsive, so literally nothing works besides the hardware buttons on the tower.  
<ctl>-<alt>-F1/F2/F3 ...F9 that's how you change consoles.  Anything else would probably be stopped by the GUI issue, but changing consoles goes through to the OS, unless the OS is locked up too.  That seldom happens IME, the entire OS locking up.

> **bradleypariah said:**
> I don't have SSH set up.  I've never learned how to log in via SSH.  I have another computer (laptop) running 18.04 on the network, but the only method I have ever used to have them interact with one another is KDE Connect.  I can run commands through there.  I suppose I could attempt to restart plasma.  Does restarting plasma reinitialize the GPU driver?
We are very different types of users.  I use ssh at least 100x a day.  I know ZERO about plasma. Sorry. I use fvwm as my window manager and no DE.
How do you transfer files?  Not using NFS or sftp or rsync or sshfs? Ouch.
Setting up ssh is pretty easy.  It can make using a remote desktop secure enough for access over the internet, BTW, assuming ssh-keys are used, never passwords.  3 commands on each machine and it is done. Any interest? Fine if you don't.  Even in the same house, I find it handy to ssh into systems in my office while sitting on the patio or control the music player through an ssh to a r-pi.

> **bradleypariah said:**
> At the moment, I'm at 4% CPU, about 30% RAM (I have lots of browser tabs with video open), 0% swap, and 0 kbs network.
I have a CPU load monitor in my dock, and it never shows any high usage at the times of crashes, but I'll swap out the widget for something with more information so I can monitor RAM and swap.

I'd rather see the **top** output than read an interpretation. CLI commands can be copied/pasted here. GUI stuff cannot.  **free -hm**  Plus, CLI tools work the same on desktop AND servers, where there isn't any GUI.  Only 1 tool to learn.  On a new install a few months ago, the installer only setup a 1.1G swap.  I recreated it to be 4G (a tad larger) after a lock up.

One more thing.  For video issues, check the Xorg.0.log file.  The egrep I gave at the top will hit that file, but it is worth going through it manually if you suspect a video card driver problem.

Anyways, that's enough to check for now.  Need some facts.  Log files should have something, let's hope.

---

### Post by bradleypariah on 2019-06-20
> **TheFu said:**
> We are very different types of users.

My desktop is a gaming HTPC hooked up to a projector.  (Hence me mentioning a wireless Xbox 360 controller earilier)  Fun stuff!
My laptop is an over-powered meme machine.
Both Kubuntu 18.04.
  
> **TheFu said:**
> How do you transfer files? ... Not using NFS or sftp or rsync or sshfs? Ouch.

KDE Connect.  It's ridiculously simple.  I transfer files between my phone and two computers every single day.  
If I'm on my phone, I just long-press the file(s), then choose **Share > KDE Connect (computer name)**. 
If I'm on my desktop or laptop, I just right-click the file(s), then choose **Send to (phone name) via KDE Connect**.  It also works from desktop to desktop.
I never really need to grab a file from my home computer when I'm away.  If I need online access to a certain file, I just throw it on Google Drive before I leave the house.

Here's the output of **sudo egrep -i 'error|warn' /var/log/*g**, redacted to  only include events that possibly happened yesterday (when I last experienced a  lockup):
```

/var/log/auth.log:Jun 19 08:56:22 HP-s5780t dbus-daemon[876]: [system]  Rejected send message, 1 matched rules; type="method_return",  sender=":1.81" (uid=0 pid=3449 comm="/usr/bin/python3  /usr/share/apt-xapian-index/updat" label="unconfined")  interface="(unset)" member="(unset)" error name="(unset)"  requested_reply="0" destination=":1.47" (uid=1000 pid=2385 comm="kded5  [kdeinit5]                                  " label="unconfined")
/var/log/auth.log:Jun 19 11:05:49 HP-s5780t dbus-daemon[876]: [system]  Rejected send message, 2 matched rules; type="method_call",  sender=":1.123" (uid=1000 pid=10711 comm="/usr/bin/pulseaudio  --daemonize=no " label="unconfined")  interface="org.freedesktop.DBus.ObjectManager"  member="GetManagedObjects" error name="(unset)" requested_reply="0"  destination="org.bluez" (bus)
/var/log/auth.log:Jun 19 11:12:34 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 1 matched rules; type="method_return",  sender=":1.77" (uid=0 pid=3563 comm="/usr/bin/python3  /usr/share/apt-xapian-index/updat" label="unconfined")  interface="(unset)" member="(unset)" error name="(unset)"  requested_reply="0" destination=":1.44" (uid=1000 pid=2485 comm="kded5  [kdeinit5]                                  " label="unconfined")
/var/log/auth.log:Jun 19 14:11:55 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 2 matched rules; type="method_call",  sender=":1.125" (uid=1000 pid=11026 comm="/usr/bin/pulseaudio  --daemonize=no " label="unconfined")  interface="org.freedesktop.DBus.ObjectManager"  member="GetManagedObjects" error name="(unset)" requested_reply="0"  destination="org.bluez" (bus)
/var/log/auth.log:Jun 19 14:15:05 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 1 matched rules; type="method_return",  sender=":1.77" (uid=0 pid=3563 comm="/usr/bin/python3  /usr/share/apt-xapian-index/updat" label="unconfined")  interface="(unset)" member="(unset)" error name="(unset)"  requested_reply="0" destination=":1.131" (uid=1000 pid=11217 comm="kded5  [kdeinit5]                                  " label="unconfined")
/var/log/auth.log:Jun 19 16:47:46 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 2 matched rules; type="method_call",  sender=":1.194" (uid=1000 pid=19189 comm="/usr/bin/pulseaudio  --daemonize=no " label="unconfined")  interface="org.freedesktop.DBus.ObjectManager"  member="GetManagedObjects" error name="(unset)" requested_reply="0"  destination="org.bluez" (bus)
/var/log/auth.log:Jun 19 16:50:58 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 1 matched rules; type="method_return",  sender=":1.77" (uid=0 pid=3563 comm="/usr/bin/python3  /usr/share/apt-xapian-index/updat" label="unconfined")  interface="(unset)" member="(unset)" error name="(unset)"  requested_reply="0" destination=":1.200" (uid=1000 pid=19372 comm="kded5  [kdeinit5]                                  " label="unconfined")
/var/log/auth.log:Jun 19 18:17:10 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 0 matched rules; type="method_return",  sender=":1.3" (uid=115 pid=889 comm="avahi-daemon: starting up "  label="unconfined") interface="(unset)" member="(unset)" error  name="(unset)" requested_reply="0" destination=":1.259" (uid=1000  pid=21523 comm="/usr/lib/firefox/firefox " label="unconfined")
/var/log/auth.log:Jun 19 18:17:10 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 0 matched rules; type="method_return",  sender=":1.3" (uid=115 pid=889 comm="avahi-daemon: starting up "  label="unconfined") interface="(unset)" member="(unset)" error  name="(unset)" requested_reply="0" destination=":1.259" (uid=1000  pid=21523 comm="/usr/lib/firefox/firefox " label="unconfined")
/var/log/auth.log:Jun 19 18:25:59 HP-s5780t dbus-daemon[873]: [system]  Rejected send message, 0 matched rules; type="method_return",  sender=":1.3" (uid=115 pid=889 comm="avahi-daemon: starting up "  label="unconfined") interface="(unset)" member="(unset)" error  name="(unset)" requested_reply="0" destination=":1.265" (uid=1000  pid=21523 comm="/usr/lib/firefox/firefox " label="unconfined")
/var/log/auth.log:Jun 19 19:30:03 HP-s5780t dbus-daemon[885]: [system]  Rejected send message, 1 matched rules; type="method_return",  sender=":1.71" (uid=0 pid=2771 comm="/usr/bin/python3  /usr/share/apt-xapian-index/updat" label="unconfined")  interface="(unset)" member="(unset)" error name="(unset)"  requested_reply="0" destination=":1.42" (uid=1000 pid=1430 comm="kded5  [kdeinit5]                                  " label="unconfined")
/var/log/auth.log:Jun 19 21:52:33 HP-s5780t dbus-daemon[885]: [system]  Rejected send message, 2 matched rules; type="method_call",  sender=":1.101" (uid=1000 pid=7640 comm="/usr/bin/pulseaudio  --daemonize=no " label="unconfined")  interface="org.freedesktop.DBus.ObjectManager"  member="GetManagedObjects" error name="(unset)" requested_reply="0"  destination="org.bluez" (bus)
/var/log/auth.log:Jun 19 21:57:24 HP-s5780t dbus-daemon[885]: [system]  Rejected send message, 1 matched rules; type="method_return",  sender=":1.71" (uid=0 pid=2771 comm="/usr/bin/python3  /usr/share/apt-xapian-index/updat" label="unconfined")  interface="(unset)" member="(unset)" error name="(unset)"  requested_reply="0" destination=":1.107" (uid=1000 pid=7826 comm="kded5  [kdeinit5]                                  " label="unconfined")

/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 58 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 58 package 'dpkg':

/var/log/bootstrap.log:Selecting previously unselected package libgpg-error0:amd64.
/var/log/bootstrap.log:Preparing to unpack .../libgpg-error0_1.27-6_amd64.deb ...
/var/log/bootstrap.log:Unpacking libgpg-error0:amd64 (1.27-6) ...
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:Setting up libgpg-error0:amd64 (1.27-6) ...
/var/log/bootstrap.log:update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults

/var/log/kern.log:Jun 18 22:15:06 HP-s5780t kernel: [    4.703327] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Jun 19 08:50:43 HP-s5780t kernel: [    1.801462] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Jun 19 08:50:43 HP-s5780t kernel: [    4.347136] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Jun 19 08:50:43 HP-s5780t kernel: [    4.675446] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Jun 19 11:05:42 HP-s5780t kernel: [ 8106.487124]  nvidia-modeset: WARNING: GPU:0: Lost display notification  (0:0x00000000); continuing.
/var/log/kern.log:Jun 19 11:05:44 HP-s5780t kernel: [ 8108.487476]  nvidia-modeset: ERROR: GPU:0: Idling display engine timed out:  0x0000917d:0:0
/var/log/kern.log:Jun 19 11:05:46 HP-s5780t kernel: [ 8110.487463]  nvidia-modeset: ERROR: GPU:0: Idling display engine timed out:  0x0000917e:0:0
/var/log/kern.log:Jun 19 11:05:50 HP-s5780t kernel: [ 8113.648546]  nvidia-modeset: WARNING: GPU:0: Lost display notification  (0:0x00000000); continuing.
/var/log/kern.log:Jun 19 11:05:52 HP-s5780t kernel: [ 8115.649207]  nvidia-modeset: ERROR: GPU:0: Idling display engine timed out:  0x0000917d:0:0
/var/log/kern.log:Jun 19 11:08:59 HP-s5780t kernel: [    1.801418] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Jun 19 11:08:59 HP-s5780t kernel: [    4.542998] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Jun 19 11:08:59 HP-s5780t kernel: [    4.782898] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Jun 19 18:36:46 HP-s5780t kernel: [    1.802061] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Jun 19 18:36:46 HP-s5780t kernel: [    5.033533] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Jun 19 18:36:46 HP-s5780t kernel: [    5.074716] random: 7 urandom warning(s) missed due to ratelimiting

/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```

Does any of that meaning anything to you?  I'm noticing a lot of PulseAudio, some NVidia stuff, and I don't understand what the errors about my ext4 drive are about.  sdb2 is my slash partition.

Konsole won't let me highlight its text when I run the top command because the output is dynamic.  I ran **top -n 1**:

```

 PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND         
 5000 torriso+  20   0 1922616 274028  96792 S  25.0  3.4   9:29.90 chromium-browse 
 1410 torriso+  20   0 3733452 406924 107600 S  12.5  5.0  16:32.97 kwin_x11        
 4042 torriso+  20   0 1162948 253940  97732 S  12.5  3.1  20:21.43 chromium-browse 
 6998 torriso+  20   0   44236   4124   3428 R  12.5  0.1   0:00.03 top             
 1030 root     -51   0       0      0      0 S   6.2  0.0   7:04.44 irq/27-nvidia   
    1 root      20   0  225340   9084   6740 S   0.0  0.1   0:02.88 systemd         
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd        
    3 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_gp          
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_par_gp      
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:0H-kb 
    8 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_wq    
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.08 ksoftirqd/0     
   10 root      20   0       0      0      0 I   0.0  0.0   0:03.30 rcu_sched       
   11 root      20   0       0      0      0 I   0.0  0.0   0:00.00 rcu_bh          
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/0     
   13 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/0      
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0         
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1         
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/1      
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/1     
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.03 ksoftirqd/1     
   19 root      20   0       0      0      0 I   0.0  0.0   0:00.13 kworker/1:0-mm_ 
   20 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/1:0H-kb 
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/2         
   22 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/2      
   23 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/2     
   24 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/2     
   26 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/2:0H-kb 
   27 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/3 

```

---

### Post by TheFu on 2019-06-20
Did the system crash at Jun 19 11:08:59 or 11:05?  Or did it just go to sleep/standby?

There are reports of the nvidia driver crashing systems [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=905309](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=905309)
Most of the other things seem related to KDE, which I know nothing about.

As far as the disk is concerned, I'd check the SMART data using **smartctl**.

kwin is using almost 4G of RAM!!!  Now I know why NOT to use KDE.  I hope that isn't normal.
On my system:```

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND    
 1815 root      20   0  562828  76940  46524 S   1.0  1.0  78:43.54 Xorg       
 2243 thefu     20   0  171704  19860   8900 S   1.0  0.2   1:56.42 fvwm2
```
is the total WM/GUI handling everything.

---

### Post by bradleypariah on 2019-06-20
> **TheFu said:**
> Did the system crash at Jun 19 11:08:59 or 11:05?  Or did it just go to sleep/standby?

There are reports of the nvidia driver crashing systems [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=905309](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=905309)
Most of the other things seem related to KDE, which I know nothing about.

I don't quite remember.  I'll check into it. Looks like the driver there is a different version than I am using, but I did notice that OBS won't record on this latest driver.  Perhaps it's causing more problems than I realized.  I'll roll back to some other version.

> **TheFu said:**
> As far as the disk is concerned, I'd check the SMART data using **smartctl**.

Will do.

> **TheFu said:**
> kwin is using almost 4G of RAM!!!  Now I know why NOT to use KDE.

LOL. NO.  Haha.  Plasma can run on the leanest hardware, but if you have a lot of RAM, it'll take a little more.  Kinda like Chrome.  KWin in the paste I originally gave you was referring to X11, which probably meant that Steam was downloading a game or something.  Maybe a video was playing on a store page in the background.  Here's another top output:
```

PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND         
26403 torriso+  20   0   44236   3876   3188 R   6.2  0.0   0:00.02 top             
    1 root      20   0  225340   9080   6736 S   0.0  0.1   0:03.02 systemd         
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd        
    3 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_gp          
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_par_gp      
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:0H-kb 
    8 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_wq    
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.31 ksoftirqd/0     
   10 root      20   0       0      0      0 I   0.0  0.0   0:13.66 rcu_sched       
   11 root      20   0       0      0      0 I   0.0  0.0   0:00.00 rcu_bh          
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/0     
   13 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/0      
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0         
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1         
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/1      
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/1     
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.13 ksoftirqd/1     
   19 root      20   0       0      0      0 I   0.0  0.0   0:00.39 kworker/1:0-mm_ 
   20 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/1:0H-kb 
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/2         
   22 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/2      
   23 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/2     
   24 root      20   0       0      0      0 S   0.0  0.0   0:00.05 ksoftirqd/2     
   26 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/2:0H-kb 
   27 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/3         
   28 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/3      
   29 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/3     
   30 root      20   0       0      0      0 S   0.0  0.0   0:00.03 ksoftirqd/3     
   32 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/3:0H-kb
```

Plasma has more customization options than any other desktop, V-Sync actually works, and the list just goes on.  I'm a bit pragmatic.  If I pay for system hardware, I'm going to use it.  I want a beautiful experience.  fvwm, i3, and other window-manager-only experiences seem too utilitarian.  I want ***art***.  I don't doubt at all that your WM has helped you squeak out every last drop of performance from your rig, but to me, running a computer without a DE is like removing the body of your car just to prove that the lighter weight improves gas mileage.  I'll go ahead and enjoy my stylish design, beautiful paint job, and air conditioning, thank you.  ;)  LOL

Back on topic though, thank you very much for the help so far.  I guess this limits the possibilities to bad sectors on my SSD, which I'll know about soon, or it's my GPU, or the GPU driver.  Thanks for pointing me in the right direction.  I'm actually in the middle of taking an LPI Linux+ Certification course online these days, so hopefully soon I'll be able to help someone else as you did with me.  Sadly, no one at all responded to this exact same post over on the Kubuntu forums.

---

### Post by Autodave on 2019-06-21
First of all, listen to TheFu.  From my own way of thinking, this could also be a hardware problem.  Overheating?  Fans clean and operating properly?  Vents unobstructed?

Power supply weak?  Memory chips failing?

A quick way to get an idea whether it is overheating is to remove the cover and run it.  Maybe even a small fan blowing on it.

---

### Post by bradleypariah on 2019-06-21
> **Autodave said:**
> Overheating?  Fans clean and operating properly?  Vents unobstructed?

No.  Usually sitting in the mid-thirties.

> **Autodave said:**
> Power supply weak?  

How would I test that?

> **Autodave said:**
> Memory chips failing?

If I'm on an UEFI system, and I create a bootable ISO, can I still run memtest86 from that?  


P.S. - Since I swapped GPU drivers, I have not yet experienced another lock-up.

---

