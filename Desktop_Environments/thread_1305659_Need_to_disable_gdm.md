---
title: "Need to disable gdm"
date: 2009-10-30
forum: Desktop Environments
---

### Post by linuxuser9999 on 2009-10-30
Does anybody know how to disable gdm (gnome) so I can boot to the command line in 9.10?

---

### Post by jeffus_il on 2009-10-30
One of the ways is to run ```
sudo sysv-rc-conf 
``` in a terminal and remove the X's using the space bar in the line starting with gdm.

Alternatively you can access a console using <Ctrl><Alt><F1> when gdm is running.

Good Luck

---

### Post by minaev on 2009-10-30
I'm afraid that developers have totally mutilated the runlevel system of Ubuntu. Perhaps, playing with /etc/init/gdm.conf might help.

---

### Post by dj-toonz on 2009-10-30
or hold shift down while the systems booting & it brings up the menu

---

### Post by dcc24 on 2009-10-30
I've tried /etc/init.d/gdm off but it says upstart doesn't support "off". Any ideas?

---

### Post by minaev on 2009-10-30
dcc24,

To stop GDM, you have to give the command `stop', not `off': ```
/etc/init.d/gdm stop
```

But it will only stop gdm for this session. It will still be started after reboot. 

Perhaps, if you edit the file /etc/init/gdm.conf and replace the line
```
stop on runlevel [016]
```
with
```
stop on runlevel [0126]
```

it might work. Cannot check the idea right now, sorry... Or just make some more or less random changes in this script so it would not run GDM :) I mean, like, change `/usr/sbin/gdm' to `/no/more/gdm'.

---

### Post by dcc24 on 2009-10-30
Yeah, but I don't want to "stop" it, I want it off. Before 9.10 "/etc/init.d/gdm off" worked just fine.

But, I guess you're right, messing up the init script seems to be the only way.

---

### Post by sisco311 on 2009-10-30
> **dcc24 said:**
> 
But, I guess you're right, messing up the init script seems to be the only way.

Try something like:

```

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (**runlevel [3]**
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0**2**16]

```

to start gdm only if you switch/boot to runlevel 3 and stop it in runlevel 2.

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

> **dcc24 said:**
> Yeah, but I don't want to "stop" it, I want it off. Before 9.10 "/etc/init.d/gdm off" worked just fine.

```
sudo service gdm stop
```

---

### Post by linuxuser9999 on 2009-10-30
Thank you all for your help. I really appreciate it. I've used Sisco's suggestion of typing sudo service gdm stop. It works good enough for me. I know I said that I needed to disable gdm to boot up to the command line but it seems I'll still be able to do whatever I have to do. But if I need to permanently disable gdm, I will try those suggestions about modifying the gdm.conf file or the init scripts.

---

### Post by rockney on 2009-11-02
For admins who actually use the power of runlevels and /etc/init.d this thing called Upstart is just a cruel joke!

It seems they want to make us either 1) custom edit all those pseudo-scripts to teach them how to obey runlevels, or  2) always boot the box the same way.

Is that correct?  Am I missing something?

What is the "advantage" in a server environment?

Is it is possible to NOT use Upstart in 9.10?

Can it be uninstalled without totally destroying the system? (NO- researched this. Uninstalling it would uninstall most of the GUI and applications - can YOU say dependency?)

It seems Upstart is related to highly-dynamic computers - like laptops - with all the "event driven" whiz-bang stuff. But that it is totally irrelevant to a server and is the wrong paradigm for that environment. Worse - there does not appear to be a way to use the notion of a runlevel without customizing all the Upstart stuff - making the box harder to maintain.

For instance - who decided that if a box has XWindows installed that it will ALWAYS be run regardless of how the /etc/rcN.d is setup? Or that's it's OK to blindly stomp on configuration with a one-size-fits-all upgrade?

As far as I'm concerned this is media and toy driven and has no place in a production environment. Are there any alternatives to Upstart with Ubuntu?

---

### Post by linuxuser9999 on 2009-11-02
About minaev's suggestion on messing with the init scripts, I actually opened up /etc/init/gdm.conf and just commented out the line that reads **exec gdm-binary $CONFIG_FILE ** just before the end script line. Now I can boot up straight to the command line without having to load the Gnome Desktop. But don't take my word for it, I don't know if that's the proper way of disabling a program from starting up during boot. All I know is that it worked for me.

---

### Post by rockney on 2009-11-02
> **linuxuser9999 said:**
>  I don't know if that's the proper way of disabling a program from starting up during boot. All I know is that it worked for me.

That'll work but "initctl" is the prescribed tool to change things.

My complaint is the "Upstart" thing has convoluted the start-up even further - and that some fool made the decision that if XWindows is installed it will always be run. There may be other changes - that's all the further I've gotten.

During the 9.04-to-9.10 upgrade the /etc/init.d gdm script (and others) were deleted and replaced with symbolic links to /etc/init pseudo-scripts with yet another different syntax that are NOT the same as what was in /etc/init.d.  In 9.10 I do not know if it is even possible to change how gdm and other things are started.

If any of those scripts are edited then it becomes a maintenance issue. The whole runlevel mechanism has been perverted and thoroughly messed-up. And Upstart is touchy and fragile making it entirely inapproriate for a server environment.

Besides - as far as I can tell all this Upstart stuff is aimed at something like a laptop where things are plugged-in and out dynamcially. People running production servers DO NOT do that kind of stuff.

Frankly - my guess is the Ubuntu organization has too much focus on making it "more convenient and simpler" for end-users like it's some kind of iToy thing while BREAKING it for serious production and engineering users. If this trend of turning their backs on admins continues we WILL rip it out and change distros on many servers and even more workstations and stop wasting our time.

Their assumptions about usage are wrong, and QA seems to be non-existent - especially for the upgrade specifications.

---

### Post by iruel on 2009-11-02
you could use "boot-up manager" on karmic by default you couldn't found it,because you need to download first just like usually
```
sudo apt-get install bum
```
and on jaunty it's integrated,on ***System > Preferences > Services***;)

---

### Post by z0mb13e on 2009-11-04
I've been going round in circles with this...

Recently upgraded (a low powered VIA system that I mainly use as a NAS and print server) to 9.10 - figured I would see what the new desktop features look like (albeit slowly) and then dump the GUI but the init scripts for GDM were missing.

(Not to mention that 'sudo stop gdm' didn't actually appear to stop the GUI - at least remotely. I killed a few apps and it looks like it has finally gone away).

Seems the upgrade deleted the init scripts for GDM from the various run levels as part of the move to upstart.

So now trying to get my head round Upstart and the config file to stop GDM from starting on the default run level, rather than it starting and then being told to stop.


====================

start on (filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0126]


====================

I will reserve judgement on Upstart until I have learnt more about it, but it will make me wary of installing the next LTS release in a production env.

---

### Post by sisco311 on 2009-11-04
> **z0mb13e said:**
> I've been going round in circles with this...



Once again:
```

start on (runlevel [3]
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0126]

```

You can strat/stop it:

```
sudo service gdm start/stop
```
or
```
sudo initctl start/stop gdm
```

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

---

### Post by z0mb13e on 2009-11-04
> **sisco311 said:**
> Once again:
```

start on (runlevel [3]
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0126]

```

Thanks - needed to see that again as it was out of context (for me at least) the first time round. Now that I have a better understanding of whats going on with the startup it makes sense.

As for shutting down the GUI, the commands didn't work until I killed a few apps. I tried earlier (remotely via ssh) and nothing happened. When I got a look at the GUI there was no indication of a pending closure. I tried again and still nothing. After killing firefox and gnome panel processes it seems to have closed. Not sure if it closed cleanly - will have to check later.

I can see what Upstart is about, I figure the change is inevitable, shame the documentation is so sketchy right now.

[EDIT]

Looks like something weird was going on with GDM.

It seems to start and stop as expected now - trying a reboot to see if it boots up without a GUI.

Yup - works a treat. Off to see if I can't find some more documentation on Upstart

[/EDIT]

---

### Post by Argyled on 2009-11-08
I tried to use "bum" to deactivate gdm, but the "boot up manager", while it seems to be able to disable services that are running, does not seem to be able to actually effect the boot process, and my changes are ignored.  Am I doing something wrong?  Is this a bug?

---

### Post by gamaral on 2009-11-08
You can disable by running "echo > /etc/X11/default-display-manager" as root to remove the forced dm on boot.

I would also remove gdm from all rc*.d just to be safe: "update-rc.d -f gdm remove" as root, but not sure it might be needed. The init on *ubuntu is messed up for n00b protection.

Hope it helps

---

### Post by sisco311 on 2009-11-08
> **Argyled said:**
> I tried to use "bum" to deactivate gdm, but the "boot up manager", while it seems to be able to disable services that are running, does not seem to be able to actually effect the boot process, and my changes are ignored.  Am I doing something wrong?  Is this a bug?

It's not a BUG. 

Upstart was first included in Ubuntu in the 6.10 (Edgy Eft) release in late 2006, replacing sysvinit. For compatibility reasons most of the services were managed using the old sysvinit scripts. Ubuntu 9.10 (Karmic Koala) introduced native Upstart bootup.

bum is a GUI to manage sysvinit style init scripts. In Ubuntu 9.10 most of the sysvinit style init scripts are replaced with Upstart jobs.

Jobs are defined in files placed in /etc/init, the name of the job is the filename under this directory without the .conf extension. They are plain text files and should not be executable.

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html") 

To disable gdm, you have to edit the /etc/init/gdm.conf file. For details see my post above.

---

### Post by sisco311 on 2009-11-08
> **gamaral said:**
> 
I would also remove gdm from all rc*.d just to be safe: "update-rc.d -f gdm remove" as root, but not sure it might be needed.


Nope, since there are no symlinks to gdm in /etc/rc*.d.

> **gamaral said:**
> 
The init on *ubuntu is messed up for n00b protection.


That's incorrect. Most sysvinit scripts are replaced by Upstart jobs.

---

### Post by falconindy on 2009-11-08
> **sisco311 said:**
> To disable gdm, you have to edit the /etc/init/gdm.conf file. For details see my post above.
Not true. As stated above, it can be removed from the init sequence as follows:
```
sudo update-rc.d -f gdm
```
I was just playing with this last night. Discovered [this](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/478019) which is definitely a bug.

---

### Post by sisco311 on 2009-11-08
> **falconindy said:**
> Not true. As stated above, it can be removed from the init sequence as follows:
```
sudo update-rc.d -f gdm
```
I was just playing with this last night. Discovered [this](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/478019) which is definitely a bug.

It will not work in 9.10 since there are no system startup links for /etc/init.d/gdm.


from man update-rc.d:
> 
update-rc.d - install and remove **System-V style** init script links.

gdm (in 9.10) is controlled by **an Upstart job** and **NOT** by a System-V style init script.

---

### Post by Argyled on 2009-11-08
Sisco311,

Thank you for your clarification with regards to sysv vs upstart.  Your advice for preventing gdm by editing /etc/init/gdm.conf has worked for me.

However, it has introduced a new problem in that I no longer have audio when I start X with the startx command.  There doesn't seem to be any indication of a problem in any of the /var/log files.  This appears to be a 'silent' failure, if you will.  I suppose I should open a new thread for this?

---

### Post by sisco311 on 2009-11-08
> **Argyled said:**
> Sisco311,

Thank you for your clarification with regards to sysv vs upstart.  Your advice for preventing gdm by editing /etc/init/gdm.conf has worked for me.

However, it has introduced a new problem in that I no longer have audio when I start X with the startx command.  There doesn't seem to be any indication of a problem in any of the /var/log files.  This appears to be a 'silent' failure, if you will.  I suppose I should open a new thread for this?

Is the sound muted or you get permission errors?

Do you get sound if you start gdm?
```
sudo service gdm start
```

---

### Post by Argyled on 2009-11-09
> **sisco311 said:**
> Is the sound muted or you get permission errors?

Do you get sound if you start gdm?
```
sudo service gdm start
```

The sound isn't muted and I don't appear to be getting permission errors anywhere that I've been able to find.  I do get sound if I start gdm, but the X session I'm in when I start it is either closed by gdm or crashes.

I started a new thread for this here: [http://ubuntuforums.org/showthread.php?t=1320661](http://ubuntuforums.org/showthread.php?t=1320661)

Thanks!

---

### Post by toehser on 2009-11-18
The problem is also weak "conversion" from sysv stuff.

I was already on 9.10 with everything working, meaning SLIM _NOT_ GDM was enabled in the sysv stuff.

Then today's update TURNED ON GDM in UPSTART, but LEFT SLIM trying to start, which BROKE EVERYTHING.

If GDM was disabled (no links in rc.? directories), then UPSTART CONVERSION SHOULD HAVE DETECTED THAT AND LEFT IT DISABLED.

Just wasted hours with a broken display to fix this and re-disable GDM.  Long live SLIM, down with GDM, who needs to waste the memory for a login manager?

---

### Post by sisco311 on 2009-11-18
> **toehser said:**
> The problem is also weak "conversion" from sysv stuff.

I was already on 9.10 with everything working, meaning SLIM _NOT_ GDM was enabled in the sysv stuff.

Then today's update TURNED ON GDM in UPSTART, but LEFT SLIM trying to start, which BROKE EVERYTHING.

If GDM was disabled (no links in rc.? directories), then UPSTART CONVERSION SHOULD HAVE DETECTED THAT AND LEFT IT DISABLED.

Just wasted hours with a broken display to fix this and re-disable GDM.  Long live SLIM, down with GDM, who needs to waste the memory for a login manager?


How did you disabled GDM?

Slim is not in the Karmic repositories, it has some serious security issues. 


[http://osdir.com/ml/ubuntu-devel-discuss/2009-09/msg00097.html]("http://osdir.com/ml/ubuntu-devel-discuss/2009-09/msg00097.html")
>  The reason it is not in karmic (and can't be now) is presumably because it was not in Debian when we synced from Debian earlier in the release cycle. Ubuntu has not modified it in any way - we've just taken it from Debian. If it gets back in Debian it will get back in Ubuntu.

Looking at packages.debian.org I find slim in lenny and sid. It has some terrible bugs though including one that says you can login as root without a password! It sounds like it is good that it is not in karmic!

How did you installed SLIM?

---

### Post by toehser on 2009-11-19
It is a virtual machine with memory use by far the most highest importance.  Slim / LXDE is great.  Sorry to hear it has bugs, maybe I'll look into and try to fix.  Don't care about the bugs, though, really, the host machine is secure enough that it doesn't matter if the login manager on the guest is buggy.

Not sure whether GDM was disabled with no links in rc.? or with DEFAULT_DISPLAY_MANAGER stuff or what.  Bottom line:  GDM didn't start.  My business if something else did.  Ran aptitude full-upgrade.  Suddenly GDM did start, and started broken.

Not sure how I installed slim, either, but probably back around the time of Hardy, and ever since, it "just worked", and the Intrepid update I don't think re-turned-on GDM, and the Karmic update didn't, either, it was fine with Karmic/Slim _after_ Karmic install, then a recent update broke it.  Which is worse.

---

### Post by jbygden on 2009-12-11
So, Sisco

From reading this thread I can see that you are very good at telling people what doesn't work anymore, and that it's not a bug that it doesn't work like it used to.

Still though, no answer to the initial question.

How do one permanently disable gdm (or any upstart job, for that matter), preferably without having to edit a script that might be updated and by that restored?

(i.e. what we used to do using 'update-rc.d -f gdm remove')

/Jonas

---

### Post by iscatel on 2009-12-11
well, this disables sound, as a previous post pointed out, but here goes:

in /etc/default/grub, comment out 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

add

GRUB_CMDLINE_LINUX_DEFAULT="text"

then

sudo update-grub

this will pass "text" on the kernel line, disabling gdm.

---

### Post by zika on 2009-12-11
> **iscatel said:**
> well, this disables sound, as a previous post pointed out, but here goes:

in /etc/default/grub, comment out 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

add

GRUB_CMDLINE_LINUX_DEFAULT="text"

then

sudo update-grub

this will pass "text" on the kernel line, disabling gdm.With "text" in kernel boot line, with 2.6.32-999 sound works, once You are in X. Just tried, listening to music while writing this.
BTW that is the best way to use development release of OS. I've been exploiting "text" for some time. Ever since the similar thread was active in Karmic testing ...

---

### Post by sisco311 on 2009-12-11
> **jbygden said:**
> So, Sisco

<snip>

Still though, no answer to the initial question.

How do one permanently disable gdm (or any upstart job, for that matter), preferably without having to edit a script that might be updated and by that restored?

(i.e. what we used to do using 'update-rc.d -f gdm remove')

/Jonas

Reinstalling the package will not overwrite the gdm.conf file, a package upgrade will ask you if you want to replace the manually edited file with the one provided by the package distributor:
```
Configuration file `/etc/init/gdm.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** gdm.conf (Y/I/N/O/D/Z) [default=N] ?
```

In case of gdm you can use the *text* kernel parameter or you can comment out /usr/sbin/gdm from the /etc/X11/default-display-manager file.


BTW, *update-rc.d -f service remove* removes the System V style init  script  links  /etc/rc{0,1,2,3,4,5,6,S}.d/NNservice  whose  target  is  the  script /etc/init.d/service.

If you reinstall or upgrade the service, the missing symbolic links are reinstalled too. ;)

---

### Post by iscatel on 2009-12-12
> **zika said:**
> With "text" in kernel boot line, with 2.6.32-999 sound works, once You are in X. Just tried, listening to music while writing this.
BTW that is the best way to use development release of OS. I've been exploiting "text" for some time. Ever since the similar thread was active in Karmic testing ...

not in stable.   startx doesn't seem to start all the services, though I can't see why.   To get X up and running as expected, you seem to be forced to go through gdm.  Totally irrelevant if you don't need X anyway (netbook being used to learn programming, text only at the moment, so console is just fine)  I ended up putting an extra boot entry into

/etc/grub.d/40_custom 

so I can choose normal, gdm and everything, or just my old VCs, vim, etc. Off topic, but had the UNR on that machine, but went through the whole installation again with Xubuntu, prefer mighty mouse to fisher price....

---

### Post by zika on 2009-12-12
> **iscatel said:**
> not in stable.   startx doesn't seem to start all the services, though I can't see why.   To get X up and running as expected, you seem to be forced to go through gdm.  Totally irrelevant if you don't need X anyway (netbook being used to learn programming, text only at the moment, so console is just fine)  I ended up putting an extra boot entry into

/etc/grub.d/40_custom 

so I can choose normal, gdm and everything, or just my old VCs, vim, etc. Off topic, but had the UNR on that machine, but went through the whole installation again with Xubuntu, prefer mighty mouse to fisher price....It seems that, slowly, grub2 shows its good sides ... Good idea ...

---

### Post by dugh on 2010-01-04
```

sudo mv /etc/init/gdm.conf /etc/init/gdm

```

bingo, no more gnome on bootup

of course to re-enable, just rename the /etc/init/gdm file back to gdm.conf

Unfortunately, to manually start gdm (which I still like to do occasionally on my server), I still had to rename the file back to gdm.conf, then run 'sudo start gdm'.
But then you have to remember to rename the file back to gdm (no .conf) afterward or it will start on boot again next time.



> **sisco311 said:**
> Reinstalling the package will not overwrite the gdm.conf file, a package upgrade will ask you if you want to replace the manually edited file with the one provided by the package distributor:
```
Configuration file `/etc/init/gdm.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** gdm.conf (Y/I/N/O/D/Z) [default=N] ?
```

In case of gdm you can use the *text* kernel parameter or you can comment out /usr/sbin/gdm from the /etc/X11/default-display-manager file.


BTW, *update-rc.d -f service remove* removes the System V style init  script  links  /etc/rc{0,1,2,3,4,5,6,S}.d/NNservice  whose  target  is  the  script /etc/init.d/service.

If you reinstall or upgrade the service, the missing symbolic links are reinstalled too. ;)

---

### Post by scorp123 on 2010-01-05
EDIT:

duh. I am too slow today. The answer was already given early on in this thread. :D

---

### Post by tristram_ on 2010-01-06
> **zika said:**
> With "text" in kernel boot line, with 2.6.32-999 sound works, once You are in X. Just tried, listening to music while writing this.
BTW that is the best way to use development release of OS. I've been exploiting "text" for some time. Ever since the similar thread was active in Karmic testing ...

Sounds like great a great solution.... 

but I don't have a file /etc/default/grub to edit!! :(

---

### Post by komputes on 2010-02-05
I had a hard time because I was following guides that were not tested on 9.10. In fact you don't need to mess with GDM's configuration as GRUB2 is the easiest way to get this done. Here are the steps:

1 - Edit the GRUB2 configuration defaults

```
$ sudo gedit /etc/default/grub
```2 - Change the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```3 - Save and close the grub file

4 - Update grub so that the changes are propagated to grub's configuration file (to all current and future kernels)

```
$ sudo update-grub
```That it! Simple right? :)

If you ever need to log into gnome, use the **startx** command. If you want GDM to start use the **sudo gdm start** command.

Hope this helps people from wasting hours of trying to disable GDM on 9.10 using older guides that suggest editing gdm.conf, moving gdm.conf, using update-rc.d, rcconf or sysv-rc-conf - none of those worked for me. This was the cleanest/best way I found of doing this.

Cheers!

:guitar:

---

### Post by oldos2er on 2010-02-05
Thanks for posting this. If only I'd known this sooner, I wouldn't have uninstalled gdm. Live and learn.

---

### Post by zika on 2010-02-05
> **oldos2er said:**
> Thanks for posting this. If only I'd known this sooner, I wouldn't have uninstalled gdm. Live and learn.We wrote about "text" option in Karmic development cycle and in this thread I think in December if not even earlier...

---

### Post by komputes on 2010-02-05
> I don't have a file /etc/default/grub to edit

There are two reasons why I think this could be.

1) You have an upgraded system and you are using GRUB rather than use GRUB2
2) You are not using Ubuntu 9.10

---

### Post by komputes on 2010-02-05
> **zika said:**
> We wrote about "text" option in Karmic development cycle and in this thread I think in December if not even earlier...

Unfortunately some people need a step by step walk through. I saw your post concerning GRUB2's benefits but it did not occur to me immediately that it was the solution. Hopefully this will help someone in the future. Cheers!

---

### Post by oldos2er on 2010-02-05
> **zika said:**
> We wrote about "text" option in Karmic development cycle and in this thread I think in December if not even earlier...

Thanks. I should read the development and testing forum more often.

---

### Post by 23dornot23d on 2010-02-05
Removed GDM2 ..... now my machine boots ok and also exits properly from KDE, I have also disabled Akonadi too ....

( It used to hang and never log out of KDE ..... I had to go into a terminal to do a reboot or shutdown.)

___________________________________________________________________

Using KDM and the majority of boot display problems have now disappeared 
  and my machine does its startup correctly ....

[http://www.youtube.com/watch?v=5KtO9R0pui0](http://www.youtube.com/watch?v=5KtO9R0pui0)

Great thread ..... if I had not seen this I would still be using Mandriva 2010 as my main linux System ....... 

____________________________________________________________________

Now just the one problem left ...... the correct mounting at boot of my external IOMEGA TERRA USB drive 
to solve and the system ....... is good ...... again ........ worked fine in 8.10 and 9.04 ..... ? 
In 9.10 why was something changed to stop it mounting properly ..... 

I hope the problems soon get resolved in Gnome Nautilus and GDM2 .....

---

### Post by argos3016 on 2010-02-19
Well. I did all things that i discovered Googling (grub, update.d, bum...) and yes, GDM doesn't start ,but the sound nor.
That's my problem.

---

### Post by bhmildy on 2010-03-01
Hi, newbie here.
I'm trying to disable the desktop occasionally, rather than every time I boot.  FYI, I'm trying to run virtualbox with Win2k pro with 168 MB RAM on a 512MB computer, and would like to run virtualbox and guest OS from the command line without the overhead of the desktop gui.

Running 9.10, on Dell dimension 4600 PC.

I've tried this from a terminal, and from [ctrl] +[alt] +[F1]
sudo etc/init.d/gdm stop
(doesn't recognize command)

[ctrl] +[alt] +[backspace] does nothing.

"sudo pkill Xorg" just reboots my GUI

Specific step-by-step instructions are the most helpful for me, because I'm early in the learning curve.  Thanks
Russ

---

### Post by zika on 2010-03-02
```
sudo service gdm stop
```

---

### Post by gottijr on 2010-03-11
> **sisco311 said:**
> 

```

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (**runlevel [3]**
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0**2**16]

```



  I've done what sisco said

  now i start gdm with gdm start

  the question is : how do i stop gdm

  cause none of this work
```

  sudo gdm stop
  sudo /etc/init.d/gdm stop

```

  i've been trying to fix this problem for a while. pls advice

---

### Post by sisco311 on 2010-03-11
> **gottijr said:**
> I've done what sisco said

  now i start gdm with gdm start

  the question is : how do i stop gdm

  cause none of this work
```

  sudo gdm stop
  sudo /etc/init.d/gdm stop

```

  i've been trying to fix this problem for a while. pls advice

start it with:
```
sudo initctl start gdm
```
and stop it with:
```
sudo initctl stop gdm
```

or switch the *runlevel*:
```
sudo initctl emit 3
```
```
sudo initctl emit 2
```

---

### Post by zika on 2010-03-11
> **gottijr said:**
> I've done what sisco said

  now i start gdm with gdm start

  the question is : how do i stop gdm

  cause none of this work
```

  sudo gdm stop
  sudo /etc/init.d/gdm stop

```  i've been trying to fix this problem for a while. pls advicestart:```
sudo service gdm start
```stop:```
sudo service gdm stop
```restart:```
sudo service gdm restart
```

---

### Post by gottijr on 2010-03-11
after testing all the options i figured out that i can stop it only if i start with service gdm start -> service gdm stop

  thanks again

  just to figure out something

  what is the best way to disable gdm

  runlevel (3)

  or 

  quiet splash text?

  which would be the most healthy one?

  thanks

  p.s. after reboot tried
  ```

  service gdm start
  
  and got:
 
   gdm stop/waiting
  
```

  thanks

---

### Post by gottijr on 2010-03-11
strange i can't start it anymore (gdm)

  i get this error

  "start: unknown job: gdm"

  same with /etc/init.d/gdm

  pls help i really wanne figure this one out

---

### Post by zika on 2010-03-11
> **gottijr said:**
> after testing all the options i figured out that i can stop it only if i start with service gdm start -> service gdm stop

  thanks again

  just to figure out something

  what is the best way to disable gdm

  runlevel (3)

  or 

  quiet splash text?

  which would be the most healthy one?

  thanks

  p.s. after reboot tried
  ```

  service gdm start
  
  and got:
 
   gdm stop/waiting
  
```  thanksYou must use **sudo** in order to have enough privilege to start/stop gdm...

---

### Post by gottijr on 2010-03-11
I will post the resolve for me!

  I disabled the boot in gdm with
 "vi /etc/init/gdm.conf"

> **sisco311 said:**
> 
```

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

#start on (filesystem
#          and started hal
#          and tty-device-added KERNEL=tty7
#          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0**2**16]

```



  than i can start and stop service gdm without a problem

```

  sudo service gdm start
  sudo service gdm stop

```

  the other options didn't allowed me to start stop service because of errors posted previous in this thread

---

### Post by gottijr on 2010-03-11
> **zika said:**
> You must use **sudo** in order to have enough privilege to start/stop gdm...

  I agree with you... sorry didn't post i was using it with root priviledge.
  still those issues on both ubuntu servers!!!
  on both disabled text or runlevel.

---

### Post by zika on 2010-03-11
Revert /etc/init/gdm.conf to its original state. Reboot machine, and, in GRUB, using "E" edit the kernel-line adding **text** after quiet splash...whatever... When You get login prompt, login and You're supposed to be able to use sudo service gdm stop/start... GDM will not start automagically, and... After You're sure You're satisfied with this, You can alter grub and make change permanent... This is the way with lest trouble and easily reverted...
text=no gdm...whatever window manager is in use
single=recovery mode...

---

### Post by gottijr on 2010-03-11
> **zika said:**
> Revert /etc/init/gdm.conf to its original state. Reboot machine, and, in GRUB, using "E" edit the kernel-line adding **text** after quiet splash...whatever... When You get login prompt, login and You're supposed to be able to use sudo service gdm stop/start... GDM will not start automagically, and... After You're sure You're satisfied with this, You can alter grub and make change permanent... This is the way with lest trouble and easily reverted...
text=no gdm...whatever window manager is in use
single=recovery mode...

  I'm really interested in what you are saying

  but not sure if i get it right!

  i changed the grub with including quiet splash text

  it does disable the gdm boot

  I can login with sudo start gdm "gdm start"

  no problem by here!

  but we get back to the old problem

  after gdm starts 

  i can't stop it anymore. that was the problem

  tried all 3 - on 2 ubuntu server

  1. gdm stop
  2. service gdm stop
  3. /etc/init.d/gdm stop

  none works

---

### Post by zika on 2010-03-11
> **gottijr said:**
> I'm really interested in what you are saying

  but not sure if i get it right!

  i changed the grub with including quiet splash text

  it does disable the gdm boot

  I can login with sudo start gdm "gdm start"

  no problem by here!

  but we get back to the old problem

  after gdm starts 

  i can't stop it anymore. that was the problem

  tried all 3 - on 2 ubuntu server

  1. gdm stop
  2. service gdm stop
  3. /etc/init.d/gdm stop

  none worksDid You go to one of tty1, tty2,...,tty6 and try to stop it from there or You were stopping it from GDM itself? How did You got out from gdm?

---

### Post by gottijr on 2010-03-11
> **zika said:**
> Did You go to one of tty1, tty2,...,tty6 and try to stop it from there or You were stopping it from GDM itself? How did You got out from gdm?

  I start gdm

  than i'm in

  i open a terminal and try service gdm stop, or gdm stop, or anything!

  am i doing something wrong?

---

### Post by zika on 2010-03-11
> **gottijr said:**
> I start gdm

  than i'm in

  i open a terminal and try service gdm stop, or gdm stop, or anything!

  am i doing something wrong?Yes. Ctrl-Alt-F1 and You're in tty1. Then try to stop gdm, once You're out of tty7 where You're running gdm. Can't stop gdm while in gdm...

---

### Post by gottijr on 2010-03-11
> **zika said:**
> Yes. Ctrl-Alt-F1 and You're in tty1. Then try to stop gdm, once You're out of tty7 where You're running gdm. Can't stop gdm while in gdm...

  I risking to look bad right now...

  but i don't get anything with Ctrl-Alt-F1

  it's not like something is changing

  i'm in gdm - i should open a terminal? ... press Ctrl-Alt-F1 (should something change?). If i press Ctrl-Alt-F2 there should be a diff?

---

### Post by zika on 2010-03-12
> **gottijr said:**
> I risking to look bad right now...

  but i don't get anything with Ctrl-Alt-F1

  it's not like something is changing

  i'm in gdm - i should open a terminal? ... press Ctrl-Alt-F1 (should something change?). If i press Ctrl-Alt-F2 there should be a diff?Ctrl-LeftAlt-F1.

---

### Post by Crass Spektakel on 2010-04-23
My problem is pretty closely related, I do not want to start gdm but get a useful text mode but keep the option to start gdm.

Starting grub with "text" instead of "quiet splash" made the splashscreen disappear but now I get a black screen and nothing else. No text mode login, just black all over.

If I then start gdm and kill it again then I get a beautiful textmode.

Any ideas?

---

### Post by komputes on 2010-04-23
Hi Crass,

What version of Ubuntu and what version of GRUB do you have installed? The output of the following commands will answer these questions:

```
$ lsb_release -a
$ dpkg -l | grep grub
```

---

### Post by Crass Spektakel on 2010-05-02
> **komputes said:**
> Hi Crass,

What version of Ubuntu and what version of GRUB do you have installed? The output of the following commands will answer these questions:

```
$ lsb_release -a
$ dpkg -l | grep grub
```

 I decided to reinstall the final release before going deeper into detail. Now I have Lynx final, problem stays the same.

 From what I found out the text console is actually there, just invisible. I can log in blindly and start gdm, works fine.

 Checking out /var/log/syslog shows several pages of the following log message on every reboot, even without starting gdm:

```
May  2 17:53:36 boni kernel: [  600.520434] [drm] nouveau 0000:01:00.0: PGRAPH_NOTIFY - nSource: PATCH_EXCEPTION, nStatus: INVALID_STATE PROTECTION_FAULT
May  2 17:53:36 boni kernel: [  600.520460] [drm] nouveau 0000:01:00.0: PGRAPH_NOTIFY - Ch 0/3 Class 0x004a Mthd 0x0c08 Data 0xc97b00b0:0x00000000
```

and finally

```
May  2 17:53:36 boni kernel: [  600.520530] [drm] nouveau 0000:01:00.0: Setting dpms mode 1 on vga encoder (output 0)
```

---

### Post by Crass Spektakel on 2010-05-02
> **Crass Spektakel said:**
> ```
May  2 17:53:36 boni kernel: [  600.520530] [drm] nouveau 0000:01:00.0: Setting dpms mode 1 on vga encoder (output 0)
```

I found help at [Freedesktop]("http://bugs.freedesktop.org/show_bug.cgi?id=27211"), testing right now:

[QUOTE=Freedesktop]The noaccel parameter is a Nouveau module parameter, so either pass it to the nouveau module on load (modprobe.conf), or if nouveau is built-in, nouveau.noaccel=1 on kernel command line. Your X uses the Vesa driver? That will screw up the card, if Nouveau is loaded. Either use Nouveau DRM with Nouveau DDX, or no Nouveau at all with Vesa DDX.[/QUOTE]

---

