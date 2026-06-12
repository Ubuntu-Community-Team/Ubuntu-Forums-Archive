---
title: "Is Firefox slow for anyone?"
date: 2010-09-25
forum: Desktop Environments
---

### Post by ildella on 2010-09-25
Hi. 

In my experience since many years and ubuntu and firefox version, I have always found that the browser is slow. I am not referring here to web page rendering or javascript performance, I am talking about GUI responsivness. 

I know is a general linux desktop problem but now that there is chrome, I see how this problem lays somewhere in the Firefox stack. 

You see that while moving between tabs: opening, closing, switching... you have a neat perception of slowness and unresponsiveness. And the more tab you open, the more it gets slow. 

Same operations in chrome are a breeze. So now I am wondering why. I'd like to help at least in identifying the problem. 

Any of you notice the same slowness and unresponsiveness in Firefox GUI compared to Chrome?

---

### Post by Frogs Hair on 2010-09-25
I use FF beta 4 and Namoroka and don't notice any drag in the GUI function . I also have Opera on a different OS and there no question about which is faster when it comes to browsing . Post your hardware specs , that may shed some light on the matter.

---

### Post by roggenschrotbrot on 2010-09-25
firefox3 is quite bloated, even without loaded addons. thats supposed to change with ff4. i'd love to switch to midori or an other lightweight browser, if it had something like the firefox "mouseless browsing" addon.

---

### Post by theozzlives on 2010-09-25
I just switched to Chrome this morning. There's no doubt about it, Chrome is indeed faster. I put it on both my Linux boxes and my "7" box.

---

### Post by ildella on 2010-09-25
Dell XPS 1530, nvidia 8600M GT running on a Intel Core 2 Duo T7250  @ 2.00GHz
I think the problems relay in the nvidia drivers that perform bad on some operations. Anyway, Chrome does not suffer for this so probably is some libraries that Firefox uses and Chrome doesn't, I think at the GTK level or even under say cairo... no real idea, would like to know about a test to perform to dig into the problem.

---

### Post by theozzlives on 2010-09-25
> **ildella said:**
> Dell XPS 1530, nvidia 8600M GT running on a Intel Core 2 Duo T7250  @ 2.00GHz
I think the problems relay in the nvidia drivers that perform bad on some operations. Anyway, Chrome does not suffer for this so probably is some libraries that Firefox uses and Chrome doesn't, I think at the GTK level or even under say cairo... no real idea, would like to know about a test to perform to dig into the problem.

As far as FF is concerned, I don't think nVidia is the problem. My laptop uses an Intel GPU.

---

### Post by lovinglinux on 2010-09-25
IMO you can't really compare the two browsers, because Chrome doesn't have a fraction of Firefox features and interface customization capabilities. If Chrome was in the same level as Firefox in regard to these aspects, it wouldn't be as snappy.

I'm currently using Firefox 4, which is really great and far superior than Chrome but Firefox 3.6 was fast enough for me too.  I usually have more than 60 extensions installed and I don't have performance issues, even considering my hardware is not that good. My GPU is an old nVidia 7300 GT and I have a Core2 Duo. 

Anyway, if you compare both browsers using a clean user profile you will see there isn't any perceptible difference. IMO what makes the browser slow are the user profiles, mainly because slow extensions, sub-optimal settings and bloated databases. If you have the habit of saving, moving and deleting many bookmarks for example, your *places.sqlite* can become filled with left-overs and unless you vacuum the database frequently, it can slow down several things, like typing an address in the awesome bar.

In regard to opening several tabs, is probably your hardware that can't handle too  many tabs. Have you tried to open the same number of tabs with the same pages on both browsers to see the difference?

---

### Post by perspectoff on 2010-09-25
Yeah, only in recent versions.

Chromium doesn't have many of the add-ons I like for Firefox.

Konqueror for KDE (Kubuntu) does, and it is faster than Firefox, too. It is based on the same Gecko engine but apparently hasn't had all the recent bloat that Firefox has been getting since 3.5 and later.

But, to be perfectly honest, website availability on the Internet is still 99% of slowdowns on the Internet, and the browser delays are relatively insignificant in comparison. Google (highest website availability) always loads instantly for me, even in Firefox 3.6.

---

### Post by ildella on 2010-09-25
Yes I can work on chrome without performance degradation as many tabs I open while firefox suffers with more than 6-7 tabs on screen. 
Generally, Chrome opens/close/switch is smooth in firefox quicly becomes slow. 

I have a clean profile with last FF4, merged all the preferences with Sync and installed just diigo and feedly on both browser and still the responsiveness in firefox is worst compared to chrome. 

I do not keep almost any bookmark in general. 

I also see som javascript issue in the latest builds: feedly is not as smart as usual and Twimbow is almost non usable in FF while super-fast in chrome. 

I see that FF use a lot the disc while chrome does not. I can note the different when sometime I run the browsers from an OS running on a USB key. Chrome does not use the disk so does not suffer from USB 2.0 limitations. 

I can try to disable disk cache or something else, but as a matter of fact, user experience chrome offers is of a faster and more fast and responsive UI, web rendering and javascript pereformance.

---

### Post by tlu on 2010-09-25
In order to speed up Firefox I recommend to consult these sites:

[http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)
[http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html)
[http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)

Moreover, if you look at [http://arewefastyet.com/?machine=5](http://arewefastyet.com/?machine=5) which compares the speed of the javascript engines of Firefox 4 with the Apple and Chrome ones you'll see that with the combination of the traditional JIT and the new JaegerMonkey JIT FF4 is coming very close to its competitors lately. The speed advantage of Chrome is becoming smaller and smaller :)

---

### Post by ildella on 2010-09-25
> **tlu said:**
> In order to speed up Firefox I recommend to consult these sites:

[http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)
[http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html)
[http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)

Moreover, if you look at [http://arewefastyet.com/?machine=5](http://arewefastyet.com/?machine=5) which compares the speed of the javascript engines of Firefox 4 with the Apple and Chrome ones you'll see that with the combination of the traditional JIT and the new JaegerMonkey JIT FF4 is coming very close to its competitors lately. The speed advantage of Chrome is becoming smaller and smaller :)

Thanks for the tutorial, I'll follow them 
I follow Are We Fast Yet daily :) Benchmark can be helpful but despite that ones, I experience some really slow jaavascript webapp on FF that are super fast on chrome. 

We'll see the final FF4...

---

### Post by lovinglinux on 2010-09-25
> **ildella said:**
> Yes I can work on chrome without performance degradation as many tabs I open while firefox suffers with more than 6-7 tabs on screen. 
Generally, Chrome opens/close/switch is smooth in firefox quicly becomes slow. 

I have a clean profile with last FF4, merged all the preferences with Sync and installed just diigo and feedly on both browser and still the responsiveness in firefox is worst compared to chrome. 

I do not keep almost any bookmark in general. 

I also see som javascript issue in the latest builds: feedly is not as smart as usual and Twimbow is almost non usable in FF while super-fast in chrome. 

I see that FF use a lot the disc while chrome does not. I can note the different when sometime I run the browsers from an OS running on a USB key. Chrome does not use the disk so does not suffer from USB 2.0 limitations. 

I can try to disable disk cache or something else, but as a matter of fact, user experience chrome offers is of a faster and more fast and responsive UI, web rendering and javascript pereformance.

For the sake of curiosity I just opened 50 random tabs from my bookmarks. There is no delay whatsoever when switching, dragging, opening or closing tabs. There must be something wrong on your end.

Have you noticed the CPU usage during the lag?

---

### Post by Dr. C on 2010-09-27
One suggestion to speed up Firefox, if running flash, is to install the [Better Privacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/") plug in and get rid of those LSOs or "Flash Cookies". The performance improvement especially on Firefox startup can be very significant.

---

### Post by sidzen on 2010-09-27
> **tlu said:**
> In order to speed up Firefox I recommend to consult these sites:

[http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)
[http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html)
[http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)

Moreover, if you look at [http://arewefastyet.com/?machine=5](http://arewefastyet.com/?machine=5) which compares the speed of the javascript engines of Firefox 4 with the Apple and Chrome ones you'll see that with the combination of the traditional JIT and the new JaegerMonkey JIT FF4 is coming very close to its competitors lately. The speed advantage of Chrome is becoming smaller and smaller :)

THANKS, ildella.  Better than the one I had -- [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by Banned. on 2010-09-27
Actually, I think it is slower. That is why I am using chrome.

---

### Post by Andrew.Z on 2010-09-28
> **FineE said:**
> One suggestion to speed up Firefox, if running flash, is to install the Better Privacy plug in and get rid of those LSOs or "Flash Cookies". The performance improvement especially on Firefox startup can be very significant.

Personally I haven't noticed a performance improvement, but if you like to  to delete things, try [BleachBit](http://bleachbit.sourceforge.net/) which has many options, such as deleting DOM Storage ("HTML5 cookies") for Firefox (since version [0.8.1](http://bleachbit.sourceforge.net/news/test-bleachbit-081-beta)), Adobe Flash cache, etc.  The only thing I noticed which makes Firefox faster is vacuuming the SQLite databases: if you haven't done it in a while, it can make a big difference.

There's an old version of BleachBit available through 'apt-get install bleachbit' or a new .deb on the web site above.

---

### Post by ildella on 2010-09-29
It was a problem related to nvidia drivers. Today, tired, I installed latest beta 260 series and the computer is like new. All the visual defects are gone, compiz animations are smoother, everything generally faster (editing large text files) and the annoying "gpu alwasy at maximum clock" issue is gone. 

I almost have a new laptop now... quite sad I also order a new one just today. Today I hate nvidia for delivering bad drivers which make the laptop works under it's real performance for years. New laptop has the intel HD integrated chipset :)

---

### Post by Dustin2128 on 2010-09-29
test the minefield build, much faster than 3.6

---

### Post by ildella on 2010-09-29
I am using minefield since a couple of month and is indeed faster but the awful nvidia drivers slow everything down. Till yesterday... :)

---

### Post by Dustin2128 on 2010-09-29
> **ildella said:**
> I am using minefield since a couple of month and is indeed faster but the awful nvidia drivers slow everything down. Till yesterday... :)
nvidia drivers slowed it down? Please explain.

---

### Post by ildella on 2010-09-29
Generally speaking, they have lot of problems: rendering, speed, but nothing too much annoying. But the Powermizer is buggy. Connected to an external monitor it *always* go at maxmimum clock, GPU go 90 celsius and then everything slow down. When using the laptop monitor, this behavior is less frequent but present.  
The last release resolve this problem and that is half of the issue. Generally all animations are now smoother and the gui a lot more responsive. This is the first driver version that works really good since three years.

---

### Post by Dustin2128 on 2010-09-29
> **ildella said:**
> Generally speaking, they have lot of problems: rendering, speed, but nothing too much annoying. But the Powermizer is buggy. Connected to an external monitor it *always* go at maxmimum clock, GPU go 90 celsius and then everything slow down. When using the laptop monitor, this behavior is less frequent but present.  
The last release resolve this problem and that is half of the issue. Generally all animations are now smoother and the gui a lot more responsive. This is the first driver version that works really good since three years.
that's strange, I've always bought geforce cards precisely because they ran well with linux. Do you download drivers from the repos or the nvidia site?

---

### Post by lovinglinux on 2010-09-30
> **ildella said:**
> It was a problem related to nvidia drivers. Today, tired, I installed latest beta 260 series and the computer is like new. All the visual defects are gone, compiz animations are smoother, everything generally faster (editing large text files) and the annoying "gpu alwasy at maximum clock" issue is gone. 

I almost have a new laptop now... quite sad I also order a new one just today. Today I hate nvidia for delivering bad drivers which make the laptop works under it's real performance for years. New laptop has the intel HD integrated chipset :)

I just installed the 260 driver using [ubuntu-x-swat]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates") ppa. I also feel like using a new machine. Everything starts faster and runs smoother. Amazing. I can even watch YouTube while running Windows 7 on a VM and spin the cube without a glitch. Application starts faster and close faster too.

My system performance wasn't bad before this upgrade, but is wasn't smooth as it was with some older kernel.

---

### Post by ildella on 2010-09-30
I installed it from the repo, always. 

Like lovinglinux said, today at work my machine is new. Eclipse and Firefox seems twice as faster and reactive, while before were sloppy. I am so disappointed today: I had this laptop since 30 months and now is faster to me then when it was brand new. And I have a new one on the way I do not need that much now...

---

### Post by lovinglinux on 2010-09-30
> **ildella said:**
> I installed it from the repo, always. 

Like lovinglinux said, today at work my machine is new. Eclipse and Firefox seems twice as faster and reactive, while before were sloppy. I am so disappointed today: I had this laptop since 30 months and now is faster to me then when it was brand new. And I have a new one on the way I do not need that much now...

I'm about to install the driver on a low-end laptop we have here. I wonder if it will make some miracle...:)

---

### Post by searchfgold6789 on 2010-09-30
It seems to me as if Firefox is focused on ease of use and safety, not speed.

---

### Post by tlu on 2010-09-30
> **searchfgold6789 said:**
> It seems to me as if Firefox is focused on ease of use and safety, not speed.

What makes you think so? Okay, it's probably true for FF 3.6 (although its speed can be optimized with the recommendations in the links of post #10) but obviously no longer for FF 4.0 - see the violet line in [http://arewefastyet.com/?machine=4](http://arewefastyet.com/?machine=4)

Besides, ildella's problem was caused by the nvidia graphics driver.

---

### Post by SeijiSensei on 2010-09-30
As an AdBlock Plus user, I've found that many commercial sites load much more slowly these days because of the large number of ads, tracking scripts, and other junk they include.  Often there can be a lag of ten to twenty seconds while I wait for various requests to the doubleclick.net's of the world to time out.  Things were better when ads were simply objects that could be blocked.  Embedded scripting has made things much worse since the display of the rest of the page often depends on the script either returning an object or timing out.  

It's almost made me willing to turn off ABP and see all the crap again. Almost...

---

### Post by NightwishFan on 2010-09-30
Firefox oddly enough has always worked fantastically for me even though Webkit blows it out of the water on the Sunspider test.

---

### Post by lovinglinux on 2010-09-30
> **searchfgold6789 said:**
> It seems to me as if Firefox is focused on ease of use and safety, not speed.

Mozilla has been improving Firefox speed on every new major release. When Firefox 3.5 was released, there was a huge improvement over Firefox 3.0 in terms of performance. Firefox 3.6 improved performance by 20% over 3.5 and Firefox 4 is 3 times faster than Firefox 3.0.

Now with the competition with Google, Mozilla is attacking performance issues more aggressively. Is a cat and mouse game.

---

### Post by tlu on 2010-09-30
> **SeijiSensei said:**
> 
It's almost made me willing to turn off ABP and see all the crap again. Almost...

Interesting! This contradicts my observations: With ABP enabled most sites load faster.

---

### Post by lovinglinux on 2010-09-30
> **tlu said:**
> Interesting! This contradicts my observations: With ABP enabled most sites load faster.

Sometimes I get problems with some web sites due to ABP, but they are not common and tend to go away with the extension updates.

---

### Post by msakms on 2010-09-30
I've moved to Chromium web browser for the exact "slow response" reason on firefox. May be I'll try FF new release when it's out to see if it gets any faster. All in all, FF is way better when it comes to managing your bookmarks, tabs, mail plugins and so.

---

### Post by tlu on 2010-10-01
> **lovinglinux said:**
> Sometimes I get problems with some web sites due to ABP, but they are not common and tend to go away with the extension updates.

And since Wladimir Palant is now able to do [full-time development]("http://adblockplus.org/blog/important-changes-coming-to-the-adblock-plus-project") of ABP we should expect further improvements.

---

### Post by lovinglinux on 2010-10-01
> **tlu said:**
> And since Wladimir Palant is now able to do [full-time development]("http://adblockplus.org/blog/important-changes-coming-to-the-adblock-plus-project") of ABP we should expect further improvements.

That's great news. Thanks for sharing.

---

### Post by tlu on 2010-10-02
> **lovinglinux said:**
> That's great news. Thanks for sharing.

You're welcome! As a matter of fact there seem to be very significant speed improvements ahead - see for details [https://adblockplus.org/forum/viewtopic.php?t=6118](https://adblockplus.org/forum/viewtopic.php?t=6118)

BTW: Thanks for your tutorials - they are really great!

---

### Post by lovinglinux on 2010-10-02
> **tlu said:**
> BTW: Thanks for your tutorials - they are really great!

You are welcome and thanks for the comment.

---

### Post by skoope on 2010-10-02
I found Firefox runs slower in Ubuntu 10 than Vista64 on same PC.... especially uploading and downloading...... why so??? Is it my Ubuntu amd64 or Firefox is the problem??

---

### Post by lovinglinux on 2010-10-02
> **skoope said:**
> I found Firefox runs slower in Ubuntu 10 than Vista64 on same PC.... especially uploading and downloading...... why so??? Is it my Ubuntu amd64 or Firefox is the problem??

Please keep in mind the OP is talking about interface responsiveness and not download/upload speed.

About your speed issues, there is not enough info to determine the source of the problem. Have you tested other browsers in both OSs?

---

### Post by Navyblue on 2010-10-14
I have FireFox 3.6 on both 32bit Vista and 64bit Ubuntu on the same machine, scrolling is significantly smoother on Vista eventhough it is 32bit. If we bring Flash into the picture there is no comparison. Is FireFox badly compiled on Ubuntu or is it a case of bad Intel graphic driver? I just came back after a long break from Linux and am rather disappointed.

---

### Post by NightwishFan on 2010-10-14
I find smooth scrolling does not like me however flash seems to work great here. Intel Series 4 Mobile.

---

### Post by lovinglinux on 2010-10-14
> **Navyblue said:**
> I have FireFox 3.6 on both 32bit Vista and 64bit Ubuntu on the same machine, scrolling is significantly smoother on Vista eventhough it is 32bit. If we bring Flash into the picture there is no comparison. Is FireFox badly compiled on Ubuntu or is it a case of bad Intel graphic driver? I just came back after a long break from Linux and am rather disappointed.

Is the graphic driver.

---

### Post by boboro on 2010-11-14
Hi all,

I used to have this problem in Maverick as well. But not anymore after I follow the tip from here: [http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)

I'm not sure why we should disable IPv6, but increase pipelining sounds make sense to me.

Regards,
boboro

---

### Post by sandman3838 on 2011-03-24
I just tried Firefox 4 with some tweaking that suggestions that I found here and other places on the Web and I still can't beat the speed of SWIFTFOX!

Now Firefox 4 in Windows 7 is a whole different ballgame, that Windows version is just as fast as SWIFTFOX in Ubuntu 1104 .......... perhaps faster!  Why?

With Ubuntu I'm sticking with Swiftfox.

---

### Post by mikewhatever on 2011-03-24
Necromancing?

---

### Post by tlu on 2011-03-25
> **sandman3838 said:**
> I just tried Firefox 4 with some tweaking that suggestions that I found here and other places on the Web and I still can't beat the speed of SWIFTFOX!

Did you try FF 4 with a new profile? It's possible that the (old) profile you're using is causing problems - this was the case on my machine. With the new profile FF 4 is very fast here and definitely much faster than FF 3.6.

> Now Firefox 4 in Windows 7 is a whole different ballgame, that Windows version is just as fast as SWIFTFOX in Ubuntu 1104 .......... perhaps faster!  Why?

Under Linux hardware acceleration is not yet supported. It will come in a future version.

---

### Post by VanillaMozilla on 2011-03-25
My gosh, there's a lot of bad advice here.  I don't see any useful help so far.  EDIT:  the previous post, #46 got it right.  Don't fall for stupid tweaks like pipelining.  That has NOTHING to do with your problem, and is not even generally advisable.

You shouldn't have any problems with Firefox on that computer.  Usually, performance problems are because of user modifications or additions (i.e., themes, extensions, and maybe funny user settings).  Sometimes plugins could be a culprit if they are hogging CPU time.

Try starting in safe mode (do NOT make changes permanent!!), or if that fails, create a new profile for testing (do NOT delete the old one!!) to get yourself a totally default configuration.  The following link describes these, but also has a lot of other detailed half measures if you are detail oriented.  Myself, I just use the industrial-strength option (new profile, which takes about a minute).
[http://kb.mozillazine.org/Standard_diagnostic_%28Firefox%29](http://kb.mozillazine.org/Standard_diagnostic_%28Firefox%29)

And ah, yes, I almost forgot, Flash and JavaScript.  Flash and JavaScript are sometimes used by Web sites for the sole purpose of churning your CPU, making the fan come on, and annoying you with flashy effects instead of content.  Sometimes the scripts do nothing at all except slow down everything.  If that's the case, it's easy to block either or both.  The NoScript extension is one way (I rarely recommend extensions, but this one does what it's supposed to at low cost), but there are others.

If you still have problems, try either
[www.mozillazine.org](www.mozillazine.org) or
support.mozilla.org .

---

### Post by mr_niceguy on 2011-11-21
> **lovinglinux said:**
> Is the graphic driver.

^This is true for many people with NVidia cards.

If you install the binary NVidia driver you need to also remove the nouveau driver. (Could this step be automated in the future?)

```
sudo apt-get remove xserver-xorg-video-nouveau
```

---

### Post by lovinglinux on 2011-11-24
The Walking Thread is back.

Closing it.

---

