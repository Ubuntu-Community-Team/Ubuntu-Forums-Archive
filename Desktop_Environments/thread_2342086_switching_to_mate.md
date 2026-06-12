---
title: "switching to mate"
date: 2016-11-03
forum: Desktop Environments
---

### Post by jgw on 2016-11-03
I have been running with ubuntu 16.04 and unity and decided to change to mate.  As far as I know I have installed all the mate stuff.  After I had installed everything suddenly my machine gifted me with a mate logo.  If I moved the cursor around I got a screen blanker.  After a bit I re-booted.  then I got my normal unity screen.  Then I tried to log out to get the choice between desktops.  I logged out, no problem, I was then treated to my background and nothing I could do would change anything.  I am, currently, trying to reboot again.

All I want to do is to move to the mate desktop and turn off unity.  I have been reading stuff for a couple of hours but nobody is actually giving any steps.  I am trying to deal only with posts for this year so the directions are not too old.  

I see where I now have a mate terminal and something called software boutique.  I can find nothing else to run.  I went to symantic and searched for mate.  I have a LOT of this stuff installed (theme, common, guide, applet common, netbook common, control center, media, wallpapers, settings, desktop-common, dock-applet, power manager common, mate-utils, etc.   unity is still running as is the launcher.  My load is between 4.?? and 7.?? and I think I am in trouble.

I logged out again.  This time I got a mate login screen (blue swirly background with mate logo).  I duly signed in and it did absolutely nothing.  I moved my cursor around and pressed keys, etc.  Nothing happened and, then, it simply went back to the unity screen.  I logged out again and this time there was no mate sign in and after doing something I am back, yet again, in the unity desktop.  It sat there for a bit and then, yet again, I have a log in block and, under that, the mate icon asnd "ubuntu 'MATE.  Now I have the blue swirly screen background with the icon and the words "ubuntu MATE" and that just went away and I now just have a screen showing the background.  If I left click I get a box with choices, new folder, new document, open terminal, organize desktop, change desktop background, etc.  Its now started my browser (firefox)  There is a problem with the browser in that I have no top bar, or the screen size is wrong.  This machine has intel graphics.  I read someplace that I need to install an intel graphics driver - anybody know if I should do that?

I should also mention that I am running an eee pc 1005hab which runs at 1.6mgh with an atom cpu.


Thoughts?

---

### Post by jerome1232 on 2016-11-03
All that is needed to install mate is a meta-package that installs everything ubuntu-mate. Make sure that meta-package is installed.
```
sudo apt install ubuntu-mate-desktop
```

You should be greeted by a different looking greeter that looks like my attached image.
[ATTACH=CONFIG]271946[/ATTACH]

There should be a small icon near the top right, if you click it it should give you options on which environment to login under, ensure Mate is selected.

---

### Post by jgw on 2016-11-03
Thank you for the reply.

I* went to synaptic on this one.  Seems that ubuntu-mate-desktop has unmet dependencies and symantic can't fix the problem  (says its broken).  I have told sympantic to fix the problem and it thinks it has but has not. Symantic tells me that is unable to correct problems, you have held broken package.
error,pkgproblemresolver-resolve generated breaks, this may be caused by held packages.
Unable to correct dependencies, etc

I cannot delete this either (with symantic)  I will try 'sudo apt-get ubuntu-mate-desktop remove" and see what happens

I tried the sudo apt-get remove ubuntu-mate-desktop and it told me it couldn't because its not installed.  
dpkg --get-selections | grep hold returns nothing
I ran the install with aptitude and it tried to fix stuff.  now back to sympantic to see what it thinks
Aptitude still tells me I am holding broken packages - dpkg tells me I have nothing held

I am doomed?

---

### Post by Frogs Hair on 2016-11-03
Try the following one at a time. 

```
sudo dpkg --configure -a 
``````
sudo apt-get -f install 
```

---

### Post by jerome1232 on 2016-11-04
It would be helpful to see the output of ```
dpkg --get-selections | grep hold
``` or any other commands you run.

To copy from a terminal use shift+ctrl+c. To make it easier to read click the hash tag symbol before you paste the code into the forum window.

---

### Post by jgw on 2016-11-04
I give up.  What I am going to do (as I write this) is to do a clean install of mate on that system.  Its my wife's and there is little there except for firefox, which I backed up, so I think its going to be just fine.  I appreciate the replies but I was just spending waaay too much time on this one and this is the sane way to go.

Thanks again!

---

