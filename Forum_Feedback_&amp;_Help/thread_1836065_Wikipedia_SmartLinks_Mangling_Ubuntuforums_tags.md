---
title: "Wikipedia SmartLinks Mangling Ubuntuforums tags?"
date: 2011-08-30
forum: Forum Feedback &amp; Help
---

### Post by northd_tech on 2011-08-30
I have noticed in the Networking & Wireless subforum that the Wikipedia SmartLinks seem to be "breaking" the Ubuntuforums thread tags. It seems like the Wikipedia link is taking priority over the Ubuntuforums tag somehow.

For example, the "broadcom" on this thread:

**Wifi not working on my HP Pavilion dv6000 laptop.**
[http://ubuntuforums.org/showthread.php?t=1763621](http://ubuntuforums.org/showthread.php?t=1763621)

the "asus" on this thread:

**Bad Password Asus-n13**
[http://ubuntuforums.org/showthread.php?t=1833778](http://ubuntuforums.org/showthread.php?t=1833778)

and the "sony vaio" and "ralink" on this thread:

Wireless not working on RaLink RT3090 with Ubuntu 10.04
[http://ubuntuforums.org/showthread.php?t=1490123&page=5](http://ubuntuforums.org/showthread.php?t=1490123&page=5)

On my browser (Firefox 6.0 under Windoze Vista Home Premium SP2 6.0.6002 [COLOR=Red]**at the moment only**[/COLOR]- but usually Firefox under Ubuntu 10.04.3 LTS), I am only noticing this in the "Networking & Wireless" subforum index pages:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
[http://ubuntuforums.org/forumdisplay.php?f=336&order=desc&page=2](http://ubuntuforums.org/forumdisplay.php?f=336&order=desc&page=2)

If I go to those specific threads that I listed, then the tags at the bottom of the page work perfectly normally.  I only see the Wikipedia black links on the "Networking & Wireless" subforum index pages (and the Wiki Smartlinks show up as a black link with a dashed underline rather than the [COLOR=RoyalBlue]blue[/COLOR] Ubuntuforums tag).  I would attach a screenshot, but unfortunately I am doing some housekeeping/backup under Windoze Vista, and apparently my screen shot program is somewhere over halfway "crashed" in Vista- surprise!

Also these 2 threads show the same thing for "ralink" & "networkmanager":
[http://ubuntuforums.org/showthread.php?t=1835712](http://ubuntuforums.org/showthread.php?t=1835712)

and for "port forwarding":
[http://ubuntuforums.org/showthread.php?t=1835810](http://ubuntuforums.org/showthread.php?t=1835810)

It is more of an irritation than a huge problem, since clicking on the thread title will take one to the thread (where the Ubuntuforums tags work normally and show up as [COLOR=RoyalBlue]blue[/COLOR] rather than that _dashed underline Wikipedia black_).

EDIT:  I just noticed that it is also doing this in the middle of the CODE tags in the middle of my post #2 here for the commands "lsmod" and "iwconfig"- is there a way to turn this off in my user control panel somehow?:

[http://ubuntuforums.org/showpost.php?p=11202325&postcount=2](http://ubuntuforums.org/showpost.php?p=11202325&postcount=2)

---

### Post by northd_tech on 2011-08-30
I just found this in a search- now it looks like I need to go 'search & destroy' this nasty "SkipScreen" plugin (that I don't remember installing or anything else about, but I have updated Firefox twice recently- from 3.6 to 5.x to 6.0):

> **How to remove “smartlink to:” from firefox**

                                                                   15                         Nov                     
                                                                   Today I noticed something on my [Firefox]("http://en.wikipedia.org/wiki/Firefox")  installation. Every site I visited has a link that says smartLink to:  and links to Wikipedia and other sites. I don’t remember adding this  feature. It’s really annoying there is no easy way to tell the  difference between smartLink and the site links and I endup clicking  smartLinks.
 I start to look who hijacked my browser. After googling few words It  turns out to be skipscreen plug-in is adding links to the pages. I was  pissed off not only because they don’t ask permission to install but there is no option to turn it off.  The solution is disabling skipscreen plug-in. If you don’t like smartLinkand you can either disable or remove SmartLinks completely through the Firefox –> Tools menu>>SmartLinks (at bottoom of the list)>> Remove Smart Link.
> [Val]("http://www.getsmartlinks.com/")                                                                      
 November 17, 2010 at 13:05                                                                                                                                                     
Hi, I’m with the company that created SmartLinks.  Sorry for the confusion we caused you.  
 One point of clarification: SkipScreen does ask for permission to  install SmartLinks through an opt-in window when you install their  add-on.  You must have inadvertently hit the “accept” button to get  SmartLinks.  We’ve had some other users do the same without realizing  it, so we’re redesigning the opt-in window to be more prominent and  clear.
 Also, if you find that you inadvertently accepted SmartLinks and you  don’t like it, you can either disable or remove SmartLinks completely  through the [Firefox]("http://en.wikipedia.org/wiki/Firefox") –> Tools menu.
 Again, sorry for any confusion caused.  You can learn more about SmartLinks and how it works here: [http://skipscreen.getsmartlinks.com/](http://skipscreen.getsmartlinks.com/).  Thanks!
[http://fablex.wordpress.com/2010/11/15/how-to-remove-smartlink-tofrom-firefox/](http://fablex.wordpress.com/2010/11/15/how-to-remove-smartlink-tofrom-firefox/)

EDIT:  In the Firefox 6.0 Menu bar (which of course was disabled by default after the updates to look all "Google Chromey":rolleyes:):

Tools > SmartLinks > [uncheck "Enable SmartLinks"] or [choose "Remove SmartLinks" to remove completely]

more about "SmartLinks"/SkipScreen here:

[http://fox-lingo.getsmartlinks.com/about](http://fox-lingo.getsmartlinks.com/about)

(Apparently these "SmartLinks" rode in on/under my FoxLingo translator plugin, or else an update 'dragged it home'- grrrrrr..... )

---

### Post by northd_tech on 2011-09-01
I don't seem to be seeing this problem under Ubuntu 10.04.3 LTS (with Firefox just barely updated to 3.6.21 a few moments ago).  

I guess it was just an issue running Firefox 6.x under Windows Vista with the Fox Lingo translation add-in (and that nasty 'SkipScreen' plugin that was making all the Wiki SmartLinks).

---

