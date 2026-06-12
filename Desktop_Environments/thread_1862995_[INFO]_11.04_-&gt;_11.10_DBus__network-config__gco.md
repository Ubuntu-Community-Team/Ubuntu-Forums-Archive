---
title: "[INFO] 11.04 -&gt; 11.10 DBus / network-config / gconf boot error Info Thread"
date: 2011-10-17
forum: Desktop Environments
---

### Post by geudrik on 2011-10-17
Because it appears there are a good many of us that have run into issues during their upgrades from 11.04 to 11.10, resulting in the issues, and similar issues, the ones below, I figured that I would take a minute to cover them and compile a list of proposed solutions.

Please post responses, ideas, tips, suggestions etc and I will update this thread accordingly.


[COLOR="Red"]**_[SIZE="3"]Issues[/SIZE]_**[/COLOR]

**_Issue 1:_** At boot time, you get a slew of messages akin to this, then X fails to load at all and all you have is TTY...
```

modem-manager[898]: Could not get the system bus. make sure the message bus daemon is running! 
message: failed to connect to socket /var/run/dbus/system_bus_socket: connection refused

```

**_Issue 2:_**
```

** (gdm-binary:2292): WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

```

**_Issue 3:_**
```

(process:3547): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```


[COLOR="Lime"]**_[SIZE="3"]SOLUTIONS[/SIZE]_**[/COLOR]

The solutions are suggestions that I have come across on the forums, that have seemed to be working for a good many people. I would suggest that should you be experiencing any of these issues, you give them a try.  I encourage feedback on this thread!

First, when the screen goes black and X fails to start, press CTRL-ALT-F1 to drop to TTY1 and login as normal. This will drop you into single-user mode, aka run-level 2

```

sudo mv /var/run/* /run/
sudo mv /var/lock/* /run/lock/
sudo rm -r /var/run
sudo rm -r /var/lock
sudo ln -s /run /var/run
sudo ln -s /run/lock /var/lock
sudo rm /run/dbus/*

```
What's happened here? 11.10 had paths changed, and the upgrade tool fails to symlink properly.
Credit: codac ([COLOR="Orange"][source]("http://ubuntuforums.org/showthread.php?t=1859432")[/COLOR])

[COLOR="Magenta"]Note:[/COLOR] If you are getting an error re: no such file or directory, try running
```
sudo mkdir /run/lock
``` prior to running the above block.

[COLOR="Magenta"][SIZE="3"]_**TIPS**_[/SIZE][/COLOR]

If you are still having issues, try re-running the sym-link part
```

sudo ln -s /run /var/run
sudo ln -s /run/lock /var/lock

```

If you have issues when you try to sudo update-grub, try
```

sudo ln -s /var/run/ /run/
sudo ln -s /var/lock/ /run/lock/

```

As a final step, you should also run:
```

sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a

```

---

### Post by Teque5 on 2011-10-17
Thanks! The basic solution fixed my problem.

---

### Post by BulentCOSKUN on 2011-10-17
Hi,

Thanks for this solution. First Option has worked for me.
:)

---

### Post by geudrik on 2011-10-18
I'm glad that this has been of help :)

---

### Post by lwhitmore on 2011-10-19
First solution worked for me too.  Thanks.  God only knows how a 'regular' user is supposed to deal with this kind of thing :-P

---

### Post by shaolin_ on 2011-10-21
Thanks my man. Your solution worked great!

---

### Post by ozi_lion on 2011-10-22
Worked for me too, thanks a lot

---

### Post by eggplant37 on 2011-11-10
Adding in my two cents... two laptops here had similar problems on upgrade. Thanks for saving my tail.

---

### Post by jacopo3001 on 2011-11-12
Seems I am in this situation too, like described in **Issue 1**.
But, maybe being a complete newbie with linux, i got stuck at step one:  when I 
sudo mv /var/run/* /run/

it runs few lines, then stops at
'/var/run/vmblock-fuse/dev' -> '/run/vmblock-fuse/dev'
and I dont know how to continue.

I restarted the computer with the power button, tried again and again stoped at the same point.

What am i missing?

---

### Post by jacopo3001 on 2011-11-14
seems the problem is related to VMWARE.
i found some details further details here:
[http://www.digitalxerf.com/ubuntu-11-10-upgrade-first-thoughts/](http://www.digitalxerf.com/ubuntu-11-10-upgrade-first-thoughts/)
[http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/](http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/)

will try and let you know.

---

### Post by JoWi on 2011-11-22
Thanks, solution worked fine! :)

---

### Post by jorb on 2012-06-05
This works for me :) Now if only I could do-release-upgrade without something breaking!

---

