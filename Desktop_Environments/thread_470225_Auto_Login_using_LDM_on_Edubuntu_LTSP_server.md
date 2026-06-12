---
title: "Auto Login using LDM on Edubuntu LTSP server"
date: 2007-06-10
forum: Desktop Environments
---

### Post by MartinJ on 2007-06-10
Hi,

I'm thinking about setting up and installing an Edubuntu terminal server with several clients.

Is it possible for each client to automatically login after booting up?  Ideally, I'd rather not have to issue usernames and passwords, but have one set up for each client.

Thanks

---

### Post by Azzuron on 2007-08-30
did you ever find a solution to this? I need to do the same thing, auto login to bare x11 desktop and run a script... It seems that the GDM that is used by ltsp is different from the regular one that is installed, i dont know if it is LDM, or not, but LDM wasn't installed on my system, and i couldn't find any config info about it anywhere... thanks!

  --Dave

---

### Post by 3rdtechie on 2008-01-12
> **Azzuron said:**
> did you ever find a solution to this? I need to do the same thing, auto login to bare x11 desktop and run a script... It seems that the GDM that is used by ltsp is different from the regular one that is installed, i dont know if it is LDM, or not, but LDM wasn't installed on my system, and i couldn't find any config info about it anywhere... thanks!

  --Dave

I would like to install LDM also, but can't get it.  I clicked LDM to install from the CD using the  Synaptic Package Manager, but I don't see any difference.  How do I run LDM so I can set up my Thin Client Server? :confused:  My TFTP is not working and I thought LDM would help since I am a n00bie to Linux command line command.  I want to run a LTSP thin client network, but it is way harder than it should be to set up.  DHCP3 runs. I have the Etherboot floppies.  I have it wired with 2 ethernet cards.  But, it won't connect.  I had to install Edubuntu from the Live CD and then add packages from the server CD since the Server CD kept hanging during installation.  I thought LTSP worked with Edubuntu "out of the box."  :x

---

### Post by adamlamee on 2008-05-11
have you tried:

[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html)

about 1/3 way down "auto login features"?

---

### Post by casey.mynott on 2008-06-05
> **adamlamee said:**
> have you tried:

[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html)

about 1/3 way down "auto login features"?

I have tried this with no luck. Any Edubuntu LTSP experts that have this feature working??? Anyone????

---

### Post by casey.mynott on 2008-06-07
> **casey.mynott said:**
> I have tried this with no luck. Any Edubuntu LTSP experts that have this feature working??? Anyone????

SOLVED! After spending some time on the BCFOSS gmail mail list the answer came up. Your lts.conf file must be setup like the example below. It worked and my students and I are much happier. ;)

[00:50:04:72:6A:C4]
    LDM_AUTOLOGIN=true
    LDM_USERNAME=computer
    LDM_PASSWORD=computer

---

