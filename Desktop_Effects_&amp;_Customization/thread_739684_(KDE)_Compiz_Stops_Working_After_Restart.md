---
title: "(KDE) Compiz Stops Working After Restart"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by Chris From California on 2008-03-30
Hey guys, I switched over to KDE from GNOME, and manged to get Compiz working with all the effects using this tutorial 

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

However once I restart all the effects are gone ( cube desktop etc ) 

How do i turn the effects back on and keep them on? Thanks :)


Note: 2 more things

 I also get 16 desktop boxes on my toolbar, anyway to change that to only 4? 
 I also noticed that when Compiz is turned on I have a little "adept notifier" that sits there and does nothing. 
and last but not least I used to have some nifty sounds but they're gone. ( When maximizing windows etc there where little sounds that played. That would drive most people nuts but I enjoy it ) 



Thanks guys!!!

---

### Post by Zorael on 2008-03-30
KDE doesn't load Compiz by default, and the easiest way to change this is by making a startup script. There's likely a way to change that default though, somewhere.

```
#!/bin/bash

killall adept_notifier

compiz --replace --ignore-desktop-hints &

sleep 10
adept_notifier &
```
Create a file like so and place it in ~/.kde/Autostart. You'll need to flag it as executable, too.

The --ignore-desktop-hints argument will help you get 4 desktops instead of 16.

Adept notifier is notorious for bugging out like that, so the script will kill it before loading compiz, then restart it ten seconds afterwards.

As for the sounds, they sadly don't carry over. When you run Compiz as your window compositor it will launch Emerald as its default window decorator, and it isn't aware of the KDE sound settings. There is a window decorator designed to behave as KDE's standard window "manager" (at a lack of a better term), but I found it to be buggy. Regardless, if you want to try it out, you should be able to enter 'kde-window-decorator' in the Command field under the Window Decorations plugin, in ccsm. 

Alternatively, to try it out temporarily, open a console and enter 'kde-window-decorator --replace &'. To restart Emerald, do 'emerald --replace &'. And to restart KWin (exit Compiz), do 'kwin --replace &'.

---

### Post by Chris From California on 2008-03-31
SWEEEET!!! Seems to working now. Just as a side note I was able to get the sounds back by going into the sound manager and enabling the sounds again. ( I know duh right. Simple tasks in Linux are taking me a bit to get used to ) For some reason they had been disabled? Either way everything seems to be back to normal. Linux is so freaking sweet the options are insane. I now have all 3 of my machines running linux. Ubuntu on my laptop, Kubuntu on my desktop and Edbunutu on my wifes machine. ( Who hated it at first but now loves the "shaky windows" lol ) 

My new favorite phrase "oh yea, but can Vista do this!...." *shows spinning box with rain*

Thanks!!!

---

