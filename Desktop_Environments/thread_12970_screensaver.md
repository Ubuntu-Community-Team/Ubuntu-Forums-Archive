---
title: "screensaver"
date: 2005-01-28
forum: Desktop Environments
---

### Post by danip on 2005-01-28
Is there a way to make it so that gnome recognizes I am watching a movie so that the screen saver quits turning on every minutes while im running on battery power?  I went in and turned the screen saver off and turned off power management yet every minute or so my screen just goes black...rather annoying.

---

### Post by banadushi on 2005-01-28
If your using totem, fullscreen, then it should automatically tell xscreensaver to not activate.

Have a good one!

Jason

---

### Post by clparker on 2005-01-28
Since totem is the WORST ubuntu media player...that's not an option

---

### Post by Perfect Storm on 2005-01-28
If you are using Mplayer:

Select 'Preferences' in Mplayer. Click on the 'Misc' tab. There's an option called 'Stop XScreenSaver'.



.:=The AI Dude=:.

---

### Post by Yukonjack on 2005-01-28
Applications--->System Tools--->System Monitor Scroll down near the bottom xscreensaver and click end process. This should do it for you.

---

### Post by Perfect Storm on 2005-01-28
Isn't it a bit harsh if he want to only disable the screensaver while seeing a DVD/movie?

---

### Post by danip on 2005-01-30
None of those seem to work the screen still just goes black after about a minute

---

### Post by Yukonjack on 2005-01-30
Sounds like other problem than a screensaver in Ubuntu. If you turn off all screensaver from menu and process, maybe overheating. Or this could be a setting in your bios for your laptop energy saver or something along these line. Might be the wrong driver in your movie player.

PS: AI it's call trouble-shooting

---

### Post by danip on 2005-01-30
Anybody know how to get into the bios on a laptop?  The only thing I have ever been able to figure out is if i press f12 it gives me options of wether to boot from a hard drive cd or a few more options.

---

### Post by Yukonjack on 2005-01-30
Need more info of your laptop: brand, mb, chips ect......

---

### Post by Yoda_Oz on 2005-01-30
if its a dell press f2 at the same time you are supposed to press f12 to get the boot options. you know... when the BIG dell logo comes up!

---

### Post by danip on 2005-01-30
It is a toshiba satellite pentium 4 mobile 2.8ghz....ive tried to look this up before on how to get into the bios but never had any success

---

### Post by lukem on 2005-01-30
Many machines will tell you what to press in the first screens when you power up.

---

### Post by Yukonjack on 2005-01-30
[QUOTE=danip]It is a toshiba satellite pentium 4 mobile 2.8ghz....ive tried to look this up before on how to get into the bios but never had any success[/QUOTE]
 Could be the Del key.

---

### Post by danip on 2005-01-30
figured it out was the esc key (weird).  There was an option in the bios under battery management that said display power off and it was set to 3 minutes, i disabled it and the display still turns off every minute or so despite all screen saver options being turned off.  Any other suggestions?  Is hoary stable enough to try upgrading to that and see if that fixes anything?

---

### Post by bitfoo on 2005-01-30
Have you click Computer > Desktop Preferences > Screensaver and set "Blank After" to 0.  If that was already suggested feel free to smack me. :|

---

### Post by danip on 2005-01-30
I had screen saver disabled...tryied turning it on and doing that but still nothing.

---

### Post by danip on 2005-02-04
Could this be a ACPI setting?  If so how do i edit that?

---

### Post by danip on 2005-02-04
I uninstalled all acpi packages and discovered that is definintly the problem.  Can anybody tell me how to fix this now?

---

