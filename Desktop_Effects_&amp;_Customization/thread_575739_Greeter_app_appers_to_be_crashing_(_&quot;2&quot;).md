---
title: "Greeter app appers to be crashing ( &quot;2&quot;)"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by beto113 on 2007-10-14
Hi there 

I was curious about Ubuntu then ive decided to give a try i downloaded the 7.10 RC... so yea just great OS as far i could see everything was working out of the box... i have a laptop AMILO 1536 with a ATI x1400 and i enable the visual effects with a compiz fusion.. and was doing great until i decided to plugg my second monitor... 

now notthing is working im not even able to login to do anything coz just after the loading screen this messenge appear..." The application appears to be crashing. Attempting to use a different one"

so PLS help me....

btw to enable the compiz i used this guild 
[http://blog.stephanbuys.com/2007/04/compiz-and-ubuntu-feisty-fawn-ati-x1400.html]("http://blog.stephanbuys.com/2007/04/compiz-and-ubuntu-feisty-fawn-ati-x1400.html")

after i got this problem i tried this one... i found googling this problem but didnt work as well

"""I searched on the Ubuntu forums, most of the fixes on the Ubuntu forums talked about unchecking the box but the problem was that I couldn&#8217;t login into the system to do that in the first place. After studying the gdm.conf I figured out a way to fix this.

If the GUI fails to load and you are unable to access the system menu then you should try the instructions below.

1. first reboot your computer into maintenance mode/recovery mode.

2. open /etc/gdm/gdm.conf-custom by entering the following command

sudo vim /etc/gdm/gdm.conf-custom

3. press i to enter into insert mode. Locate the following line and comment it by inserting a # in front of the line.

GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

4. press the Esc key and then type in :wq to save and quit the editor.

5. type sudo init 6 to rebootthat should fix the problem.I am using gutsy tribe 5 and looks like this problem has been present in Ubuntu ever since dapper hope they fix it before gutsy gets released.
""""


So the thing is i dont really now if ive done anything bad with this last guild and if i did i dont know how to that this off..

Edit: when i plugged my second monitor i setted to this second monitor behave as a mirror from the first one


Anyway Thanks Beto

---

