---
title: "Linux Home Automation"
date: 2009-01-05
forum: General Help
---

### Post by djcrash1981 on 2009-01-05
Good day to all and a happy new year.

I want to start a project but i don't know where to start, so i hope here can find a little of light.

Like the title says i want to start a home automation process, I've googled it and found this particular page:
[http://www.linuxha.com](http://www.linuxha.com)

And I've also found this Ubuntu related project:
[http://www.linuxmce.com/](http://www.linuxmce.com/)

But I don't know which hardware i have to buy or even if my electric installation is going to work.

Thanks for your time, and sorry for my bad english.

---

### Post by 2hot6ft2 on 2009-01-05
You mean like this?
[http://ubuntuforums.org/showthread.php?t=757755](http://ubuntuforums.org/showthread.php?t=757755)

Or this
[http://plutohome.com/](http://plutohome.com/)
That's wild, you gotta watch the flash there.

---

### Post by Maheriano on 2009-01-05
I'm doing the same, I can help you out with the media aspect of it if you like. I have my Ubuntu box set up as my media centre right now, your options are Elisa, MythTV/Mythbuntu or LinuxMCE if you want to manage your media files. I use Elisa and Myth TV simply because LinuxMCE requires an older version of KDE to be installed and Mythbuntu scares me. Both are complete reinstalls and I want to stick with what I have running already. Either way you should research them all and find out what's best for you. After that, get a SPDIF cable running to set up AC3 passthrough in order to get 5.1 Dolby Digital sound from your machine.

As for other things, check out ZoneMinder for home security, it'll run both wired or wireless cameras and does a phenomenal job.

I'm also running my desktop machine as a webserver if you want to do that, you can serve up all your media/files to access them remotely without having to use a remote connection and even stream your song collection.

For the specific automation side of things, there's a unit called the Fusion Brain which we use the car computer community, you can buy them online for about $60. Lots of digital/analogue inputs/outputs and you can attach relays to any of them to hook them up to whatever you want. The only issue with them is that they haven't released a Linux driver for them but maybe someone here can hack it together. Otherwise you can even set up each pin on your serial connector to output a signal to a relay and work the same way.

---

### Post by 2hot6ft2 on 2009-01-05
Just finished reading a 8 page thread on LinuxMCE that died about a year ago. Not really worth linking to now. Looking at the Current Events for it here [http://wiki.linuxmce.com/index.php/Current_events](http://wiki.linuxmce.com/index.php/Current_events) and the changes log for it here [http://wiki.linuxmce.com/index.php/Special:Recentchanges](http://wiki.linuxmce.com/index.php/Special:Recentchanges) it looks like it's being heavily developed if I'm reading it right. Some pages haven't been updated in 6 months.

Nice to see it hasn't died as it looks like it has the potential to be pretty nice one day.

---

### Post by djcrash1981 on 2009-01-05
> **2hot6ft2 said:**
> You mean like this?
[http://ubuntuforums.org/showthread.php?t=757755](http://ubuntuforums.org/showthread.php?t=757755)

Or this
[http://plutohome.com/](http://plutohome.com/)
That's wild, you gotta watch the flash there.

Thanks for the really fast replay, in my first attempt i would like to do is what is explained on the forum, after that i would like to try the "pluto" thing :D

So, anyone know what i have to buy first to do the lights thing??


Thanks a lot for all your help :D

---

### Post by txcrackers on 2009-01-06
Most of the HA technology uses house-wiring and currents that are US-standard (120V, 60 Hz). You'll probably want to start there...

---

### Post by Sable683 on 2009-01-06
I built a LinuxMCE machine using most of the same components from the demo video and the media center worked like it said. The sound is incredible using the optical output to a Sony 5.1 digital surround stereo. It's just like being in a theater. I have not tried some of the home automation yet, but this is something that I do want to research. 
   The reason they use an older version of Kubuntu is because once the Kubuntu release comes out, they developers need to tweak the MCE portion to make sure everything works... A good rule of thumb is when 8.10 comes out, LinuxMCE should be using 8.04 (give or take a month or two). The ultimate goal for LinuxMCE was to make it distro independent so you would be able to install it with any linux distro. I do not know if this is still the case, but I would rather use a gnome desktop instead of a KDE one. 
   All in all, it is a pretty good system, I even run an old laptop as a diskless media director (pxe boot) to control things. Another thing that works is using a wiimote like a wireless mouse to control your media center. I am waiting for Neil Cherry's book Linux Smart Homes for Dummies to arrive (ordered last week).

---

