---
title: "nomachine so unreliable"
date: 2007-07-28
forum: Desktop Environments
---

### Post by tigerstripedcat on 2007-07-28
[B]Is anyone else trying to keep a persistent session up on a nomachine server?

If anyone is successfully using nomachine from several computers and able to keep a session active for weeks at a time with fiesty, please let me know.  And let me know how much ram you have.
[/B]

  I try to use nomachine on feisty with 4 different computers.  Usually it works for a day or so and a couple of reconnects, but after a few times I get a "connection lost with server" and then I try and reconnect and all the work on my session is gone.   (And it's never worked from a windows client.  Again it worked a few times but crashes when a flash 9 video is running.)  And the log files are so confusing, I don't know where to look.

Nomachine is the best thing since sliced bread, but It's so aggravating.  Aside from buying more ram and wiping Ubuntu and starting over, I'm running out of ideas.

---

### Post by MrHippocampus on 2007-07-28
I don't normally use sessions, probably because the first time I tried to it didn't work and I couldn't log in again. I think sessions being a bit dodgy is a common problem. I would try using NX 3.0 (if your not using it already)

---

### Post by Sarah Dryell on 2007-07-30
Hello,

NoMachine was rather concerned by this post and would like to ask the author to contact me, either via this forum or privately, and provide the version of the software you are using. This is because with the release of NX 3.0, we fixed some issues very similar to the ones you are describing:

1) the X11 agent was causing lost connections and the feature of session resume to not function correctly. If the problem is still occurring, we need to investigate.

2) The following Trouble Report was fixed: [http://www.nomachine.com/tr/view.php?id=TR10D01530](http://www.nomachine.com/tr/view.php?id=TR10D01530), which we opened in relation to Flash Player 9 beta.  Can I ask what is crashing, the session or the browser?

Finally, the location of the logs. If you want to take a look in the logs, 

- Session directories are placed in the home dir under .nx. They are named C-<session id> for running sessions and F-C-<session id> for failed sessions.

- Search for core files in the home directory. If the agent crashed, a core file should have been generated.

- NX Server and NX Node (the process that monitors the agent) write messages in the syslog /var/log/messages).  'grep NX /var/log/messages > syslog.extract' helps you to extract  the relevant messages. In this particular case, you would look for 'ERROR: Unexpected termination of nxagent because of signal: 11' .

If these issues are occurring in NX 3.0, you can send me the logs directly and I will make sure our support team takes a look, opens the relative Trouble Reports and works on implementing fixes. 

Kind regards,

Sarah Dryell
NX Support
NoMachine.com

---

### Post by tekoholix on 2007-08-13
Sarah Dryell,

I would have to agree, on the concept that nomachine's server-end package is unreliable, but more so in the initial installation / config.  I run Feisty, fully upgraded to present-day, and the most recent versions of the nomachine client, node and server installed.

To begin with, I followed the nomachine installation instructions TO THE T, with the ONLY variation being the creation and propagation of my own key, which did succeed.

At first, before I learned where all the logs are, for troubleshooting, when I logged on (using my own keys) from a Feisty notebook on my OWN LAN, I auth'd just fine, and saw the desktop begin to load.  ALWAYS, within tenth's of a second of the gnome panels loading, I would be booted, and told of a network error.  Began looking for info that might help me get this issue resolved, and found DOZENS of posts, showing completely unrelated errors, somewhat related errors, and complete successes in install / config, on the same OS as I am running.

Attempted some of the fixes that might have helped my own situation, and now cannot even start the server service...  All tests show server not running, and cannot start it.

How reliable is that?  Of course, I do understand that there can be differences in system hardware and software inventories and configurations, which might affect paths, dependencies and such, but your install SHOULD be able to AT LEAST check that it will have what it needs, before installing, and causing us so much troubleshooting...

As well, I find that your policy of offering NO free support to free version users is pretty normal, IF / WHEN YOU HAVE COMPLETE DOCUMENTATION for these users to make use of, or make it open-source, so that we have the resources to support ourselves.  I cannot count how many other posts I've seen, on this and various other forums, about the ridiculously incomplete, inaccurate, and otherwise just plain wrong documentation available.  Now, having followed it perfectly, and then hunted for self-help when YOUR instructions DID NOT WORK, I must firmly agree...

Paul Harmor
Tekoholix.Computer.Services


EDIT:  I might add, that due to the complete lack of support on these packages, and more importantly, the complete lack of operability that I experienced with them, after 2 full days trying, I finally broke down and installed the FreeNX packages from the Seveas repo's, AND IT ALL WORKED WITHOUT A HITCH, in less than 15 minutes...  Much as I still imagine the official nomachine packages to be more up-to-date and functional, if they don't work at all, what good are they???  Open-source, AGAIN, kicking the crap out of proprietary software, and at their own game, as well...  lol

---

### Post by LordChaos73 on 2007-08-17
Hi,

I've installed the deb's from [http://www.nomachine.com/download-package.php?Prod_Id=1](http://www.nomachine.com/download-package.php?Prod_Id=1) on my feisty machine at home, but I seem to get disconnected every time Gnome has just finished starting up:

Aug 17 07:47:09 shuttlex gconfd (ericd-20577): starting (version 2.18.0.1), pid 20577 user 'ericd'
Aug 17 07:47:09 shuttlex gconfd (ericd-20577): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 17 07:47:09 shuttlex gconfd (ericd-20577): Resolved address "xml:readwrite:/home/ericd/.gconf" to a writable configuration source at position 1
Aug 17 07:47:09 shuttlex gconfd (ericd-20577): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 17 07:47:09 shuttlex gconfd (ericd-20577): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 17 07:47:09 shuttlex gconfd (ericd-20577): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 17 07:47:16 shuttlex gconfd (ericd-20577): Resolved address "xml:readwrite:/home/ericd/.gconf" to a writable configuration source at position 0
Aug 17 07:47:19 shuttlex NXNODE-3.0.0-76[20540]: ERROR: Unexpected termination of nxagent because of signal: 11 Logger::log nxnode 3752
Aug 17 07:47:19 shuttlex NXNODE-3.0.0-76[20540]: ERROR: run command: process: 20554 died because of signal: 11 Logger::log nxnode 3759
Aug 17 07:47:21 shuttlex NXNODE-3.0.0-76[20562]: ERROR: Error when monitoring session: Unexpected termination of nxagent 'NXSessionMonitor::__setSessionStatus'
Aug 17 07:47:21 shuttlex NXNODE-3.0.0-76[20562]: Directory '/home/ericd/.nx/C-shuttlex-1006-5B5E0411B4CB6492EDD3DB594FF14851' renamed into '/home/ericd/.nx/F-C-shuttlex-1006-5B5E0411B4CB6492EDD3DB594FF14851' for further investigation Logger::log nxnode 5911
Aug 17 07:47:21 shuttlex NXNODE-3.0.0-76[20562]: session monitor: cleaning session files: removing '/tmp/.X11-unix/X1006' Logger::log nxnode 8449
Aug 17 07:47:21 shuttlex NXNODE-3.0.0-76[20562]: session monitor: cleaning session files: removing '/tmp/.X1006-lock' Logger::log nxnode 8458
Aug 17 07:47:22 shuttlex NXNODE-3.0.0-76[20540]: Session 'unix-gnome' on port '1006' failed. Logger::log nxnode 5990
Aug 17 07:47:24 shuttlex NXSERVER-3.0.0-63[20556]: ERROR: NXNodeExec: Cannot kill nxssh process: No such process 'NXNodeExec::exec'
Aug 17 07:47:24 shuttlex NXSERVER-3.0.0-63[20556]: User 'ericd' from 'XXX.XX.XX.XX' logged out. 'NXLogin::reset'

I've added EnableUnencryptedSession = "0" to both node.cfg and server.cfg but that didn't help.

Thanks,

Eric

---

### Post by LordChaos73 on 2007-08-17
I fixed it by disabling beryl-manager at Gnome startup.

Regards,

Eric

---

### Post by mchaley on 2007-11-12
FreeNX > NoMachine?

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

