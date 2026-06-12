---
title: "Team Fortress 2 boosting performance help?"
date: 2010-06-19
forum: Gaming &amp; Leisure
---

### Post by ucal on 2010-06-19
TF2 runs like crap right now, so here's what I've got on my todo list so far:

Start it in a separate x-server:  Got to figure out how to do this.

Configure it so Compiz turns off when it runs:  Should help a little.  

Run it in opengl mode:  No idea if this will help, or if it's even possible, but I figured since it runs for macs now, it should be possible.  

Turn all the settings on low:  Don't want to have to do this, since it ran fine on Windows, but it seems to be a necessity.  I really wish ATI would actually support their linux market >_<

Update Drivers.  I've heard that the open source drivers actually run better than the proprietary ones in certain situations, so I'm going to experiment.  Either way, I'll probably be running the latest version of whatever driver I choose.  

Got any more performance tweaks I could do, or any comments on the ones I'm going to attempt?

---

### Post by HoKaze on 2010-06-19
Just as a little note, quite a few people I know have noticed that even on windows recent updates have made the game run a lot worse. One person I know who has a fairly decent (if slightly old) Nvidia card on Win7 used to be able to run TF2 on some of the higher settings with no issues but these days has to run far lower settings to get good FPS and even then gets stuttering every now and again.
In other words, as of late TF2 has been slower in both windows and linux so beyond what you're already doing there's not much you can do until Valve fix these issues.

Also, although it won't make much difference, avoid having any large programs running in the background and make sure that your CPU(s) are set to either ondemand or performance.
I'm no expert on this or anything though, so don't take my word for it. I've just seen that quite a few people are having issues...

---

### Post by ucal on 2010-06-19
> **HoKaze said:**
> Just as a little note, quite a few people I know have noticed that even on windows recent updates have made the game run a lot worse. One person I know who has a fairly decent (if slightly old) Nvidia card on Win7 used to be able to run TF2 on some of the higher settings with no issues but these days has to run far lower settings to get good FPS and even then gets stuttering every now and again.
In other words, as of late TF2 has been slower in both windows and linux so beyond what you're already doing there's not much you can do until Valve fix these issues.

Also, although it won't make much difference, avoid having any large programs running in the background and make sure that your CPU(s) are set to either ondemand or performance.
I'm no expert on this or anything though, so don't take my word for it. I've just seen that quite a few people are having issues...

That makes a lot of sense actually.  I installed another source game from Steam, Vampire, The Masquerade, and it runs just as well as it did on windows for me (which, granted, is still slightly buggy, but that's the game's issue, and not one I can really fix).  TF2 however, a source game, doesn't run nearly as well.  Granted, the only similarities are the engine, but it goes to show that something valve did upped the requirements of TF2.  This could be something like model and texture quality (very likely), or maybe engine specific tweaks. 

How would I go about setting my cpu to performance.  I remember in arch, there were terminal commands to do so, but those were specific to cpufreq.  Does ubuntu use cpufreq?

---

### Post by HoKaze on 2010-06-19
There are several ways of setting cpu frequency. There's the cpu frequency monitor for GNOME panel, the cpufreq-selector command and of course, plain old echoing to the correct file.

For the first one just right click the GNOME panel and choose the "CPU frequency scaling monitor". You'll need one montior for every CPU you have. Right click on them and choose preferences/properties and select the CPU you wish that specific monitor to work for (e.g. CPU 0, CPU 1). Then just left click them and you'll be able to choose frequency and governor for each CPU. (It may prompt you for the root password however)
If you're using GNOME this is the easiest and simplest method in the long run, I recommend it.

Assuming that you're not using GNOME or just want to do it the old fashioned way, the command is cpufreq-selector and you use the -f option to choose frequency, -g to choose from the available governors (e.g. powersave, performance, ondemand) and -c to choose the CPU. An example would be: "cpufreq-selector -c 0 -g ondemand" to set CPU 0 to ondemand.

Finally, I can point you towards this script I wrote that uses the echo method and uses a simple GTK dialog to set the governor for all CPUs, no matter how many you have: [http://gtk-apps.org/content/show.php/CPU+frequency+governor+selector?content=124444&PHPSESSID=594bd15a06ae1691b675c1ac4882898d](http://gtk-apps.org/content/show.php/CPU+frequency+governor+selector?content=124444&PHPSESSID=594bd15a06ae1691b675c1ac4882898d)
It requires zenity and must be run as root though (if it's not run as root it'll prompt for the password using gksu). It's good for those who aren't using GNOME or KDE, although KDE and GNOME users can make use of it too.

Hope all this info helps! Be sure to ask if you encounter problems or need anything explaining.

---

### Post by ucal on 2010-06-19
I've actually got a pretty big problem.  TF2 is locking up after a few minutes of gameplay.  It freezes, and then plays the last half second of audio over and over again until I power off the computer.  Any ideas?

---

### Post by HoKaze on 2010-06-19
> **ucal said:**
> I've actually got a pretty big problem.  TF2 is locking up after a few minutes of gameplay.  It freezes, and then plays the last half second of audio over and over again until I power off the computer.  Any ideas?
Back when Valve were allowing people a free trial of TF2 about a week ago I got the same issues, although I was able to close it usually if I waited long enough. Unfortunately I don't own the game myself so I can't be of much help and when I checked on the Wine app database nobody else had any answers.
Although nowhere near as bad, I noticed that one of my friends was having similar stuttering problems on rare occasions on Windows. Those usually only lasted a few seconds though.

From what little research I've done, simply disabling sound doesn't make a difference and even on minimal settings this still occurred when using wine. Try keeping an eye on the winehq appdb page for TF2: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901) somebody may eventually come up with a solution. In the meantime, trying fiddling with various wine settings. Maybe change the windows version, see if disabling sound makes any difference and just generally experiment. You might also want to try using an older/newer version of wine and see if that makes a difference.

I'm sorry, wine isn't really may area of expertise. You could try posting a bug report or comment over at winehq or you could start a thread in the Wine section of the forum as you're more likely to get a response from somebody more in the know there. Sorry I can't help more. 
Again, recent updates seem to be the issue as looking at winehq there are plenty of reports from a month ago and earlier of people running the game pretty smoothly.

Good luck, hope you get it sorted out.

---

