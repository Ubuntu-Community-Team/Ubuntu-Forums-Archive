---
title: "cannot login myuser gui account"
date: 2012-09-23
forum: Desktop Environments
---

### Post by kelmark2180 on 2012-09-23
I don't know what changed, but I aam not able to login to my normal user account. I have two accounts don & donald. In xubuntu when I try to login to don I key pw, screen blanks and I'm right back to login screen. Yes, I changed password for don in a terminal under login donald w/su don as root. I know I am keying the pw correctly.

I looked at lightdm.conf and saw lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative 

That stopped me, simple just got complicated. This is Ubuntu 12.04.1 LTS under xubuntu & NO UNITY.

Files:
```

don@don-us64:~$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
don@don-us64:~$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
autologin-guest=false
autologin-user=don
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
don@don-us64:~$ ls -l /etc/lightdm
total 12
-rw-r--r-- 1 root root 175 Apr 10 12:32 lightdm.conf
lrwxrwxrwx 1 root root  55 Apr 10 11:45 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r-- 1 root root 683 Feb 24  2012 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r-- 1 root root 456 Mar 22  2012 users.conf
don@don-us64:~$ cat /etc/alternatives/lightdm-gtk-greeter-config-derivative
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/xfce4/backdrops/xubuntu-precise-right.png
theme-name=Greybird-lightdm
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true
don@don-us64:~$ 

```
I would appreciate any help since I'm at a basic install w/o the don login.
Thanks, Don

---

### Post by Bashing-om on 2012-09-23
Don;

 Hello....see if this gets ya back ..

Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

           HTH <==BDQ

---

### Post by steeldriver on 2012-09-23
it sounds to me more like a session startup problem than an authentication problem

first thing I would check is ownership / permissions on your .Xauthority file

```
ls -l /home/don/.Xauthority
```

if that looks OK I would move on to the greeter log and see if there are any clues there

---

### Post by kelmark2180 on 2012-09-24
steeldriver; Thanks for help, I guess root rw is ok?
don@don-us64:/var$ ls -l /home/don/.Xauthority
-rw------- 1 root root 53 Sep 22 12:38 /home/don/.Xauthority

Thanks, I Never knew a greeter.log existed. The x-0greeter.log could not find some .png splash files, (I'll look) but I doubt a warning killed the login AND I saw some authentication error for user: don 
(lightdm-gtk-greeter:2611): Gtk-WARNING **: Theme parsing error:

```
Some of my lightdm.log:
[+226.23s] DEBUG: Started session 2384 with service 'lightdm', username
'lightdm'
[+226.32s] DEBUG: Session 2384 authentication complete with return value
0: Success
[+226.32s] DEBUG: Greeter authorized
[+226.32s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+226.32s] DEBUG: Session 2384 running command
/usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+226.61s] DEBUG: Greeter connected version=1.2.1
[+226.61s] DEBUG: Greeter connected, display is ready
[+226.61s] DEBUG: New display ready, switching to it
[+226.61s] DEBUG: Activating VT 7
[+226.61s] DEBUG: Stopping greeter display being switched from
[+227.60s] DEBUG: Greeter start authentication for don
[+227.60s] DEBUG: Started session 2430 with service 'lightdm', username
'don'
[+227.62s] DEBUG: Session 2430 got 1 message(s) from PAM
[+227.62s] DEBUG: Prompt greeter with 1 message(s)
[+259.91s] DEBUG: Continue authentication
[+261.91s] DEBUG: Session 2430 authentication complete with return value
7: Authentication failure
[+261.91s] DEBUG: Authenticate result for user don: Authentication failure
[+261.91s] DEBUG: Session 2430 exited with return value 1
```

I suppose I should try the other post and change my password, but I thought I had accomplished that through the terminal. 

THIS puzzles me at begining of log with the sutologin stuff, since I have change that to allow a password and when it drops the root priveliges??
The only occurence of > Starting new display for automatic login as user don is in the begining of lightdm.log

RE:
```
lightdm.log
[+0.02s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.02s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1101
[+0.02s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.02s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registered seat module xlocal
[+0.02s] DEBUG: Registered seat module xremote
[+0.02s] DEBUG: Adding default seat
[+0.02s] DEBUG: Starting seat
[+0.02s] DEBUG: Starting new display for automatic login as user don
[+0.02s] DEBUG: Starting local X display
[+0.04s] DEBUG: X server :0 will replace Plymouth
[+0.08s] DEBUG: Using VT 7
[+0.08s] DEBUG: Activating VT 7
[+0.08s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.08s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.08s] DEBUG: Launching X Server
[+0.08s] DEBUG: Launching process 1124: /usr/bin/X :0 -auth
/var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.08s] DEBUG: Waiting for ready signal from X server :0
[+0.08s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.08s] DEBUG: Registering seat with bus path
/org/freedesktop/DisplayManager/Seat0
[+2.34s] DEBUG: Got signal 10 from process 1124
[+2.34s] DEBUG: Got signal from X server :0
[+2.34s] DEBUG: Stopping Plymouth, X server is ready
[+2.37s] DEBUG: Connecting to XServer :0
[+2.49s] DEBUG: Automatically logging in user don
[+2.49s] DEBUG: Started session 1278 with service 'lightdm-autologin',
username 'don'
[+2.65s] DEBUG: Session 1278 authentication complete with return value
0: Success
[+2.65s] DEBUG: Autologin user don authorized
[+2.75s] DEBUG: Autologin using session xubuntu
[+2.79s] DEBUG: Dropping privileges to uid 1000
[+2.79s] DEBUG: Restoring privileges
[+2.80s] DEBUG: Dropping privileges to uid 1000
[+2.80s] DEBUG: Writing /home/don/.dmrc
[+2.85s] DEBUG: Restoring privileges
[+2.94s] DEBUG: Starting session xubuntu as user don
[+2.94s] DEBUG: Session 1278 running command /usr/sbin/lightdm-session
startxfce4
[+3.06s] DEBUG: New display ready, switching to it
[+3.06s] DEBUG: Activating VT 7
[+3.06s] DEBUG: Registering session with bus path
/org/freedesktop/DisplayManager/Session0
[+3.06s] DEBUG: Session 1278 exited with return value 1
[+3.06s] DEBUG: User session quit
```

I guess I'm no self trained log looker,
Thanks for your help, I'll keep pokin and hopin
Don

---

### Post by jrog on 2012-09-24
> **kelmark2180 said:**
> steeldriver; Thanks for help, I guess root rw is ok?
don@don-us64:/var$ ls -l /home/don/.Xauthority
-rw------- 1 root root 53 Sep 22 12:38 /home/don/.Xauthority
That file should not be owned by root. You can either change ownership to your user as follows:

```
sudo chown don:don /home/don/.Xauthority
```or perhaps simply remove it and restart (this would require the command 'rm -f /home/don/.Xauthority', without the quotes).

---

### Post by steeldriver on 2012-09-24
^^^ exactly this (except I think that you can rm the file without sudo - since you own the parent dir)

---

### Post by jrog on 2012-09-24
> **steeldriver said:**
> ^^^ exactly this (except I think that you can rm the file without sudo - since you own the parent dir)
You're right; I'll remove the unnecessary 'sudo' from the prior post. Thanks!

---

### Post by kelmark2180 on 2012-09-24
Thanks So Very Much to both: steeldriver and jrog!
I had to ctrl/alt/f1 into a TTY terminal (again) and did the rm -f /home/don/.Xauthority and sudo restart lightdm and I NOW have my desktop BACK.

I have no idea how the .Xauthority was rw by root, but you solved it!

Thanks again, Don 
(I'll try to mark this as SOLVED)

---

### Post by jrog on 2012-09-24
Glad it worked out!

---

### Post by JKyleOKC on 2012-09-24
> **kelmark2180 said:**
> I have no idea how the .Xauthority was rw by root, but you solved it!This is probably how it happened, from your initial post above: > Yes, I changed password for don in a terminal under login donald w/su don **as root**.If you used "sudo" to get there, it probably set root as the user and group when changing the password. Fortunately, you now know how to fix it if it ever happens again...

---

### Post by kelmark2180 on 2012-09-24
> **JKyleOKC said:**
> This is probably how it happened, from your initial post above: If you used "sudo" to get there, it probably set root as the user and group when changing the password. Fortunately, you now know how to fix it if it ever happens again...
I checked, (all is well):
don@don-us64:~$ find / -iname .xauthority -print 2>/dev/null
/home/don/.Xauthority
/home/donald/.Xauthority
/home/smbuser/.Xauthority
don@don-us64:~$ ls -l /home/don/.Xauthority
-rw------- 1 don don 53 Sep 24 20:24 /home/don/.Xauthority
don@don-us64:~$ ls -l /home/donald/.Xauthority
-rw------- 1 donald donald 53 Sep 24 12:41 /home/donald/.Xauthority
don@don-us64:~$ ls -l /home/smbuser/.Xauthority
-rw------- 1 smbuser smbuser 0 Sep 23 06:00 /home/smbuser/.Xauthority
Thanks, Don

---

