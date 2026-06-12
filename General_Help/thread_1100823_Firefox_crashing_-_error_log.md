---
title: "Firefox crashing - error log?"
date: 2009-03-19
forum: General Help
---

### Post by retrodans on 2009-03-19
My firefox seems to crash irregularly, and it is making my ubuntu installation frustrating, and unusable.  I am unsure as to why it crashes, I have installed the firefox plugin 'flashblock' so flash doesn't get rendered, but it still crashes.  There doesn't seem to be an obvious pattern to the crashes, so am unsure where to start with working out the problem.

If anyone has had similar problems that would be great, or just an idea on where to get some form of firefox error log would be great.

Thankyou,
Dan

---

### Post by prince_niceguy on 2009-03-19
try disabling the addon, that should avoid the crashing for the time being. i have adblock installed, which basically blocks flash ads, scripts, divs etc etc. if it is sufficient for your use then you can install that, it has not crashed on me so far.

---

### Post by retrodans on 2009-03-19
Sadly that didn't solve the problem.  I have had the problem for a while and installed flash block as one of the suggested issues was that flash has issues in ubuntu.

---

### Post by prince_niceguy on 2009-03-19
try renaming your firefox profile and start from scratch with a blank profile and see if it helps installing only adblock and no flashblock.

---

### Post by retrodans on 2009-03-20
I created a new profile, and added the ad blocker addon, sadly it still seems firefox crashes.  It just closes itself down all of a sudden sometimes, with no alert messages or anything.

---

### Post by prince_niceguy on 2009-03-20
have you tried reinstalling firefox after completely removing it in synaptic?

---

### Post by retrodans on 2009-03-20
Have just done that, and it still seems to either close or grey screen me.  It appears to not just be firefox either, I installed epiphany, and seem to have the same problem.

---

### Post by prince_niceguy on 2009-03-20
install epiphany-webkit and remove gecko engine, lets see if it resolves the epiphany issue, if yes then there is some gecko related issue... which version of firefox is getting installed ??

---

### Post by retrodans on 2009-03-20
I installed epiphany-webkit and removed epiphany-gecko

Sadly it then closed unexpectantly after only a short while browsing.

I went into help in epiphany to check it was using web-kit and it said

"Lets you view web pages and find information on the Internet.
Powered by WebKit"

---

### Post by prince_niceguy on 2009-03-20
am not sure where the issue is. are you trying any speicific site which is causing this issue? does these site contian flash objects?

are you having desktop effects on? if yes, can you try removing the effects and see if it is owrking or not.

---

### Post by retrodans on 2009-03-21
I did have desktop effects on, I have now disabled this.  It didn't solve the problem.  I then proceeded to disable javascript, which seemed to solve the issue, but made a lot of pages unusable (especially as I am a web developer and need to test javascript).

I am thinking it is still flash causing the problem, how to I completely uninstall flash from the computer altogether?  I am unsure which version I have, and just want to remove it all and see how that goes for a while.

It seems to happen on a variety of sites, and when I had flash blocker installed, but blocker has to be aware it's flash first, which may be where the problem is occurring.

---

### Post by prince_niceguy on 2009-03-21
try removing flashplugin-nonfree from the synaptic, then enable javascript and see if it works.

---

### Post by retrodans on 2009-03-21
Sadly that installation isn't there, I believe, whilst following a solution on a different post I was told to uninstall this, and install a different plugin for flash.  So I may have to go back and find out what this plugin was, when I just search for flash in synaptic, it doesn't find anything though.

---

### Post by retrodans on 2009-04-01
After reinstalling firefox and flash, I still have the problem with it all.  It still appears to happen more often on google maps and hotmail, but not always.  I am yet to find something that definately causes the crash.

I read that if I run firefox through terminal, I should get more information, but all it says is that firefox unexpectedly terminated, so not a lot of information there.

I am thinking it could be flash banners and the like at the moment.

---

### Post by wizardStan on 2009-04-06
I am having the same problem, with certainty that it isn't flash.  I removed the flash plugin the first time the problem occurred for me and was still able to reproduce.  Same symptom: Firefox just closes totally unceremoniously.
It usually triggers when opening a lot of tabs.  I have about 50 webcomics in my bookmarks, and every morning I just select "Open All in tabs" and wait for them all to open.  Once all 50 or so are open and I start reading is when it crashes.  I'll read one, move to the next, read that one, click the next tab, read, next tab, etc...  Occasionally, clicking the next tab will cause Firefox to freeze for about a second or two, and then the whole thing closes.  It also happens at other times with fewer tabs, but after opening so many tabs at once is the most common.  It could be a memory thing, or simply increasing the odds by having more tabs. (To qualify that, the odds of rolling a natural 20 goes up if you use more dice, for example)
This is in Ubuntu Ibex 64.  Is there maybe a way to get it to produce a dump file when it crashes?  Maybe that might be useful to see what exactly it was doing when it decided to close.

---

### Post by JasonDFR on 2009-04-10
I have had the same problem before. Firefox closing unexpectedly. It was happening a lot when I tried to load Gmail, but not exclusively with the Gmail. I have no idea what caused this.

I have tried all the suggestions previously mentioned in this thread. Nothing worked.

I have done a clean install of Ubuntu since then and haven't had the *same* problem since.

I'm on Ubuntu 9.04 beta. Today I ran apt-get upgrade. This may or may not have anything to do with the following firefox problem.

Now, when I open a new tab File, New Tab, or CTRL-T, the new blank tab opens and immediately after firefox shuts down. Same thing as before, except now I can identify a specific action that causes firefox to close.

Ideas?

---

### Post by retrodans on 2009-04-12
Sadly I still have no new information on what is happening with this.  I still get the issue with it.  Mostyle on google maps and hotmail, it is, in my opinion, a serious problem, it happens on several browsers, and can make using the internet impossible, so I have had to start logging into Vista dual boot instead, which isn't great tbh.  Any ideas would be most gratefully accepted.

Dan

---

### Post by Rackstar on 2009-04-12
Hey,

I have the exact same issues, I have tried everything. Flashblock, new profile, removing flash, reinstalling firefox, ... As disabling javascript is no option for me (Also a webdeveloper) I did not do that. I was even that despared that I reinstalled ubuntu 8.10.

I have read about people saying "Run firefox in debug mode" but I really can't seem to figure this out.

Have you filed a bug report yet? I will certainly confirm it.

Also my Thunderbird crashes irregular, just closes with no warning, when just in background, or when making a new mail. I don't know if they are related, but they are both mozilla products.

This is a real pain in the *** for user experience, as email and browsing are fundamental for any OS. Really humiliating when I try to show a site to my girlfriend and it just crashes on me, or worse, crashes when performing a payment online (happened once).

If anybody wants to help, really please do so. I'm sooo despared, it has been months.

---

### Post by retrodans on 2009-04-12
Hi Rackstar, I haven't filed a bug report yet, I haven't done that before, should it be raised with Ubuntu or mozilla bug?  I will then do so, as it seems this isn't a common problem, or a mistake on my behalf now, as several of us are having the same (or similar) issue.

Dan

---

### Post by Rackstar on 2009-04-12
Hi retrodans.

I had some good experiences with Ubuntu bugreport:
[http://www.ubuntu.com/community/reportproblem](http://www.ubuntu.com/community/reportproblem)

Before you file a bug report always check that website for similar bugreports, and confirm it. (The more people that confirm, the more attention it gets)

I never used the mozilla bug thing. I have been googling around. And it might just be a samba problem. Are you using Ubuntu 8.10? This came with a Samba upgrade.

See this post:
[http://forums.mozillazine.org/viewtopic.php?p=6016775#p6016775](http://forums.mozillazine.org/viewtopic.php?p=6016775#p6016775)

They say something about disabling something in samba. But I really don't get it. I'll try to look further.

---

### Post by Rackstar on 2009-04-12
Mother mary, I think we may have a solution!

The thing they said in the topic in my last post, was disabling WINS resolution in samba.

```
sudo nano /etc/nsswitch.conf
```

Look for something like:
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```
and remove wins out of the list like this

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

I remember that I had put wins there to get my network HDD going. But I stopped using it, since it made more problems than it solved them. (only allowing fat32, ...)

But this still is a quite big problem in samba if this is true. Because putting wins in this list makes it possible to use the name of windows computers to make connection, or something. I may need it in the future.

I did some heavy browsing (opening couple of 50 websites, mostly news/tv websites, and social networks, because they gave the most problems) and it holds. Same for thunderbird. (Also Evolution crasht like thunderbird in the past, that was my first reason to switch to thunderbird).

Let's hope everything holds. If so, I'll be one lucky man.

---

### Post by Rackstar on 2009-04-12
Let me know if this solved your problem.

I made a blogpost about it:
[http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/](http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/)

---

### Post by retrodans on 2009-04-13
So far so good, thankyou ever so much.  I will continue to test, and see if it reoccurs again at some point.  But this looks to have solved the problem, hopefully this wont be an issue in the next release.

Cheers,
Dan

---

### Post by Rackstar on 2009-04-13
It was a pleasure, your case helped me find what was wrong with mine.
Hope this helps other people too. 

I don't think it will be much of a problem in the future, because I read the bug has been accepted by samba, so probably will be fixed in the next release.

---

### Post by wizardStan on 2009-04-15
Unfortunately I don't have WINS in my nsswitch.conf file and I'm still getting the unknown crash.  It is much more rare, however.  I wonder if it's something akin to an out of memory error.
Why hasn't the original question been answered: is there somewhere that Firefox will (or can be made to) dump error logs to?

---

### Post by retrodans on 2009-04-16
I'm not sure there is a way, I have been trying to find out,  but to no avail.  I was told to try opening firefox using the terminal, as when it crashes a little information is given as to why.  I was just told terminated, but if it's an out of memory error you are trying to confirm, maybe it will tell you more.

Dan

---

### Post by GnuGuy on 2009-04-16
> **wizardStan said:**
> Unfortunately I don't have WINS in my nsswitch.conf file and I'm still getting the unknown crash.  It is much more rare, however.  I wonder if it's something akin to an out of memory error.
Why hasn't the original question been answered: is there somewhere that Firefox will (or can be made to) dump error logs to?

I do not have wins in my nsswitch.conf either. Does this sound familiar to you? [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/362150](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/362150) also could you close firefox entirely, and run the command "firefox" from the terminal and paste the result when firefox crashes? If you can't get to the terminal because of the crash then you can press "ctrl+alt+F3" and login and type killall firefox and then return to your main gui (ctrl+alt+F7) you may already know that though.

---

### Post by Rackstar on 2009-04-16
There is a way to open firefox in debug mode.

If you open terminal and run firefox with "firefox --debug" or "firefox -g" it shows more information.

But I did not really understand how this worked. It also needs a package called gdb, but you should get more information from someone more experienced. But maybe this sets you off in a right direction.

If you google around, you will find ways to debug firefox, but it's not always that easy. 

There is also a sort of checklist you could try do before you start debugging: Check if it really is a firefox fault. Try installing other browsers and check if they fail also.

---

### Post by wizardStan on 2009-04-18
Ahah!
Does this error make sense to anybody?

The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 42977223 error_code 14 request_code 155 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by dazzlindonna on 2009-04-18
This has been happening to me for the last few days, and I've narrowed it down (for me) to javascript issues.  If I turn off javascript, the problem goes away.  Turn it back on, and certain web pages with some sort of javascript on them will close FF down.

I don't yet know if it's a particular javascript function or what, yet.  But for me, it's definitely js related.

P.S. removing wins from samba did not help my problem.

One other thing: widgetbox.com is a perfect example of a page that will shut FF down if I have js turned on, but loads fine if js is off.  

Other info that may be useful: Running Ubuntu 8.10 (64 bit) and FF 3.0.8 on a modern box with 3 gigs ram.

---

### Post by VastOne on 2009-04-19
> **dazzlindonna said:**
> This has been happening to me for the last few days, and I've narrowed it down (for me) to javascript issues.  If I turn off javascript, the problem goes away.  Turn it back on, and certain web pages with some sort of javascript on them will close FF down.

I don't yet know if it's a particular javascript function or what, yet.  But for me, it's definitely js related.

P.S. removing wins from samba did not help my problem.

One other thing: widgetbox.com is a perfect example of a page that will shut FF down if I have js turned on, but loads fine if js is off.  

Other info that may be useful: Running Ubuntu 8.10 (64 bit) and FF 3.0.8 on a modern box with 3 gigs ram.

Agree with all you have said Donna.

I am 64 bit and this issue has followed me on this machine from Gutsy all the way to Jaunty RC now. On another machine I have never seen the error or problem.  My specific definitive FF crash site is Yahoo mail, but now even sites that always worked (MLB.com, ESPN.com) are crashing. The other machine is a 64 bit and using the same flash, v10 Alpha, and the same FF and add ons.

Strangely enough, Youtube has never been a problem. It is very difficult to put a finger on this one, ie, is it hardware? is it Flash? is it Firefox? I have completely wiped this system to bare bones to go to ext4 in Jaunty and the results are exactly the same now matter what version of Ubuntu, Flash (using v10 alpha) or Firefox version 3.08

Spending a 20 career as a trouble shooting specialist, this one has me scratching my bald head even balder... I have basically given up on it as unsolvable and stay away from the known crash sites.  I have loaded Epiphany and it does not crash at any of these sites.... It is just a little too bland of a browser..

2 cents...Done

VastOne

---

### Post by dazzlindonna on 2009-04-19
Well, it's definitely just a Firefox issue, as far as I can tell.  The same sites that crash FF work fine in Opera and IE.

* I've tried running in -safe-mode, but that doesn't help, so it's not due to a plugin.

* I've tried running FF 3.0.8 in Windows and it works fine, so it's just the Linux version of FF that has the problem.

*I've tried it on a 32-bit Wubi laptop, and it works fine there, so it might be just 64-bit problem, but a friend of mine has no problem on his 64-bit system.

* Like you, Youtube works fine for me.

* I've tried using Noscript to isolate individual scripts, but so far (other than being a PITA to deal with), I haven't been able to figure out what type of script is the problem (if it is just one type).

This problem is getting worse for me, and I'm really having a hard time figuring out what to do.  I don't want to give up FF, but it's looking like I've got to make some sort of decision.  This is making my little online life more and more miserable.

---

### Post by VastOne on 2009-04-19
> **dazzlindonna said:**
> Well, it's definitely just a Firefox issue, as far as I can tell.  The same sites that crash FF work fine in Opera and IE.

* I've tried running in -safe-mode, but that doesn't help, so it's not due to a plugin.

* I've tried running FF 3.0.8 in Windows and it works fine, so it's just the Linux version of FF that has the problem.

* Like you, Youtube works fine for me.

* I've tried using Noscript to isolate individual scripts, but so far (other than being a PITA to deal with), I haven't been able to figure out what type of script is the problem (if it is just one type).

This problem is getting worse for me, and I'm really having a hard time figuring out what to do.  I don't want to give up FF, but it's looking like I've got to make some sort of decision.  This is making my little online life more and more miserable.

Hi Donna...

The frustration continues for me as well

I tried this: 

Code

firefox -profilemanager -no-remote

Created a new profile and called it test

And had no crashes


Started my profile back up and removed all add ons and plug ins and Yahoo crashed again and again I even removed my Theme and was down to bare bone...CRASH


I then installed the latest Java JDK as stated in another thread as the solution and still get the same issue...CRASH

This is so bizarre...It makes no sense at all

VastOne

---

### Post by dazzlindonna on 2009-04-19
I solved this! (well, for me anyway, hopefully for you too).

Cooliris plugin was the issue for me.  Uninstalling it solved the problem.  Even though safemode didn't help, I decided to start uninstalling plugins anyway, and I started from the ones I most recently installed.  I realized when I saw Cooliris in the plugin list that I'd installed it around the same timeframe as this issue started.  So I uninstalled it first, restarted FF, and the problem is gone!  (for now anyway, fingers crossed that it stays that way).

---

### Post by VastOne on 2009-04-19
> **dazzlindonna said:**
> I solved this! (well, for me anyway, hopefully for you too).

Cooliris plugin was the issue for me.  Uninstalling it solved the problem.  Even though safemode didn't help, I decided to start uninstalling plugins anyway, and I started from the ones I most recently installed.  I realized when I saw Cooliris in the plugin list that I'd installed it around the same timeframe as this issue started.  So I uninstalled it first, restarted FF, and the problem is gone!  (for now anyway, fingers crossed that it stays that way).

I do not have Cooliris...What doews it do?  I only have the basic plugins installed the out of the box ones so to speak, only added the 64 bit Alpha

---

### Post by dazzlindonna on 2009-04-19
Darn, hoped that would help you, but I guess not.  Cooliris (cooliris.com) turns FF into a slick media browser that flies around, zooms, etc.  Pretty, but perhaps a little too invasive.

I wonder if using a version of FF lower than 3.0.8 would work for you?

---

### Post by VastOne on 2009-04-19
> **dazzlindonna said:**
> Darn, hoped that would help you, but I guess not.  Cooliris (cooliris.com) turns FF into a slick media browser that flies around, zooms, etc.  Pretty, but perhaps a little too invasive.

I wonder if using a version of FF lower than 3.0.8 would work for you?

Nope...I posted this in another link, this has followed this machine from every update beginning at Gutsy-Heron-Intrepid to now Jaunty and every FF version through that process.

VastOne

---

### Post by dazzlindonna on 2009-04-19
VastOne, since temp profile works for you, I'd suggest starting fresh with that one and slowly add things back, one at a time, testing after each.

---

### Post by VastOne on 2009-04-19
> **dazzlindonna said:**
> VastOne, since temp profile works for you, I'd suggest starting fresh with that one and slowly add things back, one at a time, testing after each.

I was wrong, this is happening even on a new profile.When I run it from terminal and it exits, I get a message of Illegal Instruction

Of note, this is only at Yahoo Mail and not at any other site from Yahoo.com.

It does happen on any video from MLB.com and ESPN.com too.

Anyone know where I can get more info (log?) on what this illegal instruction is?

VastOne

Edit:

Upon further review it appears to be a hardware issue after all. I have a AMD 64 3400+ Family 15 that apparently has LAHF issues and it's all over the web about these known issues and I have as yet found a solution

---

### Post by dazzlindonna on 2009-04-19
Ok, so the problem returned for me, and even happens with a clean test profile.  Here's the error that I get in terminal.

~$ firefox -profilemanager -no-remote
LoadPlugin: failed to initialize shared library /home/donna/.cxoffice/win98/desktopdata/cxnsplugin/linux/dosdevices_c^3A_Program+Files_Netscape_Communicator_Program_Plugins_np32dsw.dll.so [/home/donna/.cxoffice/win98/desktopdata/cxnsplugin/linux/dosdevices_c^3A_Program+Files_Netscape_Communicator_Program_Plugins_np32dsw.dll.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /home/donna/javax86/jre1.6.0_05/plugin/i386/ns7/libjavaplugin_oji.so [/home/donna/javax86/jre1.6.0_05/plugin/i386/ns7/libjavaplugin_oji.so: wrong ELF class: ELFCLASS32]
sh: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
ICEDTEAPLUGIN_DEBUG = (null)
Segmentation fault

(no idea why it mentions win98; that seems odd)

So it's looking for npviewer and can't find it and has some wrong ELF classes.  No idea what any of it means, but maybe someone here does.

Oh, and VastOne, I also have a AMD 64 but it's a 5000+

I'm guessing it's this bug: [https://bugs.adobe.com/jira/browse/FP-1026](https://bugs.adobe.com/jira/browse/FP-1026)

---

### Post by VastOne on 2009-04-19
> **dazzlindonna said:**
> Ok, so the problem returned for me, and even happens with a clean test profile.  Here's the error that I get in terminal.

~$ firefox -profilemanager -no-remote
LoadPlugin: failed to initialize shared library /home/donna/.cxoffice/win98/desktopdata/cxnsplugin/linux/dosdevices_c^3A_Program+Files_Netscape_Communicator_Program_Plugins_np32dsw.dll.so [/home/donna/.cxoffice/win98/desktopdata/cxnsplugin/linux/dosdevices_c^3A_Program+Files_Netscape_Communicator_Program_Plugins_np32dsw.dll.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /home/donna/javax86/jre1.6.0_05/plugin/i386/ns7/libjavaplugin_oji.so [/home/donna/javax86/jre1.6.0_05/plugin/i386/ns7/libjavaplugin_oji.so: wrong ELF class: ELFCLASS32]
sh: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
ICEDTEAPLUGIN_DEBUG = (null)
Segmentation fault

(no idea why it mentions win98; that seems odd)

So it's looking for npviewer and can't find it and has some wrong ELF classes.  No idea what any of it means, but maybe someone here does.

Oh, and VastOne, I also have a AMD 64 but it's a 5000+

I'm guessing it's this bug: [https://bugs.adobe.com/jira/browse/FP-1026](https://bugs.adobe.com/jira/browse/FP-1026)

Donna

Are you using the Adobe Alpha 64 libflashplayer.so? If not, search the forum here and install it after you remove all other traces of java plugins. The instructions are very specific on how to do it.

VastOne

---

### Post by dazzlindonna on 2009-04-20
Fairly certain I am using it, but what the heck, I'll redo if necessary. Might help.  Will let you know.

UPDATE: and...that worked.  I was using it, but I reinstalled anyway.  Will see if it lasts this time.  Thanks.

ANOTHER UPDATE: Ok, I give.  It keeps returning. I can usually "fix" it, temporarily, but it eventually begins again.  I even upgraded to Jaunty today, which "fixed it" again, but it just reappeared again.  Not happy.

HOPEFULLY THE LAST UPDATE: I started over completely with a fresh Firefox install, fresh profile, and completely removed all flash related stuff, then reinstalled all flash related stuff.  That seems to have finally done the trick.

---

### Post by Daremo_06 on 2009-05-10
I had posted in a similar thread on here and I was directed to this thread.  However, in the meantime, I had upgraded to 9.04.  Since then, I have had zero (O) instances of FF crashing as it was under 8.10.  

So either there was a bug somewhere that got fixed, or during the installation, it overwrote a setting or configuration that was causing the crash in the 1st place.

---

### Post by nicolasdiogo on 2012-06-30
it seems to be related to CXOFFICE (cross-office)

if you uninstall then reinstall flashplugin it should set the necessary variables correctly

and no more errors

---

### Post by oldos2er on 2012-06-30
Old thread closed.

---

