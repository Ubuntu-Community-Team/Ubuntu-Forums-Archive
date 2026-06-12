---
title: "Firefox shuts down a lot"
date: 2009-05-15
forum: General Help
---

### Post by Crazy K on 2009-05-15
Ever since I did an update to firefox about 2 or so months ago, I've been having problems. What happens is this. It closes down on my if I have more than one or two site's up at the same time. It also depends on the site. Like if it's Myspace, I usually can't open another tab and go to another site without it closing down on me. Anyways I want to know how to fix this problem, as it annoys my family and I. I always clear out my private data, so that's not the problem.

---

### Post by utnubuuser on 2009-05-15
Hi have you tried reinstalling firefox?

> sudo apt-get install -reinstall firefox

---

### Post by Crazy K on 2009-05-15
no, but I will try it. I know I did the last update, and that didn't help me out either.

---

### Post by leomelo on 2009-05-15
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by Crazy K on 2009-05-15
So I tried the sudo apt-get install -reinstall firefox. But it didn't work. Here's what it said: 

E: Command line option 'r' [from -reinstall] is not known.

> [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa) 

And what does this do?

---

### Post by pparise on 2009-05-15
This has been happening to me fairly regularly on Intrepid also. It just shuts down while attempting to load a site. No warnings or popups, the window just closes, bang! I suspect it's something on the page, like Flash or something but the same site loads fine on other occasions, so it's kind of random. Could the system logs help diagnose the problem in this type of shutdown?

---

### Post by Crazy K on 2009-05-15
I have no idea. Firefox does the same for me. I actually disabled shockwave and I was able to surf around for quite a while. Had maybe 9 or so tabs running and it was slow, but it didn't close down on me. Anyways once I enabled shockwave it started doing it all over again. so idk. 

if this helps, here are the plugins I have enabled: 

Shockwave flash 9.0 r159
Totem web browser plugin 2.22.1
Windows Media Player plug-in 10 (compatible; totem)
Windows Media player plugin

I currently have VLC multimedia plugin (compatible Totem 2.22.1) Disabled, But I'm going to re-enable it soon. 

Here are my extensions: 

DownloadThemAll 1.1.3
Google Toolbar for Firefox 3.1.20081127L
Stealther 1.0.6
Stumbleupon 3.29
TabRenamizer 0.8.13
Ubuntu Firefox Modifications 0.5 

So yeah if that helps at all. 

By the way, I have 1GB of ram, so I should be able to run a lot a tabs.

---

### Post by pparise on 2009-05-16
Well there are so many combinations of possible factors that it really could be anything. I've looked at the various logs via System > Administration > System Log with no luck. There just doesn't seem to be enough information to debug this so I guess I'll just try and catch which site seems to cause problems and see if I can go from there...

---

### Post by Sewje on 2009-05-16
You can try Firefox Preferences->Content, Enable JavaScript Advanced setting and untick everything in there.
And install Adblocker Plus if you haven't.

---

### Post by ravindra.rajaram on 2009-05-16
I had seen a similar problem before. The problem apparently was with Google Toolbar.
Disabling the Google Toolbar solved the problem.

---

### Post by Crazy K on 2009-05-16
Yeah I can try those ideas out. I'll update you on my progress.

Edit - 

I just tried the adobe trick, and it's actually working quite well. I currently have this page open as well as 4 others, 3 Myspace pages and one lastfm page. Anyways it seems to be doing fine now. I'll update you all if anything happens.

---

### Post by paradigm2 on 2009-05-16
> **Crazy K said:**
> Yeah I can try those ideas out. I'll update you on my progress.

Edit - 

I just tried the adobe trick, and it's actually working quite well. I currently have this page open as well as 4 others, 3 Myspace pages and one lastfm page. Anyways it seems to be doing fine now. I'll update you all if anything happens.

You might also consider running the Firefox 3.5 shiretoko beta:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

It will run along side of Firefox 3.0.x add it will appear as "Shiretoko" in your Applications -> internet menu.  In my opinion it is much better with resources (both cpu and memory) and quicker as well.  Most importantly a lot of bugs seemed to have been fixed.

There is a catch though.  More than likely not all of your extensions will work.  Most will probably work, especially if you disable the version checking.  But more than likely not all of them.  There is another catch too....this isn't a official firefox release yet.

---

### Post by Crazy K on 2009-05-17
So yeah, taking the google toolbar off didn't do anything. Also tried that adobe trick, and that too didn't help for long. Also, do I have to un-install the google toolbar or somehting? 

Anyways I'll test out the Firefox 3.5 shiretoko beta next.

---

### Post by Crazy K on 2009-05-18
Yeah I couldn't install the Firefox 3.5 shiretoko beta. So yeah idk what to do now.

---

### Post by utnubuuser on 2009-05-20
sorry,  I think that's supposed to be --reinstall, with two hyphens, not one.

---

### Post by Crazy K on 2009-05-29
Tried the re-install, and that too did not work. 

Is there any other ways of fixing this problem?

---

### Post by ronaldo01 on 2009-05-29
Please reinstall and it should works fine for you

---

### Post by Crazy K on 2009-05-29
I already did that. Firefox still closes down on me.

---

### Post by utnubuuser on 2009-05-29
reinstall option requires two hyphens --reinstall.

Have you tried completely removing FF then reinstalling?> sudo apt-get remove firefox --purge (notice the double hyphen)reboot, then> sudo apt-get install firefox.

---

### Post by Crazy K on 2009-05-29
Didn't do that, I'll try that next.

---

### Post by Crazy K on 2009-05-29
So yeah tried it once, and it seemed to work for a while, but then firefox started closing down again. 

I did it yet again, so hopefully this time it works. 

Also, I have Firefox 2 on this computer as well. So I have Firefox 3.0.10 and Firefox 2. Could this be the problem?

---

### Post by Crazy K on 2009-05-30
OK, so I think the problem is with Ubuntu. The Galeon web browser also closes out like firefox. So what can I do to help this stop?

---

### Post by Crazy K on 2009-05-31
I'd like to update you all on this. I checked the preferences on firefox, and noticed in the Updates section that Firefox is unchecked for further undates. Well, I try to check it, but it doesn't allow it. Here's a pic if you don't get what I mean: 

[http://img.photobucket.com/albums/v434/CrazyK12/ff.jpg](http://img.photobucket.com/albums/v434/CrazyK12/ff.jpg)

---

### Post by lavinog on 2009-05-31
My firefox shutdown without warning for me recently...I thought it was odd, but couldn't get it to do it again.

---

### Post by Soul-Sing on 2009-05-31
> I'd like to update you all on this. I checked the preferences on firefox, and noticed in the Updates section that Firefox is unchecked for further undates. Well, I try to check it, but it doesn't allow it. Here's a pic if you don't get what I mean:

Thats perfect. allright.
firefox update should be grayed-out. Ubuntu does that part of the job. Add-ons updates "are done" by firefox....

---

### Post by Crazy K on 2009-05-31
Alright, that's good to know. Btw, do you want me to post pics of everything in the preferences? If it can help fix the problem. I dissabled some ad-ons like Stealthier, and the Tab Renamerizer, though I doubt that has anything to do with the problem. 

But yeah I'll post some more pics if it can help me out.

---

### Post by Soul-Sing on 2009-05-31
> **lavinog said:**
> My firefox shutdown without warning for me recently...I thought it was odd, but couldn't get it to do it again.


4 things:

1) preferences/security: attacksite "service", high cpu. Experimental feature imho
2) two sorts of java installed, or not completely installed
3) two sorts of flash: gnash and flash-non free "interfering"
4) add-ons, to many, or bad sofware.

edit: or a "corrupt" ./mozilla home

---

### Post by Crazy K on 2009-05-31
Here's some pics of the applications list: 
[http://img.photobucket.com/albums/v434/CrazyK12/app1.jpg](http://img.photobucket.com/albums/v434/CrazyK12/app1.jpg)
[http://img.photobucket.com/albums/v434/CrazyK12/app2.jpg](http://img.photobucket.com/albums/v434/CrazyK12/app2.jpg)
[http://img.photobucket.com/albums/v434/CrazyK12/app3.jpg](http://img.photobucket.com/albums/v434/CrazyK12/app3.jpg)
[http://img.photobucket.com/albums/v434/CrazyK12/app4.jpg](http://img.photobucket.com/albums/v434/CrazyK12/app4.jpg)

I realized I could of stretched it out, but oh well. 

Here's the menu for the java content: 
[http://img.photobucket.com/albums/v434/CrazyK12/contentjava.jpg](http://img.photobucket.com/albums/v434/CrazyK12/contentjava.jpg)

The encription area: 
[http://img.photobucket.com/albums/v434/CrazyK12/encrip.jpg](http://img.photobucket.com/albums/v434/CrazyK12/encrip.jpg)

My plugin list:
[http://img.photobucket.com/albums/v434/CrazyK12/plugin1.jpg](http://img.photobucket.com/albums/v434/CrazyK12/plugin1.jpg)
[http://img.photobucket.com/albums/v434/CrazyK12/plugin2.jpg](http://img.photobucket.com/albums/v434/CrazyK12/plugin2.jpg)

---

### Post by lavinog on 2009-05-31
> **leoquant said:**
> 4 things:

1) preferences/security: attacksite "service", high cpu. Experimental feature imho
2) two sorts of java installed, or not completely installed
3) two sorts of flash: gnash and flash-non free "interfering"
4) add-ons, to many, or bad sofware.

edit: or a "corrupt" ./mozilla home

#2 seems likely, I will have to check it out when i get back to that computer.
Thanks for the clues

---

### Post by Soul-Sing on 2009-05-31
Crazy K

Do you use firefox beta 3.5 for linux?

---

### Post by Crazy K on 2009-05-31
No, I'm using 3.0.10 at the moment.

---

### Post by martini1179 on 2009-06-01
> **Crazy K said:**
> Ever since I did an update to firefox about 2 or so months ago, I've been having problems. What happens is this. It closes down on my if I have more than one or two site's up at the same time. It also depends on the site. Like if it's Myspace, I usually can't open another tab and go to another site without it closing down on me. Anyways I want to know how to fix this problem, as it annoys my family and I. I always clear out my private data, so that's not the problem.


So in other words, whenever Firefox decides to spontaneously close, you're always opening/trying to open a new tab?

---

### Post by martini1179 on 2009-06-01
> **leoquant said:**
> 4 things:

1) preferences/security: attacksite "service", high cpu. Experimental feature imho
2) two sorts of java installed, or not completely installed
3) two sorts of flash: gnash and flash-non free "interfering"
4) add-ons, to many, or bad sofware.

edit: or a "corrupt" ./mozilla home

Just out of curiosity, what are the right packages that need to be installed for Java? I have the same problem as the OP with Firefox closing constantly, and have the following Java packages currently installed: 

sun-java6-bin  ver 6-13-1
sun-java6-jre   ver 6-13-1
sun-java6-plugin ver 6-13-1
java-common ver 0.30ubuntu4

---

### Post by Soul-Sing on 2009-06-01
Crazy K thanks for the information. On my system, and on my firefox i have got the same preferences....
And i have got no problems with firefox.

---

### Post by Crazy K on 2009-06-01
> **martini1179 said:**
> So in other words, whenever Firefox decides to spontaneously close, you're always opening/trying to open a new tab?

Not really. Firefox usually closes whenever I have a site like myspace or youtube up. I usually have a one other tab up when it closes on me. 

Also I don't think it's firefox. Like I said, I tried the Galeon web browser, and that too closes down on me. Is there anything I can do with Ubuntu to fix the problem?

---

### Post by lavinog on 2009-06-02
> **leoquant said:**
> 4 things:

1) preferences/security: attacksite "service", high cpu. Experimental feature imho
2) two sorts of java installed, or not completely installed
3) two sorts of flash: gnash and flash-non free "interfering"
4) add-ons, to many, or bad sofware.

edit: or a "corrupt" ./mozilla home

I had a flash 9 plugin in my ~/.mozilla/plugins folder that was of course carried over from the upgrade.

---

### Post by Crazy K on 2009-06-03
Btw, again, it can't be firefox. I also have the Galeon web browser on here, and that too closes down on me if I have a certain website like myspace or youtube up. 

Is there anything in Ubuntu I can change to fix this problem?

---

### Post by Teutorix on 2009-06-03
I used to have a similar problem in firefox due to RAM leakage. after a while on sites with a high cache usage, like watching videos, or playing games on newgrounds and even myspace pages with a lot of messy HTML.

It dosent seem like the same problem but I changed the settings so that firefox dosent keep more than 100MB of ram at any one time, that helped me solve my issue, but as i said it might not be the same problem.

---

### Post by Soul-Sing on 2009-06-03
> **Teutorix said:**
> I used to have a similar problem in firefox due to RAM leakage. after a while on sites with a high cache usage, like watching videos, or playing games on newgrounds and even myspace pages with a lot of messy HTML.

It dosent seem like the same problem but I changed the settings so that firefox dosent keep more than 100MB of ram at any one time, that helped me solve my issue, but as i said it might not be the same problem.

Yep, good proposal.+1
All these firefox issue's can't be solved with a single, one way solution. Sometimes the firefox issue's are so random en ambigious...

---

### Post by Crazy K on 2009-06-03
> **Teutorix said:**
> I used to have a similar problem in firefox due to RAM leakage. after a while on sites with a high cache usage, like watching videos, or playing games on newgrounds and even myspace pages with a lot of messy HTML.

It dosent seem like the same problem but I changed the settings so that firefox dosent keep more than 100MB of ram at any one time, that helped me solve my issue, but as i said it might not be the same problem.

I'll try that out. btw, I noticed that I had 50MB for the cache, should I put it to 100MB or lower it?

But yeah, I put it to 100MB.

---

### Post by TheForumTroll on 2009-06-03
Well if the problem isn't with Firefox this wont help much but you could try running firefox with a clean profile. Add --profilemanager to the Firefox shortcut and create a test profile and see if that helps.


Also you could try the official Firefox from Mozillas site. For some reason the application that collect data about crashes in Firefox was removed in the Ubuntu version so debugging is hard. Since it updates itself there should be no need to worry about security issues.

EDIT: Ops, breakpad isn't in 64bit releases at all so it's not just in Ubuntu :)

---

### Post by lavinog on 2009-06-04
> **Crazy K said:**
> Btw, again, it can't be firefox. I also have the Galeon web browser on here, and that too closes down on me if I have a certain website like myspace or youtube up. 

Is there anything in Ubuntu I can change to fix this problem?

I suspect flash is the cause since both of those sites are very flash oriented.
try removing flash in synaptic. then load firefox and go to tools>addons>plugins and see if shockwave flash is listed. If it is, then you need to manually remove it.
unfortunately there are various places flash can be located.
try this:
```

sudo updatedb
locate libflashplayer.so

```

Once flash is completely removed, reinstall flash from synaptic

---

### Post by Crazy K on 2009-06-04
Alright I uninstalled this: flashplugin-nonfree 

I went to addons and shockwave flash was gone, so that worked.

I noticed that I didn't have adobe-flashplugin installed instead, so I went ahead and installed that. And it shows up now on my addons list. So hopefully that's correct. Otherwise I'll re-do it over correctly. :)

EDIT:

Seems to be working fine now. :)

Thanks for all the help!

---

### Post by veltsu on 2009-06-12
I've been experiencing the same problem myself with Jaunty and FF 3.0.10.

After reading this thread I tried the flash thing too. I removed the flashplugin-nonfree but Shockwave Flash was still visible in the plugins of FF. I didn't remove it from there manually (how to do that exactly?) but flash works so I'll see if this fixed my problem.

Thanks to all for your help.

---

### Post by martini1179 on 2009-06-13
Start firefox via the terminal, by typing "firefox" at the prompt, and start browsing until the browser crashes. Leave the terminal running so that it can record the error. 

If, and only if you get a BadIDChoice error, similar to the following: 

"
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
"

then I have some good news for you, a fix has been committed and uploaded to jaunty-proposed. 

The package is called libxcb. I'm still a relative noob, so I can't speak to the wisdom of installing proposed packages, but they are working on it and hopefully it'll be available soon. 

[ [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220628](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220628) ]

---

