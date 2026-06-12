---
title: "Xubuntu and FreeNX problems, help?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by onyx on 2006-02-11
Okay, so I installed Xubuntu, but I am having some problems.  The system does not have a monitor/keyboard/mouse.  I connect to it using FreeNX.  Now FreeNX does not show you a login screen for the system, it just logs you in.  I was able to start up Xubuntu by going to desktop settings for my FreeNX client on my Windows system and selecting "Custom" and telling it to run the command "startxfce4".

So here is my problem, it works, but the desktop is tiny!  I am guessing less than 640x480.  I don't have this problem when I connect and use GNOME.

Any guesses?  I was thinking maybe I could pass the desktop size as a parameter to startxfce4?  I am not sure here.  I searched quite extensively and didn't find any topics about this or using other desktops with FreeNX.

Thanks!

---

### Post by onyx on 2006-02-11
Hmm, nobody has any idea on this?

---

### Post by onyx on 2006-02-14
Found the solution myself, so HA!

[http://forum.xfce.org/index.php?topic=1825.0]("http://forum.xfce.org/index.php?topic=1825.0")

Basically, go the the XFCE installation directory and rm/mv display_plugin.*

For my default installation I went to /usr/lib/xfce4/mcs-plugins/ and the file was in there.  Just moved it to display_plugin.disabled and the resolution problem was fixed.  Yay!

---

### Post by dk_pa on 2006-03-06
Thanks for posting this information I ended up needing it today!  Thanks a lot =)  

FreeNX + XFCE = Friggin' Great!

---

### Post by malaprohibita on 2006-03-08
I'll second the thanks for the information.  I just used it myself.

---

### Post by dermotti on 2006-03-12
This is a REALLY good post, i was referred to it. Awesome info!!!

---

### Post by harisund on 2006-08-07
Thanks for this information.

---

### Post by h2o on 2006-09-15
I was also getting this problem but you will see at the end of this msg that it got connected while seting it up.

I am using freenx on xubuntu. local nxclient connects fine but it does not start the window manager, i m running xfce.

```

vmware@xubuntu:~$ sudo nxsetup --setup-nomachine-key
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N] n
Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=/usr/bin/dbus-launch --sh-syntax --exit-with-session startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_GNOME=/usr/bin/dbus-launch --sh-syntax --exit-with-session gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is bb:ba:9d:ae:8c:55:f5:b4:8b:90:2f:33:27:15:15:f4.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 quit
Quit
<--- done

Ok, nxserver is ready.

PAM authentication enabled:
  All users will be able to login with their normal passwords.

  PAM authentication will be done through SSH.
  Please ensure that SSHD on localhost accepts password authentication.

  You can change this behaviour in the /etc/nxserver/node.conf file.
Have Fun!

```

Here is the error after successfully connection and login. Message i get "session startup fail" and here isthe complete trace.

```

NX> 203 NXSSH running with pid: 11866
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 8888
NX> 211 The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is bb:ba:9d:ae:8c:55:f5:b4:8b:90:2f:33:27:15:15:f4.
Are you sure you want to continue connecting (yes/no)? 
Failed to add the host to the list of known hosts (/home/vmware/.ssh/known_hosts).
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: vmware
NX> 102 Password: 
NX> 103 Welcome to: xubuntu user: vmware
NX> 105 listsession --user="vmware" --status="suspended,running" --geometry="1024x768x24+render" --type="unix-application"
NX> 127 Sessions list of user 'vmware' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: vmware
NX> 105 startsession  --virtualdesktop="1" --application="startxfce4" --link="adsl" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="localhost" --type="unix-application" --cookie="******" --geometry="1024x722" --kbtype="pc102/us" --screeninfo="1024x722x24+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: xubuntu-1000-B2F4E0CBC2740CE9CB68CDDC10A6B0BC
NX> 705 Session display: 1000
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: da036326bd40a5acc7bedcf7213871d8
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 879a755746132b1786ef801e2a5c4f88
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
/usr/lib/nx/nxserver: line 891: 11999 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.

```

---

### Post by h2o on 2006-09-15
i am unable to go to this link getting [B]The topic or board you are looking for appears to be either missing or off limits to you.
[/B]
> **onyx said:**
> Found the solution myself, so HA!

[http://forum.xfce.org/index.php?topic=1825.0]("http://forum.xfce.org/index.php?topic=1825.0")

Basically, go the the XFCE installation directory and rm/mv display_plugin.*

For my default installation I went to /usr/lib/xfce4/mcs-plugins/ and the file was in there.  Just moved it to display_plugin.disabled and the resolution problem was fixed.  Yay!

---

### Post by jimcooncat on 2006-09-19
h2o, I had that problem using a new Windows client with an older nxserver (Seveas's breezy freenx package). I found an older Windows client then it worked well for me.

---

### Post by perunaion on 2006-10-28
I am using xubuntu with xfce4 and attempting to get nx working on the system.  At the moment I have tried both startxfce4 and xfce4-session to no avail.  I have checked my sshd_config file nad it seems alright.  I get past authentication, but seem to fail when the client attempt to start the window manager.  Helps or suggestions in getting this working would be greatly appreciated!
-danny.

edit: I am able to connect via putty and forward x11 to my local cygwin install of x11.  Dunno if that helps, just something to note I guess.

```

prog@host:~$ sudo nxsetup
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N] n
------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually.
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N] nSetting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=/usr/bin/dbus-launch --sh-syntax --exit-with-session startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_GNOME=/usr/bin/dbus-launch --sh-syntax --exit-with-session gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 quit
Quit
<--- done

Ok, nxserver is ready.

PAM authentication enabled:
  All users will be able to login with their normal passwords.

  PAM authentication will be done through SSH.
  Please ensure that SSHD on localhost accepts password authentication.

  You can change this behaviour in the /etc/nxserver/node.conf file.
Have Fun!

```
```
NX> 203 NXSSH running with pid: 7388
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.5 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: prog
NX> 102 Password: 
NX> 103 Welcome to: host user: prog
NX> 105 listsession --user="prog" --status="suspended,running" --geometry="1600x1200x32+render" --type="unix-application"
NX> 127 Sessions list of user 'prog' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: prog
NX> 105 startsession  --taint="1" --virtualdesktop="0" --application="/usr/bin/startxfce4" --link="wan" --backingstore="1" --nodelay="1" --encryption="1" --cache="32M" --images="128M" --samba="1" --media="1" --mediahelper="esd" --session="hdprog" --type="unix-application" --cookie="******" --kbload=" --kbload=pc102/en_US" --keymap=" --keymap=en_US" --kbtype="pc102/en_US" --keybd="1" --screeninfo="1024x768x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: cse-507-t06-1000-09BB719D98F9461742BB0A09C1B5E5C8
NX> 705 Session display: 1000
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: a4204dd8e1bd065a0376dc8582cd220c
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 8a47a61e26cf0145fe3f5a226ca9573b
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 891:  7376 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.


```

---

### Post by drdnl on 2006-11-08
I have the exact same error when running Gnome/nxserver and nxclient, it logs in, authenticates and then just dies. For me the solution is to run NO p2p software. As long as azureus and amule are not running it works fine,

does this work for anyone?

---

### Post by dermotti on 2006-11-10
Ive had issue getting FreeNX to work properly on Edgy. But i have a workaround.

Uninstall all yourfreeNX crap.

Install the NX-server .deb from here
[http://www.nomachine.com/download-package.php?Prod_Id=3](http://www.nomachine.com/download-package.php?Prod_Id=3)

And use hte latest client from here
[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)


This package worked flawlessly automagically with xubuntu edgy. At Least for me :-)

---

### Post by vinodis on 2006-11-20
Thankyou very much. your solution worked!

---

