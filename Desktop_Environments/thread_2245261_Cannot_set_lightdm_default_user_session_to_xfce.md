---
title: "Cannot set lightdm default user session to xfce"
date: 2014-09-22
forum: Desktop Environments
---

### Post by henrylaw on 2014-09-22
I'm customising an Ubuntu 14.04 desktop environment for a specific group of users who require the xfce desktop, using the gtk greeter. I want to make xfce the default for all users, and despite doing what I think is everything required by the documentation new users still get the ubuntu desktop when they log in. Can someone tell me where I'm going wrong?

lightdm version is [COLOR=#0000ff]1.10.1-0ubuntu1[/COLOR]

List of available desktops:

[COLOR=#0000ff]ls /usr/share/xsessions/*.desktop
/usr/share/xsessions/ubuntu.desktop  /usr/share/xsessions/xubuntu.desktop
/usr/share/xsessions/xfce.desktop[/COLOR]

All configuration files which have a user-session key are set to xfce:
```
for D in /usr/share/lightdm/lightdm.conf.d /usr/local/share/lightdm/lightdm.conf.d /etc/xdg/lightdm/lightdm.conf.d/usr/local/share/lightdm/lightdm.conf.d /etc/lightdm; do echo "Scanning $D"; grep user-session $D/*.conf; done
Scanning /usr/share/lightdm/lightdm.conf.d
/usr/share/lightdm/lightdm.conf.d/70-sirius.conf:user-session=xfce
Scanning /usr/local/share/lightdm/lightdm.conf.d
grep: /usr/local/share/lightdm/lightdm.conf.d/*.conf: No such file or directory
Scanning /etc/xdg/lightdm/lightdm.conf.d/usr/local/share/lightdm/lightdm.conf.d
grep: /etc/xdg/lightdm/lightdm.conf.d/usr/local/share/lightdm/lightdm.conf.d/*.conf: No such file or directory
Scanning /etc/lightdm
/etc/lightdm/lightdm.conf:user-session=xfce
/etc/lightdm/lightdm-gtk-greeter.conf:user-session=xfce
```
Extract from /var/log/lightdm/lightdm.log for the first login of a newly-created user (you can see the configuration files listed above being scanned):
```
[+0.02s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/70-sirius.conf
[+0.02s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.02s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.02s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
...
[+0.76s] DEBUG: Seat: Display server ready, starting session authentication
[+0.77s] DEBUG: Session pid=1196: Started with service 'lightdm-greeter', username 'lightdm'
[+0.83s] DEBUG: Session pid=1196: Authentication complete with return value 0: Success
... I'm using the lightdm-gtk-greeter, hence the references to lightdm-gtk-greeter.conf earlier ...

[+5.62s] DEBUG: Session pid=1196: Greeter start authentication for testuser
[+5.62s] DEBUG: Session pid=1519: Sending SIGTERM
[+5.62s] DEBUG: Session pid=1521: Started with service 'lightdm', username 'testuser'
[+5.63s] DEBUG: Session pid=1519: Terminated with signal 15
[+5.63s] DEBUG: Session: Failed during authentication
... no idea what that's about. On the greeter screen it was a clean login ...

[+5.63s] DEBUG: Seat: Session stopped
[+5.64s] DEBUG: Session pid=1521: Got 1 message(s) from PAM
[+5.64s] DEBUG: Session pid=1196: Prompt greeter with 1 message(s)
[+9.26s] DEBUG: Session pid=1196: Continue authentication
[+9.34s] DEBUG: Session pid=1521: Authentication complete with return value 0: Success
[+9.34s] DEBUG: Session pid=1196: Authenticate result for user testuser: Success
[+9.34s] DEBUG: Session pid=1196: User testuser authorized
[+9.34s] DEBUG: Session pid=1196: Greeter sets language en_GB
[+9.38s] DEBUG: Session pid=1196: Greeter requests session ubuntu
[+9.41s] DEBUG: Writing /home/testuser/.dmrc

```
"... Greeter requests session ubuntu" ... **why?** I've worn out my brain and my googling fingers trying to find out; all assistance will be gratefully received.

---

### Post by henrylaw on 2014-09-22
Sorry, discovered minor coding error in my bash commands to search for user-session strings. This is the right set, but there are still nothing but xfce requests everywhere so it makes no difference to my question:
```
Scanning /usr/share/lightdm/lightdm.conf.d
/usr/share/lightdm/lightdm.conf.d/70-sirius.conf:user-session=xfce

Scanning /usr/local/share/lightdm/lightdm.conf.d
grep: /usr/local/share/lightdm/lightdm.conf.d/*.conf: No such file or directory

Scanning /etc/xdg/lightdm/lightdm.conf.d
grep: /etc/xdg/lightdm/lightdm.conf.d/*.conf: No such file or directory

Scanning /usr/local/share/lightdm/lightdm.conf.d
grep: /usr/local/share/lightdm/lightdm.conf.d/*.conf: No such file or directory

Scanning /etc/lightdm
/etc/lightdm/lightdm.conf:user-session=xfce
/etc/lightdm/lightdm-gtk-greeter.conf:user-session=xfce
```

---

### Post by deadflowr on 2014-09-22
I tend to make the file in /etc/lightdm/lightdm.conf.d/50-myconfig.conf
Then add the lines

```
[SeatDefaults]
user-session=xfce
```

then save.

Note this is done as root.

More here
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by henrylaw on 2014-09-23
deadflowr suggested (thank you) that I create /etc/lightdm/lightdm.conf.d/50-myconfig.conf. I did so (naming it [FONT=courier new]50-Sirius.conf[/FONT] for project-naming reasons) and put the suggested content into it but still with the result that a new user gets an "ubuntu" session (Unity, in other words).  So I deleted all configuration files _except_ 50-Sirius.conf, with the following contents:
```
~$ cat /etc/lightdm/lightdm.conf.d/50-Sirius.conf
[SeatDefaults]
user-session=xfce
```
... and still a newly-created user gets an "ubuntu" session.  Am I wrong to suspect a bug at this point? 

Here is the lightdm configuration data (extracted by a simple bash script I wrote). You can see the files it looks for and the appearance of only one user-session key:
```
Looking for .conf files in /usr/share/lightdm/lightdm.conf.d
  Found /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
  Found /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
  Found /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
  Found /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
  Found /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
Looking for .conf files in /usr/local/share/lightdm/lightdm.conf.d
  None found
Looking for .conf files in /etc/xdg/lightdm/lightdm.conf.d
  None found
Looking for .conf files in /etc/lightdm/lightdm.conf.d
  Found /etc/lightdm/lightdm.conf.d/50-Sirius.conf

Looking for user-session keys
/usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
  No 'user-session' key
/usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
  No 'user-session' key
/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
  No 'user-session' key
/usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
  No 'user-session' key
/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
  No 'user-session' key
/etc/lightdm/lightdm.conf.d/50-Sirius.conf
  user-session=xfce
/etd/lightdm/lightdm.conf
  Not found
```
Here is the beginning of the lightdm log (yes, I did restart lightdm!)
```
[+0.00s] DEBUG: Starting Light Display Manager 1.10.1, UID=0 PID=11152
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-Sirius.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus ... etc
```
The only oddity here is that lightdm says it's loading configuration from [FONT=courier new]/etc/lightdm/lightdm.conf[/FONT] which, as you can see from my earlier listing, doesn't exist.

... and here is the part of the log showing authentication of "testuser" and the "request" for an ubuntu session:
```
[+154.93s] DEBUG: Session pid=12176: Greeter connected version=1.10.1
[+155.62s] DEBUG: Session pid=12176: Greeter start authentication for testuser
[+155.62s] DEBUG: Session pid=12308: Started with service 'lightdm', username 'testuser'
[+155.63s] DEBUG: Session pid=12308: Got 1 message(s) from PAM
[+155.63s] DEBUG: Session pid=12176: Prompt greeter with 1 message(s)
[+158.98s] DEBUG: Session pid=12176: Continue authentication
[+159.07s] DEBUG: Session pid=12308: Authentication complete with return value 0: Success
[+159.07s] DEBUG: Session pid=12176: Authenticate result for user testuser: Success
[+159.07s] DEBUG: Session pid=12176: User testuser authorized
[+159.07s] DEBUG: Session pid=12176: Greeter sets language en_GB
[+159.13s] DEBUG: Session pid=12176: Greeter requests session ubuntu
[+159.13s] DEBUG: Writing /home/testuser/.dmrc
[+159.16s] DEBUG: Seat: Stopping greeter; display server wil ... etc
```
"Greeter requests session ubuntu"?  Lies!

Should I raise a bug report?

---

### Post by henrylaw on 2014-09-24
OK, I've found the seat of this problem.  I disabled /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf, which is the configuration file which specifies the gtk greeter; the system then reverts to the Unity greeter.  Problem solved!  The default session for a newly-created user is now xfce, as desired.

So the bug, if there is one, is in lightdm-gtk-greeter and not in lightdm itself.

---

