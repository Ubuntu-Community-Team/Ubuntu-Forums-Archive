---
title: "Uplink 1.55 for Ubuntu not working right"
date: 2012-05-09
forum: Gaming &amp; Leisure
---

### Post by calavier62 on 2012-05-09
Hey all,

For quite awhile, I've been a huge uplink fan- and when i noticed it was available for download in the software center, I was thrilled. To be honest, I doubt I spent much longer then 25 seconds before purchasing it. 

But upon starting up the game, I noticed that none of the buttons on the bottom left hand of the screen would work, with the exception of the "Applications" menu. And when I went to look in the options, things only got worse, as ALL of the buttons are on the bottom right hand of the screen, and clicking them does nothing.

In short, I had to reboot my computer with work in the background. 

I don't know whether or not it is a window border issue (I'd presume not, as I can access ONE button on the bottom of the screen), an operating system issue (I know this game worked in the last release), or an issue with Uplink itself.

I don't want to go complaining to Introversion or Canonical before getting at least some reports of others having the issue (or similar issues), and I know that it's not a specific hardware issue. 

Thanks in advance!
-Camden

---

### Post by thatguruguy on 2012-05-09
> **calavier62 said:**
> Hey all,

For quite awhile, I've been a huge uplink fan- and when i noticed it was available for download in the software center, I was thrilled. To be honest, I doubt I spent much longer then 25 seconds before purchasing it. 

But upon starting up the game, I noticed that none of the buttons on the bottom left hand of the screen would work, with the exception of the "Applications" menu. And when I went to look in the options, things only got worse, as ALL of the buttons are on the bottom right hand of the screen, and clicking them does nothing.

In short, I had to reboot my computer with work in the background. 

I don't know whether or not it is a window border issue (I'd presume not, as I can access ONE button on the bottom of the screen), an operating system issue (I know this game worked in the last release), or an issue with Uplink itself.

I don't want to go complaining to Introversion or Canonical before getting at least some reports of others having the issue (or similar issues), and I know that it's not a specific hardware issue. 

Thanks in advance!
-Camden

It would be helpful to know which version of Ubuntu you're running, and what hardware you're running it on. You might also consider running the game from the terminal, and posting the output.

It's difficult to help you without some basic information.

---

### Post by calavier62 on 2012-05-09
Sorry, I've got mono so I totally spaced on giving my hardware specs (which is especially weird because I often help beginners with hardware problems, and have to ask them to post their specs)

CPU: AMD Vision E350 1.6ghz dual core (64bit running 32bit kernel with PAE enabled)
RAM: 3gb
Video: ATi Radeon HD 6310, with 512mb dedicated DDR3 video RAM - using proprietary drivers
Computer Manufacturer: HP; model HP-2000-329WM

I have no idea where Uplink is installed, nor do I know if there's a terminal command to start it. I checked the "/bin" "/usr/bin" "/sbin" "/usr/sbin" "/usr/local/bin" and "/usr/games" directories, with nothing coming up. It could be that I've used Red Hat distros primarily for eight years and Debian (ubuntu) installs files to other directories.

And before I forget, I'm running Ubuntu 12.04.

Thanks!
-Camden

---

### Post by thatguruguy on 2012-05-10
According to [this thread at the Introversion board]("http://forums.introversion.co.uk/uplink/viewtopic.php?t=39325"), the issue may involve screen resolution.  You should try the suggestions in that thread and see if that solves the issue.  Specifically, try it in windowed mode, change the resolution in the "options" menu of the game to maximum, and then restart it.

You may want to look in /usr/share/games or /usr/local/games for the executable file.  If it's not there, you can always look at the uplink.desktop file under /usr/share/applications to see where the file is.

---

