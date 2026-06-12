---
title: "Firefox Issue Sticky?"
date: 2010-06-14
forum: Forum Feedback &amp; Help
---

### Post by PinchedNerve on 2010-06-14
Could we get a Firefox flash & any other issue sticky? FF is a disaster in 10.04 & one only has to search the Ubuntu forums to figure it out. In this sticky should also be a recommendation to download Google Chrome with links to the downloads.

Please don't take this as I am some rabid Chrome supporter either. I've been using FF for years & the issues have forced me to use Chrome till FF is fixed.

Sure i'll get a couple replies about how wonderful FF works for a few people, but again, search the forums & there are plenty of people having issues with FF & 10.04

---

### Post by pastalavista on 2010-06-14
I think the issue is flash more than Firefox because Chrome isn't that much better. I'm using the adobe-flashplugin now and it works better in some ways and worse in others than flashplugin-nonfree. It also depends a lot on your GPU and Xorg versions too. It's really all a complicated mess and graphics drivers seem to change faster than Adobe and Linux flash developers can keep up with.

---

### Post by John Bean on 2010-06-14
> **PinchedNerve said:**
> Sure i'll get a couple replies about how wonderful FF works for a few people

How do you know it's only "a few", and just how many is that anyway?

> but again, search the forums & there are plenty of people having issues with FF & 10.04

Happy people don't post to say they're happy but those with a problem make a lot of noise. If I had to make a guess I'd say that the silent majority of Firefox users are happy with it, those with a problem are a vocal minority.

---

### Post by veggen on 2010-06-14
> **PinchedNerve said:**
> In this sticky should also be a recommendation to download Google Chrome with links to the downloads.

I'm only half-serious* here, but maybe it's time to give [Opera](http://www.opera.com) a go ;)

*because I know suggesting a different browser isn't much help.

---

### Post by lovinglinux on 2010-06-14
> **John Bean said:**
> How do you know it's only "a few", and just how many is that anyway?

Happy people don't post to say they're happy but those with a problem make a lot of noise. If I had to make a guess I'd say that the silent majority of Firefox users are happy with it, those with a problem are a vocal minority.

I agree.

BTW, [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Man_Beach on 2010-06-14
> **PinchedNerve said:**
> Could we get a Firefox flash & any other issue sticky? FF is a disaster in 10.04 & one only has to search the Ubuntu forums to figure it out. In this sticky should also be a recommendation to download Google Chrome with links to the downloads.

Please don't take this as I am some rabid Chrome supporter either. I've been using FF for years & the issues have forced me to use Chrome till FF is fixed.

Sure i'll get a couple replies about how wonderful FF works for a few people, but again, search the forums & there are plenty of people having issues with FF & 10.04

I agree. Firefox has been really getting on my nerves these past 6 weeks - ever since I installed 10.04. Random crashes back to the login screen when browsing are a pain and something I've never experienced before with 2 previous versions of Ubuntu (or SuSe before that). Try googling 'ubuntu firefox crash', for example. Unfortunately, problems like this don't show up on the live CD - they only appear after you've been using it a while.

I suspect that my 5 year old computer with its ageing ATI video card might have something to do with it - but it's worked very well up to now and it's not as if I'm trying to do anything new like play fancy games or anything - I'm just browsing the internet.

In the meantime, I'm on Chrome and it seems to be working very well (touch wood).

---

### Post by PinchedNerve on 2010-06-14
> **John Bean said:**
>  those with a problem are a vocal minority.
Unlikely. More then likely, the vocal minority are new/newish to Ubuntu/Linux & not familiar enough with Ubuntu/Linux to not ask for help.

If I had to guess (just like you), the "Silent Majority" are much more able to trouble shoot there own Ubuntu/Linux issues as well as tolerating the issue. Also likely possible they are using a different browser altogether.

Just because people are not posting in no way means they are not having issues. Most of us know that already though.

---

### Post by bodhi.zazen on 2010-06-14
> **PinchedNerve said:**
> Could we get a Firefox flash & any other issue sticky? FF is a disaster in 10.04 & one only has to search the Ubuntu forums to figure it out. In this sticky should also be a recommendation to download Google Chrome with links to the downloads.

Please don't take this as I am some rabid Chrome supporter either. I've been using FF for years & the issues have forced me to use Chrome till FF is fixed.

Sure i'll get a couple replies about how wonderful FF works for a few people, but again, search the forums & there are plenty of people having issues with FF & 10.04

lolwut ???

I have had no problems with Firefox in Ubuntu 10.04 nor do I see wide spread firefox problems on the forums.

All browsers can have issues, and if you want to use Chrome, Chromium has less problems for some then Chrome.

What problem are you having with firefox and what makes you think we need a sticky for such a problem ?

Can you provide links to such threads on the forums that there is some systemic problem with firefox ?

Did you file a bug report on launchpad ?

---

### Post by proggy on 2010-06-14
I never have had problems with FF or flash on Ubuntu ,but i never was able to install it in internet explorer on windows even the 32 bit version of it.

---

### Post by bodhi.zazen on 2010-06-14
I did find this bug report on Launchpad :

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772)

There is a fix released.

Is this the bug you are asking about ?

Other then that I found reports about firefox crashing with the use of NoScript, which I have not seen as I use ff + NoScript on Ubuntu without any problem.

The other problem I found was with Flash. Again, I dl flash from Adobe and not the Ubutnu repos.

At any rate, if you think a sticky would help, please provide more details.

---

### Post by lovinglinux on 2010-06-14
> **bodhi.zazen said:**
> Other then that I found reports about firefox crashing with the use of NoScript, which I have not seen as I use ff + NoScript on Ubuntu without any problem.

I also use NoScript and don't have any problems, but I have seen a couple of users with such issues. Nevertheless, I don't think that deserves a sticky, since the number of users with such issue is negligible.

> **bodhi.zazen said:**
> The other problem I found was with Flash. Again, I dl flash from Adobe and not the Ubutnu repos.

If there is the need for a new sticky, then I would suggest one about flash, not about Firefox. Most threads I reply about Firefox issues are flash related and usually also affect other browsers.

The most common topics are:

[LIST=1]
[*]not being able to play flash videos due to multiple plugin installation (swfdec-mozilla along with flashplugin-nonfree)
[*]not being able to interact with flash controls when running a 32bit plugin on a 64bit browser
[*]jerky playback when viewing videos in fullscreen
[*]browser crashing when viewing videos in fullscreen
[*]no sound in flash videos
[/LIST]
There are some solutions that work in variable degrees:

[LIST=1]
[*]Remove swfdec-mozilla and install flashplugin-nonfree. Some users need more complicated solutions due to multiple attempts to install flash, which can include even Wine, but this can be solved (most of the time) with [FLASH-AID](http://flash-aid-extension.blogspot.com/) extension or [Adobe Tools](http://ubuntuforums.org/showthread.php?t=1414595).
[*] I used to recommend the 64bit flash version, but this is not an option anymore. So I am recommending [this workaround](http://ubuntuforums.org/showpost.php?p=9455221&postcount=18) now.
[*]sometimes can be solved with [Override GPU Validation](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
[*]solution varies
[*]sometimes can be fixed [with this](http://ubuntuforums.org/showpost.php?p=9402185&postcount=7).
[/LIST]

This is what I can remember right now, but I was thinking about doing some sort of issue analysis to determine the best solutions for each problem, in order to improve my tutorial. I could provide this info for a sticky if needed, but would take some time. There are a lot of threads to examine. With such huge amount of flash threads is easy to lose track of the effectiveness of a solution.

---

### Post by themarker0 on 2010-06-14
I have daily issues of firefox crashing and greying out. I didn't bother making a launchpad or even a thread for the fact that i can't be the only one.

---

### Post by lovinglinux on 2010-06-14
> **themarker0 said:**
> I have daily issues of firefox crashing and greying out. I didn't bother making a launchpad or even a thread for the fact that i can't be the only one.

If you want some help, create a new thread describing your problem and post the link here.

---

### Post by themarker0 on 2010-06-14
> **lovinglinux said:**
> If you want some help, create a new thread describing your problem and post the link here.

I thought i edited that with more info. I must've not. Oh well. Done.

[http://ubuntuforums.org/showthread.php?p=9462023#post9462023](http://ubuntuforums.org/showthread.php?p=9462023#post9462023)

---

### Post by PinchedNerve on 2010-06-15
> **lovinglinux said:**
> If there is the need for a new sticky, then I would suggest one about flash, not about Firefox. Most threads I reply about Firefox issues are flash related and usually also affect other browsers.

The most common topics are:

[LIST=1]
[*]not being able to play flash videos due to multiple plugin installation (swfdec-mozilla along with flashplugin-nonfree)
[*]not being able to interact with flash controls when running a 32bit plugin on a 64bit browser
[*]jerky playback when viewing videos in fullscreen
[*]browser crashing when viewing videos in fullscreen
[*]no sound in flash videos
[/LIST]
There are some solutions that work in variable degrees:

[LIST=1]
[*]Remove swfdec-mozilla and install flashplugin-nonfree. Some users need more complicated solutions due to multiple attempts to install flash, which can include even Wine, but this can be solved (most of the time) with [FLASH-AID](http://flash-aid-extension.blogspot.com/) extension or [Adobe Tools](http://ubuntuforums.org/showthread.php?t=1414595).

[*] I used to recommend the 64bit flash version, but this is not an option anymore. So I am recommending [this workaround](http://ubuntuforums.org/showpost.php?p=9455221&postcount=18) now.
[*]sometimes can be solved with [Override GPU Validation](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
[*]solution varies
[*]sometimes can be fixed [with this](http://ubuntuforums.org/showpost.php?p=9402185&postcount=7).
[/LIST]

This is what I can remember right now, but I was thinking about doing some sort of issue analysis to determine the best solutions for each problem, in order to improve my tutorial. I could provide this info for a sticky if needed, but would take some time. There are a lot of threads to examine. With such huge amount of flash threads is easy to lose track of the effectiveness of a solution.

I seriously doubt its a "flash" issue when I have none of these issues in Chrome. Frankly I am tired of all the "code" work just to get flash & FF to play nice with one another. If some of you seem to be in heaven with FF that's great but a lot of us are not & constantly having to use terminal & code to remove, install, & on & on for flash is ridiculous.

Flash doesn't work in FF for a lot of us but does in Chrome...  I've tried all the tricks & the only time it worked right was when lovinglinux had his addon that installed the 64bit version of Flash. Since 64 flash is killed its back to Flash/FF hell again.

Issues are, Flash embedded videos won't work unless I set my Visual Effects to "None" & when it is set to none then when in forums with embedded videos, as soon as I scroll the video out of view I get grey bars all around all the videos.

This forum has the popup preview window that pops up for threads & as soon as I scroll the page I get the damn grey bars again. Mind you none of this happens in Chrome.  Its also not a video card/driver issue because I have 4 computers running 10.04 Ubuntu 2 with ATI & 2 with nVidia, all having the same issues....  I keep the OS up to date, in fact I check it multiple times a day.

In [Netbook remix]("http://ubuntuforums.org/showthread.php?t=1479514") I can't use FF at all because it totally screws up the screen to where everything is unreadable. This FF/Flash issue is so god damn annoying I am considering trying 32bit Ubuntu on my other 3 desktops but I really don't want to go that route.

[COLOR="Red"]If this really was a "Flash" issue solely, then why the hell wouldn't the same issues be produced in Chrome!?!?!?[/COLOR] 

The only issues I have with Chrome so far is 1 forum I frequent doesn't support Safari browsers worth a damn & I don't have an extension in Chrome capable of monitoring & notifying multiple webmail accounts at the same time....


I apologies for some of my language, but this FF/Flash issue is really getting on my nerves & I am pretty tired of trying to fix it. I now have to use both browsers depending on what I am doing.... Chrome for most of my surfing & FF for 1 stinking forum & checking my webmail accounts easily.

---

### Post by pastalavista on 2010-06-15
> **PinchedNerve said:**
> ...
I apologies for some of my language, but this FF/Flash issue is really getting on my nerves & I am pretty tired of trying to fix it. I now have to use both browsers depending on what I am doing.... Chrome for most of my surfing & FF for 1 stinking forum & checking my webmail accounts easily.
I have to apologize too for allowing your whining to bother me more than any computer problem ever has. I'm un-subscribing from this thread now.
Good luck finding the digital bliss you seem to demand.

---

### Post by PinchedNerve on 2010-06-15
> **pastalavista said:**
> I have to apologize too for allowing your whining to bother me more than any computer problem ever has. I'm un-subscribing from this thread now.
Good luck finding the digital bliss you seem to demand.

Whatever dude. Having FF & Flash work is to much to ask I guess.

[IMG]http://img.photobucket.com/albums/v141/Devourer/IMG_0590.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v141/Devourer/IMG_0589.jpg[/IMG]

Sorry about the pictures, but every time I hit print screen the grey boxes go away.

---

### Post by lovinglinux on 2010-06-15
> **PinchedNerve said:**
> I seriously doubt its a "flash" issue when I have none of these issues in Chrome. Frankly I am tired of all the "code" work just to get flash & FF to play nice with one another. If some of you seem to be in heaven with FF that's great but a lot of us are not & constantly having to use terminal & code to remove, install, & on & on for flash is ridiculous.

Flash doesn't work in FF for a lot of us but does in Chrome...  I've tried all the tricks & the only time it worked right was when lovinglinux had his addon that installed the 64bit version of Flash. Since 64 flash is killed its back to Flash/FF hell again.

Issues are, Flash embedded videos won't work unless I set my Visual Effects to "None" & when it is set to none then when in forums with embedded videos, as soon as I scroll the video out of view I get grey bars all around all the videos.

This forum has the popup preview window that pops up for threads & as soon as I scroll the page I get the damn grey bars again. Mind you none of this happens in Chrome.  Its also not a video card/driver issue because I have 4 computers running 10.04 Ubuntu 2 with ATI & 2 with nVidia, all having the same issues....  I keep the OS up to date, in fact I check it multiple times a day.

In [Netbook remix]("http://ubuntuforums.org/showthread.php?t=1479514") I can't use FF at all because it totally screws up the screen to where everything is unreadable. This FF/Flash issue is so god damn annoying I am considering trying 32bit Ubuntu on my other 3 desktops but I really don't want to go that route.

[COLOR="Red"]If this really was a "Flash" issue solely, then why the hell wouldn't the same issues be produced in Chrome!?!?!?[/COLOR] 

The only issues I have with Chrome so far is 1 forum I frequent doesn't support Safari browsers worth a damn & I don't have an extension in Chrome capable of monitoring & notifying multiple webmail accounts at the same time....


I apologies for some of my language, but this FF/Flash issue is really getting on my nerves & I am pretty tired of trying to fix it. I now have to use both browsers depending on what I am doing.... Chrome for most of my surfing & FF for 1 stinking forum & checking my webmail accounts easily.

One thing you are forgetting to consider is that Chrome doesn't allow you to configure anything, extensions are very limited and it doesn't have many built-in features. So of course it will produce less problems. If you compare a vanilla Firefox with a clean profile and Chrome, Firefox is practically as fast as Chrome and works beautifully. 

Google is very smart. They released a browser that is extremely fast and has very limited features, so they are attracting users that are not satisfied with Firefox performance and are whiling to sacrifice customization capabilities. But once the users realize they miss those nice Firefox features and powerful extensions, Google will add more features and extension APIs that at some point will cause similar problems.

I also need to say that the latest 32bit version of flash is working beautifully here. I can even play my ISP streaming videos in fullscreen, which I wasn't capable with the 64bit or the old 32bit version. That problem was affecting every browser, including Chrome.

Also please notice that I use KDE and Kwin, not Gnome and Compiz.

---

### Post by PinchedNerve on 2010-06-15
> **lovinglinux said:**
> One thing you are forgetting to consider is that Chrome doesn't allow you to configure anything, extensions are very limited and it doesn't have many built-in features. So of course it will produce less problems. If you compare a vanilla Firefox with a clean profile and Chrome, Firefox is practically as fast as Chrome and works beautifully.

Actually I am not forgetting it, I would prefer to use FF, but grey bars blocking text in threads or on news sites is just endlessly annoying.  Most of the tests I've run shows FF is faster for me (with the config tweaks) but I don't use many addons for FF either.  10 total, 1 of which came in the Ubuntu FF install "Ubuntu FF Modifications" & another one for scrolling that I added today. 

FF Addons

1-ClickWeather
Adblock Plus
Better Privacy
Gmail Checker
New Tab Homepage
Quake Live
Ubuntu FireFox Modifications
United States English Dictionary
Yet Another Smooth Scrolling

I have disabled most with the same issues occurring.  Btw: My intention for the thread request was only to make it easier for others to have a 1 stop issues report & probable fix thread.  I'm sure any mod could update the starting sticky with work around/fixes.

I'll try disabling the ubuntu mods, but I would be surprised if that was the issue.

Edit: no idea what "KDE and Kwin, not Gnome and Compiz." means to me.  I am a Ubuntu noob.

Edit again. Disabled all Addons Except the Ubuntu Mod & still get the Grey bars.  Tried disabling just Ubuntu Mods & still got the grey bars. Lastly, I disables all addons & still get the grey bars.

---

### Post by lovinglinux on 2010-06-15
> **PinchedNerve said:**
> Actually I am not forgetting it, I would prefer to use FF, but grey bars blocking text in threads or on news sites is just endlessly annoying.  Most of the tests I've run shows FF is faster for me (with the config tweaks) but I don't use many addons for FF either.  10 total, 1 of which came in the Ubuntu FF install "Ubuntu FF Modifications" & another one for scrolling that I added today. 

FF Addons

1-ClickWeather
Adblock Plus
Better Privacy
Gmail Checker
New Tab Homepage
Quake Live
Ubuntu FireFox Modifications
United States English Dictionary
Yet Another Smooth Scrolling

I have disabled most with the same issues occurring.  Btw: My intention for the thread request was only to make it easier for others to have a 1 stop issues report & probable fix thread.  I'm sure any mod could update the starting sticky with work around/fixes.

I'll try disabling the ubuntu mods, but I would be surprised if that was the issue.

Edit: no idea what "KDE and Kwin, not Gnome and Compiz." means to me.  I am a Ubuntu noob.

Edit again. Disabled all Addons Except the Ubuntu Mod & still get the Grey bars.  Tried disabling just Ubuntu Mods & still got the grey bars. Lastly, I disables all addons & still get the grey bars.

I have experienced that issue before, but it simply disappeared, so I don't know what was causing it. It must be related to Compiz.

[KDE](http://en.wikipedia.org/wiki/KDE) is another popular [Desktop Environment](http://en.wikipedia.org/wiki/Desktop_environment), which uses [Kwin](http://en.wikipedia.org/wiki/Kwin) [window manager](http://en.wikipedia.org/wiki/X_window_manager) instead of Compiz.

I would recommend that you create a new Ubuntu user and login with that account to see if the problem persists. Post the results.

---

### Post by PinchedNerve on 2010-06-15
> **lovinglinux said:**
> I would recommend that you create a new Ubuntu user and login with that account to see if the problem persists. Post the results.
Ok, I tried it & still got the grey bars.

I would be interested in knowing how many other people get this issue. Maybe a poll? If not many are getting this from the default ISO install then it would have to be on my end in some way. But its highly annoying whatever is causing it.

---

### Post by cariboo on 2010-06-15
This really isn't the place to get your problem solved, but have you tried creating a new profile, to see if that solves the problem?

---

### Post by PinchedNerve on 2010-06-15
> **cariboo907 said:**
> This eally isn't the place to get your problem solved, but have you tried creating a new profile, to see if that solves the problem?

Originally I wasn't looking to get my problem solved with this thread. I was requesting a sticky because its obvious that there is a lot of issues for people regarding FF/Flash. I am not convinced its strictly a "Flash" issue though considering all the attempts I've tried at fixing the issue & they've all revolved around Flash. Personally I think its a FF issue since multiple flash installs, removals, & so on have all failed for me at the same time I do not have 1 single Chrome/Flash issue.

In any case, yes I tried a new profile with the same grey box results. If the powers that be have decided that they do not wish to make a sticky regarding FF/Flash, then this thread can be closed (I wasn't intending this thread ever be the sticky BTW).

---

### Post by lovinglinux on 2010-06-15
> **PinchedNerve said:**
> Originally I wasn't looking to get my problem solved with this thread. I was requesting a sticky because its obvious that there is a lot of issues for people regarding FF/Flash. I am not convinced its strictly a "Flash" issue though considering all the attempts I've tried at fixing the issue & they've all revolved around Flash. Personally I think its a FF issue since multiple flash installs, removals, & so on have all failed for me at the same time I do not have 1 single Chrome/Flash issue.

In any case, yes I tried a new profile with the same grey box results. If the powers that be have decided that they do not wish to make a sticky regarding FF/Flash, then this thread can be closed (I wasn't intending this thread ever be the sticky BTW).

Create a new thread for your problem if you haven't already.

---

### Post by bodhi.zazen on 2010-06-16
> **PinchedNerve said:**
> Originally I wasn't looking to get my problem solved with this thread. I was requesting a sticky because its obvious that there is a lot of issues for people regarding FF/Flash. I am not convinced its strictly a "Flash" issue though considering all the attempts I've tried at fixing the issue & they've all revolved around Flash. Personally I think its a FF issue since multiple flash installs, removals, & so on have all failed for me at the same time I do not have 1 single Chrome/Flash issue.

In any case, yes I tried a new profile with the same grey box results. If the powers that be have decided that they do not wish to make a sticky regarding FF/Flash, then this thread can be closed (I wasn't intending this thread ever be the sticky BTW).

I am open to a sticky, but you have not provided sufficient information for a sticky.

I would say it is a minority of people who have a problem with firefox, and the problems are obviously varied.

So far you are the only person I know who has grey bars with firefox and you do not know the cause of your problem or the solution.

I am sorry your are having this problem, and I would give you a fix if I knew one, but I do not see a sticky as helpful to your plight.

---

### Post by Kir_B on 2010-06-16
> **PinchedNerve said:**
> Could we get a Firefox flash & any other issue sticky? FF is a disaster in 10.04 & one only has to search the Ubuntu forums to figure it out. In this sticky should also be a recommendation to download Google Chrome with links to the downloads.

Please don't take this as I am some rabid Chrome supporter either. I've been using FF for years & the issues have forced me to use Chrome till FF is fixed.

Sure i'll get a couple replies about how wonderful FF works for a few people, but again, search the forums & there are plenty of people having issues with FF & 10.04

I'm also having similar issues with Firefox. 

I went onto the Youtube site the other day, looking to see what videos were available concerning the Bilderberg groups recent annual get together to decide all of our futures. I ran into a [five part video]("http://www.youtube.com/watch?v=FleUn8pgn0c&feature=PlayList&p=FA3FC4137F90BF67&playnext_from=PL&index=0&playnext=1") from Jesse Ventura's newish show. I put together a [playlist]("http://www.youtube.com/watch?v=FleUn8pgn0c&feature=PlayList&p=FA3FC4137F90BF67&playnext_from=PL&index=0&playnext=1") and began to watch it, but _every_ time it goes to the second part, Firefox crashes. There's no error report, so filing a bug report isn't as simple as normal.

I uninstalled Swiftfox and re-installed it to no avail. I then repeated the process only this time removing the folder containing the configurations Etc., but the same issue rears it's ugly head. I then uninstalled the Swiftfox along with it's folder in my home folder and this time installed Firefox 3.6.3, but still, the issue remains.

I finally gave up trying to fix it, after following several different fixes that I'd found here on these forum threads. The strange thing, is that I finally got to watch the entire playlist from start to finish, only using Seamonkey to do it. I hate to use Seamonkey for Youtube, as it doesn't display the text properly, making it very difficult to browse video titles.

I don't know how many hours I've wasted on this issue, but it reminds me of one of the issues that lead to me leaving Windoze for the wonderful world of Linux and Ubuntu ([.net framework]("http://en.wikipedia.org/wiki/Mozilla_Firefox#.Net_Framework_3.5_Service_Pack_1") causing never ending crashes  requiring several reboots per day). It really is quite frustrating, but it appears to me, that it's a Firefox issue with flash.

A sticky would be very helpful, that is, if someone comes up with a fix that works. In the meantime, I'll be avoiding Youtube Etc., as I really am quite addicted to my Firefox browser, along with the [forty plus add-ons]("https://addons.mozilla.org/en-US/firefox/search/?q=lucid+lynx&cat=collections&pp=20&advanced=") I've got installed in it.

Good luck to all. Kirby :confused:

---

### Post by PinchedNerve on 2010-06-16
> **Kir_B said:**
> I'm also having similar issues with Firefox. 

I went onto the Youtube site the other day, looking to see what videos were available concerning the Bilderberg groups recent annual get together to decide all of our futures. I ran into a [five part video]("http://www.youtube.com/watch?v=FleUn8pgn0c&feature=PlayList&p=FA3FC4137F90BF67&playnext_from=PL&index=0&playnext=1") from Jesse Ventura's newish show. I put together a [playlist]("http://www.youtube.com/watch?v=FleUn8pgn0c&feature=PlayList&p=FA3FC4137F90BF67&playnext_from=PL&index=0&playnext=1") and began to watch it, but _every_ time it goes to the second part, Firefox crashes. There's no error report, so filing a bug report isn't as simple as normal.

I uninstalled Swiftfox and re-installed it to no avail. I then repeated the process only this time removing the folder containing the configurations Etc., but the same issue rears it's ugly head. I then uninstalled the Swiftfox along with it's folder in my home folder and this time installed Firefox 3.6.3, but still, the issue remains.

I finally gave up trying to fix it, after following several different fixes that I'd found here on these forum threads. The strange thing, is that I finally got to watch the entire playlist from start to finish, only using Seamonkey to do it. I hate to use Seamonkey for Youtube, as it doesn't display the text properly, making it very difficult to browse video titles.

I don't know how many hours I've wasted on this issue, but it reminds me of one of the issues that lead to me leaving Windoze for the wonderful world of Linux and Ubuntu ([.net framework]("http://en.wikipedia.org/wiki/Mozilla_Firefox#.Net_Framework_3.5_Service_Pack_1") causing never ending crashes  requiring several reboots per day). It really is quite frustrating, but it appears to me, that it's a Firefox issue with flash.

A sticky would be very helpful, that is, if someone comes up with a fix that works. In the meantime, I'll be avoiding Youtube Etc., as I really am quite addicted to my Firefox browser, along with the [forty plus add-ons]("https://addons.mozilla.org/en-US/firefox/search/?q=lucid+lynx&cat=collections&pp=20&advanced=") I've got installed in it.

Good luck to all. Kirby :confused:
Thanks for the reply.  I too went the Seamonkey route, as well as Opera, & Chrome to find out what the heck is going on with FF & Flash as well as countless hours trying to resolve the problems I am having. Unfortunately I ran into the usual STFU & accept the issue from some people.

A sticky would be useful to a lot of the people that Ubuntu seems to want to attract, but I am getting the impression that FF having significant flash issues in Ubuntu is something that has to be suppressed rather then discussed.

I hate to say it, but today was the first day I booted into Vista 64 in 2 weeks & you know what, it was nice having a FF browser that actually worked without graphical issues...

---

### Post by cariboo on 2010-06-16
We can't put up a sticky, unless there is some content, what would you like the contents of the sticky to be? Unfortunately you seem to be one of the few with the problem please give us some guidance.

@Kir_B, the videos work fine in html5, how's things in Kitimat?

---

### Post by Kir_B on 2010-06-16
> **cariboo907 said:**
> We can't put up a sticky, unless there is some content, what would you like the contents of the sticky to be? Unfortunately you seem to be one of the few with the problem please give us some guidance.

@Kir_B, the videos work fine in html5, how's things in Kitimat?

Thanks for the response cariboo907.

If you mean, hows my internet connection. The answer is the same as always. Not great, but good enough that I don't have to buff up the video before I begin watching. 

This is the first time that I've tried to run any flash videos in quite some time. Definitely the first time since I upgraded to lucid, which with the exception of my Windoze no longer booting, the Plymouth not displaying during the boot process, and this strange flash thing, it's been a pretty flawless upgrade. Everything else is running great, if not, better than before.

I'm going to try a few more things out and see if I can narrow this down. I just hate to go through that dependency list again, as I seem to recall having bleeding eyes the last time I attempted it.

I am left with a question though, and would appreciate learning what you mean by "html5". Is there a setting in Firefox that I'm missing, or...?

Thanks again. Kirby

P.S. The weather is fair to good at the moment, Fishing is as always, slow to fair and the employment opportunities are nil to none. So, everything is going along at a very nice pace for many.

---

### Post by cariboo on 2010-06-17
I use chrome/chromium, at the bottom of the youtube page, there is a link to join the html5 beta group. Once you become a member, if a video has been converted from flash to html5 you will automagically view the video in html5 instead of flash.

My brother-in-law has family in Terrace, and I spent a very long Jaunary there several years back. I've never seen so much snow fall in one day as I did then.

---

### Post by Kir_B on 2010-06-17
> **cariboo907 said:**
> I use chrome/chromium, at the bottom of the youtube page, there is a link to join the html5 beta group. Once you become a member, if a video has been converted from flash to html5 you will automagically view the video in html5 instead of flash.

My brother-in-law has family in Terrace, and I spent a very long Jaunary there several years back. I've never seen so much snow fall in one day as I did then.

Thanks for the info cariboo907. I'll have to do a little research into it. 

I'm really quite stubborn, and if I'm one of the very few with this issue, which appears to be the case, it's most likely been caused by something that I've done (big surprise :shock:). I'll be guaranteed to learn something by sorting it out myself. I've had this issue in the past, with both Firefox and Icecat. I managed to sort out the Firefox/Flash at least once already, but sadly, I couldn't manage to get the Icecat to work properly with Flash/Gnash. Despite many days trying, Icecat just didn't appear to be quite ready for prime time, at least at the time that I tried it out.

If anyone has had any success with Icecat recently, I'd really appreciate a response, as I'd prefer to take the open source route, if at all possible. It's been quite a while since I tried Icecat, so perhaps it's time to give it another go.

As the thread suggests, a sticky, or a trouble shooting thread would be nice, as it really is a lot of reading of many, many threads to find all of the ways that people have used to get it working in the past. Many of those older fixes may perhaps no longer be applicable these days and may actually do more harm than good. Just a thought.

But then again, perhaps Canonical has got it all figured out and it's just us rookies mucking things up, leaving many of us banging our heads against the wall. I just hate to think that this may be scaring the rookies away and sending them back into the welcoming arms of the Windoze criminal monopoly :twisted:.

Thanks again. Kirby

P.S. They do get a lot of snow in terrace, but you really should have taken  the drive thirty five miles to the south, as we more often than not, get  two to three times more per year than Terrace. The native spelling of  Kitimat, is actually "Kitimaat", and If I remember correctly, the  translation is something like, "valley of the deep snow". It really is  something to see when the snowbanks are fifteen to twenty plus feet  tall. As long as I'm not doing the shoveling #-o, I love it! ):P

---

### Post by cariboo on 2010-06-17
> P.S. They do get a lot of snow in terrace, but you really should have taken the drive thirty five miles to the south, as we more often than not, get two to three times more per year than Terrace. The native spelling of Kitimat, is actually "Kitimaat", and If I remember correctly, the translation is something like, "valley of the deep snow". It really is something to see when the snowbanks are fifteen to twenty plus feet tall. As long as I'm not doing the shoveling , I love it! 

Down here in the Williams Lake area we get on average about 3-4 feet of snow a year, that's enough for me. :)

---

### Post by pricetech on 2010-06-17
I too have no problems with Firefox.  I don't use flash however because it was such a thorn in the side with Hardy, I didn't even bother once I moved to Lucid.

I lean towards agreeing with those who say it's flash, not Firefox, based upon the above.

As I understand it, a sticky should at least start with a solution, not problem.  Perhaps the OP should sort the problem out, then offer his solution as the basis for the sticky he wants.

---

### Post by lovinglinux on 2010-06-27
I started working on a Flash troubleshooting tutorial.

See:

[http://www.ubuntuforums.org/showthread.php?t=1517564](http://www.ubuntuforums.org/showthread.php?t=1517564)
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

