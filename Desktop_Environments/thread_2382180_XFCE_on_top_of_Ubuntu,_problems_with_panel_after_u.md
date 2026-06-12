---
title: "XFCE on top of Ubuntu, problems with panel after upgrade to 16.04"
date: 2018-01-10
forum: Desktop Environments
---

### Post by greyfaux01 on 2018-01-10
Im using XFCE on top of an Ubuntu install, and i upgraded from 14.04 to 16.04, and now having panel problems. Previously i had panel problems, but i was able to kill the process 'application-indicator-service' and fixed my panel (brough mega/dropbox icons up, as well as a few others that were missing).. Now after the upgrade, panel problems upon boot, but problem is, when i go to kill that process, its now longer there in 16.04.


I read a couple different possible fixes, but not sure if one is right for me, none seemed to be the same exact situation as mine, and i didnt know which was the 'best' fix to try. I'd like to do least amount of change to the OS if possible, as well as retain the ability to have my lxde desktop, gnome fallback (if its still there), and the super-rare occasions when i log into unity still work (if unity is even still there, not sure).. Some of the fixes were specific to xfce only, and seemed like it would mess up the other DE's i have along with the xfce.


The problem is now, i have a couple resource monitors in the panel, and their usually greyed/whited out, while almost constantly flashing the colored boxes on/off.. The colors are the indicators of the cpu usage, etc. This problem is not the exact same as when i was killing the application-indicator-service, slightly different, same area of panel though.


Any help is greatly appreciated. I can only check every day or 3, but i will definitely not disappear, so any help will not be a waste. Thanks again.

[ATTACH=CONFIG]278125[/ATTACH]

---

### Post by TheFu on 2018-01-10
Sometimes different DEs use the same config files.  That means sometimes incompatible configuration changes break a DE or multiple DEs.

The good news is that these settings are per userid.  So, checking if this is the issue is easy.  Make a new userid, login with that and see if the problem still exists.  

It is best to NOT use multiple DEs under the same userid, for that reason.  But different people have different risk acceptance levels.

If you are interested in techniques to have the different accounts work together, besides at the DE level, there are some methods. They aren't point-n-click and might seem complex, but not THAT hard either. Ask.

---

### Post by greyfaux01 on 2018-01-10
Ok thanks for the info. Honestly, if i had to choose, i would rather TRY to use the same userid (im assuming thats a user profile that i login to at bootup), and try to fix things as they come up. I can handle a *somewhat* high risk level when it comes to cosmetics, but if things could possibly break entirely, then, well, i dont have the spare time to dedicate (school/work/kid). I think i have another user account on this desktop that i created during some xsession/xlock or something failure, i had to create a seperate user account to fix the first one. So i will indeed try that and post back when i get a chance.

The one reason i feel using the same userid (again im assuming thats the same as user account, by all means please correct me if im wrong), is i dont make THAT many config changes. I do change settings sometimes inside the DE, using the gui tools that the DE provides, but as far as this desktop goes, i got it how i like it, and dont plan on making any serious changes to it.

But yea i had a feeling 'fixing' the xfce problems using the 'wrong' method could mess up my other DE's, im glad you verified that possiblity for me. I may have had similar problems in the past, but i just had that sort of intuition that fixing xfce could break lxde/gnome etc. Btw, if you want to give me some sort of explanation of how to use different accounts working together, i'd be glad to hear it. Like i said, i would rather not, because im assuming it will be extra work (ie time) to get things to work together, so dont take too much of your time, but i generally only use xfce here anyway, if that makes a difference. I just keep the other DE's around for either backup (once i was not able to login to xfce but the others saved me), or for when i bring my computer downstairs and use it for different purposes (HTCP for example). I mean i want the best of both worlds, and am willing to pay the price, as long as its only cosmetic damage im risking. I consider things like the lxde power button disappearing to be cosmetic, because all i had to do was install a package to get the power button menu back. So im willing to accept a form of risk, as long as its easy to lookup/fix.

And again thanks for your help, your info confirms i should be cautious about what xfce fix i choose to use based on the fact that i have other DE's installed. I will indeed login as my other user account under xfce and report back about the panel.

---

### Post by greyfaux01 on 2018-01-10
Ok that was interesting. I logged in as my other user, and it was the first time i logged in as that user under xfce, so it was asking me to set up a panel, i chose 'default', and it set it up. I went to add the 'resource monitor' or 'load indicator', 'indicator-multiload' as in the 'about sectiong, or looking for one of the various names it has, and low and behold its nowhere to be found. I didnt find anything at all about a cpu monitor, resource monitor, load indicator, etc etc.. Apparently there is no resource monitor panel applet anymore for xfce in 16.04.

I could be doing something wrong, in fact i hope i am, but i dont remember it being that hard to put on the panel initially. I thought i just went to 'add panel items' and chose 'resource monitor' or something along those lines. So if it is indeed no longer supported, well, that sucks, cuz it is an awesome applet that lets me have a realtime view of everything going on (my computer swaps too much sometimes, as well as the usual application using too much cpu, or bandwidth etc).. So im kinda bummed its gone.

Anyway, i went ahead and manned up, and went to delete it, but im not seeing a way to remove the broken one off my panel. When i right-click on the resource monitor, i dont get the normal 'properties' 'add/remove' options that i get with almost every other panel applet, i only get the resource monitor options, same as when i left click. That menu gives me.. nevermind.. i just seen theres no 'remove', but there is a 'quit', so i quit the applet, and now its gone. Im assuming it will be there on startup again, and im assuming theres a way to remove it from startup. Yea, i just checked the 'session adn startup' menu, and listed is the 'system load indicator'...

I also seen the 'indicator-application-service' process which used to not be there.. thats interesting.. im going to go ahead and try and experiment, im gonig to have the resource monitor and the indicator'application-service start at boot, then i will try my old trick of killing indicator-application-service, and see if that makes the resource monitor normal again. If that doesnt work, i'll untick both of them from session and startup.

Ok seems this is considered a solution. Thanks for the idea of logging in as another user. If you know of a supported alternative to 'indicator-multiload', 'resource monitor' or any panel applet for xfce that can show me realtime cpu/ram/network/etc info, that would be awesome. 
Otherwise, thanks again.

---

### Post by TheFu on 2018-01-10
The issue isn't with having different DEs installed. That isn't an issue.
The problem is **using** them under the same userid - with the same $HOME.  Those based on gnome will probably use the same config files, so if 1 DE thinks a setting means X and another DE thinks the same setting means Y, boom, problem.  It gets more complicated when a setting enables other, child settings that also conflict.

So ... really the best answer is to use different userids for the different DEs.

OTOH, lots of people do use different DEs and never see any issues, so this is likely something in YOUR specific situation.  But until you create a new userid (fresh is better than reusing one), and login with the DE you need to test and see that the problem doesn't exist, there isn't much more we can do here.

I don't use DEs.  Not my thing.  Prefer either openbox or fvwm-crystal myself.  To each their own. ;)

As for monitoring, all my systems send their performance stats to a central server which generates web pages for each system every 4 hrs.  Most of my systems can't swap. They are tuned to prevent it and don't have any swap connected. Basically, just the desktops get swap (4G) and the central "communications server" (Exchange replacement), which is a hog.

Sorry I'm no help with most GUI things.  Hopefully someone else will see that last post and try to help?

---

### Post by flocculant on 2018-01-11
system-load is available in 16.04

---

### Post by greyfaux01 on 2018-01-14
Hey the fu, sorry for the delay, been busy at work and then there was a mini ice storm, bad enough that my car was stuck and I just got it back yesterday, just in time to go to work again. Luckily nobody ran into it while i left it on the side of the road and walked a mile home in the ice storm, uphill both ways, at 2am in the freezing cold &#129304; 

I get what your saying though, different DEs overwriting each others config files. Luckilly I think my combo of DEs and the fact that I only use 2 usually (lxde/xfce and sometimes gnome) has kept me in decent shape. That said I know lxde and xfce do share some things, although I couldn't tell you what if you asked me. 

Yea I know guis are for noobs, I'm not a 'real man' and all that because I rely on them a little too much, but I've almost perfected the art of finding a gui way to do almost everything, idk it's almost like a hobby of mine. I'm usually trying to talk others I know into at least trying Linux, so I always think 'how would a new person do this?'. That said I use the terminal often as I'm sure you could guess, since I've been with Ubuntu since hardy, and for many many things I prefer it, like for installing programs, the software centers are much slower, even lubuntu software center. 

But like I said messing with guis are a hobby, I went out of my way to get the compiz cube working after Ubuntu stopped supporting it (using lxde and gnome of course), and plus I only use my desktops as desktops, and I don't have a central server. Although in school we did try getting Ubuntu server edition running on an old server that was donated, but we failed at getting it connected to the Internet. 

Thanks for your info Fu, flocullant, that's great news. I'll hve to check that pic on my computer upstairs in a min, apparently I can't view it on my phone in mobile view. Yes I definitely want to install it then, that should fix my problems if it's been updated. Thanks so much for that info.

---

### Post by greyfaux01 on 2018-01-14
Yea flocculant, not sure why but its not on my system. If the package or process itself is called something else now after the upgrade, perhaps i need to install separately, since i did upgrade from 14.04. Im just guessing that maybe package name changed, i know whats running on my machine now (which was running on 14.04), the gui version of the program is 'system load indicator' like in your screenshot, in task manager/session and startup, which is probably the actual package name, its called 'indicator-multiload'. If its called the same thing on yours still, then i have no idea why its not there, and i would really like to know how to get it back, or get this current one thats not listed in my panel preferences working again.

Here are the screens, i included several so you can see i scrolled all the way to the bottom and its not there anywhere. The first box, 'panel' is showing all items already, no scrolling needed.[ATTACH=CONFIG]278196[/ATTACH][ATTACH=CONFIG]278197[/ATTACH][ATTACH=CONFIG]278198[/ATTACH][ATTACH=CONFIG]278199[/ATTACH]

---

### Post by flocculant on 2018-01-15
run 

```
dpkg -l xfce4-systemload-plugin |grep ii
```

See if it's installed, if not install it, it will look like this if it is

> ii  xfce4-systemload-plugin

```
sudo apt install xfce4-systemload-plugin
```

Then add it to the panel.

---

### Post by greyfaux01 on 2018-01-18
Ok cool, i didnt have that installed, and installed it, now i have at least some sort of real time system monitor. I know i could use gkrellim or conky, which ive used in the past, but i just wanted something smaller and in the panel, so thanks again.

Now i will say, i do like the old 'system load indicator' much better though, i can set the sized of the boxes, thats probably the main thing, but there are more options in general. These boxes here are tiny, their not even boxes, there tiny sticks basically, so trying to get a quick overview takes some skill with the mouse. Oh yea the other thing i like about the old one, when you right click, it gives you a complete overview of cpu/ram/swap/net in 1 click, all at once, w/out having to open up task manger. This one, you have to very carefully hover over each individual box and only get one percentage at a time, so for a quick overview, i have to hover over 1 at a time, and do it for all 3. Those 2 things are probably what i miss most about 'system load indicator' aka 'indicator-multiload'.

That said i can definitely live with this, and i definitely appreciate your help. Im just curious why the other one doesnt work, or if xfce did indeed start using this xfce4-systemload-plugin and drop support for 'system load indicator', or if its just some system bug on my end or something.

---

### Post by flocculant on 2018-01-20
> **greyfaux01 said:**
> ...

That said i can definitely live with this, and i definitely appreciate your help. Im just curious why the other one doesnt work, or if xfce did indeed start using this xfce4-systemload-plugin and drop support for 'system load indicator', or if its just some system bug on my end or something.

I can't answer that ;)

All I can say is try xfce from somewhere else and see if the old one is there. 

System load isn't something I use, consequently I have no clue what happened between 2014 and 2016 - which is what you need to know ;)

Perhaps what you called system load indicator - was in fact called something else by xfce, check here for candidates [https://git.xfce.org/](https://git.xfce.org/) 

Also when you upgraded from 14.04 to 16.04 - what got removed? Check in /var/log/dist-upgrade/ - have a look there fro packages removed.

---

### Post by greyfaux01 on 2018-01-23
Hey cool thanks for that info. I never actually knew i could see what got removed, that said, ive never actually looked at a log file either. Thanks again for all your help and info.

edit: wow looking at the git repo browser page, i found all kinds of cool panel plugins, cpugraph-plugin, netload-plugin, even some panel plugins i used to have an Mate (like the spy eyes that follow the mouse pointer across the screen).. cool stuff, i went ahead and installed a few, hey at least i have options now. Thanks again.

---

### Post by flocculant on 2018-01-23
Did you check the log to see what was removed - if anything? 

grep it for xfce :)

(re the git stuff - bear in mind things that are being worked on currently are extremely likely to have been ported to gtk3, and getting help with them here might not work, also things that no-one is interested in (people scratch their own itches) might not get updated)

---

### Post by greyfaux01 on 2018-03-20
sorry didnt realize you replied, i probably deleted the email notification when i deleted tons of other junk emails.. anyway i tried figuring out exactly which command to type to find the removed packages after upgrade, searched online, i only got 'how to remove packages' etc after upgrade.. i did find one website that tells me to put in 'grep remove /var/log/dpkg.log', and i tried that first command as is just to see what happens, and it just went right back to my username, like it 'succeeded' but it didnt list anything like the website claimed it would.. (website it probably outdated)..

 so then i tried the modified version of the directory you wanted me to look in, using grep, i typed: 'grep remove /var/log/dist-upgrade/'  .. and then i got what appears to be an error msg saying 'grep: /var/log/dist-upgrade/: Is a directory'  .....

Its totally not a big deal, i have that other resource monitor in my panel now, its not nearly as good as the old one, but it does the job.. that said, if you want me to type in the correct command using grep, to see what got removed during the upgrade, im definitely willing to learn..

My other laptop now wont connect to the internet, so i'll be making a new thread on that when i get a chance.. i tried all the troubleshooting stuff i could, and i did read the sticky about running that script to help diagnose my problem, so gonna put that on a usb now so i can run the script on the laptop (i indeed cant get online even with wired connection)..

again thanks for your help and knowledge i love learning this stuff.. if your too busy this problem is definitely solved though, so thanks again.. but i am curious what changed, purely curiosity though so dont go out of your way...

---

### Post by greyfaux01 on 2018-03-20
i hope marking the thread as solved doesnt close it

---

