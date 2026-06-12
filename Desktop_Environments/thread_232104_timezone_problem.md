---
title: "timezone problem"
date: 2006-08-08
forum: Desktop Environments
---

### Post by sutterp on 2006-08-08
I have a triple boot system, Ubuntu 6.0/SuSE linux/Windows XP.

Ubuntu, SuSE Linux and Windows are configured to local time, cmos time is localtime.

On shutdown, SuSE Linux and Windows save local time to cmos, ubuntu 6.06 saves UTC to cmos.

How and where to I change the ubuntu configuration so that, on shutdown, local time gets saved to cmos, rather than UTC?

Thanks

Peter

---

### Post by halfvolle melk on 2006-08-08
In /etc/default/rcS you can change "UTC=yes" to "UTC=no". This may fix the issue.

---

### Post by sutterp on 2006-08-08
Thanks a lot, this did solve the problem.

---

### Post by cprise on 2006-08-19
Why are people being told to edit an /etc file just to keep correct time? Can it get any worse??

No other Linux distro I use has this problem!

---

### Post by sutterp on 2006-08-19
Under Linux, one has the option to base the cmos clock either on local time or on UTC. Which one you use is up to you, and you define your preferences in /etc/default/rcS. 

With Windows, you do not have this option, you have only local time. So if you have a dual boot system with Windows and Linux, you have to use local time, otherwise the time will be incorrect after a re-boot.

You do not have this problems with other distros because other distros default to local time, in ubuntu and kubuntu, the default is UTC.

---

### Post by jimmygoon on 2006-08-19
I find that to be a pecular default as well, not that I have a problem with it. Meh, just set ubuntu and windows to both auto update their clocks...

or buy a watch... ;) j/king... I don't own one :P

---

### Post by sutterp on 2006-08-19
No, don't update the time in startup, set your system correctly; otherwise you are asking for trouble, because:

All files created/modified during the startup up to the point where time synchronisation too place will have incorrect modified/created/accessed date. Incorrect timestamps can have catastrophic effects, i.e. some cleanup script that deletes files older then a few hours will delete wrong files.

All log file entries will have incorrect timestamps.

If the machine is offering time services, client machines will pick up the wrong time if it happens that these request the time before the startup has completely finished.

Correct time and accurate time synchronisation is very important where several machines have to work together. In such an environment, none of the machines should be adrift mor then a few seconds.

---

### Post by cprise on 2006-08-19
> **sutterp said:**
> Under Linux, one has the option to base the cmos clock either on local time or on UTC. Which one you use is up to you, and you define your preferences in /etc/default/rcS. 

With Windows, you do not have this option, you have only local time. So if you have a dual boot system with Windows and Linux, you have to use local time, otherwise the time will be incorrect after a re-boot.

You do not have this problems with other distros because other distros default to local time, in ubuntu and kubuntu, the default is UTC.

IOW local time is the defacto standard, Ubuntu defaults to the opposite because it seems cool, and sending end-users into /etc with a text editor is not a usability concern.

Huh.

Ubuntu is going to have to anticipate common usage scenarios before most techies like me will ever feel comfortable recommending the OS to those who consult us. Streamlining the UI is not enough.

Ubuntu isn't even usable on most personal computers sold these days (LAPTOPS). Why? Because there are no appropriate security features for a mobile environment: No encryption of /home, no easy way to set/manage Wifi encryption, no VPN front-end, new user accounts are created with non-private home folders by default, etc. etc.

* The installer allows you to select unbootable filesystem types.

* Boot process tries to mount any external USB drives that were connected during the install -- and FAILS if even one of them is not connected.

* I had to edit /etc/gaminrc to keep gam_server from chewing up 20% of my CPU cycles (other people had problems with 100% CPU usage).

Of course, the answer is always 'hit the CLI'. Since when did the Ubuntu community adopt the same basic assumptions about maintainability as Fedora and Slackware?

---

### Post by sutterp on 2006-08-20
Maybe we should start a new thread about desirable things in ubuntu/kubuntu; maybe even somebody is listening of the developers.

I agree with most of what you say. 
localtime is a 'de-facto' standard and ubuntu/kubuntu is different. But, maybe it was developed in the UTC time zone, so for these people is does not matter and they haven't even noticed it.

Other 'desirable' features would be:

k3b allowing the burning of .ogg files, even though it lists ogg vorbis decoder in its plugins section, trying to add one results in 'unsupported format'; yet .ogg files and ogg-vorbis are GPL licensed.

sendmail configuration

usb camera installation and detection, the usb hotplug seems to work and detect the camera, but /dev/video0 does not get created.


Yes, GUI interfaces to configure the system are handy, as long as these use the standard configuration files. 

I try since years to convince Windows users to switch over to one of the Linux distros. If we are serious about this, then these kind of configuration features are a must. Windows users are used to this and will not switch to any distro where they have to use a text editor to configure their system.

On the other hand, I personally prefer to directly edit the configuration files with vi; it gives me more flexibility. The real problem is that different distros store these files in different locations and sometimes give them different names. So for somebody who switches from another distro this can be a pain in the neck.

---

### Post by cprise on 2006-08-20
I agree with most of what you say... but vi is a travesty ;)

More seriously, I think vi is fine as long as no one is forced to use it. This is actually a plus for Ubuntu, which includes the much more approachable 'nano' editor by default (nano is a clone of pico which is standard on BSD and MacOS). Having distributions that are only guaranteed to come with vi means that new users are always bumping up against the imperative to learn vi... Bad move! Young IT students see vi, xorg.conf, apache config and sendmail and think: "Screw this, I'm doing Windows or Mac instead!"

---

### Post by Statik on 2006-09-25
The only problem I see with all this is that in the Gnome time preferences you can select whether to use UTC or not, but this does not affect the rcS file. So, checking UTC or unchecking it only puts you 1 or 2 times your timezone off, not ontime. Stupid XP. I'd rather UTC, but Windoze doesn't seem to allow it. I also dislike that both OSs write the time BACK to the CMOS, without asking/informing. Caused me some headaches until I was able to figure out that they were doing it.

Statik

---

