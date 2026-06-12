---
title: "howto run a script with &quot;sudo&quot; lines at login?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by kundalinikat on 2006-03-06
I have a script that I run manually after I login, typing the root password each time for the "sudo"... I'd really like this to run on login automatically, I've tried using the System--Preferences--Sessions thing, and taking some of the advice in other posts here about auto-wlan-connectivity solutions... but is there a way I can get this to run automatically without need of the password? Maybe during the boot sequence or before the GNOME login somehow?

```
sudo iwconfig ra0 essid "MY SSID" ap 42:42:42:42:42:42
sudo iwlist ra0 scanning
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=WPAPSK
sudo iwpriv ra0 set EncrypType=TKIP
sudo iwpriv ra0 set SSID="MY SSID"
sudo iwpriv ra0 set WPAPSK="MY KEY"
sudo iwpriv ra0 set SSID="MY SSID"
sudo dhclient ra0
sudo apt-get update
```

This is a very helpful forum, I've only been using Linux for less than a month and i've learned a lot, but this stumps me.

---

### Post by issueperson on 2006-03-06
what is your script called?

EDIT:[COLOR="Red"]
Open a terminal and type:
----------------------------------
export EDITOR=gedit && sudo visudo
----------------------------------[/COLOR]
and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
[COLOR="Red"]**username**[/COLOR] ALL= NOPASSWD: [COLOR="Red"]**scriptpath**[COLOR="Red"][/COLOR][/COLOR]
-------------------------------------------------------------------
BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME.
and replace scriptpath with the path to the file you want to run without a password.

for example, i want the firestarter firewall to run at startup as sudo without typing in the password.  the last line in my file looks like:

**brady ALL= NOPASSWD: /usr/sbin/firestarter**

where "brady" is my user name and "/usr/sbin/firestarter" is the program i want to run.

so for argument sake, let's say you have the script saved as [COLOR="Red"]/opt/scripts/startupscript[/COLOR] and your user name is [COLOR="Red"]happyllama[/COLOR], your file would look like

**happyllama ALL= NOPASSWD: /opt/scripts/startupscript**

now save the file and close it.  you are now allowed to run your script as sudo without typing in a password.

so go to system > preferences > sessions and add the command you want to run at startup under "startup programs", it might look something like:
[COLOR="Red"]sudo bash /opt/scripts/startupscript[/COLOR] (replacing the path with the path to your script).

hope that can help you.  if not, let me know and i'll try to help more.

---

### Post by kundalinikat on 2006-03-06
hey awesome, that worked! thank you so much.

---

### Post by hornetcoach on 2007-12-30
My own fault I am sure but - since doing:

Open a terminal and type:
----------------------------------
export EDITOR=gedit && sudo visudo
----------------------------------
and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
username ALL= NOPASSWD: scriptpath

Since I did this  I can no longer perform any sudo function anywhere in the OS.  Any ideas how I can get back into this file and undo my damage?  ...I should have known better...there were at least two popup warnings telling me I might break my Ubuntu if I did this.

---

### Post by urukrama on 2007-12-30
You must have made an error in your sudoers file, which is annoying because you need sudo to edit that file...

You could log in recovery mode. This will boot into a command line system logged in as root. Type then the following command:

> visudo

This will open the sudoers file. Delete the lines you have added to the file and save the file (Ctrl+X, Y(es)). Visudo will automatically check for errors in the file when saving.

---

### Post by hornetcoach on 2007-12-31
Thanks a lot - visudo from the recovery console worked great.

---

### Post by klsmith259 on 2007-12-31
A much easier and better way I think is just adding the commands without "sudo" in front to /etc/rc.local. 
This is a script that is initialized at startup regardless of Desktop Environment or sudo rules.

iwconfig ra0 essid "MY SSID" ap 42:42:42:42:42:42
iwlist ra0 scanning
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwpriv ra0 set SSID="MY SSID"
iwpriv ra0 set WPAPSK="MY KEY"
iwpriv ra0 set SSID="MY SSID"
dhclient ra0
apt-get update

---

