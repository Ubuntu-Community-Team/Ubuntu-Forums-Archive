---
title: "Error starting the GNOME Settings Daemon"
date: 2007-10-22
forum: Desktop Environments
---

### Post by ajayre on 2007-10-22
About 1 in 3 or 4 times that I start Ubuntu using the real time kernel (apt-get install linux-rt) I get the following error message after logging in:

> There was an error starting the GNOME Settings Daemon. The last error was: did not receive a reply

I have search and tried all the suggestions I could find, for example messing with /etc/hosts and /etc/networks/interfaces. Also I tried disabling ESD, etc. I added the Gnome Settings Daemon to the session to run at startup, and although this works it doesn't stop the error message from appearing.

When I manually start the daemon on the command line it works but displays the following:

```
andy@pepper:~$ gnome-settings-daemon &
[1] 5559
andy@pepper:~$ 
** (gnome-settings-daemon:5559): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-zlCjJ68lrb: Connection refused

(gnome-settings-daemon:5559): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-zlCjJ68lrb: Connection refused

(gnome-settings-daemon:5559): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

** (gnome-screensaver:5566): WARNING **: failed to register with the message bus
```

The contents of /tmp are:

```
andy@pepper:~$ ls -l /tmp
total 24
drwx------ 3 andy andy 4096 2007-10-22 16:56 gconfd-andy
drwx------ 2 andy andy 4096 2007-10-22 16:56 keyring-7NPKET
srwxr-xr-x 1 andy andy    0 2007-10-22 16:57 mapping-andy
drwx------ 2 andy andy 4096 2007-10-22 17:04 orbit-andy
drwx------ 2 andy andy 4096 2007-10-22 16:56 ssh-WokgxA5102
drwx------ 3 andy andy 4096 2007-10-22 16:57 Tracker-andy.5171
drwx------ 2 andy andy 4096 2007-10-22 16:57 virtual-andy.kQaO6r
```

As you can see there are no files starting with "dbus-".

Any ideas how I can troubleshoot this further? Although it only seems to happen with the real time kernel, it may just be less frequent with the generic kernel? I haven't seen it happen yet with the generic kernel however.

I am using Ubuntu 7.10. Kernel 2.6.22-14-generic and 2.6.22-14-rt.

thanks, Andy

---

### Post by bitninja on 2007-10-22
I'm having the same problem. Not the realtime kernel was automatically recommended for me as an update...maybe I should go back to using generic?? Not sure...this hasn't happened to me with any previous version of Ubuntu, and I'm using the final of Gutsy Gibbon.

---

### Post by ajayre on 2007-10-22
I can choose between generic and real time kernels using grub, but I need the real time kernel for machine control.

Andy

---

### Post by bitninja on 2007-10-22
I can use the generic kernel but I find that after I installed the rt kernel, the generic is a little wonky. :\

---

### Post by John Harrington on 2007-10-29
This just happened to me using the generic kernel.  Running gnome-settings-daemon in terminal restored my custom desktop settings, but I got the same error messages as ajayre and mounted devices still don't appear.  I've booted up Gutsy about 20 times previously without this problem.  However, during the two immediately prior bootups I got a message about improper permissions for /home/<user>/.dmrc.  I tried to change the permissions to correct the error.  My recollection was that I changed them to 644, but they're now 600, so I think I'll change them to 644 and see what happens next time I boot.  The content of my .dmrc file in its entirety is:


[Desktop]
Session=default

As indicated above, I did select a custom desktop which was restored when I ran gnome-settings-daemon, so it must be stored somewhere.

---

### Post by bitninja on 2007-10-29
I actually just ended up reinstalling gutsy and not installing the ubuntu studio meta packages, which is what caused the rt kernel to be installed in the first place. Haven't had a hiccup since.

---

### Post by troy1of2 on 2007-11-05
I've been getting it too with the generic kernel. It only started this past week. I've been running Gutsy since early October and until now this hasn't been a problem.

---

### Post by telic on 2007-11-05
I've seen this too, a few times, with 2.6.22-14-generic under Gutsy. Here's the error message...

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.


So, I just restart. I reckon the Canonical Gods will fix it, sooner or later.

;)

---

### Post by dmalinovsky on 2007-11-05
I have this problem with both generic and rt kernel (though latter had it more frequently).  To fix the issue I just restarted X server via Ctrl+Alt+Backspace.  Maybe it'll help someone.

---

### Post by Hagbard on 2007-11-06
This bug also just occurred for me -- with no connection to the real-time kernel, which I do not use and have not installed. Stock Gutsy installation, no 3rd party scripts or w/e, upon login I received notification that GNOME settings daemon was unable to start as described by others in this thread. Whatever the issue is, it doesn't seem to be dependent on changing to real-time kernel.

---

### Post by Artemis3 on 2007-11-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had this error occur to me as well, after upgrading to gutsy. There are 2 entries in grub, one is 2.6.22blah-generic and 2.6.22blah-i386, choosing i386 makes the problem disappear. I just tried with linux-rt and it gives the same error.


As a workaround, i use alt-f2 to run gnome-settings-daemon and then it works...

---

### Post by VinceVanya on 2007-11-11
Adding gnome-settings-daemon to the session startup seems to work around the problem for me.

---

### Post by Joshua Swink on 2007-11-14
> **VinceVanya said:**
> Adding gnome-settings-daemon to the session startup seems to work around the problem for me.

Where exactly?

---

### Post by jason10 on 2007-11-14
im having exactly the same problem.  

it started when i decided to play around with compiz without having even half a clue what i was doing = (

was perfect before i had to go getting curious.  and there must be an easy fix but instead i think im just gonna reinstall the whole stupid thing  = /

good luck

---

### Post by Joshua Swink on 2007-11-15
This seems to be related to this gnome-session bug: 
[http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488)

Here is a workaround. Two files are modified.

Change /etc/X11/Xsession.d/55gnome-session_gnomerc, adding two lines (identified below by comments):

```
# ADD FOLLOWING LINE
rm -f /tmp/session-is-gnome
BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
        \( "$BASESTARTUP" = x-session-manager -a \
        "`readlink /etc/alternatives/x-session-manager`" = \
                /usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
  # ADD FOLLOWING LINE
  touch /tmp/session-is-gnome
fi
```

Then change /etc/X11/Xsession.d/99x11-common_start completely, to the following text:

```
if [ -f /tmp/session-is-gnome ]; then
  exec /usr/bin/dbus-launch $STARTUP
else
  exec $STARTUP
fi
```

---

### Post by suoko on 2007-11-15
I also have this issue with my gutsy but thougth it was related to the fact that I have "gutsy proposed" repository enabled.
Can you confirm you all have that enabled too???

---

### Post by Joshua Swink on 2007-11-15
> **suoko said:**
> I also have this issue with my gutsy but thougth it was related to the fact that I have "gutsy proposed" repository enabled.
Can you confirm you all have that enabled too???

I do not have that repository enabled.

---

### Post by LinuxSoundMan on 2007-11-16
i too get this error at no particular amount of boots. it seems to happen randomly. sometimes every 10 boots sometimes every 15 or 20 boots. seems like gnome is mucking up the boot process. any gurus have a fix for this? as a temporary fix i just log out and log back in. but this can get annoying when it happens randomly like it does on my machine. Calling all gurus for a fix for this!! bless us with your knowledge. kind regards to you all.

---

### Post by LinuxSoundMan on 2007-11-16
> **John Harrington said:**
> This just happened to me using the generic kernel.  Running gnome-settings-daemon in terminal restored my custom desktop settings, but I got the same error messages as ajayre and mounted devices still don't appear.

how exactly do you run this daemon. i typed "gnome-settings-daemon" in terminal and got this error.  "** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)"
 how do i access the daemon? thanks.

---

### Post by bassliu on 2007-11-17
thanks Joshua Swink! your code works~~~

---

### Post by yetihehe on 2007-11-17
Yes, it looks like it's working. I have amd64 and had this problem too. After EXACTLY 29 runs after gutsy installation.

---

### Post by holotone on 2007-11-21
Same problem here running Ubuntu Studio // Gutsy (w/ realtime kernel enabled), though mine seems to be a bit more frequent - Almost every time I restart my computer, and sometimes it'll take a couple log-in / log-out cycles before it'll finally start correctly.

---

### Post by Bigbird999 on 2007-11-23
Joshua Swink
> Change /etc/X11/Xsession.d/55-gnome-session_gnomerc, adding two lines (identified below by comments):
In my case the file is >  /etc/X11/Xsession.d/55gnome-session_gnomerc  (ie no dash after 55)
So far it seems to work for me.  You might want to edit your post to fix the file name

BB

---

### Post by jhenager on 2007-11-23
I have gotten that error in Fiesty as well. I largely ignored it. Seems to happen less frequently in Gutsy, in my unscientific observations.

---

### Post by darkeale on 2007-12-02
thanks joshua swink that code works a treat, that problems been annoying me for ages. this solution should get stickied or something cause loads of people have had the same thing

---

### Post by Joshua Swink on 2007-12-03
> **Bigbird999 said:**
> Joshua Swink

In my case the file is  (ie no dash after 55)
So far it seems to work for me.  You might want to edit your post to fix the file name

BB

Oop... thanks! Fixed.

---

### Post by nlz on 2007-12-04
it didn't seem to work out for me.
When i changed the code to Johua's code, i restarted and got an error about keyboard layout and i had to choose between x windows and gnome settings.

after that i had no gnome and even after killing ESD and restarting GNOME (which normally makes everything fine again, since i installed -rt)

it's a pity... But thanks anyway. I'll keep following this thread..

---

### Post by anaxol on 2007-12-05
sudo /etc/init.d/dbus restart and logging in again does the workaround here... if the fix don't help you, this will ease the pain ;)

cheers,
anx

---

### Post by AndyC_772 on 2007-12-08
I've got the same problem now too, following an upgrade to Gutsy.

How do we find out whether a fix is indeed on the way?

---

### Post by iammeagain on 2007-12-08
Joshua Swink rocks!
 I have been looking all around on different threads with similar problems and this fixed it for me. 
I have been spreading around his workaround in the forum to help others out also.

nvm it was working, but it appears I can only do one thing once until I reboot again. I am trying to change Appearance settings.

---

### Post by David Tomic on 2007-12-12
> **LinuxSoundMan said:**
> how exactly do you run this daemon. i typed "gnome-settings-daemon" in terminal and got this error.  "** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)"

This is EXACTLY the same problem as I'm having, and I can't for the life of me figure out how to fix it.

Brand new install of 7.10, applied system updates, and now I end up with this.

Any help would be GREATLY appreciated!

---

### Post by iammeagain on 2007-12-20
> **David Tomic said:**
> This is EXACTLY the same problem as I'm having, and I can't for the life of me figure out how to fix it.

Brand new install of 7.10, applied system updates, and now I end up with this.

Any help would be GREATLY appreciated!

I am no longer having this problem and don't remember what exactly was wrong. But maybe this link will help. It is related i believe [http://ubuntuforums.org/showthread.php?p=3989462#post3989462](http://ubuntuforums.org/showthread.php?p=3989462#post3989462)

---

### Post by Roo on 2007-12-21
One of the recent updates resulted in my getting this message fairly consistently (every boot).  If my memory is correct, it was the new kernel image update which started this.

As this is my desktop machine, and its physically secure, I have auto-login enabled for my user.  I suspect - but have no actual proof - that if I had disabled auto-login the problem would have gone away.

The post [http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15) from Joshua Swink appears to have resolved my problem.

My gut feeling here is this is a timing issue.

Roo

---

### Post by madmetal on 2007-12-24
> **dmalinovsky said:**
> I have this problem with both generic and rt kernel (though latter had it more frequently).  To fix the issue I just restarted X server via Ctrl+Alt+Backspace.  Maybe it'll help someone.

i just upgraded to gutsy today and faced the same problem but with X server restart everything is ok!
:KS

---

### Post by ugm6hr on 2007-12-28
Just tried Post 15 solution: [http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15)

Restarts OK - hopefully it will stay that way now!

EDIT:
Been a week now with no problems.... seems like a good solution.

---

### Post by ctpaterson on 2008-01-01
> **Joshua Swink said:**
> This seems to be related to this gnome-session bug: 
[http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488)

Here is a workaround. Two files are modified.

While I can also report *apparent* success using Joshua's workaround (the problem did not occur with any predictability), it had the side-effect of disabling Ctrl+Alt+Del as a keyboard shortcut to bring up the Logout/Reboot/etc menu.

I removed the fix and rebooted, and the three-finger-salute works once more.  If the Gnome error problem returns, I will attempt a Ctrl+Alt+Backspace and see if that deals with it.

---

### Post by esmerine on 2008-01-05
My second day using ubuntu and that freaky gnome-settings-daemon error creeped me out. But thanks to Joshua Swink my gnome is alive.
Having ctrl+alt+delete none-activeness issue too.

Anyone helps me with restoring the Ctrl+Alt+Delete command? Changing this shortcut into something else doesn't help.

---

### Post by itsjustarumour on 2008-01-06
> **Joshua Swink said:**
> This seems to be related to this gnome-session bug: 
[http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488)

Here is a workaround. Two files are modified.

Change /etc/X11/Xsession.d/55gnome-session_gnomerc, adding two lines (identified below by comments):

```
# ADD FOLLOWING LINE
rm -f /tmp/session-is-gnome
BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
        \( "$BASESTARTUP" = x-session-manager -a \
        "`readlink /etc/alternatives/x-session-manager`" = \
                /usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
  # ADD FOLLOWING LINE
  touch /tmp/session-is-gnome
fi
```

Then change /etc/X11/Xsession.d/99x11-common_start completely, to the following text:

```
if [ -f /tmp/session-is-gnome ]; then
  exec /usr/bin/dbus-launch $STARTUP
else
  exec $STARTUP
fi
```

This fix doesn't work for me, running gnome-settings-daemon in terminal still gives me:

> ian@COOLERMASTER:~$ gnome-settings-daemon

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)
ian@COOLERMASTER:~$ 


Enabling root user and then logging in with su and running gnome-settings-daemon gives me:

> ian@COOLERMASTER:~$ su
Password: 
root@COOLERMASTER:/home/ian# gnome-settings-daemon

** (gnome-settings-daemon:6328): WARNING **: Unable to connect to dbus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)
root@COOLERMASTER:/home/ian# 



I've tried adding gnome-settings-daemon to Startup Sessions but no joy.

EDIT - I'm on the 2.6.22-14-generic kernel btw.


ANOTHER EDIT - Bug 395488 at [http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488) has been marked as "obsolete", and hasn't been looked at since 6th June 2007.  I'll go and see if I can re-open it, or file a new bug.

---

### Post by itsjustarumour on 2008-01-06
"Bug 507662 has been added to the database"

[http://bugzilla.gnome.org/show_bug.cgi?id=507662](http://bugzilla.gnome.org/show_bug.cgi?id=507662)

:-)

---

### Post by vishnu_23688 on 2008-01-14
> **dmalinovsky said:**
> I have this problem with both generic and rt kernel (though latter had it more frequently).  To fix the issue I just restarted X server via Ctrl+Alt+Backspace.  Maybe it'll help someone.

thank u... this helped me.. but after facing this problem my CPU is giving some beep sound continuously for every 5 seconds!! what could be it and how can i solve it? pl reply..

---

### Post by hibajugala on 2008-01-16
I have tried to modify the code in these two files but I am unable to save it :( can someone help me?

---

### Post by ugm6hr on 2008-01-17
> **hibajugala said:**
> I have tried to modify the code in these two files but I am unable to save it :( can someone help me?

I would recommend you create a backup of the files *before* editing and resaving:

```
sudo cp /etc/X11/Xsession.d/99x11-common_start /etc/X11/Xsession.d/99x11-common_start.bkp
sudo cp /etc/X11/Xsession.d/55gnome-session_gnomerc /etc/X11/Xsession.d/55gnome-session_gnomerc.bkp
```

Then edit them:

```
gksudo gedit /etc/X11/Xsession.d/55gnome-session_gnomerc
gksudo gedit /etc/X11/Xsession.d/99x11-common_start
```

You should be able to save them if you open them with the gksudo gedit command.

Original link: [http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15)

---

### Post by rare HERO on 2008-02-13
```
$ gnome-settings-daemon

** (gnome-settings-daemon:13865): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused

(gnome-settings-daemon:13865): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-9uvtyyOYfL: Connection refused

(gnome-settings-daemon:13865): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object

** (gnome-screensaver:13874): WARNING **: failed to register with the message bus
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
```

---

### Post by vsharris on 2008-02-13
Check the following link (seems to solve the problem for me):

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)

YMMV

---

### Post by intrader on 2008-03-15
> **Joshua Swink said:**
> This seems to be related to this gnome-session bug: 
[http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488)

Here is a workaround. Two files are modified.

Change /etc/X11/Xsession.d/55gnome-session_gnomerc, adding two lines (identified below by comments):

```
# ADD FOLLOWING LINE
rm -f /tmp/session-is-gnome
BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
        \( "$BASESTARTUP" = x-session-manager -a \
        "`readlink /etc/alternatives/x-session-manager`" = \
                /usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
  # ADD FOLLOWING LINE
  touch /tmp/session-is-gnome
fi
```

Then change /etc/X11/Xsession.d/99x11-common_start completely, to the following text:

```
if [ -f /tmp/session-is-gnome ]; then
  exec /usr/bin/dbus-launch $STARTUP
else
  exec $STARTUP
fi
```


I have modified the two files as described here. Now when I start the GNOME pops up an error window stating that the session has not been active more than 10 seconds and when I click Ok, it shows up the same popup (in a loop, I guess)
When I remove the change to the two files above, I am back to the "There was an error starting the GNOME Settings Daemon. :(

---

### Post by Joshua Swink on 2008-04-24
This problem seems to have gone away in Hardy. :)

---

### Post by bizarre_status on 2008-04-29
no problem still exists, i've tryed several solution i found here but nothin' seems to be working.

---

### Post by Aearenda on 2008-05-14
Joshua Swink's workaround fails on a Gutsy multi-user system, such as Edubuntu with LTSP, because the first user to logon owns the file /tmp/session-is-gnome, and because more than one user might be logging on simultaneously. The flag file name should really incorporate a username and/or session id of some sort, so as to be unique.

---

### Post by mbutu on 2008-05-14
I had the same problem, I'm new but I think understand that in my case was appening just after setting up a wired connection... the system stop at starting so gnome-settings-daemon could not receive a reply before time out...
when I delete the wired connection all returned to work
maybe?

---

### Post by mcqustd on 2008-05-17
I have been running Gutsy with now problems on my IBM T40, but after upgrading to Hardy I started this error message and it happens every time I boot.

I am still a newbie and hesitant to add any of the proposed changes that were suggested for the Gutsy problem.

Running 2.6.24-16-genric

---

### Post by breagerey on 2008-05-19
I'm running 8.04 64 and I just had this problem.
After looking around a bit I found a post that mentioned changing 
/etc/network/interfaces
As I had recently modified this file I tried it.
It worked.

I reset the file to
 auto lo
 iface lo inet loopback

Now I need to work out how to get my bridge back in there :~/

---

### Post by Krydahl on 2008-06-22
> **mcqustd said:**
> I have been running Gutsy with now problems on my IBM T40, but after upgrading to Hardy I started this error message and it happens every time I boot.

I am still a newbie and hesitant to add any of the proposed changes that were suggested for the Gutsy problem.

Running 2.6.24-16-genric

I've just started seeing this problem on Hardy and tried Joshua Swink's fix (post 15). I can't say if it solves the problem yet because it only happens to me intermittently, but I've just rebooted and everything seems to come up fine.

I suggest backing up the 2 files you have to edit and giving it a go.

---

### Post by Tabe_ on 2008-07-01
I found that problem upgrading to 8.04, reinstalling dbus solved the problem, there's no need to edit files.

Me encontré con el mismo problema al actualizar a 8.04, reinstalando dbus se solució el problema, no hay necesidad de editar ficheros.

---

