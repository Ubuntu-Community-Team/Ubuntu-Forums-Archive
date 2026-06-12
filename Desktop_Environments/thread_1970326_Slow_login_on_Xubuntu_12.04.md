---
title: "Slow login on Xubuntu 12.04"
date: 2012-05-01
forum: Desktop Environments
---

### Post by petehall on 2012-05-01
I have recently installed Xubuntu 12.04. When logging in, the system waits for over a minute during login at the point where the desktop background and a blank menu bar has been drawn. I can move my mouse around during this time.

When I log out and then log in as "Xfce Session", I do not experience this pause. When I then log out and back in as "Xubuntu Session", it's back.

I've attached a bootlog - it looks like Xorg is using a lot of CPU?

Pete

---

### Post by mips on 2012-05-01
That image is to small to see anything.

---

### Post by petehall on 2012-05-01
> **mips said:**
> That image is to small to see anything.

Grrr damn website resizing uploaded images.

Pete

---

### Post by petehall on 2012-05-01
I've solved this by disabling non-essential startup applications and re-enabling them one by one. The culprit is xmodmap. Not sure exactly why, but it's something I can live without, so I've left it disabled.

Pete

---

### Post by mips on 2012-05-01
> **petehall said:**
> I've solved this by disabling non-essential startup applications and re-enabling them one by one. The culprit is xmodmap. Not sure exactly why, but it's something I can live without, so I've left it disabled.

Pete

I don't even have that listed as a startup application?

---

### Post by petehall on 2012-05-01
> **mips said:**
> I don't even have that listed as a startup application?

No, it's something that I added a while back to get the multimedia keys on my keyboard working. It's never given me problems up until now.

Pete

---

### Post by mips on 2012-05-01
> **petehall said:**
> No, it's something that I added a while back to get the multimedia keys on my keyboard working. It's never given me problems up until now.

Pete

Ah, ok.

---

### Post by Orbital_sFear on 2012-05-03
I have the exact same issue.  I've tried disabling all startup apps, that didn't change anything.  Watching xfce boot, it looks like lightdm   --session-child 12 19 is the last thing running before the pause, perhaps that is where the issue is?

I did notice that /etc/init.d/ondemand had a sleep 60 inside the script, disabling that didn't change anything however.

I know the system wasn't doing this when I first started.  This appears to be a new issue.

-Orbital

---

### Post by george1984 on 2012-05-04
I had this problem at login this morning, although I did not wait to see if login eventually completed.

Restored fsarchiver sda5 safety, then installed recent updates one by one.

" LVM2 application library " appears to be the culprit.

Not technical enough to know how to formally report this.

---

### Post by george1984 on 2012-05-05
For test, I installed the few updates outstanding this morning, including "LMV...".

Re-logged in. Blank screen. Restart cured this.

Login using Xfce was instant.
Login using Xubuntu gives Xubuntu wallpaper, mouse curser, but nothing else for period of 30/60 seconds, after which desktop appears as per normal.

For slow old me this is not a problem. 

This machine has drive sda w7 and xubuntu64 12.04, drive sdb mint12 mbr on each drive, Nvidia driver installed.

Another machine of modest spec, no graphics card, one drive only Xubuntu64 12.04 installed does not suffer from this problem - login is immediate.

Is it reasonable to presume that the problem is hardware specific?

---

### Post by george1984 on 2012-05-05
I have been shut down for a while.

This startup, login to Xubuntu was immediate. Unexpected. Therefore I logged out/back in and the 30/60 second delay reappeared. Also a message requesting a restart appeared, although I can think of no reason for this, as I have done nothing but start and login.

So I shutdown for a minute, then started again. Xubuntu login immediate, logout/login ... Xubuntu login immediate.

Back to normal? shhh .. not too loud.

---

### Post by andersgb1 on 2012-05-06
I'm in the same situation with Ubuntu 12.04 here! Mine also takes > 1 minute to login.

Specs: Lenovo W520, Intel i7-2720QM @ 2.20GHz, Nvidia Quadro 2000M

---

### Post by Orbital_sFear on 2012-05-08
It appears that the issue is from 3 method calls timing out.  I changed my /etc/init/lightdm.conf line from:
    exec lightdm
To:
    exec lightdm --log-dir=/var/log/lightdm

Now I had some log information.  Looking at the log I find 3 entries that are clearly causing the issue:
[+11.58s] DEBUG: Greeter quit
[+36.60s] WARNING: Could not call SetXSession: Timeout was reached
[+61.63s] WARNING: Could not call FindUserByName: Timeout was reached
[+61.63s] DEBUG: Dropping privileges to uid 1000
[+61.63s] DEBUG: Restoring privileges
[+86.65s] WARNING: Could not call FindUserByName: Timeout was reached

Notice the times.  I downloaded the source code and dug through it, it looks like there are only 3 dbus calls in the entire code base, and all 3 are timing out.

    answer = g_dbus_proxy_call_sync (proxy,
                                     method,
                                     args,
                                     G_DBUS_CALL_FLAGS_NONE,
                                     1000,
                                     NULL,
                                     &error);
    if (error)
        g_warning ("Could not call %s: %s", method, error->message);

The calls are:    
success = call_method (proxy, "FindUserByName", g_variant_new ("(s)", user), "(o)", &result);
call_method (user->priv->proxy, "SetXSession", g_variant_new ("(s)", xsession), "()", NULL);

I have an encrypted home folder, so to ensure that wasn't jamming me up, I ran the dbus commands directly:
time dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.Accounts /org/freedesktop/Accounts org.freedesktop.Accounts.FindUserByName string:linaro
real    0m25.022s

Exactly the timeout we are seeing in the logs... Now we're getting somewhere.  I'm spending time looking through dbus docs to figure out the problem with these calls.

Edit:
I've been checking my dbus setup with d-feet.  When I first run d-feet, AccountServices has no methods listed.  It appears that  restarting the accounts-daemon in /usr/lib/accountsservices causes the  required dbus methods to show up.  Something is wrong with how this  program starts up.  I'm not sure what the fix is yet.

Edit:
Almost have a fix.  
I reboot my machine.
Wait until login screen comes up.
Hit Ctrl+Alt+F1, log in.

Restart the accounts-daemon:
ps -aef | grep accounts-daemon
root      2908 1  0 12:52 tty1     00:00:00 /usr/lib/accountsservice/accounts-daemon
sudo kill 2908
/usr/lib/accountsservice/accounts-daemon

Ctrl+Alt+F7
Log into XFCE,  INSTANTLY IT LOGS IN!!!!!  I just need to figure out a smooth way to restart the daemon.  I tried doing it inside S99 local, and it didn't work.  Going to keep poking around.  Almost there.

-Orbital

---

### Post by digerati-RC1 on 2012-05-08
Can't thank you enough for looking into this.  I too am having this issue on an A8-3530 laptop.  I thought initially it was my hardware but my proprietary AMD drivers installed (after much deliberation with jockey) and then the slow bootup came.  If you find out what or where this is going let me know and I'll test some things on my end.  Thanks for looking into this, I know it is just a test of patience but I like my distro to be very fast.

---

### Post by Orbital_sFear on 2012-05-08
Alrighty,I have a hack-tastic solution for you guys.

As stated in my previous posts, the issue appears to be how/when accounts service accounts-daemon is started.

This "fix" restarts the accounts-daemon, after a successful login has been detected by lightdm.  After the restart, startxfce4 is called and your window manager boots up.  This works every time for me.

Please note, I log in with the xubuntu session type, if you use a different one, this script will need to be installed in the one you use.  Your xsessions live in /usr/share/xsessions

Applying the "fix":
1. Login
2. cd /usr/share/xsessions
3. Edit xubuntu.desktop:
. Replace the follow:
Exec=startxfce4
To read:
Exec=startxfce4-modified

4. cd /usr/bin
5. Create a file called startxfce4-modified, and store the following script into it:
#!/bin/bash

  #Restart the accounts daemon
ps -aef | grep accounts-daemon | grep -v grep | awk '{print $2}' | xargs kill -9
/usr/lib/accountsservice/accounts-daemon &
startxfce4

6. Ensure the permissions are correct on the script:
sudo chmod 755 /usr/bin/startxfce4-modified

7. Reboot

I hope this helps someone.  I was going nuts with the slow boots.  As stated, this is more of a hack than a fix.  The real fix would be fore accounts-daemon to startup correctly.

EDIT: Bug Report: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/996791)

-Orbital

---

### Post by coleman_ian on 2012-05-08
Awesome instructions Orbital_sFear

I am also suffering this problem.
I tried your workaround from your first post, using tty1 and manually restarting accounts-daemon, which worked.

I also installed your script to achieve the same effect, but it doesn't work.

Strangely, I have a 'pristine' user I just created who logs in perfectly, with or without the modified script.

However my login which suffers the problem still doesn't work even with the script installed. It still delays.

Lightdm log messages from my login:
```
[+150.13s] DEBUG: Using session xubuntu
[+150.13s] DEBUG: Stopping greeter
[+150.13s] DEBUG: Session 2635: Sending SIGTERM
[+150.16s] DEBUG: Session 2635 exited with return value 0
[+150.16s] DEBUG: Greeter quit
[+175.19s] WARNING: Could not call SetXSession: Timeout was reached
[+200.22s] WARNING: Could not call FindUserByName: Timeout was reached
[+200.22s] DEBUG: Dropping privileges to uid 1000
[+200.22s] DEBUG: Restoring privileges
[+225.25s] WARNING: Could not call FindUserByName: Timeout was reached
[+225.25s] DEBUG: Dropping privileges to uid 1000
[+225.25s] DEBUG: Writing /home/ian/.dmrc
[+225.25s] DEBUG: Restoring privileges
[+225.25s] DEBUG: Starting session xubuntu as user ian
```

and from the 'pristine' user - you can see the script does work for this user:

```
[+11.19s] DEBUG: Greeter requests session xubuntu
[+11.19s] DEBUG: Using session xubuntu
[+11.19s] DEBUG: Stopping greeter
[+11.19s] DEBUG: Session 1628: Sending SIGTERM
[+11.21s] DEBUG: Session 1628 exited with return value 0
[+11.21s] DEBUG: Greeter quit
[+11.21s] DEBUG: Dropping privileges to uid 1001
[+11.21s] DEBUG: Restoring privileges
[+11.21s] DEBUG: Dropping privileges to uid 1001
```

Any ideas why I'm not getting some script-love from my normal login?

---

### Post by Orbital_sFear on 2012-05-08
Hey [coleman_ian]("http://ubuntuforums.org/member.php?u=1292427"),

My first question would be, are you sure the script is running?  I recommend adding some debug lines into the script:

#!/bin/bash

echo "Script Started" > /tmp/startxfce4_log

  #Restart the accounts daemon
echo "PID Before Kill" >> /tmp/startxfce4_log
ps -aef | grep accounts-daemon | grep -v grep | awk '{print $2}' >> /tmp/startxfce4_log

#Restart
ps -aef | grep accounts-daemon | grep -v grep | awk '{print $2}' | xargs kill -9
/usr/lib/accountsservice/accounts-daemon &

echo "PID After Kill" >> /tmp/startxfce4_log
 ps -aef | grep accounts-daemon | grep -v grep | awk '{print $2}' >> /tmp/startxfce4_log
 sleep 1

startxfce4


After you boot, go check that the log file exists and that the numbers look possible.  If the tty1 method worked for you, then the script should provide the same results I'm getting.

-Orbital

---

### Post by coleman_ian on 2012-05-09
> **Orbital_sFear said:**
> Hey [coleman_ian]("http://ubuntuforums.org/member.php?u=1292427"),

My first question would be, are you sure the script is running?  I recommend adding some debug lines into the script:

-Orbital

I changed the script to have some debug lines (and added some timing lines) and found that yes it was running, and there is still the delay when logging in.

I also tried manually stopping the process from tty1 and then logging in, which gave me no delay. The process changed from PID 16** to 26** when I manually killed then restarted it.

I have the following two logs:

With no manual kill (ie normal gui login)
```
Script Started
13:57:14.678893897
PID Before Kill
1657
13:57:14.695178949
13:57:14.711257373
13:57:14.712579821
PID After Kill
1657
13:57:14.727990199
```


After manual kill in tty1
```
Script Started
13:59:57.373258145
PID Before Kill
2615
13:59:57.392570473
13:59:57.417445537
13:59:57.420058056
PID After Kill
2615
13:59:57.440810428
```

For my own interest I also tried running the script without restarting the accounts-daemon, ie with the kill only, but still there was the login delay.
```
Script Started
14:06:57.610547014
PID Before Kill
1629
14:06:57.625700170
PID After Kill
1629
14:06:57.655398321
```

Seems like the kill command isn't working, so to confirm here is the line in my script:
```
ps -aef | grep accounts-daemon | grep -v grep | awk '{print $2}' | xargs kill -9
```

It appears that the script is taking a long time to initialise, because when it runs it takes very little time. I'm unsure why the script is taking so long to get called, any ideas on how to find out would be great.

---

### Post by Orbital_sFear on 2012-05-09
Hey coleman,

It looks like there are permission issues going on.  Waking up this morning my script wasn't working either.  I made a quick c wrapper to ensure that my SUID bit was set and things were running as root.

Still have slow boot ups =(  I really don't know what changed, it was working yesterday.

-Orbital

---

### Post by Orbital_sFear on 2012-05-09
Alrighty, I have a more hackish solution that actually works now.  I've done more research.  It looks like the correct time for accounts_daemon to start is while the user owned lightdm --session-child is running.

I made a script which starts just before lightdm, and then watches for lightdm session-child to start.  Keep in mind this is a total hack.  

If anyone has followed my previous post on the startxfce4-modifed script, please remove that script, and set your xsession back to startxfce4.

Brief explanation about what this does.  We will save two script files into your /usr/sbin folder (The same folder where lightdm lives).  Ensure the permissions allow those to run.  Then we will edit your lightdm upstart job to run the scripts.  One of the scripts simply calls the other, and then starts lightdm.  The other runs a ps -aef every 0.5 seconds looking for a lightdm session child that isn't running as root.  When one is found, it restarts the accounts_daemon.

We run in between lightdm because lightdm is ran as root.

Here is the list of things to do:
1. Store the attached tar file.
2. Extract the tar file to /usr/sbin/ (lightdm-safe and lightdm-restart)
3. Ensure the permissions on the files are correct. 
  cd /usr/sbin
  sudo chown root:root lightdm-safe lightdm-restart
  sudo chmod 755 lightdm-safe lightdm-restart
4. Edit /etc/init/lightdm.conf:
Change the line that reads:
exec lightdm
to read:
exec lightdm-safe

You can have extra arguments after the lightdm-safe script, they get passed through to lightdm.  I have --log-file=/var/log/lightdm for arguments on mine.

I've restarted several times with this method, and it works everytime for me.

-Orbital

---

### Post by gdi2k on 2012-05-12
Thank you, this works for me. :-)

---

### Post by asterix2000 on 2012-05-12
Why is xargs started with sudo in your script lightdm-restart on line 10?

(sudo xargs kill -9)

Doesn´t it prompt for a password? Isn´t the the entire script run with root privileges?

---

### Post by Strelock on 2012-05-12
> **Orbital_sFear said:**
> Alrighty, I have a more hackish solution that actually works now.  I've done more research.  It looks like the correct time for accounts_daemon to start is while the user owned lightdm --session-child is running.

I made a script which starts just before lightdm, and then watches for lightdm session-child to start.  Keep in mind this is a total hack.  

If anyone has followed my previous post on the startxfce4-modifed script, please remove that script, and set your xsession back to startxfce4.

Brief explanation about what this does.  We will save two script files into your /usr/sbin folder (The same folder where lightdm lives).  Ensure the permissions allow those to run.  Then we will edit your lightdm upstart job to run the scripts.  One of the scripts simply calls the other, and then starts lightdm.  The other runs a ps -aef every 0.5 seconds looking for a lightdm session child that isn't running as root.  When one is found, it restarts the accounts_daemon.

We run in between lightdm because lightdm is ran as root.

Here is the list of things to do:
1. Store the attached tar file.
2. Extract the tar file to /usr/sbin/ (lightdm-safe and lightdm-restart)
3. Ensure the permissions on the files are correct. 
  cd /usr/sbin
  sudo chown root:root lightdm-safe lightdm-restart
  sudo chmod 755 lightdm-safe lightdm-restart
4. Edit /etc/init/lightdm.conf:
Change the line that reads:
exec lightdm
to read:
exec lightdm-safe

You can have extra arguments after the lightdm-safe script, they get passed through to lightdm.  I have --log-file=/var/log/lightdm for arguments on mine.

I've restarted several times with this method, and it works everytime for me.

-Orbital

Thanks! That worked for me too!

---

### Post by ambrosa on 2012-05-14
Hi Guys.
Also my system has this bug.

But I think that problems is involved for a package update.

Yesterday I migrated from Kubuntu 11.10 to Xubuntu 12.04.
I've made a fresh Xubuntu 12.04 install from Live CD formatting my "/" partition.

After install (without make any package update), my system was fine for hours. Login/logout many time without any issue.

Yesterday evening I applied the proposal update (61 packages involved).
After that the bug is come !

I've reinstalled again Xubuntu and I care about this.
Same thing: all works fine since I make package update. After that ... login bug.

So I suppose that a newer package cause this bug.
But I don't know which package..... :-(

---

### Post by pjot on 2012-05-14
I reset my old account here just to thank you, this issue has been bothering me since I upgraded to 12.04 and now this fixes it. Thank you!

---

### Post by klauskudielka on 2012-05-15
With the workarounds posted above, I still have lightdm freezing now and then after logout.

I downloaded, compiled, and installed accountsservice-0.6.20 from [http://www.freedesktop.org/software/accountsservice/](http://www.freedesktop.org/software/accountsservice/) into /usr/local/etc.

Now **all** freezes, both at login and logout, are gone.

(The xubuntu accountsservice is still at 0.6.15 and probably needs an update.)

---

### Post by tdlam on 2012-05-16
I have the same issue on MY XUBUNTU 12.04 install. I have an upgrade running form 11.10 to 12.04. I noticed that it takes what I consider a long time to 
1. Get to log in screen
2. and after log in get to completed desktop. Now as I am used to using windows where this is typical behavior its not a deal breaker for me but it IS noticeable compared to other distros I have tried. I'm a little hesitant to try a hack in the fear it could bonk my system. But I thought I would throw my situation into this forum too to let folks know that it appears to be NOT an isolated incident.
However that said...big thanks to the person who came up to with the workaround.

---

### Post by ambrosa on 2012-05-16
Dear klauskudielka

I've tried to compile account service 0.6.20 with success but I've a problem.


First of all a little howto for other guys:

[I]sudo apt-get install build-essential
sudo apt-get install intltool
sudo apt-get install libgtk2.0-dev
sudo apt-get install libpolkit-gobject-1[/I]

download [http://www.freedesktop.org/software/accountsservice/accountsservice-0.6.20.tar.xz](http://www.freedesktop.org/software/accountsservice/accountsservice-0.6.20.tar.xz) and extract with
[I]tar xvf accountsservice-0.6.20.tar.xz
cd accountsservice-0.6.20
./configure
make[/I]


now I've simply changed the original daemon with newer (making a backup first)
[I]sudo cp -a /usr/lib/accountsservice/accounts-daemon /usr/lib/accountsservice/accounts-daemon.bak
sudo killall accounts-daemon
sudo cp src/accounts-daemon /usr/lib/accountsservice/accounts-daemon[/I]

and finally I restart my system.

The problem is that login manager shows ALL accounts (see image).

**But you have right: slow login/logout DISAPPEAR !! :-) :-) :-)**

Do you know which configure option I need to set to avoid all users in login manager ?
Or the problem is regarding old configuration (0.6.15) files ?

[[img]http://s17.postimage.org/etip4hmbv/20120516_182534.jpg[/img]](http://postimage.org/image/etip4hmbv/)

EDIT: tried with *./configure --prefix=/usr* but no change

---

### Post by klauskudielka on 2012-05-17
> **ambrosa said:**
> 

Do you know which configure option I need to set to avoid all users in login manager ?



 I guess there is some xubuntu-specific configuration. Probably you need to get  the xubuntu source package (accountsservice) and see what they did with the original 0.6.15 source.

For me, the login screen is a cosmetic issue, at least it works.

Klaus

---

### Post by MLX on 2012-05-18
I installed Xubuntu 12.04 on a laptop and a desktop...only saw the slow login issue on the desktop. Other than hardware the difference in the setup was that I had multiple user accounts on the laptop and only a single user on the desktop. I just added another user to the desktop and the problem seems to be gone.

---

### Post by ambrosa on 2012-05-19
> **MLX said:**
> I installed Xubuntu 12.04 on a laptop and a desktop...only saw the slow login issue on the desktop. Other than hardware the difference in the setup was that I had multiple user accounts on the laptop and only a single user on the desktop. I just added another user to the desktop and the problem seems to be gone.

Not for me.

I started with one user = slow login
Then I add 2 different new fake users = nothing change: slow login as before

---

### Post by coleman_ian on 2012-05-20
> **Orbital_sFear said:**
> Alrighty, I have a more hackish solution that actually works now.  I've done more research.  It looks like the correct time for accounts_daemon to start is while the user owned lightdm --session-child is running.

I made a script which starts just before lightdm, and then watches for lightdm session-child to start.  Keep in mind this is a total hack.  

If anyone has followed my previous post on the startxfce4-modifed script, please remove that script, and set your xsession back to startxfce4.

Brief explanation about what this does.  We will save two script files into your /usr/sbin folder (The same folder where lightdm lives).  Ensure the permissions allow those to run.  Then we will edit your lightdm upstart job to run the scripts.  One of the scripts simply calls the other, and then starts lightdm.  The other runs a ps -aef every 0.5 seconds looking for a lightdm session child that isn't running as root.  When one is found, it restarts the accounts_daemon.

We run in between lightdm because lightdm is ran as root.

Here is the list of things to do:
1. Store the attached tar file.
2. Extract the tar file to /usr/sbin/ (lightdm-safe and lightdm-restart)
3. Ensure the permissions on the files are correct. 
  cd /usr/sbin
  sudo chown root:root lightdm-safe lightdm-restart
  sudo chmod 755 lightdm-safe lightdm-restart
4. Edit /etc/init/lightdm.conf:
Change the line that reads:
exec lightdm
to read:
exec lightdm-safe

You can have extra arguments after the lightdm-safe script, they get passed through to lightdm.  I have --log-file=/var/log/lightdm for arguments on mine.

I've restarted several times with this method, and it works everytime for me.

-Orbital




Perfect, works for me. Totally hack but thanks a lot for looking into this. Hopefully the bug is fixed soon.

---

### Post by thomgou on 2012-05-27
Slow Login 3 The Revenge
I applied the two fix and it worked for some time but it is back again. It looks like a bad terror movie

---

### Post by thomgou on 2012-05-27
> **ambrosa said:**
> Dear klauskudielka

I've tried to compile account service 0.6.20 with success but I've a problem.


First of all a little howto for other guys:

[I]sudo apt-get install build-essential
sudo apt-get install intltool
sudo apt-get install libgtk2.0-dev
sudo apt-get install libpolkit-gobject-1[/I]

download [http://www.freedesktop.org/software/accountsservice/accountsservice-0.6.20.tar.xz](http://www.freedesktop.org/software/accountsservice/accountsservice-0.6.20.tar.xz) and extract with
[I]tar xvf accountsservice-0.6.20.tar.xz
cd accountsservice-0.6.20
./configure
make[/I]


now I've simply changed the original daemon with newer (making a backup first)
[I]sudo cp -a /usr/lib/accountsservice/accounts-daemon /usr/lib/accountsservice/accounts-daemon.bak
sudo killall accounts-daemon
sudo cp src/accounts-daemon /usr/lib/accountsservice/accounts-daemon[/I]

and finally I restart my system.

The problem is that login manager shows ALL accounts (see image).

**But you have right: slow login/logout DISAPPEAR !! :-) :-) :-)**

Do you know which configure option I need to set to avoid all users in login manager ?
Or the problem is regarding old configuration (0.6.15) files ?

[[IMG]http://s17.postimage.org/etip4hmbv/20120516_182534.jpg[/IMG]]("http://postimage.org/image/etip4hmbv/")

EDIT: tried with *./configure --prefix=/usr* but no change

Dear ambrosa
  I think is something missing at  *sudo apt-get install libpolkit-gobject-1, there are two on my system **libpolkit-gobject-1-0 and *[I]libpolkit-gobject-1-dev, I installed both.  why did you copy the accounts-daemon instead of  ran make install? I am a newbie you know :confused:

It works properly with the same problem at the login manager 
 Thanks for the howto
[/I]

---

### Post by adamiak on 2012-06-05
Instead of 
> 
sudo apt-get install build-essential
sudo apt-get install intltool
sudo apt-get install libgtk2.0-dev
sudo apt-get install libpolkit-gobject-1


it is enough to just run:

**sudo apt-get build-dep accountsservice**

and then proceed with next steps (downloading, compiling).

I can confirm that this solution **works** (quick login, yeah!), but unfortunately I also see all other accounts on login window.

---

### Post by Sethramoth on 2012-06-10
Oxerror over at [_launchpad_]("https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791") says that the problem is a syptom of the updated glib-networking extension (these are installed as a part of "recommended updates").

Specifically the 2.32.1-ubuntu1 version of:

glib-networking
glib-networking-common
glib-networking-services

They seem to only affect the 64-bit version of Xubuntu.

A temporary workaround is to install 2.32.1-1 of these packages.

---

### Post by ambrosa on 2012-07-05
> **Sethramoth said:**
> Oxerror over at [_launchpad_]("https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791") says that the problem is a syptom of the updated glib-networking extension (these are installed as a part of "recommended updates").

Specifically the 2.32.1-ubuntu1 version of:

glib-networking
glib-networking-common
glib-networking-services

They seem to only affect the 64-bit version of Xubuntu.

A temporary workaround is to install 2.32.1-1 of these packages.

Installed.
Nothing change.
Slow login still here

---

### Post by asedas on 2012-07-16
ok, workaround by **ambrosa** worked. have Xubuntu 12.04 64-bit. I also see a lot of accounts on login screen... but it's faster :)

---

### Post by usrflo on 2012-07-19
As long as those slow logins happen with Xubuntu 12.04, 64-bit you can use the following patch as a workaround according to [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791) (lightdm is patched):
  
```
sudo add-apt-repository ppa:andreas-diesner/lightdm-fix-temporary
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jbowen7 on 2012-08-09
Same bug affects me. x86_64
I've been following this for a while now.. I'm sort of shocked this isn't fixed upstream yet. packages updated as of Aug-08-12


for now, my solution:

login as root on tty1
```
pkill accounts
```

---

### Post by Numer0bis on 2012-08-10
> **usrflo said:**
> As long as those slow logins happen with Xubuntu 12.04, 64-bit you can use the following patch as a workaround according to [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791) (lightdm is patched):
  
```
sudo add-apt-repository ppa:andreas-diesner/lightdm-fix-temporary
sudo apt-get update
sudo apt-get upgrade
```

Thanks for the fix. Worked for me as well

---

### Post by lukasblunschi on 2012-08-13
> **usrflo said:**
> As long as those slow logins happen with Xubuntu 12.04, 64-bit you can use the following patch as a workaround according to [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791) (lightdm is patched):
  
```
sudo add-apt-repository ppa:andreas-diesner/lightdm-fix-temporary
sudo apt-get update
sudo apt-get upgrade
```

worked for me too. thanks.

---

### Post by holadebob on 2012-09-29
I got a nice fast bootup after a clean Xubuntu 12.04 install, but after (only) installing amd drivers for HD5400, the delay after log in was really long.

 	Code:
 	sudo add-apt-repository ppa:andreas-diesner/lightdm-fix-temporary sudo apt-get update sudo apt-get upgrade 
This brought me back into the 21st century. THANK YOU, usrflo!!!

---

### Post by looniichoon on 2012-11-11
Patched package from PPA worked fine for me too. Thank you very much.

---

### Post by jkorkean on 2012-12-08
Installing accountsservice packages from quantal fixed the problem for me:

[http://packages.ubuntu.com/quantal/accountsservice](http://packages.ubuntu.com/quantal/accountsservice)
[http://packages.ubuntu.com/quantal/libaccountsservice0](http://packages.ubuntu.com/quantal/libaccountsservice0)

---

### Post by Surabaya on 2012-12-31
Hello, 

Like many others I have this bug. I had it under Mint Mate 13, Mint XFCE 13, and Mint 14 Mate. Everytime this bug appears after the first big update. Before the boot was crazy fast. 
All solution here and in others places did not worked for me. 
The only trick I found: installing Preload. And my boot is faster but not amaising. 

The simple question is: when they will really take care of this huge bug in lauch pad? What are they doing.
I know this is not here that i will have an answer, but i am very upset against them: this bug is official since more than 8 months.

Now I am an happy user of Mandrive, and there is nooooooooo slooooooow login problem.

---

### Post by rnerwein on 2012-12-31
> **Surabaya said:**
> Hello, 

Like many others I have this bug. I had it under Mint Mate 13, Mint XFCE 13, and Mint 14 Mate. Everytime this bug appears after the first big update. Before the boot was crazy fast. 
All solution here and in others places did not worked for me. 
The only trick I found: installing Preload. And my boot is faster but not amaising. 

The simple question is: when they will really take care of this huge bug in lauch pad? What are they doing.
I know this is not here that i will have an answer, but i am very upset against them: this bug is official since more than 8 months.

Now I am an happy user of Mandrive, and there is nooooooooo slooooooow login problem.
hi
what is your definition of slooooooooooooooooooooooooooooooooooooooow
cheers

---

### Post by Surabaya on 2012-12-31
> **rnerwein said:**
> hi
what is your definition of slooooooooooooooooooooooooooooooooooooooow
cheers

Hi rnerwein

After I enter my login and pass, no shortcut in desktop, dasboard empty, i cannot click anything... during almost a minute. 
Before the first big update: everything was almost instant,whatever i use Ubutu or Mint. 

For information, I used this computer 3 years with Mint 9 LTS with exactlly the same hardware and software installed: i never had this problem.

---

### Post by rnerwein on 2013-01-01
> **Surabaya said:**
> Hi rnerwein

After I enter my login and pass, no shortcut in desktop, dasboard empty, i cannot click anything... during almost a minute. 
Before the first big update: everything was almost instant,whatever i use Ubutu or Mint. 

For information, I used this computer 3 years with Mint 9 LTS with exactlly the same hardware and software installed: i never had this problem.
hi
is it possible to login to your box via ssh to another account and switch to a root shell -
sudo /bin/bash
then run strace -ff -r -t -o your_debugfie -p PID_of_ligthdm
strace gives you the systemcalls of lightdm, ff -> follow childs (own debug file per child)
-r timedifference -t timestamp -p PID
then you have to login to your account.
in the created files (it's human readable) you can see where the time is spent.
cheers

---

### Post by Surabaya on 2013-01-09
Hi, 

And thiqnk you for your help. 
I just make a fresh install of Mint 13 LTS Mate 32 Bits, to try your tip. 
But I have no ligthdm pid when i make a top; What should i type instead?

Thank you. 

> **rnerwein said:**
> hi
is it possible to login to your box via ssh to another account and switch to a root shell -
sudo /bin/bash
then run strace -ff -r -t -o your_debugfie -p PID_of_ligthdm
strace gives you the systemcalls of lightdm, ff -> follow childs (own debug file per child)
-r timedifference -t timestamp -p PID
then you have to login to your account.
in the created files (it's human readable) you can see where the time is spent.
cheers

---

### Post by Rsxhawk on 2013-01-10
> **rnerwein said:**
> hi
what is your definition of slooooooooooooooooooooooooooooooooooooooow
cheers


I have this problem with the Ubuntu 12.04 cinnamon remix as well.  I think a good definition of slow would be the fact that I dropped $600 bucks on new hardware and am running Ubuntu off an SSD now and I still have to put up with this 60 second login problem.  

Don't get me wrong, my rig boots up TO the login screen in under 10 seconds, but actually logging in takes longer?  That's unacceptable.  I'll run the suggested updates above and see if this fixes it.

---

### Post by Surabaya on 2013-01-10
> **Rsxhawk said:**
> I have this problem with the Ubuntu 12.04 cinnamon remix as well.  I think a good definition of slow would be the fact that I dropped $600 bucks on new hardware and am running Ubuntu off an SSD now and I still have to put up with this 60 second login problem.  

Don't get me wrong, my rig boots up TO the login screen in under 10 seconds, but actually logging in takes longer?  That's unacceptable.  I'll run the suggested updates above and see if this fixes it.

Hi, 

As you say: this is unacceptable. And no one looks to be willing on lauchpad to correct this bug since more than 6 months...
Hope the updates work for you. For me no.
Let us know.

---

### Post by ChrisHodgesUK on 2013-02-06
> **usrflo said:**
> As long as those slow logins happen with Xubuntu 12.04, 64-bit you can use the following patch as a workaround according to [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791) (lightdm is patched):
  
```
sudo add-apt-repository ppa:andreas-diesner/lightdm-fix-temporary
sudo apt-get update
sudo apt-get upgrade
```


The patch usrflo posted above worked fine for me for months, but  it's recently stopped (an XFCE session is fine).  Is anyone else seeing  the same thing?  Have any of the other suggested fixes dealt with this? (despite what it says on my profile, I'm on 12.04 x64 on my desktop machine)

---

### Post by saou on 2013-02-06
> **ChrisHodgesUK said:**
> The patch usrflo posted above worked fine for me for months, but  it's recently stopped (an XFCE session is fine).  Is anyone else seeing  the same thing?  Have any of the other suggested fixes dealt with this? (despite what it says on my profile, I'm on 12.04 x64 on my desktop machine)

 I have the same problem on my laptop running 12.04 x64 -- the fix in post #39 worked until a couple of days ago and then it stopped working after an update.  But curiously I've never had this problem on my desktop (also running 12.04 x64).  For now I found that the fix in  post #40 works:  After lightdm comes on, switch to tty1 and 'sudo pkill accounts'.  This fixes seems to survive after logout, but not reboot/restart.

---

### Post by gdi2k on 2013-02-07
Same here - the fix worked until a few days ago, then stopped working. Grr.

I have a machine that's been upgraded to 12.10 and it's still going strong with the original fix.

---

### Post by adiesner on 2013-02-07
> **ChrisHodgesUK said:**
> The patch usrflo posted above worked fine for me for months, but  it's recently stopped (an XFCE session is fine).  Is anyone else seeing  the same thing?  Have any of the other suggested fixes dealt with this? (despite what it says on my profile, I'm on 12.04 x64 on my desktop machine)

I just updated my repository **lightdm-fix-temporary** and uploaded a newer version with the old patch. Currently the build systems says the build will be finished 2013-02-07 8pm CEST

So this should be working soon again:
```

sudo add-apt-repository ppa:andreas-diesner/lightdm-fix-temporary
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by saou on 2013-02-07
> **adiesner said:**
> I just updated my repository **lightdm-fix-temporary** and uploaded a newer version with the old patch. Currently the build systems says the build will be finished 2013-02-07 8pm CEST

I got the updated patch earlier today via system updater.  I can confirm that it works perfectly, even after logout/reboot.  THANKS!

Now, if somebody could fix this (LTS!) upstream -- and how come my desktop has never had this problem?!

---

### Post by saou on 2013-03-30
Xubuntu's 12.04 update for March 29 contains an update for lightdm, and after I  clicked "yes" and reboot, the slooooow login returns   ;_;

---

### Post by emiguel on 2013-04-03
Same thing here :(

---

### Post by spif17 on 2013-04-06
> **saou said:**
> Xubuntu's 12.04 update for March 29 contains an update for lightdm, and after I  clicked "yes" and reboot, the slooooow login returns   ;_;
Same thing.

---

### Post by adiesner on 2013-04-18
> **saou said:**
> Xubuntu's 12.04 update for March 29 contains an update for lightdm, and after I  clicked "yes" and reboot, the slooooow login returns   ;_;

I updated my ppa:andreas-diesner/lightdm-fix-temporary with a new patched update on the 10th of april. Couldn't do it sooner as I was on vacation - sorry.

---

