---
title: "CPU cooling software for Ubuntu?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by D!mon on 2006-06-09
There was a program in Windows called CPU Idle (cooling and power management software, [http://www.cpuidle.de/)](http://www.cpuidle.de/)), is there any similar Linux program or Linux is smart enough to keep cpu cool itself?

---

### Post by GenPFault on 2006-06-09
[How Cpuidle works]("http://www.cpuidle.de/works.php").  Look at the "Why Doesn't Windows Do That?" section.  So yes, Linux already does it :)

---

### Post by mcduck on 2006-06-09
[QUOTE=GenPFault][How Cpuidle works]("http://www.cpuidle.de/works.php").  Look at the "Why Doesn't Windows Do That?" section.  So yes, Linux already does it :)[/QUOTE]
Not properly, though. At least based on my experience.

For Athlon and AthlonXP CPU's (those don't support any frequency scaling or other power saving methods) there's athcool available in repositories. It might cause some problems so test it for some time before you make it start automaticly. Running it drops my idle CPU temp from 49C to 32C..

---

### Post by D!mon on 2006-06-09
[QUOTE=mcduck]Not properly, though. At least based on my experience.

For Athlon and AthlonXP CPU's (those don't support any frequency scaling or other power saving methods) there's athcool available in repositories. It might cause some problems so test it for some time before you make it start automaticly. Running it drops my idle CPU temp from 49C to 32C..[/QUOTE]

Thank you very much!

---

### Post by Getwild2 on 2006-06-09
I have found that my system is 9 degrees cooler running this software, so far with zero glitches.  

Can someone help me in the steps (or a link to steps) to cause "sudo athcool on" to be issued automatically?  I am a supreme noob and would appreciate it!!

***EDIT:***
I went to System-Preferences-Sessions and then the Starup Programs tab.  I clicked +Add and typed in "sudo athcool on" and clicked OK.  Will this work or no?  I dont think it will because I'll be prompted for a password for sudo.  I imagine I have to create a script and perform the above steps once the script is created.  I'm not sure how to do that.  Anyone?

---

### Post by mcduck on 2006-06-09
[QUOTE=Getwild2]I have found that my system is 9 degrees cooler running this software, so far with zero glitches.  

Can someone help me in the steps (or a link to steps) to cause "sudo athcool on" to be issued automatically?  I am a supreme noob and would appreciate it!!

***EDIT:***
I went to System-Preferences-Sessions and then the Starup Programs tab.  I clicked +Add and typed in "sudo athcool on" and clicked OK.  Will this work or no?  I dont think it will because I'll be prompted for a password for sudo.  I imagine I have to create a script and perform the above steps once the script is created.  I'm not sure how to do that.  Anyone?[/QUOTE]

You're right, putting 'sudo athcool on' in sessions doesn't work. 'gksudo athcool on' would, but you'd had to enter your password every time you log in. Not nice. So here's the 'simple GUI way' to run athcool on boot:

1: Install BootUp Manager: 'sudo apt-get install bum'
2. Open BUM, it's in System/Administration/BootUp Manager (run 'killall gnome-panel' if it's not there)
3. Athcool should show on the list of services. Mark it, and click 'Apply'
4. You're done. Next time you boot your machine, athcool will start too :)

---

### Post by Getwild2 on 2006-06-09
[QUOTE=mcduck]You're right, putting 'sudo athcool on' in sessions doesn't work. 'gksudo athcool on' would, but you'd had to enter your password every time you log in. Not nice. So here's the 'simple GUI way' to run athcool on boot:

1: Install BootUp Manager: 'sudo apt-get install bum'
2. Open BUM, it's in System/Administration/BootUp Manager (run 'killall gnome-panel' if it's not there)
3. Athcool should show on the list of services. Mark it, and click 'Apply'
4. You're done. Next time you boot your machine, athcool will start too :)[/QUOTE]
THANKS A LOT!  That's a nice little GUI!

Man, I see a couple of things I could unmark.  :-k  I'll be careful of course.  Any you'd recommend removing off-hand?  I see that the entry in regards to a battery would be okay to remove, since it is a desktop PC.

---

### Post by keithjr on 2006-06-09
[QUOTE=mcduck]You're right, putting 'sudo athcool on' in sessions doesn't work. 'gksudo athcool on' would, but you'd had to enter your password every time you log in. Not nice. So here's the 'simple GUI way' to run athcool on boot:

1: Install BootUp Manager: 'sudo apt-get install bum'
2. Open BUM, it's in System/Administration/BootUp Manager (run 'killall gnome-panel' if it's not there)
3. Athcool should show on the list of services. Mark it, and click 'Apply'
4. You're done. Next time you boot your machine, athcool will start too :)[/QUOTE]


Is this where you can find any of the multitudes of modules that Ubuntu loads up that aren't listed in the /etc/modules list?  I've been itching to knock some of those off...

As far as startups you don't need... if you are on a PC then you can also kill of PCMCIA, those are laptop expansion slots.  When I get home I'll install the GUI and take a look at the list and see what else I could recommend.

---

### Post by mcduck on 2006-06-09
The ones I have disabled are bluez-utils (no bluetooth here), ppp (no modem either), laptop-mode, apmd, powernowd (my AthlonXP doesn't support it), cupsys (no printer) and hplip. Probably some others could go too, but Ubuntu is running really fast anyway and disabling those services didn't really have any noticeable effect other than cutting second or two from boot time.. So I haven't bothered checking the rest :) I just installed BUM for athcool and disabled some of the most obvious ones while I had BUM open.. 

Don't take these as recommendations, it all depends on your machine and what you need. Look for things that look like you don't need them, and then do some searching with google to check what they actually do.. (I didn't, but that doesn't mean that you shouldn't :D)

---

### Post by D!mon on 2006-06-10
also you can run ```
sudo sysv-rc-conf
``` from the console and set runlevels for athcool there (I think they should be 2,3,4,5; correct me if I'm wrong)

---

### Post by frenkel on 2006-06-10
[QUOTE=mcduck]Not properly, though. At least based on my experience.

For Athlon and AthlonXP CPU's (those don't support any frequency scaling or other power saving methods) there's athcool available in repositories. It might cause some problems so test it for some time before you make it start automaticly. Running it drops my idle CPU temp from 49C to 32C..[/QUOTE]
This has nothing to do with the Linux kernel not implementing this correctly. It's something AMD does, they don't enable those bits in the CPU, because it caused problems on some systems, just like athcool causes some soundcards not to work properly for example.

---

### Post by praveenpious on 2007-11-28
Any softwares like athcool for pentium 4 processors?

---

