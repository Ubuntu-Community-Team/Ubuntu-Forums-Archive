---
title: "Monitor goes to sleep... can't disable &quot;powersave/screensaver&quot;"
date: 2010-06-14
forum: Desktop Environments
---

### Post by andersbaath on 2010-06-14
Hi!
I have recently switched to Ubuntu (10.04) after running my system on Centos for years. This mostly due to much quicker startup times. I have a software that runs as a public presentation software on a public "bigscreen" so my Ubuntu runs like a "kiosk" pc that's always on. When i switched to Ubuntu everything worked lika a charm besides the fact that the screen falls in to "sleep"/"powersave" or something. I think that i have tried everything to prevent this. I use Gnome and i have set all the powersavings features to off. Ive tried turning acpi off and i also turn dpms off at login. Nothing seems to kill the "screen powersaving" feature. As a desperate act i tried to use a software called Coffeine, this software should prevent powersavings. I added Coffeine to autostart to activate for 48h, however it doesnt... HELP! I need the screen to atleast stay on for 24h..

Does anyone have an ide what cuses this?
Dont really want to go back to Centos now...

My system basicly looks like this:
Ubuntu 10.04
Gnome
one user that's set to autologin
Runs firefox in fullscreen on startup
one litle program installed to hide the mouse pointer when not moving it for a few seconds.

In autostart i run:
Power Manager
Coffeine
Firefox

Best regards
Anders

---

### Post by andersbaath on 2010-06-15
Does anyone know of a software that's autmoaticly moves the mouse every xx minutes (configurable), i guess this could be a ugly way to attack the problem. (Would still like to solve the root problem but need to find a solution quickly)

/Anders

---

### Post by andersbaath on 2010-06-18
Installed KDE to test if the same thing happens there and sadly it does... still havent found a solution for this, do anyone have any ide what causes this?? Don't want to go back to CentOS now everything else works so much better... :-(

/Anders

---

### Post by andersbaath on 2010-06-19
Finally found a "solution" to this, dont know if anyone is interested in what i did, but this might happen to someone else so i figure i post what i did...

One of the following solutions should have been enough but it wasent, this is what i had to do to disable the "screen powersave" mode (i know run KDE desktop but i think this should work in GNOME as well.

in file: /etc/rc.local
added following:
sh -c 'setterm -blank 0 -powersave off -powerdown 0 < /dev/console > /dev/console 2>&1'
sh -c 'xset -dpms'

in file: /etc/init.d/local
added following.
sh -c 'setterm -blank 0 -powersave off -powerdown 0 < /dev/console > /dev/console 2>&1'

Then as the user that i run KDE as i added a startup application and added the following command:
xset dpms 0 0 0 -dpms s off s 0 0 s noblank s noexpose

Works for me hope this can be of help for anyone else it sure took me a while to figure out a way around this f* bug..

/Anders

---

### Post by dkozhukhar on 2011-05-07
[http://ubuntuforums.org/showthread.php?t=347079](http://ubuntuforums.org/showthread.php?t=347079)

---

### Post by Fergor on 2011-07-24
I would like to add this.  
[http://lhansen.blogspot.com/2007/08/disabling-gnome-screensaver-thru.html](http://lhansen.blogspot.com/2007/08/disabling-gnome-screensaver-thru.html)

I dont know if it's the solution, i'm going to try it out now.

**EDIT: IT WORKS!! :D**

---

