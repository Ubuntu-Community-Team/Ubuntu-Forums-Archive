---
title: "Updates/installs hosed my system... help with restoring please"
date: 2009-01-25
forum: General Help
---

### Post by inspired on 2009-01-25
Hi folks,

I am using 8.10 intrepid.

Last night I installed a few applications, and also allowed an update to run, which had something like 50 updates waiting. It said a system restart was necessary after the updates had completed. I shut down normally and went to bed.

This morning I had lost all admin rights. Could not sudo as I was not in the sudo list (I forget the name of it). I could not do anything that required root or admin rights, like running the synaptic.  Something I installed or updated last night must have stuffed something up royally.

Following instructions in the forums I booted into recovery mode and took a look at the sudo file using visudo. Everything seemed to be the way it was meant to be so I changed nothing and exited ( :q<enter> )

I then tried issuing an adduser command to add me to the admin group. But it gave an error saying the admin group does not exist. That seemed odd, and I rebooted just to see where things were at.

When the system tried to start up it seemed to be completely hosed. Many lines relating to missing groups came up. It then hangs during the text based load up stages. I was not able to start it up.

I ascertained that the group file was cleaned out... all but two lines (root and nogroup remained but nothing else). I have followed instructions on [this thread]("http://ubuntuforums.org/showthread.php?p=6614138") to copy over the default group file from the livecd. Obviously, however, that group file is likely to be incomplete. I have installed a lot of things on this computer in the past few weeks since setting it up.

For a start, I am aware virtualbox sets up a group for itself. How do I restore the groups set up by installed applications? Just wait and see which ones are broken and then reinstall them?

I have added myself to the admin group from the recovery terminal and also the groups listed [here]("http://ubuntuforums.org/showthread.php?p=4273283"):
> sudo usermod -G ccollins,adm,uucp,dialout,cdrom, \
floppy,audio,dip,video,plugdev,scanner,netdev, \
lpadmin,powerdev,admin

Now when I start the computer it loads fine up to the login screen. I note that one or two missing group errors flash past during the boot up, but I can't see what they are. It's too fast. I will find out how to view the logs.

On the login screen my computer is being called localhost:localdomain. It should be called jonathan-ubuntu. WHy would that have changed and how do I fix it?

I am able to log in. But I have no idea what groups have been lost and what groups my username should be a member of. I have added all the default ones using lists people gave in the forums here of their group membership.

Any help is greatly appreciated.
Thanks,

Jonathan

PS. I had posted this at: [http://ubuntuforums.org/showthread.php?p=6614138](http://ubuntuforums.org/showthread.php?p=6614138)
But once I realised this was turning into a major issue, I moved it to this new thread so as to not bug the people who originally subscribed to that thread.

---

### Post by inspired on 2009-01-25
Now that I am back into my system, I have the following issues:

-Network Manager does not start up. So I can't get onto the internet with that machine yet, which makes it tricky to copy and paste info to the forums here

- I can't access various functions such as the Users and Groups tool. It says:
> **The configuration could not be loaded**
You are not allowed to access the system configuration

- I appear to again have no sudo and admin rights. I can't do anything that requires sudo.

- I have found in the system logs a record of all the groups being deleted and so forth. Looks like it happened during the updates that took place last night just before I shut down. Once I have net access on the machine in question I will post that info here, as I think it is a fairly serious issue for updates to cause this amount of havoc, if that is in fact what happened.

I will now look into how I can restore my sudo rights. There is plenty of info here in the forums on that. I will report more soon.

UPDATE: I am a member of the following groups: sudo, adm, admin... and yet I have no sudo rights. No idea what more to do. The sudoers file looks as it should be.

Thanks,

Jonathan

---

### Post by zvacet on 2009-01-25
> On the login screen my computer is being called localhost:localdomain. It should be called jonathan-ubuntu. WHy would that have changed and how do I fix it?

Boot in recovery mode and 

```
nano /etc/hosts
```

first two lines should look like this

127.0.0.1 localhost
127.0.1.1 jonathan-ubuntu

save and close.Reboot and you should be fine.

---

### Post by inspired on 2009-01-25
Further info...
In the logs I saw (as mentioned, but not pasted here as I am on a different computer for net access right now)... I saw records of every user account in passwd file being changed from its correct userid to the 65534 one that is for the nogroup. I have changed them all back. There was also a record of every group being deleted.

I still don't have Sudo rights even through I've checked the various things to check for this. Shall keep on at it... 
Any help is greatly appreciated. Been at it for 7 hours thus far.

Much thanks,

Jonathan

PS. Thanks zvacet... made that change and after a couple of reboots it worked.

---

### Post by inspired on 2009-01-25
So it appears I again have sudo rights and I am able to runs tools and apps that require admin rights.

This has taken the best part of eight hours to resolve. I have had to go through the logs and manually recreate all the groups and users based on what the logs showed being deleted, giving them all the correct ID based on what I found in the logs.

I will post the logs to show the deletions taking place as I think this is a major issue that any of the steps I took (installing some software, installing updates using update manager, checking on the sudo users file in visudo without making changes) ended up erasing my groups and changing all my users to the nouser ID.

I would greatly appreciate some input on this.

Cheers,
Jonathan

PS. I am happy to have restored my system this far. :D
Now I await to see which apps bomb out due to group and user right issues. Hopefully not too many.

---

### Post by HermanAB on 2009-01-25
Hmm, going forward, I think you need to use the trick all the old timers use: Install VMware Server or Virtualbox, then install a copy of Ubuntu in that.  That way, you can experiment in the VM, without zonking your main system.

In addition, I don't use auto-fsckup^Wupdate on my systems.  Once they are working without trouble, I leave them alone for a year (or three), then re-install from scratch.  (However, I do use strong firewalls and passwords to keep trouble makers out.)

Cheers,

Herman

---

### Post by AndreLeComte on 2009-02-19
[LIST]
[*]For some reason, I have the same issue on my desktop computer.
[*]My notebook computer was also running Ubuntu with the same username and password as my desktop system.
[*]I attached a copy of the etc/group file from my notebook to an email and sent it to my email address.
[*]I started my desktop system using the Ubunutu CD-R.
[*]I downloaded the etc/group file from my web-based email and saved it in the etc folder on my desktop computer.
[*]Now I can log into Ubuntu on my desktop computer, although some features such as visual effects and Internet access are not functioning.
[*]At the end of this message I have posted entries from the auth.log section of GNOME's System Log Viewer.
[*]How can I reverse these changes or restore my desktop system to normal working order?
[/LIST]```

&#65279;Feb 16 13:26:26 Andre polkit-grant-helper[24375]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 24350 [uid=1000] [auth=andre]
Feb 16 13:27:23 Andre groupdel[24394]: remove group `adm' 

Feb 16 13:27:23 Andre groupdel[24400]: remove group `admin' 

Feb 16 13:27:23 Andre groupdel[24409]: remove group `audio' 

Feb 16 13:27:24 Andre groupdel[24423]: remove group `cdrom' 

Feb 16 13:27:24 Andre groupdel[24429]: remove group `crontab' 

Feb 16 13:27:24 Andre groupdel[24440]: remove group `dialout' 

Feb 16 13:27:25 Andre groupdel[24446]: remove group `dip' 

Feb 16 13:27:25 Andre groupdel[24452]: remove group `disk' 

Feb 16 13:27:25 Andre groupdel[24458]: remove group `fax' 

Feb 16 13:27:25 Andre groupdel[24465]: remove group `floppy' 

Feb 16 13:27:25 Andre groupdel[24471]: remove group `fuse' 

Feb 16 13:27:26 Andre groupdel[24490]: remove group `kmem' 

Feb 16 13:27:26 Andre groupdel[24502]: remove group `lpadmin' 

Feb 16 13:27:27 Andre groupdel[24514]: remove group `mlocate' 

Feb 16 13:27:27 Andre groupdel[24520]: remove group `netdev' 

Feb 16 13:27:27 Andre groupdel[24531]: remove group `nvram' 

Feb 16 13:27:27 Andre groupdel[24537]: remove group `operator' 

Feb 16 13:27:27 Andre groupdel[24543]: remove group `plugdev' 

Feb 16 13:27:28 Andre groupdel[24555]: remove group `pulse-access' 

Feb 16 13:27:28 Andre groupdel[24561]: remove group `pulse-rt' 

Feb 16 13:27:28 Andre groupdel[24571]: remove group `sambashare' 

Feb 16 13:27:28 Andre groupdel[24579]: remove group `sasl' 

Feb 16 13:27:28 Andre groupdel[24585]: remove group `scanner' 

Feb 16 13:27:29 Andre groupdel[24592]: remove group `shadow' 

Feb 16 13:27:29 Andre groupdel[24598]: remove group `src' 

Feb 16 13:27:29 Andre groupdel[24604]: remove group `ssh' 

Feb 16 13:27:29 Andre groupdel[24610]: remove group `ssl-cert' 

Feb 16 13:27:29 Andre groupdel[24616]: remove group `staff' 

Feb 16 13:27:29 Andre groupdel[24623]: remove group `sudo' 

Feb 16 13:27:30 Andre groupdel[24633]: remove group `tape' 

Feb 16 13:27:30 Andre groupdel[24639]: remove group `tty' 

Feb 16 13:27:30 Andre groupdel[24645]: remove group `usbusers' 

Feb 16 13:27:30 Andre groupdel[24651]: remove group `users' 

Feb 16 13:27:30 Andre groupdel[24657]: remove group `utmp' 

Feb 16 13:27:30 Andre groupdel[24665]: remove group `vboxusers' 

Feb 16 13:27:30 Andre groupdel[24671]: remove group `video' 

Feb 16 13:27:30 Andre groupdel[24677]: remove group `voice' 

Feb 16 13:27:31 Andre groupdel[24683]: remove group `winbindd_priv' 

Feb 16 13:27:31 Andre usermod[24690]: change user `andre' GID from `1000' to `0'

Feb 16 13:27:31 Andre usermod[24690]: change user `andre' password

Feb 16 13:27:31 Andre usermod[24696]: change user `avahi' GID from `120' to `65534'

Feb 16 13:27:31 Andre usermod[24696]: change user `avahi' password

Feb 16 13:27:31 Andre usermod[24702]: change user `avahi-autoipd' GID from `113' to `65534'

Feb 16 13:27:31 Andre usermod[24702]: change user `avahi-autoipd' password

Feb 16 13:27:31 Andre usermod[24708]: change user `backup' GID from `34' to `65534'

Feb 16 13:27:31 Andre usermod[24708]: change user `backup' password

Feb 16 13:27:31 Andre usermod[24714]: change user `bin' GID from `2' to `65534'

Feb 16 13:27:31 Andre usermod[24714]: change user `bin' password

Feb 16 13:27:31 Andre usermod[24720]: change user `daemon' GID from `1' to `65534'

Feb 16 13:27:31 Andre usermod[24720]: change user `daemon' password

Feb 16 13:27:31 Andre usermod[24726]: change user `dhcp' GID from `102' to `65534'

Feb 16 13:27:31 Andre usermod[24726]: change user `dhcp' password

Feb 16 13:27:31 Andre usermod[24732]: change user `games' GID from `60' to `65534'

Feb 16 13:27:31 Andre usermod[24732]: change user `games' password

Feb 16 13:27:31 Andre usermod[24738]: change user `gdm' GID from `114' to `65534'

Feb 16 13:27:31 Andre usermod[24738]: change user `gdm' password

Feb 16 13:27:31 Andre usermod[24744]: change user `gnats' GID from `41' to `65534'

Feb 16 13:27:31 Andre usermod[24744]: change user `gnats' password

Feb 16 13:27:31 Andre usermod[24750]: change user `haldaemon' GID from `123' to `65534'

Feb 16 13:27:31 Andre usermod[24750]: change user `haldaemon' password

Feb 16 13:27:31 Andre usermod[24757]: change user `hplip' GID from `7' to `65534'

Feb 16 13:27:31 Andre usermod[24757]: change user `hplip' password

Feb 16 13:27:31 Andre usermod[24763]: change user `irc' GID from `39' to `65534'

Feb 16 13:27:31 Andre usermod[24763]: change user `irc' password

Feb 16 13:27:31 Andre usermod[24769]: change user `klog' GID from `104' to `65534'

Feb 16 13:27:31 Andre usermod[24769]: change user `klog' password

Feb 16 13:27:31 Andre usermod[24775]: change user `libuuid' GID from `101' to `65534'

Feb 16 13:27:31 Andre usermod[24775]: change user `libuuid' password

Feb 16 13:27:31 Andre usermod[24781]: change user `list' GID from `38' to `65534'

Feb 16 13:27:31 Andre usermod[24781]: change user `list' password

Feb 16 13:27:31 Andre usermod[24787]: change user `lp' GID from `7' to `65534'

Feb 16 13:27:31 Andre usermod[24787]: change user `lp' password

Feb 16 13:27:31 Andre usermod[24793]: change user `mail' GID from `8' to `65534'

Feb 16 13:27:31 Andre usermod[24793]: change user `mail' password

Feb 16 13:27:31 Andre usermod[24799]: change user `man' GID from `12' to `65534'

Feb 16 13:27:31 Andre usermod[24799]: change user `man' password

Feb 16 13:27:31 Andre usermod[24805]: change user `messagebus' GID from `119' to `65534'

Feb 16 13:27:31 Andre usermod[24805]: change user `messagebus' password

Feb 16 13:27:31 Andre usermod[24811]: change user `news' GID from `9' to `65534'

Feb 16 13:27:31 Andre usermod[24811]: change user `news' password

Feb 16 13:27:31 Andre usermod[24817]: change user `polkituser' GID from `122' to `65534'

Feb 16 13:27:31 Andre usermod[24817]: change user `polkituser' password

Feb 16 13:27:31 Andre usermod[24823]: change user `proxy' GID from `13' to `65534'

Feb 16 13:27:31 Andre usermod[24823]: change user `proxy' password

Feb 16 13:27:31 Andre usermod[24829]: change user `pulse' GID from `116' to `65534'

Feb 16 13:27:31 Andre usermod[24829]: change user `pulse' password

Feb 16 13:27:31 Andre usermod[24836]: change user `root' GID from `0' to `65534'

Feb 16 13:27:31 Andre usermod[24836]: change user `root' password

Feb 16 13:27:31 Andre usermod[24843]: change user `saned' GID from `127' to `65534'

Feb 16 13:27:31 Andre usermod[24843]: change user `saned' password

Feb 16 13:27:31 Andre usermod[24849]: change user `sys' GID from `3' to `65534'

Feb 16 13:27:31 Andre usermod[24849]: change user `sys' password

Feb 16 13:27:31 Andre usermod[24855]: change user `syslog' GID from `103' to `65534'

Feb 16 13:27:31 Andre usermod[24855]: change user `syslog' password

Feb 16 13:27:31 Andre usermod[24861]: change user `uucp' GID from `10' to `65534'

Feb 16 13:27:31 Andre usermod[24861]: change user `uucp' password

Feb 16 13:27:31 Andre usermod[24867]: change user `www-data' GID from `33' to `65534'

Feb 16 13:27:31 Andre usermod[24867]: change user `www-data' password

Feb 16 13:27:32 Andre groupdel[24876]: remove group `avahi' 

Feb 16 13:27:32 Andre groupdel[24882]: remove group `avahi-autoipd' 

Feb 16 13:27:32 Andre groupdel[24889]: remove group `backup' 

Feb 16 13:27:32 Andre groupdel[24895]: remove group `bin' 

Feb 16 13:27:32 Andre groupdel[24901]: remove group `daemon' 

Feb 16 13:27:32 Andre groupdel[24907]: remove group `dhcp' 

Feb 16 13:27:32 Andre groupdel[24913]: remove group `games' 

Feb 16 13:27:32 Andre groupdel[24921]: remove group `gdm' 

Feb 16 13:27:33 Andre groupdel[24927]: remove group `gnats' 

Feb 16 13:27:33 Andre groupdel[24933]: remove group `haldaemon' 

Feb 16 13:27:33 Andre groupdel[24939]: remove group `irc' 

Feb 16 13:27:33 Andre groupdel[24945]: remove group `klog' 

Feb 16 13:27:33 Andre groupdel[24951]: remove group `libuuid' 

Feb 16 13:27:33 Andre groupdel[24957]: remove group `list' 

Feb 16 13:27:33 Andre groupdel[24963]: remove group `lp' 

Feb 16 13:27:33 Andre groupdel[24970]: remove group `mail' 

Feb 16 13:27:34 Andre groupdel[24976]: remove group `man' 

Feb 16 13:27:34 Andre groupdel[24982]: remove group `messagebus' 

Feb 16 13:27:34 Andre groupdel[24989]: remove group `news' 

Feb 16 13:27:34 Andre groupdel[24998]: remove group `polkituser' 

Feb 16 13:27:34 Andre groupdel[25004]: remove group `proxy' 

Feb 16 13:27:34 Andre groupdel[25010]: remove group `pulse' 

Feb 16 13:27:35 Andre groupdel[25019]: remove group `saned' 

Feb 16 13:27:35 Andre groupdel[25025]: remove group `sys' 

Feb 16 13:27:35 Andre groupdel[25031]: remove group `syslog' 

Feb 16 13:27:35 Andre groupdel[25037]: remove group `uucp' 

Feb 16 13:27:35 Andre groupdel[25043]: remove group `www-data' 

Feb 16 13:29:40 Andre sudo: cannot execute /usr/sbin/sendmail: No such file or directory

Feb 16 13:29:40 Andre sudo:    andre : user NOT in sudoers ; TTY=pts/0 ; PWD=/home/andre ; USER=root ; COMMAND=/etc/init.d/udev restart
```

---

### Post by inspired on 2009-02-20
> **AndreLeComte said:**
> [LIST]
[*]For some reason, I have the same issue on my desktop computer.
[*]My notebook computer was also running Ubuntu with the same username and password as my desktop system.
[*]I attached a copy of the etc/group file from my notebook to an email and sent it to my email address.
[*]I started my desktop system using the Ubunutu CD-R.
[*]I downloaded the etc/group file from my web-based email and saved it in the etc folder on my desktop computer.
[*]Now I can log into Ubuntu on my desktop computer, although some features such as visual effects and Internet access are not functioning.
[*]At the end of this message I have posted entries from the auth.log section of GNOME's System Log Viewer.
[*]How can I reverse these changes or restore my desktop system to normal working order?
[/LIST]
Dude. My heart goes out to you.
That is exactly what happened to me. I was going to post logs of it all to the forums and bug trackers, but I was busy and when I went to do it the logs had already gone. Please make a copy of the various logs which show the time you did the update. Include the Synaptic log to get a record of exactly WHAT was updated.
When was the last time you ran an update?
I see my system has for the last two days been telling me there are 53 updates available. I have not run them because I cringe at the thought of what they might do. It was a large number like that (40 or 50+) that I accepted and ran when this system hosing happened.

All I can recommend is what I did. 
[LIST=1]
[*]I manually recreated every group that was removed;
[*]put all the GIDs back to their correct number by following what they were in the logs (the one you have included here);
[*]added my username to the sudoes (there are many instances of info on how to do that here in the forums and elsewhere).
[*]I got hold of a copy of a working Groups file and used it as an example of what groups my username should be a member of. Sounds like you can use the one from your other computer as an example to work from. I got mine from various ones people had posted to the forums etc.
[/LIST]  

I think that's all I did. Not sure. Has been a while since that happened and I started this thread.
I will be away all weekend. But if next week I see you have unanswered questions I'll see what I can do/say to help.

Big thing I am keen to see is that this issue be reported with all supporting info. I am not a linux pro, so perhaps someone else would kindly comment on what Andre needs to gather up in terms of logs and info in order to report this so that it can be looked into. This is a major bug or issue or something.

Cheers,

Jonathan

**BY THE WAY... I've just reread what I had posted previously. I see I've spelt out a fair bit on how I went about fixing this. I suggest you read the full thread and make use of the info that is here already.**

---

### Post by nalimilan on 2009-08-27
AndeLeComte: The logs you attached are really interesting, they're the first that I've read that could actually help fixing that horrible bug.

From the line
> &#65279;Feb 16 13:26:26 Andre polkit-grant-helper[24375]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 24350 [uid=1000] [auth=andre]
I understand that you started the users-admin tool from System->Administration->Users and Groups before things went wrong. Is that the case? Do you remember exactly what operations you performed then? It looks like the groups list used by the configuration tool got empty, so all groups were eventually removed, logically leading to major problems on the system.

Thanks in advance! All those informations can help us fixing bug 160862 on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/160862](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/160862)

---

