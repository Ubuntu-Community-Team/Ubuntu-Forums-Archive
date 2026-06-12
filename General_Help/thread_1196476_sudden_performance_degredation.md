---
title: "sudden performance degredation"
date: 2009-06-25
forum: General Help
---

### Post by ishaan123 on 2009-06-25
Hi, I'm not sure what category this problem goes in, so I am posting it here. I am running 8.04 on a Dell D830. It works wonderfully for a few days. Then, performance suddenly begins degrading. First, streaming video suddenly becomes choppy and weird, then the desktop graphics get choppy, firefox freezes, and eventually the mouse stops moving and I have to restart. Its a gradual process, so I'm not sure what the cause is or how I'm triggering it. After I first notice it, it freezes my computer within ten minutes. Restarting the computer temporarily makes it better, but it freezes again.

However, I spent several weeks with Ubuntu working fine when I wasn't connecting to the internet, and it was also working fine for seceral days when i was connected to the internet but not using it for anything other than visiting these forums and downloading packages. If this was windows I would say I'm somehow repeatedly catching malware, but since its Linux I doubt that is possible. I'm very stumped. I fixed the problem once with a fresh install, but then it happened again. This is my third install and obviously constant reinstalling is not a permanent solution. Any ideas?

---

### Post by Vikhyath on 2009-06-25
What's your computer configuration??

---

### Post by futz on 2009-06-25
> **ishaan123 said:**
> Any ideas?
You didn't "Enable assistive technologies" did you? That's a HUGE performance killer. I did it by accident once, just tinkering. Spent the next few weeks wondering why Pan was running in slow motion, eating all available RAM and killing the machine every time I used it. Disabled assistive technologies and all was well again.

---

### Post by Vikhyath on 2009-06-25
use the **system monitor** to monitor different processes .check if some malicious process accesses too much resources

---

### Post by ishaan123 on 2009-06-25
k, so I was using youtube and it was working fine for hours. Then I visited the website "last.fm" and the stream suddenly became choppier. sound remained normal. Then I visited youtube again to test it, and predictably, it had become choppy as well. Now my windows are choppy if I drag them along the screen. If all goes the same as before, my computer will freeze soon. Same website causes no problems in windows. I don't know if last.fm is the cause of the problems but the problems began minutes after I visited there. Does anyone else visit last fm/have this problem? (I'm 99% sure the site has no malware, I have had NO problems in windows)

---

### Post by ishaan123 on 2009-06-25
Is** system monitor **a terminal command? If so I'm getting
**"command not found**". There is no monitor option under my system tab.

---

### Post by paul_be on 2009-06-25
no its gui
system > administration > system monitor

also are you only having issues with programs that dont use the internet.  Could be a bandwidth issue.  Also I use last.fm with no issues.

---

### Post by Vikhyath on 2009-06-25
Does this problem start when you try using a certain application??

---

### Post by ishaan123 on 2009-06-25
thansk, found system moniter, but I'm not sure how to interpret the information that it gives me. 

Even after I close all internet browsers and disconnect, everything is slower, even the task bar menus. However, the problem does not begin unless I visit certain internet sites, such as last.fm.

I did not enable assistive techs as far as I remember. Can it enable itself somehow? Its a naked install, except I installed the updates, ran the following command
[B]apt-get install flashplugin-nonfree
[/B]to install flash, and enabled "NVIDIA accelerated graphics drivers (latest cards)".

---

### Post by ishaan123 on 2009-06-25
> **Vikhyath said:**
> Does this problem start when you try using a certain application??

Yes, certain websites, such as last.fm. However, since its a gradual process, I can't be sure exactly when the problem begins. It usually takes a few minutes before it slows enough for me to notice.

---

### Post by paul_be on 2009-06-25
go to the processes tab and see if anything is using up too many resources. ie 99% of the cpu

---

### Post by Vikhyath on 2009-06-25
If you meant you've just installed the latest video card drivers, then you might be experiencing compatibilty issues.
Although these problems should be resrticted to display, i suggest u roll back to the driver versions you had previously

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> Yes, certain websites, such as last.fm. However, since its a gradual process, I can't be sure exactly when the problem begins. It usually takes a few minutes before it slows enough for me to notice.

I think is probably something in flash or java on Last.fm site that is causing this. Flash sucks on Ubuntu.

You could also disable Remote Desktop. I don't if it can cause problems in Hardy, but it is causing high CPU usage in Jaunty, even when idle.

Try using [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) extension, to block scripts you don't need. It's a security extensions, but it also help with performance when viewing sites with too many scripts.

---

### Post by ishaan123 on 2009-06-25
I should mention this is 64 bit. As im typing this msg, the text is appearing slower than I can type....its just going to get worse and worse and im eventually going to have to do a new install.

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> I should mention this is 64 bit. As im typing this msg, the text is appearing slower than I can type....its just going to get worse and worse and im eventually going to have to do a new install.

Try some of the tweaks from [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by paul_be on 2009-06-25
you may try to install the last.fm player from synaptic instead of streaming it from a web browser

---

### Post by ishaan123 on 2009-06-25
Reinstalled Flash player, no effect.
Tried using Epiphany instead, no effect. (Does that mean the firefox tweaks won't help?)

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> Reinstalled Flash player, no effect.
Tried using Epiphany instead, no effect. (Does that mean the firefox tweaks won't help?)

Most of the tweaks I suggest there are not flash related. They help improve overall Firefox performance, which ultimately has some effect on flash. There are also some xorg and general tweaks.

---

### Post by alberto ferreira on 2009-06-25
Have you seen if some process is using too much system resources already?!

Go to the tab processes>Click on the "%CPU" column to order the results>If needed click again so that they are sorted downards for easier visualisation> If some process is taking too much system resources tell us the name of the process

Do the same for the "Memory" column


You can also check the "Resources" tab to see the total of the CPU and RAM usage

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> I should mention this is 64 bit. As im typing this msg, the text is appearing slower than I can type....its just going to get worse and worse and im eventually going to have to do a new install.

Check if Firefox is using too much memory. I'm experiencing the exact same problem, described above, right now. The system monitor reveals that Firefox is using 401Mb of Resident Memory and climbing (it was 388 Mb just a couple of minutes ago). I have only two tabs opened, one is the Ubuntu forum and the other is Google Reader. This suggests that might be something related to the ajax features on Google Reader page (possible javascript).

Anyway, 400 Mb of RAM is way too much, even for Firefox. Normally it would use something between 90 Mb and 150 MB. Yesterday I had a similar memory leak and Firefox was using 650 Mb. I'm still trying to figure out what's going on.

---

### Post by ishaan123 on 2009-06-25
damn I had it all nice with all the %cpu numbers written down and then my computer did the freezing thing. Ok I'll just summerize this time...Running youtube causes no problems, no process takes more than 7% of cpu. Running last fm, firefox uses 7-22 percent of cpu, gnome system moniter uses 30-50% of the cpu, and compiz.real uses 30-50% of the cpu. when  I close lsat fm and start youtube, youtube has almost the same same numbers as last.fm. When I close all tabs except ubuntu forums, gnome system moniter and compiz.real jump around a little more than they did before I ran last fm when I type. (0-5%) 

On a side note, right before freezing, mouse and keyboard function became choppy and firefox, and then System moniter windows went gray, and sound got stuck on the same note.

---

### Post by ishaan123 on 2009-06-25
oh, and firefoz is at 57.3 MiB. It doesn't seem to be changing though..

Also, before my computer froze, restarting undid the bad effects of last.fm, but ever since the computer freeze, restarting did not remedy the problems and youtube videos contunue to be choppy even though I never used last fm. Therefore I can't get the CPU usage numbers from before using last.fm back without doing a fresh install. But I can tell you that after using last fm, all the %cpu numbers seem to be bigger.

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> damn I had it all nice with all the %cpu numbers written down and then my computer did the freezing thing. Ok I'll just summerize this time...Running youtube causes no problems, no process takes more than 7% of cpu. Running last fm, firefox uses 7-22 percent of cpu, gnome system moniter uses 30-50% of the cpu, and compiz.real uses 30-50% of the cpu. when  I close lsat fm and start youtube, youtube has almost the same same numbers as last.fm. When I close all tabs except ubuntu forums, gnome system moniter and compiz.real jump around a little more than they did before I ran last fm when I type. (0-5%) 

On a side note, right before freezing, mouse and keyboard function became choppy and firefox, and then System moniter windows went gray, and sound got stuck on the same note.

Gnome System Monitor is a CPU intensive application, which is kind of ironic. Anyway, you shouldn't worry about it's usage. Instead of using Gnome System Monitor, use the command *top* in the terminal [see footnote].

What look strange is compiz usage. When idle my compiz uses 1-6% and only when rotating the cube that it goes to 24%. So your reading of 30-50% might suggests that something is not right with the graphical part of your system. How much compiz uses when idle, without opening last.fm?

> **ishaan123 said:**
> oh, and firefoz is at 57.3 MiB. It doesn't seem to be changing though..

Also, before my computer froze, restarting undid the bad effects of last.fm, but ever since the computer freeze, restarting did not remedy the problems and youtube videos contunue to be choppy even though I never used last fm. Therefore I can't get the CPU usage numbers from before using last.fm back without doing a fresh install. But I can tell you that after using last fm, all the %cpu numbers seem to be bigger.

OK. I'm probably shooting in the dark, but do you have enabled "Automatically remember running applications when logging out" in "System >> Preferences >> Startup Applications" ? If you do, disable it.

Additionally, close Firefox, locate your Firefox profile [see footnote] and delete the file *sessionstore.js*. Then start Firefox again and see how it goes. 


> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

> [color=#CC0000]**Note: **[/color]Firefox stores user data on a special folder called profile. It contains all your bookmarks, extensions, passwords, cookies and other stuff. Profiles are stored in your home directory, under the hidden folder .mozilla/firefox/. To see it, you need to hit CTRL+H when browsing home.

---

### Post by ishaan123 on 2009-06-25
I tried doing the same thing on ephiphany, and npviewer.bin got bigger and bigger untill it took up 100% of the cpu and froze everything (only in last fm and no problems in youtube until after using last.fm). However, epiphany lasts slightly longer and no other processes start to "grow", unlike in firefox.

I don't have "automatically remember..." checked. But, in my computer its system>preferences>sessions, if that matters.

i don't think I have that folder.


.mozzila
opening that I have
"Extentions" and "Firefox"
                     opening Firefox
            s7wlcgvi.default and "profiles.ini"
               
 none of which contain sessionstore.js.

Being unable to find it in my home folder, I typed about:config and set browser.sessionrestore.enabled to false. There was no effect. If you think deleting the file would still help, could you please give me the exact termninal commands to do so? I don't know how to use the terminal.

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> I don't have "automatically remember..." checked. But, in my computer its system>preferences>sessions, if that matters.

Is the same thing. They changed the name in Jaunty just to create this type of confusion :)

> **ishaan123 said:**
> 
i don't think I have that folder.
.mozzila
opening that I have
"Extentions" and "Firefox"
                     opening Firefox
            s7wlcgvi.default and "profiles.ini"
               
 none of which contain sessionstore.js

Your profile folder is ~/.mozilla/firefox/s7wlcgvi.default. The *sessionstore.js* is inside it.

> **ishaan123 said:**
> Being unable to find it in my home folder, I typed about:config and set browser.sessionrestore.enabled to false. There was no effect. If you think deleting the file would still help, could you please give me the exact termninal commands to do so? I don't know how to use the terminal.

```
rm -f ~/.mozilla/firefox/s7wlcgvi.default/sessionstore.js
``` 

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by ishaan123 on 2009-06-25
wow...it seems to have improved! I'm not 100% sure whether its actually better because its a gradual effect, so I'll leave last.fm running for an hour or so and then do a follow up. post. for now, npviewer is running steady in the 18-22% range and all other processes tend to stay under 10%.

---

### Post by ishaan123 on 2009-06-25
false alarm...it still ended up slowing.

---

### Post by ishaan123 on 2009-06-25
but here is the weird thing...neither compiz nor npviewer go above 10% anymore when I use last.fm, but npviewer goes really high (40-60% ) in youtube. 

Btw when I entered that code in the terminal, nothing happened. It was as if I just pressed enter, like so
[B]
ishaan@ishaan-laptop:~$ rm -f ~/.mozilla/firefox/s7wlcgvi.default/sessionstore.js
ishaan@ishaan-laptop:~$ rm -f ~/.mozilla/firefox/s7wlcgvi.default/sessionstore.js
[/B]

---

### Post by ishaan123 on 2009-06-25
I highly doubt that the problem is with Firefox, since Epiphany and Galeon have the exact same problem, unless all three browsers are built similarly.

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> false alarm...it still ended up slowing.

It will slow down because the problem is something related to last.fm page (probably javascript). Deleting the *sessionstore.js* helps to solve the persistence of this issue after closing last.fm page. If you close Firefox, delete the *sessionstore.js* file, reboot, start Firefox and don't open Last.fm again, then you won't have problems. Just stay away from Last.fm until you find a better solution. 

You might want to try using [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) extension for Firefox, to prevent the page from loading scripts, which are probably the culprit. You will be able to browse Last.fm, but I'm not sure if you will be able to use all features, because they probably need javascript.

I'm helping another user with the same problem, but on a different web site. See discussion at [http://ubuntuforums.org/showthread.php?t=1196716](http://ubuntuforums.org/showthread.php?t=1196716).

---

### Post by ishaan123 on 2009-06-25
If I try the command after running last fm, the problem does not go away. I only thought it was helping because I had restarted the computer and then ran the command, but actually the increased performance had come from the restart. It turns out restarting linux fixes it, but turning it off and then on doesn't, for some reason.

---

### Post by ishaan123 on 2009-06-25
so I don't think the command actually did anything, because the problem doesn't go away even if I close last.fm and run the command.

---

### Post by QIII on 2009-06-25
Haven't had a chance to really scour the thread, so forgive me if I go off track or ask something that has already been asked...

Do you have Vino running?

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> so I don't think the command actually did anything, because the problem doesn't go away even if I close last.fm and run the command.

Ok,

try this command after opening last.fm to see if the problem goes away or if it stays.

```
killall firefox
```

---

### Post by lovinglinux on 2009-06-25
> **QIII said:**
> Haven't had a chance to really scour the thread, so forgive me if I go off track or ask something that has already been asked...

Do you have Vino running?

+1

I have already suggested to disable the Remote Desktop, but the OP didn't mentioned if he tried that.

---

### Post by ishaan123 on 2009-06-25
Sorry, must have overlooked that. Remote desktop was disabled by default and is still disabled.   I used NoScript to disable all functions on last.fm except for audio/video stream, but to no avail. I guess the stream script is the one causing the problem.

---

### Post by ishaan123 on 2009-06-25
killall firefox closes all firefox windows. When I reopen them, the problem persists.

---

### Post by lovinglinux on 2009-06-25
> **ishaan123 said:**
> killall firefox closes all firefox windows. When I reopen them, the problem persists.

The problem persists if you don't open Last.fm page, but open Firefox and browse other web sites?

---

### Post by QIII on 2009-06-25
Was just reading a post or two on a German Firefox forum about a guy complaining about last.fm crashing his Firefox.

Is it possible that a crash might cause some file corruption?

Would it be worth backing up all your Firefox preferences, uninstalling then reinstalling Firefox (what a pain, I know) and seeing if the problem persists?

---

### Post by lovinglinux on 2009-06-25
> **QIII said:**
> Is it possible that a crash might cause some file corruption?

Would it be worth backing up all your Firefox preferences, uninstalling then reinstalling Firefox (what a pain, I know) and seeing if the problem persists?

It's possible that the crash could cause corruption of the profile, but re-installing Firefox is not necessary and won't help. Deleting the profile might help.

---

### Post by ishaan123 on 2009-07-24
solved...this one really made me smack myself. The fan was blocked, and performance got worse as the computer got hotter. Unblocking the fan solved the problem. :D

---

