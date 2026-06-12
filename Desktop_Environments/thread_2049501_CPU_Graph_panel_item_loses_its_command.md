---
title: "CPU Graph panel item loses its command"
date: 2012-08-28
forum: Desktop Environments
---

### Post by JKyleOKC on 2012-08-28
I have a problem that may be somewhat similar to that in [http://ubuntuforums.org/showthread.php?t=2039681](http://ubuntuforums.org/showthread.php?t=2039681) but it differs in that it's not random as in the other thread.

I've just installed Xubuntu 12.04.1 in a brand new machine and am configuring it to match as closely as possible the look and feel of the 10.04.4 installation that died with the previous box. The CPU Graph plugin for the top panel loses its associated command (which I changed from the original default to "xterm -e top" to match the 10.04 default) at every login. Nothing else seems to be affected, but that line of the launcher configuration file gets everything from "=" to "\n" wiped out.

I've tried setting the permissions on that file to 444, but that made no difference. And even after I changed them to 444 to force read-only to everyone, the "properties" listing for that item was still able to change both the setting and the file itself. I presume that this means that whatever is happening is going on under super-user permissions during either the log-in or log-out sequences, but I haven't been able to determine whether it's a bug or a misconfiguration of something else...

---

### Post by LewisTM on 2012-08-28
I've seen this "override" behavior a few times and I'm still looking for a good explanation. It seems that Xfce processes can inherit superuser privileges from LightDM or X and revert ANY ownership or permission changes that users attempt to apply to their config files.

I found the only way to prevent file changes by Xfce plugins is to do a file system lock
```
sudo chattr +i <file>
```
That will for sure keep your config file intact. It may or may not solve your problem. Chances are the plugin will spawn with empty or default settings regardless; it just won't be able to save those settings to disk. If your settings are indeed valid then this should be considered a bug.

Cheers!

---

### Post by JKyleOKC on 2012-08-28
I'll give that a try and report back. Thanks!

EDIT: Nothing seemed to work; I then found the CPU Graph web pages through the xfce site, and discovered that it's a bug in the applet that was fixed two builds ago, but only for xfce 4.10 users. Upgrading to 4.10 via its PPA took care of the problem.

---

### Post by JKyleOKC on 2012-09-01
> **JKyleOKC said:**
> Upgrading to 4.10 via its PPA took care of the problem.Except that it didn't. I don't know why it worked for a few sessions, but then it went back to its old ways.

I dug through the xfce-goodies web site and found that the fix was version 1.0.2 of the applet -- but the PPA only has 1.0.1, so no fix is in a repository yet.

Checking the latest source links on the goodies pages indicates that version 1.0.5 has been released already, though. I've downloaded source for this latest version, which should include the fix, but I'd like to make it into a deb package that Synaptic could control. I have no problem going the configure/make/install route (been using assembly language since mainframe days in the 1960s) but I like the tracking features of a package manager...

Can anyone recommend a good utility for dealing with this? And is there anything special I need to do to create a 64-bit version of the applet, compatible with the xfce 4.10 panel?

Alternatively, how can I request that the PPA be updated to the latest version? I suspect that it was frozen at 1.0.1 for the 10.04 release, but that's holding up a really annoying bug fix...

---

### Post by JKyleOKC on 2012-09-02
Finally solved!!!

And my solution also fixed the inability to launch the command by clicking in the graph area.

What I did was to search through Launchpad to locate the version 1.0.5 deb file (in the correct architecture) that has been created for Quetzal, download it direct to my machine, and install it with debi. Actually when I double-clicked the downloaded file, Software Center popped up and did the upgrade for me, but I then ran debi to make sure the right version was in place.

It now behaves just the way the old applet does in Lucid. How can I request that this version be backported to Precise in the PPA? It works just fine here despite being built for Quetzal...

EDIT: Here's the LaunchPad link: [https://launchpad.net/ubuntu/quantal/+source/xfce4-cpugraph-plugin/+builds](https://launchpad.net/ubuntu/quantal/+source/xfce4-cpugraph-plugin/+builds)

---

