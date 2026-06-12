---
title: "GNOME wont let me in!"
date: 2007-02-21
forum: Desktop Environments
---

### Post by Mark C on 2007-02-21
Help!

GNOME wont let me in, KDE does but I like GNOME better.

Anyway, it all started when I upgraded my settings to [enable cpu scaling for the coolnquiet technology]("http://www.ubuntuforums.org/showthread.php?t=366450&highlight=powernow") embedded in my desktop. After I reboot to see if the modules works, and it does btw, whenever I log in to GNOME, it greets me with this:

[[IMG]http://img03.picoodle.com/img/img03/7/2/21/t_Screenshot1m_c03d10a.png[/IMG]](http://www.picoodle.com/view.php?srv=img03&img=/7/2/21/f_Screenshot1m_c03d10a.png)

So I thought I'd try to manually start GNOME which I did, but when I try to start gnome-sessions and it tries to start gnome-settings-daemon, then it triggers that thing again: 

[[IMG]http://img02.picoodle.com/img/img02/7/2/21/t_Screenshotm_8b49ebd.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/2/21/f_Screenshotm_8b49ebd.png)

but thankfully I have metacity running now, so I can close the thing.

Ive searched the forums and found a similar problem, but to my disgrace I don't have that problem because I don't have alsa-utils-gui whatchamacallit installed.

Any ideas on how I could fix this problem? It's forcing me to use KDE...
Or if there is no other way, then how can I disable this evil gnome-settings-daemon, and what does this demon do anyway besides causing trouble?

Thanks for reading, and I hope you would at least comment on my situation.

---

### Post by bobpaul on 2007-02-21
Oh! I've had this happen to me once way back on gentoo... it has to do with a gnome setting--duh--but.. grr, I don't remember the specifics.

You're gnome settings are all in ~/.gnome* files. You can find the files and folders in xterm by doing "ls .gnome*"

Things I would try:
1) Look at and edit your .gnomerc. These things that happen whenever gnome startup. Maybe one of them is causing the problem

2) Rename .gnome folders. I'd start with .gnome2/ -- it's probably in there. If you rename the folder gnome will use the default values for anything stored in there.
**Eg**
```
 ~$ mv .gnome2 .gnome2-backup 
```
if that doesn't help
```
 ~$ rm -rf .gnome2 
~$ mv .gnome2-backup .gnome2
``` and repeat with another folder. 

3) Once you find the folder you can narrow down to the specific file, and then maybe try editing the file to figure out what's causing the trouble. the 'diff' tool could let you compare the broken backup to the working default tool.

Thought -- the problem might also be in gconf. that's the .gconf/ folder... gconf holds a lot of settings, but that's what backups are for! ;)

More thoughts -- it could also be a permissions issue. Try the following:
```
 ~$ chown -R $USERNAME:$USERNAME ~/
~$ sudo chmod 777 /tmp
```

---

### Post by Mark C on 2007-02-21
I've tried running GNOME as a different user to simulate having the default values instead of rename deleting them, however the problem persists.

I can access GNOME thru the terminal by creating an instance of gnome-terminal, and a whole tab of nautilus, gnome-panel and metacity, I've tried running gnome-session again, and then, after a while, here's what comes up:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

:?:

---

### Post by bobpaul on 2007-02-21
Sounds like a problem in dbus message passing. I'm not sure dbus itself is the problem, or if it's just that gnome-settings-daemon isn't running. Did you verify your /tmp folder is user writable? I guess that'd probably screw up kde, too, though...

Hmm... ```
dpkg --search `which gnome-settings-daemon`
gnome-control-center: /usr/bin/gnome-settings-daemon
```
Maybe re-install the gnome-control-center package?

---

### Post by Mark C on 2007-02-21
> **bobpaul said:**
> Sounds like a problem in dbus message passing. I'm not sure dbus itself is the problem, or if it's just that gnome-settings-daemon isn't running. Did you verify your /tmp folder is user writable? I guess that'd probably screw up kde, too, though...

Hmm... ```
dpkg --search `which gnome-settings-daemon`
gnome-control-center: /usr/bin/gnome-settings-daemon
```
Maybe re-install the gnome-control-center package?

I've already done that. I removed/installed the package, but still no dice. Anyway, the dmesg post gave me an idea, so I started gnome-session, and then started another terminal tab then typed 

dmesg |tail

And then, surprise!:
> 
[   47.295305] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   47.295345] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[   47.295347] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8
[   47.295350] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   48.141411] lp0: using parport0 (interrupt-driven).
[   49.748026] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 6:00.0] forgot to specify physical device; fix it!
[   49.748620] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 6:00.0] forgot to specify physical device; fix it!
[   49.748651] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 6:00.0] forgot to specify physical device; fix it!
[   50.101818] eth0: no IPv6 routers present
[   63.693910] eth0: no IPv6 routers present

I don't know how it could be relevant but I hope it helps.

---

### Post by bobpaul on 2007-02-21
I'm really out of ideas, but I'll keep an eye on the thread. Hopefully someone else knows something. Have you considered undoing whatever you did for cool'n'quiet? I'm really not familiar with that process.

---

### Post by Mark C on 2007-02-21
It's ok, thanks for trying to help anyway.

I tried unchecking CoolNQuiet in the BIOS, yet the problem persisted. Oh well, i've just configured the sounds in KDE, I hope I enjoy my stay while I be patient for any additional replies on this thread. :)

And wow, kde IS fast.

---

### Post by bobpaul on 2007-02-23
Consider this a bump... Maybe try removing all gnome packages, sudo aptitude clean, then re-add ubuntu-desktop to reinstall all the gnome stuff. 

You could also purge all the gnome stuff to have it remove it's settings. I don't think purge will remove settings in your home folder. If it's affecting a new user account, the problem must be a package, /etc setting, or default profile (/etc/skel I believe)

---

### Post by Zaphod on 2007-02-26
I think I am having the exact same problem as you:confused: 

When I started my computer yesterday , upon entering Gnome a screen popped up wich said something about some Gome settings demon not running . I logged out and in again and then no error ... so all good 

Until today ... First things seemed ok , my desktop came up and I opened Swiftfox and Thunderbird . Then the computer froze so I ctrl+alt+backspace and now when I log into Gnome I get the first screen in your first mail ..
Failsafe Gnome is the same ..

:(

---

### Post by navneeth on 2007-02-26
Wow...everyone having problems with the daemon. I'm typing from failsafe mode, but am not quite sure what do after this to get back my Ubuntu proper.

---

### Post by Zaphod on 2007-02-26
Now I'm really baffled ...

After trying alot of things and nothing worked (reinstalled Gnome didnt do nothing) , I decided on 1 more reboot and GUESS WHAT ?!??

And Gnome works :confused:  

I'm sure its not related to anything I did ....

---

### Post by Mark C on 2007-02-27
> **Zaphod said:**
> Now I'm really baffled ...

After trying alot of things and nothing worked (reinstalled Gnome didnt do nothing) , I decided on 1 more reboot and GUESS WHAT ?!??

And Gnome works :confused:  

I'm sure its not related to anything I did ....

Too bad I decided to switch to KDE.

---

### Post by navneeth on 2007-02-27
I've installed Kubuntu-Desktop now. It's a bit of mess though, with both KDE and GNOME stuff in the menus. Can I get back to GNOME by uninstalling ubuntu-desktop and then reinstalling it?

---

### Post by Mark C on 2007-02-27
> **navneeth said:**
> I've installed Kubuntu-Desktop now. It's a bit of mess though, with both KDE and GNOME stuff in the menus. Can I get back to GNOME by uninstalling ubuntu-desktop and then reinstalling it?

Did not work for me.

You could try installing XFCE-core or KDE-core instead of kubuntu though, much lighter and doesn't install unwanted apps.

---

### Post by navneeth on 2007-02-27
Actually, I want GNOME. It's simpler, although it doesn't seem to provide as many option as KDE (and that has a downside, too).

---

### Post by bobpaul on 2007-02-27
> **navneeth said:**
> Can I get back to GNOME by uninstalling ubuntu-desktop and then reinstalling it?

Uninstalling and reinstalling should fix a broken package. Purging and reinstalling should fix a broken config or a broken package (purge will uninstall and also delete the config files used by those packages).

Keep in mind, though, that the Ubuntu-Desktop package is a metapackage, so removing and reinstalling this won't do anything at all... you actually have to remove and reinstall the gnome packages themselves.

---

### Post by Zaphod on 2007-02-27
It is still a bit quirky for me , booted my pc just now with another message about Gnome Settings Daemon not running but everything seems to work

---

### Post by navneeth on 2007-02-27
> **bobpaul said:**
> Uninstalling and reinstalling should fix a broken package. Purging and reinstalling should fix a broken config or a broken package (purge will uninstall and also delete the config files used by those packages).

Keep in mind, though, that the Ubuntu-Desktop package is a metapackage, so removing and reinstalling this won't do anything at all... you actually have to remove and reinstall the gnome packages themselves.

Hmm... So what should I do? I'm sitting here with KDE (and, of course, a broken GNOME). Here's the background info on the problem.
[http://ubuntuforums.org/showpost.php?p=2216219&postcount=1](http://ubuntuforums.org/showpost.php?p=2216219&postcount=1)

---

### Post by gigake on 2007-02-27
I have the same problem.
I did: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

And now when I run command:
/etc/init.d/network stop 
then I can log into gnome.

But when network is running, then I can't :(

Can somebody say why this happens ?

---

### Post by navneeth on 2007-02-27
> **Zaphod said:**
> It is still a bit quirky for me , booted my pc just now with another message about Gnome Settings Daemon not running but everything seems to work

I don't know why that message pops-up, but that's a really nice wallpaper. Where did you get it from? :)

---

### Post by bobpaul on 2007-02-27
> **navneeth said:**
> Hmm... So what should I do? I'm sitting here with KDE (and, of course, a broken GNOME). Here's the background info on the problem.
[http://ubuntuforums.org/showpost.php?p=2216219&postcount=1](http://ubuntuforums.org/showpost.php?p=2216219&postcount=1)

Themes, you say? Can you provide more details? Were you working with Beryl, simply used synaptic to install someting-artwork packages, or what?

---

### Post by Zaphod on 2007-02-27
> **navneeth said:**
> I don't know why that message pops-up, but that's a really nice wallpaper. Where did you get it from? :)

From this forum , was in one of monthly desktop showoff thread (January)

I think , well I am pretty sure it was there ...

---

### Post by navneeth on 2007-02-28
> **bobpaul said:**
> Themes, you say? Can you provide more details? Were you working with Beryl, simply used synaptic to install someting-artwork packages, or what?

Nothing of that sort. I don't have Beryl - all I was doing System->Prefernces->Themes Manager. I was just choosing between icon themes that were already installed. This has happened before,i.e. Themes Manager crashing Ubuntu, and not letting me in, and I installed Ubntu again, without going into failsafe mode, but that was just a little time after I had installed the OS, so I had not customised it much. But now, I have a lot of custom settings.

---

### Post by nosh on 2007-02-28
Hey, I just had this same problem with gnome:

There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.

Anyways, this happened about half the time I logged on, and always when I logged off and immediately logged on.  Good news is I think I fixed it.  The problem was in /etc/network/interfaces

Not quite sure how I fixed it or how the whole thing works, but I hope this helps!

---

### Post by dreamsayer on 2007-03-15
> **Mark C said:**
> Help!

GNOME wont let me in, KDE does but I like GNOME better.

Anyway, it all started when I upgraded my settings to [enable cpu scaling for the coolnquiet technology]("http://www.ubuntuforums.org/showthread.php?t=366450&highlight=powernow") embedded in my desktop. After I reboot to see if the modules works, and it does btw, whenever I log in to GNOME, it greets me with this:

[[IMG]http://img03.picoodle.com/img/img03/7/2/21/t_Screenshot1m_c03d10a.png[/IMG]](http://www.picoodle.com/view.php?srv=img03&img=/7/2/21/f_Screenshot1m_c03d10a.png)

So I thought I'd try to manually start GNOME which I did, but when I try to start gnome-sessions and it tries to start gnome-settings-daemon, then it triggers that thing again: 

[[IMG]http://img02.picoodle.com/img/img02/7/2/21/t_Screenshotm_8b49ebd.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/2/21/f_Screenshotm_8b49ebd.png)

but thankfully I have metacity running now, so I can close the thing.

Ive searched the forums and found a similar problem, but to my disgrace I don't have that problem because I don't have alsa-utils-gui whatchamacallit installed.

Any ideas on how I could fix this problem? It's forcing me to use KDE...
Or if there is no other way, then how can I disable this evil gnome-settings-daemon, and what does this demon do anyway besides causing trouble?

Thanks for reading, and I hope you would at least comment on my situation.


I had this same problem today. I searched the forums and the net high and low, and tried all of the suggestions mentioned. Nothing worked. Typing gnome-settings-daemon in a terminal gave me a clue. There were a bunch of error messages re: label foregrounds and backgrounds.

So I logged into KDE and selected System Settings & in the Look & Feel section for Appearance, Desktop,Splash Screen & Window behavior I set all of the options contained to their defaults. I logged out of KDE and back into Gnome and Wallah!

I just happened to add KDE to my working Ubuntu system last night. I wanted to try something different. I suspect that the kpersonalizer that runs at first start may have caused this? Just a guess. I re-ran it and was playing around with the different themes. And this was after I successfully logged back and forth between Gnome and KDE without this problem.

---

### Post by whistlerspa on 2007-03-15
Me too and I posted separately on this before I saw this thread. I didn't install anything at all - it just started yesterday for no apparent reason. I notice the Networking tool from Administration menu is now a blank empty box - significant of anything? 

No sound working either

---

### Post by Mark C on 2007-03-15
Mine was a Feisty problem.

After uninstalling and purging the whole gnome-control-center package and updated them to the new version, the evil bug that blocked me from entering GNOME normally had been gone. This happened weeks ago, but I thought no one else will have the problem so I didn't post.

By the way, if this happens to you, you can try installing XFCE instead of KDE because XFCE is faster to install and you can run gnome-panel within it to make it look like GNOME.

---

### Post by gladstone on 2007-09-22
I had this aswell.

I managed to rename ~/.gnome2 to ~/.gnome2bak and rebooted. It recreated the ~/.gnome2 folder and logged in fine.

I then just restored my backup and it seems fine. (I did delete ~/.gnome2/accels/gnome-session-properties at first, but it was still fine after restoring it) :confused:

Edit:

I actually located the problem file to be /etc/network/interfaces (I'd been trying to setup my wireless before). Here's the link to the bug on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/61381](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/61381)

Some other things that you could try if that doesnt help:

* Remove folder /temp/orbit-[YOUR LOGIN NAME]
* Remove ~/.gconf/desktop/gnome/applications/window_manager
* If none of the above, try removing ~/.gconf and ~/.gnome2

(Make backups before)

---

