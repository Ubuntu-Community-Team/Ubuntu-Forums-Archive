---
title: "flash no sound with firefox 3.6"
date: 2010-04-03
forum: Desktop Environments
---

### Post by kakyoism on 2010-04-03
Just upgraded to firefox 3.6 on Hardy.
Now no sound with youtube or any flash videos.

I tried to reinstall flashplugin-nonfree, no effect.


Please help!

---

### Post by 2hot6ft2 on 2010-04-03
[No sound on YouTube or Hulu videos - [FOT009]]("http://lovinglinux.megabyet.net/?page_id=220#No-sound-on-YouTube-or-Hulu-videos-2")

From here
 [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by adam814 on 2010-04-03
The version of flash with Hardy is probably pretty old by now.  Why not manually install a newer version from Adobe (since you've installed a newer browser anyway)?  It's usually just a matter of accepting the license and copying the "libflashplayer.so" that extracts to /usr/lib/mozilla/plugins.

---

### Post by kakyoism on 2010-04-04
I tried both of your solutions. 
Doesn't work...

Here is the result of calling "locate libflashplayer.so"
/home/kakyo/.flock/plugins/libflashplayer.so
/home/kakyo/.flock/plugins/tmp/libflashplayer.so
/home/kakyo/.flock/plugins/tmp/npwrapper.libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/share/flock/plugins/libflashplayer.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

---

### Post by kakyoism on 2010-04-04
BTW, my opera-10 works just fine.

---

### Post by 2hot6ft2 on 2010-04-04
lovinglinux is the creator of the Firefox troubleshooting thread and the website so I would ask in his troubleshooting thread since he's the go to guy for firefox issues.
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by lovinglinux on 2010-04-04
> **2hot6ft2 said:**
> lovinglinux is the creator of the Firefox troubleshooting thread and the website so I would ask in his troubleshooting thread since he's the go to guy for firefox issues.
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Try to go to "System >> Preferences >> Sound" and change the options there from automatic to "ALSA". I haven't been using Gnome for a while, but that used to work for me.

If that doesn't work, try to install the 64bit version of the flash plugin. It looks like you have a 64bit system with the 32bit version of flash. Use [this tool](http://ubuntuforums.org/showthread.php?t=1414595) to remove flash then install the 64bit version.

---

### Post by adam814 on 2010-04-04
+1

I'd forgotten that Hardy still used nspluginwrapper with the 32-bit plugin.  I use the 64-bit plugin myself and it's much faster and more stable (with the exception of hulu.com).

---

### Post by lovinglinux on 2010-04-05
> **Ububtubobl said:**
> I also tried the suggestions in the stickies without success . Finally went to Java web site and found I didn't have latest version so using the synaptic mgr in System, Administration uploaded and installed. Seems to have solved the problem.

[color="Sienna"][list][*]**Source:** [[color="DarkSlateGray"]Re: No flash audio in firefox or chrome[/color]]("http://ubuntuforums.org/showpost.php?p=9077234")

[*]**Tags:** [[color="DarkSlateGray"]No flash audio in firefox or chrome[/color]]("http://www.google.com/search?q=No+flash+audio+in+firefox+or+chrome+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")

[*][[img]https://secure.delicious.com/favicon.ico[/img]]("http://del.icio.us/post?url=http://ubuntuforums.org/showpost.php?p=9077234&title=Re:+No+flash+audio+in+firefox+or+chrome") [[img]http://www.google.com/favicon.ico[/img]]("http://www.google.com/bookmarks/mark?op=add&bkmk=http://ubuntuforums.org/showpost.php?p=9077234&title=Re:+No+flash+audio+in+firefox+or+chrome")[/list][/color]

---

### Post by SuilAmhain on 2010-04-06
I Increased my PCM Volume to max. Solved problem. 

No Config changes required anywhere else...

---

### Post by micio on 2010-04-08
My previous experience were sorted by booting the newer kernel after a normal system upgrade.

In little words, I upgraded the kernel, but not the menu.lst file, so I was booting the old kernel... then I edited the mene.lst by adding the new kernel entry and after I ran that kernel.

Micio

---

### Post by tracyapotter on 2010-05-06
My problems was the PCM mixer setting at zero also.

My wall now has a hole the size of my head in it!

---

