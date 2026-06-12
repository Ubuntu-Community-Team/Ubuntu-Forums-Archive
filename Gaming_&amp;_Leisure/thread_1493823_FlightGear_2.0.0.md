---
title: "FlightGear 2.0.0"
date: 2010-05-26
forum: Gaming &amp; Leisure
---

### Post by ThePol2 on 2010-05-26
I spent the better part of a week trying to get FlightGear 2.0.0 running, so I thought I'd post my solution here to help others.
 
**Situation:** Running Ubuntu 10.04 (32 bit). I wanted to upgrade to FlightGear 2.0.0 since it has some nifty features 1.9.1 is lacking (1.9.1 is the version in the repos). FlightGear 2.0.0 worked when first installed (as per the [FlightGear Wiki]("http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu")), but died after I made some audio changes in the configuration menu. FlightGear would throw a segmentation fault on startup. I tried uninstalling, recompiling FlightGear (multiple times), using the GetDeb version, etc. All would die on startup. FlightGear worked under another user but never under my user. Log-level=debug didn't provide much help.
 
**Solution:** Macafyc in 2009 posted this workaround for Ubuntu 9.10 -- create an empty file in the home directory with name .alsoftrc with this line of text:
 
drivers=alsa.
 
Apparently, this is a known bug: 
[https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/403363](https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/403363)
[http://www.pulseaudio.org/wiki/PerfectSetup#OpenALApplications](http://www.pulseaudio.org/wiki/PerfectSetup#OpenALApplications)
 
I am up and running using the GetDeb version of FlightGear 2.0.0 and everything is great! One thing to note -- I tried resetting the audio setting back to the defaults in FlightGear and removing the alsoftrc file. FligthGear threw the same segmentation fault so I put the file back and now everything is A-OK.

---

### Post by Sealbhach on 2010-05-26
Thanks for passing on your tips.

I use the [compilation script]("http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu"), works great every time.

It's very simple, download the script and run it, the script does everything, nothing you need to do but watch it running.

.

---

### Post by ThePol2 on 2010-05-26
> **Sealbhach said:**
> Thanks for passing on your tips.
 
I use the [compilation script]("http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu"), works great every time.
 
It's very simple, download the script and run it, the script does everything, nothing you need to do but watch it running.
 
.
 
I used that same script to download and compile FligthGear 2.0.0 multiple times. Because of the PulseAudio issue I noted above, however, FlightGear was still failing on my system with a segmentation fault (FWIW I have a SoundBlaster card). This segmentation fault happened when I tried using the download_and_compile.sh script *and* when I tried the GetDeb version of FlightGear 2.0.0. My only solution was the workaround I mentioned above.

---

### Post by Sealbhach on 2010-05-26
Oh, OK I didn't see that. My comment was irrelevant then.:oops:

.

---

### Post by ubudog on 2010-10-07
Thanks for sharing this, fixed all my FlightGear problems.

---

