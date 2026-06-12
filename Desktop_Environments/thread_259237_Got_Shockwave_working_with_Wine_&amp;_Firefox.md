---
title: "Got Shockwave working with Wine &amp; Firefox"
date: 2006-09-17
forum: Desktop Environments
---

### Post by mebo on 2006-09-17
Yes, I have finally gotten Shockwave 10 to work with Firefox running under wine.  This was driven purely by my kids desire (and bugging me) and my desire NOT have them run XP.  I guess Habbo Hotel is a must have....

Warning: This aint pretty, but it works....

Requirements: 
-Wine & Windows version of Firefox installed (lots of posts to get that going so I wont reiterate.)
-an XP machine (somewhere) with Shockwave already installed (I had Shockwave 10 installed, YMMV with other versions)
(Just for the record, I already had Flash 9 installed and working under wine, but don't know if that helped in any way getting Shockwave working. Flash was installed from previous posts also.)

1. Make sure you've actually run Firefox under wine so that all the directories will be set up by the system.

2. From the WinXP machine copy the '\Windows\system32\Macromed\Shockwave 10' directory to your Wine "Drive C" windows/system32/Macromed directory

3. Note that since I already had installed Flash under wine, the Macromed directory already existed in the wine file structure along with other directories that had been created during the Flash install.  There are some directories called "common" and such, but don't really know if these interact with Shockwave.  YMMV if you don't have Flash installed and these other directories don't exist.

4. From the WinXP machine copy the files "np32dsw.dll" and "ShockwavePlugin.class" in the "\Program Files\Mozilla Firefox\plugins" to your to your Wine "Drive C" windows/Program Files/Mozilla Firefox/plugins directory.

5. Now we need to let Firefox know that the plugin is available.  Go to your Wine "Drive C" /windows/profiles/yourusername/Application Data/Mozilla/Firefox directory and open up the "pluginreg.dat" file with a text editor. Replace "yourusename" with your Ubuntu login username above.  It should already be there... (Note I had found it easiest to open the text editor and then drag the file into it because of the file extension....)

6. Immeadiately below the [PLUGINS] entry in the file, add the following lines:
```
C:\Program Files\Mozilla Firefox\plugins\np32dsw.dll|$
|$
1154071974000|1|1|$
Adobe Shockwave for Director Netscape plug-in, version 10.1|$
Shockwave for Director|$
1
0|application/x-director|Shockwave Movie|dir,dxr,dcr|$
```

(Note that I got these lines from the WinXP box that I had.  I'm pretty sure that some of the "settngs" in these lines are probably specific to Shockwave version 10, so if you have another version, go find similar lines on your XP box under /Documents and Settings/winloginname/Application Data/Mozilla/Firefox directory.)

7. Save the file.

8. Crank up Firefox under wine.

9. Navigate to Adobe Shockwave/Flash test page at [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and it should load seperate Shockwave and Flash applets that say "Installation complete"

10. You could then also go check out Habbo Hotel at "http://www.habbo.com/client.action"  If that loads, then everthing is working great.

11. One other tidbit, after went to that "Habbo Hotel" above, I noticed that the fonts displayed in the Shockwave app were barely readable on the little login dialog box that was displayed.  (I haven't spent much {if any} time tweaking Wine, but I figured maybe Shockwave was just missing some fonts and that would be easy to remedy).  So I copied all of my ttf fonts that I had loaded on my WinXP box to the Wine "Drive C" /windows/fonts directory.  When I reloaded Habbo, everything looked nice and readable.

That's it. Good luck. I've only been trying to get this dang app working for about 3 months now....

Now, if someone can tell me how to get PrintShopPro working under Linux, I really can finally dump XP in my house...

---

### Post by Royal2000H on 2006-09-22
Installing shockwave through wine worked just as well

---

### Post by campidg on 2006-09-27
Royal2000H, how did you install the windows version of shockwave in linux firefox via wine?  

I tried installing windows firefox as per mebo's instruction but wine would not install it from where I downloded it to. I kept getting this error message: 

cameron@Camssystem:~/Desktop$ wine Firefox Setup 1.5.0.7.exe
wine: could not load L"c:\\windows\\system32\\Firefox.exe": Module not found

Cheers, Cam

---

### Post by moreinfo on 2006-09-27
Thanks for the info.

I'm a newbie, I tried your idea but I don't have any win system.

I downloaded firefox for windows and "opened" it with wine(default). Worked perfectly, using the opened firefox, I then went to shockwave and downloaded version 10, again worked perfectly at the mentioned "Habbo Hotel".

like you mentioned the fonts are abit hard to see, any suggestions on how to fix these without a win system?

With no win system I never copied anything across, I also didn't add the shockwave stuff, but shockwave works fine.  The firefox shortcut was added to the desktop, which is good for me, because I don't know how to find any window files that I have downloaded.  Any suggestions here would be good.

Thanks in advance

---

### Post by mebo on 2006-09-27
Looks like you guys are having an easier time installing shockwave than I did.  I couldn't get the installer to run.

On the fonts, you can just download ttf files off the net, or if you just have to have windows fonts, then you'll need to find a friend.

---

### Post by Phrellex on 2007-10-15
You can just get Internet Explorer for Linux. It works pretty good with shockwave and plugins, but you need to have a windows licence to use it or otherwise its supposly illegal. O_o

---

