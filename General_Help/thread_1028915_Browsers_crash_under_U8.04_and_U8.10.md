---
title: "Browsers crash under U8.04 and U8.10"
date: 2009-01-02
forum: General Help
---

### Post by skern03 on 2009-01-02
There are a number of threads on Firefox crashes, so it's nothing new. I upgraded from U8.04 to U8.10, but it's no better.

Then I tried Seamonkey, and it worked fine for a couple of days. Now it too is crashing.

I'm baffled. :confused:

Anyone have any ideas what I can do?

Just in case you ask...
Specs:
P4 3.0 gHz, not overclocked
1.5 GB RAM
ATI Radeon 128 MB card (forget the model#)
No proprietary video drivers are installed.
120 GB SATA drive (new) with U8.10 installed
Linux:20 GB root, 2 GB swap, rest /home
40 GB NTFS drive w/Windows XP installed
Samsung IDE DVD (new)
On-board LAN 
Cable modem, regularly get 800+ kbps download speeds. According to CNET Bandwidth test: 2995.6 Kbps. So it can't be the connex.

---

### Post by rumli on 2009-01-02
Are the crashes typically happening when you are viewing Flash content (like YouTube, Hulu, etc.)?

---

### Post by skern03 on 2009-01-02
> **rumli said:**
> Are the crashes typically happening when you are viewing Flash content (like YouTube, Hulu, etc.)?

No. They often happen when posting content to this forum.

---

### Post by skern03 on 2009-01-03
Bump!
:confused:

---

### Post by fragos on 2009-01-03
I switched to Epiphany. It has the occassional crash when I close a tab but it is so much faster restarting than Firefox That I don't find the crash as objectionable. Epiphany will also allow you to install with webkit. I've both webkit and gecko versions installed.

---

### Post by skern03 on 2009-01-03
> **fragos said:**
> I switched to Epiphany. It has the occassional crash when I close a tab but it is so much faster restarting than Firefox That I don't find the crash as objectionable. Epiphany will also allow you to install with webkit. I've both webkit and gecko versions installed.

I'm getting the same results with Seamonkey - less crashes. However, with Firefox, when I restore a session I can usually get back text typed into a post, for example, not just the tabs. I've had one crash during a forum post using Seamonkey. When I restarted, I didn't get the option to restore the session, and I lost everything I'd typed.

Seamonkey may also have cured some of the other unexplained crashes. My system sometimes crashed all the way back to the login prompt.

I may try Epiphany... I also heard that Opera was pretty good, but that was in the context of Firefox loading pages slowly. I've never experienced that, but then, I have a pretty fast connex to the internet.

---

### Post by skern03 on 2009-01-04
Any other suggestions?

Bump...

---

### Post by jnewl on 2009-01-19
I have the same problem. Every browser I've tried crashes (turns grey and refuses to respond) constantly and has to be restarted. It has something to do with page loading and scrolling, as one of those two things is always underway when the crash occurs. Sometimes the browser will recover after 10 or 15 seconds, but most of the time it either doesn't recover or is taking so long I just manually close it with the "X" button and restart. Also, it seems to get worse over time, with crashes only occurring sporadically when I first start using a new browser and then gradually getting to the point where they're almost constant. This has happened with Opera, Flock, and plain vanilla Firefox. I have not tried using any other browsers.

I've been using Ubuntu for about six months now and I love the OS, but this problem is really taking its toll on my patience.

---

### Post by fragos on 2009-01-19
Greying out seems to mean taking a long time to respond -- not necessarily a crash. When your system actualy comes back from the grey it may indicate a performance issue. Do you have lots of applications open? How much memeory do have? Is swap space being used? In a terminal session run "free". It will show how memory is being used. THe line "Swap:" will tell you if you're using swap space. The more swap you use the slower your system will be. I'd recommend increasing memory until swap space is rarely used. 1GB did it for me. The best memory performances comes when two memory sticks with the same specs are used. I've two 512KB. I also use a Epiphany which is a faster browser than Firefox.

---

### Post by skern03 on 2009-01-19
In my case, the browsers simply shut down and vanish. Firefox is the worst offender. I've also noticed when I use Firefox, sometimes my CPU utilization gradually increases to the point where the only cure is to reboot. Right now, I'm using Firefox, and it is relatively stable. Sometimes I use Seamonkey. I have far less crashes with Seamonkey than Firefox. I don't experience the greyed out windows. 

I also wonder if scripts on pages are causing it. I have four pages as my home "page." Ubunutu, Yahoo Mail, NASA's Astronomy Picture of the Day and weather for my area. 

I have 1.5 GB RAM, and a 2 GB swap space. The swap is barely used.

---

### Post by fragos on 2009-01-19
Web sites speeds vary greatly. Those with lots of background data processsing like gmail can be slower to start. Much of the web is poorly coded. In fact a study by Opera showed that less than 5% of sites pass HTML validation tests. Flash slows things down as will large images that aren't tuned for web display. My sites always come up fast because they are hand coded and carefully tuned for performance. Many sites use CMS, Content Management Systems, which make site maintainance simpler for the webmaster but may bloat the sites and add lots of background processing. When you have a site that performs poorly give yourself a baseline for comparison by accessing a well coded site. I for one am very curious to see how well Chrome performs once there is a version for Linux available. Fortunately there is a lot of work going on to improve the performance of javascript. Also the next release of Ubuntu will include the ext4 file system which will improve the performance of any system it's used on.

To improve my systems performance I've disabled system services that I don't use like Tracker. The more stuf that runs in the background the slower your system will be and the longer it will take to boot up.

---

### Post by skern03 on 2009-01-19
> **fragos said:**
> Web sites speeds vary greatly. Those with lots of background data processsing like gmail can be slower to start. Much of the web is poorly coded. In fact a study by Opera showed that less than 5% of sites pass HTML validation tests. Flash slows things down as will large images that aren't tuned for web display. My sites always come up fast because they are hand coded and carefully tuned for performance. Many sites use CMS, Content Management Systems, which make site maintainance simpler for the webmaster but may bloat the sites and add lots of background processing. When you have a site that performs poorly give yourself a baseline for comparison by accessing a well coded site. I for one am very curious to see how well Chrome performs once there is a version for Linux available. Fortunately there is a lot of work going on to improve the performance of javascript. Also the next release of Ubuntu will include the ext4 file system which will improve the performance of any system it's used on.

To improve my systems performance I've disabled system services that I don't use like Tracker. The more stuf that runs in the background the slower your system will be and the longer it will take to boot up.

For me, it is clearly not a performance issue. I'm not trying to be rude or disrespectful; your point is well taken and I agree with you. Performance is fine, and my CPU utilization clocks along at ~5-15%, and then Firefox or Seamonkey just disappears. Sometimes in the middle of a post.

---

### Post by jnewl on 2009-01-19
> **fragos said:**
> Greying out seems to mean taking a long time to respond -- not necessarily a crash. When your system actualy comes back from the grey it may indicate a performance issue. Do you have lots of applications open? How much memeory do have? Is swap space being used? In a terminal session run "free". It will show how memory is being used. THe line "Swap:" will tell you if you're using swap space. The more swap you use the slower your system will be. I'd recommend increasing memory until swap space is rarely used. 1GB did it for me. The best memory performances comes when two memory sticks with the same specs are used. I've two 512KB. I also use a Epiphany which is a faster browser than Firefox.

Thanks for your reply. Here are the results of "free":

             total       used       free     shared    buffers     cached
Mem:       2057284    1862272     195012          0     195368     848980
-/+ buffers/cache:     817924    1239360
Swap:      6040400       8492    6031908

I only have Opera, the default Text Editor and the dictionary open (in addition to any background processes, which are just the standard fare*). Opera hasn't crashed on me yet this session, but I know from past experience it soon will.

EDIT: My current CPU usage minus the System Monitor itself is 2%.

EDIT EDIT: After reading your response to the other poster, I'm becoming more and more convinced it might be the sites I'm visiting. There are a couple that it always seems to happen with, although they're not the only ones. But the frequency of it on those sites makes me suspicious. Presuming for the moment that that *is* the problem, what would you recommend I do?

---

### Post by skern03 on 2009-01-19
> **jnewl said:**
> 
...I'm becoming more and more convinced it might be the sites I'm visiting. There are a couple that it always seems to happen with, although they're not the only ones. But the frequency of it on those sites makes me suspicious. 

And the worst part of that is one of the most frequently visited sites for me is RIGHT HERE!  ;)

---

### Post by fragos on 2009-01-19
> **jnewl said:**
> Thanks for your reply. Here are the results of "free":

             total       used       free     shared    buffers     cached
Mem:       2057284    1862272     195012          0     195368     848980
-/+ buffers/cache:     817924    1239360
Swap:      6040400       8492    6031908

I only have Opera, the default Text Editor and the dictionary open (in addition to any background processes, which are just the standard fare*). Opera hasn't crashed on me yet this session, but I know from past experience it soon will.

EDIT: My current CPU usage minus the System Monitor itself is 2%.

EDIT EDIT: After reading your response to the other poster, I'm becoming more and more convinced it might be the sites I'm visiting. There are a couple that it always seems to happen with, although they're not the only ones. But the frequency of it on those sites makes me suspicious. Presuming for the moment that that *is* the problem, what would you recommend I do?

You have plenty of memory and not using hadly any swap at all. There's not a whole you can do about a poorly designed web site or one that has a lot of background database access. I have a well tuned but modest system. AMD Sempron 2800+, 1GB, FX5200. 7,200 RPM - 16MB cache hard disk. Chances are you have more machine than I do. I run Epiphany for my primary browser and get acceptable performance. Grey outs were common with Firefox 3 which was better than Firefox 2. I can't recall any browser greyouts with Epiphany. I get an occasional crash with Epiphany when closing a tab but it restarts quickly and resumes where it left off. I recommend you try Epiphany. I've got 6 different wbe browsers installed that I use to insure compatibility for the sites I develop. Epiphany used the same Gecko rendering engine as Firefox but has fewer available extensions. So users get extension crazy and run 30 or more. That extra bloat can cause problems.

---

### Post by fragos on 2009-01-19
This site isn't very fast and sees a lot of use which can slow things down further. It is hardly one of the slowest.

---

### Post by jnewl on 2009-01-19
> **fragos said:**
> You have plenty of memory and not using hadly any swap at all. There's not a whole you can do about a poorly designed web site or one that has a lot of background database access. I have a well tuned but modest system. AMD Sempron 2800+, 1GB, FX5200. 7,200 RPM - 16MB cache hard disk. Chances are you have more machine than I do. I run Epiphany for my primary browser and get acceptable performance. Grey outs were common with Firefox 3 which was better than Firefox 2. I can't recall any browser greyouts with Epiphany. I get an occasional crash with Epiphany when closing a tab but it restarts quickly and resumes where it left off. I recommend you try Epiphany. I've got 6 different wbe browsers installed that I use to insure compatibility for the sites I develop. Epiphany used the same Gecko rendering engine as Firefox but has fewer available extensions. So users get extension crazy and run 30 or more. That extra bloat can cause problems.

Thanks very much for your help. I'll install Epiphany and give it a go in the morning. I'll also try to remember to return here and report whether it was a success or not since that might be a help to others.

Thanks again!

EDIT:  I've installed Epiphany and used it all day. So far so good! I'm not a huge fan of the browser as it's very bare-bones, but hey, if it works I'll make do.

---

### Post by rumli on 2009-01-20
One things you might like to try:
1. Close Firefox.
2. Go to your home directory in Nautilus, press CTRL-H to see hidden files, and delete the ".mozilla" folder.  **Important warning**: This will delete all your Firefox user settings, extensions, cache, browser history, saved passwords, etc., so don't do this if you can't afford to lose that info.  I assume you're fine with that since you're ready to abandon Firefox for Epiphany.

Also do a "sudo apt-get update && sudo apt-get dist-upgrade" to update Firefox to the latest version.

---

### Post by CrusaderAD on 2009-01-20
I had the same exact problem. It was certainly associated with flash and or ubuntu restricted video codecs being installed. Uninstall these and see if it works.

---

### Post by skern03 on 2009-01-21
> **raptormanad said:**
> I had the same exact problem. It was certainly associated with flash and or ubuntu restricted video codecs being installed. Uninstall these and see if it works.

The only thing Ubuntu I have installed is the Ubuntu Extension, Firefox Modifications 0.6, which tags along for the ride.

As for Flash, I've disabled the Shockwave Flash plugin.

Any suggestions on replacements for the Shockwave plugin?

---

### Post by skern03 on 2009-01-21
What video cards are you folks using?

I have an ATI Radeon w/128 MB RAM if memory serves. Although there is a restricted driver available, I am not using it. Tried it once a month ago with poor results.

---

### Post by fragos on 2009-01-21
> **skern03 said:**
> The only thing Ubuntu I have installed is the Ubuntu Extension, Firefox Modifications 0.6, which tags along for the ride.

As for Flash, I've disabled the Shockwave Flash plugin.

Any suggestions on replacements for the Shockwave plugin?

The open source version of flash is the package "gnash" which you can install with Synaptic. I'm not sure which version of flash it's comporable to. I've no direct experience with it.

---

### Post by skern03 on 2009-01-21
> **fragos said:**
> The open source version of flash is the package "gnash" which you can install with Synaptic. I'm not sure which version of flash it's comporable to. I've no direct experience with it.

It's loaded... thanks for the tip!

---

### Post by skern03 on 2009-01-21
> **fragos said:**
> The open source version of flash is the package "gnash" which you can install with Synaptic. I'm not sure which version of flash it's comporable to. I've no direct experience with it.

Gnash doesn't render the Radar Map on weather.com. It loads the page part way, then says "Stopped." The frame is totally blank.

However, Firefox hasn't crashed in 1.5 hours, almost a record! :D

---

### Post by fragos on 2009-01-21
As one would expect, gnash will trail the features found in the latest release of flash -- now 10. If gnash is at flash ver 7 or 9 and a site uses features beyond that you may very well get the result you are. The radar image is a new one so perhaps it requires rev 10. Most sites standardize on older releases of flash to insure they're viewable by the largest number of users. It's not uncommon to find systems still running ver 7. I'll bet you won't have trouble with sites like Youtube and Google -- they know better. The radar comes from NOAA which is a government organization -- nuff said. Good luck with gnash. I've had no problems with flash and Epiphany so I'm at flash rev 10 and the radar images display for me.

---

### Post by skern03 on 2009-01-22
> **fragos said:**
> I've had no problems with flash and Epiphany so I'm at flash rev 10 and the radar images display for me.

Ditto w/Seamonkey, but some features in Seamonkey trail Firefox, or so it seems. So far, though Firefox hasn't crashed in 24 hours - I left it on all night just to see. Usually, it would have crashed, even without use.

---

### Post by grndslm on 2009-01-22
The problems are definitely flash related.

I'm still on 8.04, so things could be differently on 8.10.  I remember when 8.04 first came out, Firefox would always crash with many tabs open and opening just one flash site.  I upgraded to flash 10 beta, and the problems went away.  I have reinstalled 8.04 and deleted my .mozilla profile, but still have flash 9, and i haven't had a crash yet.

Deleting .mozilla works because as the program is updated, so do the config files... and if you've got an old config, you get no fix.

---

### Post by skern03 on 2009-01-22
Well so much for gnash and no crash. Right after I posted 24 hours crash-free, my entire system locked up while using Firefox. Had to use the freak'n switch to restart. :mad:

---

### Post by skern03 on 2009-01-22
> **grndslm said:**
> The problems are definitely flash related.

I'm still on 8.04, so things could be differently on 8.10.  I remember when 8.04 first came out, Firefox would always crash with many tabs open and opening just one flash site.  I upgraded to flash 10 beta, and the problems went away.  I have reinstalled 8.04 and deleted my .mozilla profile, but still have flash 9, and i haven't had a crash yet.

Deleting .mozilla works because as the program is updated, so do the config files... and if you've got an old config, you get no fix.

Here's what I've run in the past... not sure if it deletes ./mozilla:
```
sudo killall -9 -r firefox
sudo apt-get purge firefox firefox-3.0 ubufox
sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support
```

---

### Post by skern03 on 2009-01-25
> **fragos said:**
> I switched to Epiphany. It has the occassional crash when I close a tab but it is so much faster restarting than Firefox That I don't find the crash as objectionable. Epiphany will also allow you to install with webkit. I've both webkit and gecko versions installed.

Installed Epiphany today. Some concerns:
[LIST]
[*]You can't bookmark multiple tabs as the homepage.
[*]You can't install bookmarks in a bookmark bar under the menu system.
[*]If you open a new tab, it opens the home page, not a blank tab (seems a waste of resources to me).
[/LIST]
Hasn't crashed yet, but the day is still young! :)

---

### Post by fragos on 2009-01-25
> **skern03 said:**
> Installed Epiphany today. Some concerns:
[LIST]
[*]You can't bookmark multiple tabs as the homepage.
[*]You can't install bookmarks in a bookmark bar under the menu system.
[*]If you open a new tab, it opens the home page, not a blank tab (seems a waste of resources to me).
[/LIST]
Hasn't crashed yet, but the day is still young! :)

Your 1 & 3 don't bother me because I leave my home page blank favoring performance and the fact I open many blank tabs for doing searches. Your #2 is a disappointment to me as well -- the tree structure is much more efficient for locating bookmarks. My workaround is to name the topic so that in sort order subtopics follow the main topic.

/home/fragos/.gnome2/epiphany/bookmarks.rdf is where bookmarks are stored. Rdf files are XML which means there are subject to manual editing. The question I have is there a markup for subtopics? And of course what would Epiphany do with it? I've not yet checked to see if there's a feature request registered for sub-topics.

---

### Post by skern03 on 2009-01-25
> **fragos said:**
> Your 1 & 3 don't bother me because I leave my home page blank favoring performance and the fact I open many blank tabs for doing searches. Your #2 is a disappointment to me as well -- the tree structure is much more efficient for locating bookmarks. My workaround is to name the topic so that in sort order subtopics follow the main topic.

/home/fragos/.gnome2/epiphany/bookmarks.rdf is where bookmarks are stored. Rdf files are XML which means there are subject to manual editing. The question I have is there a markup for subtopics? And of course what would Epiphany do with it? I've not yet checked to see if there's a feature request registered for sub-topics.

Another thing in Epiphany's favor -- it seems to consume far less resources than Firefox. Firefox (at least in Ubuntu 8.10) is a glutton. As soon as I launch, it often spikes CPU utlization way high, where it stays. When I check the running processes, Python is cranked up pretty high with multiple threads. Sometimes it doesn't release the threads, and the CPU utilzation stays high. The only fix is a restart.

In Firefox's defense, it is likely to be Flash, but still, the plugin should function a tad better. :(

I don't remember this in earlier versions of Ubuntu/Firefox.

---

### Post by skern03 on 2009-01-25
> **fragos said:**
> Your 1 & 3 don't bother me because I leave my home page blank favoring performance and the fact I open many blank tabs for doing searches. Your #2 is a disappointment to me as well...

Here's another - you can't set a preference to open links in a new tab. It opens a new instance of Epiphany.

---

