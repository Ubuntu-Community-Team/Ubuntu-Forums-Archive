---
title: "Google Chrome / Chromium Browser work in Gnome, but no in KDE"
date: 2010-01-25
forum: Desktop Environments
---

### Post by james_xxx on 2010-01-25
I use either the Google-Chrome beta (.deb downloaded from Google) or Chromium-Browser (from the daily ppa) on a number of different machines, both at home and at work.

In all but one case, Chrome/Chromium works fine. The exception is on my primary desktop PC at home. This machine is a Core 2 Quad w/4GB RAM, running the 64-bit version on K/Ubuntu 9.10.

On this machine, I am generally unable to run either Chome/Chromium, at least when using KDE. The browser starts up, but when I select a page for it to load, it acts like it is trying, but then appears to time-out. (I then get the 'Aw snap' message.) If I then close the browser, I notice that 'ps aux' shows that several processes related to Chrome remain running, and have to be manually killed.

The confusing thing is, that if I log out of my KDE session, then start a Gnome session, Chrome seems to work just fine.

Has anyone else experienced anything like this? Any suggestions as to what the issue may be?

I should also mention, that in looking into this, I did set this particular desktop to start using Google's DNS service. It didn't seem to have any effect on anything.

I have poked around through the forums, but have not seen any threads dealing with this kind of an issue.

Thanks!

---

### Post by lovinglinux on 2010-01-25
I can confirm that. I don't have Gnome installed to test, but I'm experiencing the exact same problem on KDE 64bit. BTW, ipv6 is disabled here.

I don't care that much, because I still believe nothing beats Firefox and it works great for me, even with more than 40 extensions installed. But I need to test web sites on different browsers.

---

### Post by baddog144 on 2010-01-25
I have been using Kubuntu 9.10 64-bit for quite a while with chromium from the daily ppa, and have experienced no such problems :S

---

### Post by james_xxx on 2010-01-25
baddog144,

I am also having no problem with Chrome (or Chromium) in Kubuntu 9.10 64-bit on several other machines. That is what makes this a bit confusing.

---

### Post by james_xxx on 2010-01-27
Bump...

---

### Post by minaev on 2010-01-30
I have the same problem. Not Kubuntu, just plain Ubuntu, but Gnome is not launched. I use Stumpwm.

Chromium worked well for some time after installation, but then it stopped working with the same symptoms. First, I thought the problem began after I installed libnss3-tools to manage certificates. So, I removed the package and reinstalled Chromium. Then, I thought I should remove ~/.pki, too. It didn't help. So, I tried to clean all Chromium directories (I only found ~/.config/chromium). Nothing helped yet...

---

### Post by minaev on 2010-01-30
I think I found a solution. Could someone with similar problems try and start Chromium with disabled plugins:
```
chromium-browser --disable-plugins
```

---

### Post by lovinglinux on 2010-01-30
> **minaev said:**
> I think I found a solution. Could someone with similar problems try and start Chromium with disabled plugins:
```
chromium-browser --disable-plugins
```

I can confirm. It works without the plugins.

---

### Post by minaev on 2010-01-30
This is not a solution, though, cause it brings other problems, like disabling downloading files (including extension). Perhaps, someone can find the plugin that causes Chromium to stall?

---

### Post by lovinglinux on 2010-01-30
> **minaev said:**
> This is not a solution, though, cause it brings other problems, like disabling downloading files (including extension). Perhaps, someone can find the plugin that causes Chromium to stall?

I would bet on flash :) Definitely is not java, since I don't have java installed.

---

### Post by minaev on 2010-01-30
I have an impression that some other command-line options could produce the same effect. Could you, please, check --no-sandbox? I think it might solve the original problem without adding more problems.

---

### Post by lovinglinux on 2010-01-30
> **minaev said:**
> I have an impression that some other command-line options could produce the same effect. Could you, please, check --no-sandbox? I think it might solve the original problem without adding more problems.

This works for me:

```
chromium-browser %U --no-sandbox --enable-plugins
```

---

### Post by james_xxx on 2010-01-30
I thought this thread had died. Glad to find out this isn't just me.

I am using the Google-chrome beta on this box. Running 'google-chrome --disable-plugins' does work, but 'google-chrome %U --no-sandbox --enable-plugins' does not. :(

I have thought about perhaps deleting config files and starting fresh, but have not yet done so.

I wonder why I have had so many fewer issues using Chrome in Gnome than in KDE.

---

### Post by Untitled_No4 on 2010-01-31
I've just realised that I had the same problem on my home machine although Chrome works okay in my office machine.

```
sudo aptitude purge google-chrome-beta
sudo aptitude clean
```

and then reinstalling from the Google Chrome website fixed it for me.

---

### Post by james_xxx on 2010-01-31
I just tried 'aptitude purge' and 'aptitude clean', then re-installed, but unfortunately the same problem remains.

---

### Post by minaev on 2010-02-03
james_xxx,

Could you try to: 
1. open about:plugins page in Chrome, 
2. determine  Shockwave plugin (it would be libflashplayer.so, I assume), 
3. find the file in your file system (`locate libflashplayer.so`), 
4. quit Chrome, 
5. move libflashplayer.so to another location and 
6. launch Chrome again and check whether it still hangs?

---

### Post by james_xxx on 2010-02-14
Sorry for taking so long to respond. I have been involved with too many other things.

I once again recently deleted chromium-browser and all associated files, and re-installed. I did the same thing again yesterday, then installed google-chrome-beta once again. Either way, I have the same problem.

I am still baffled that it is only on this particular machine (the Quad Core machine mentioned in my signature) that Google Chrome will not work when using KDE. It does work in KDE if plugins are disabled. It works fine in Gnome **with** plugins enabled. I use Chromium Browser on my PC at work in KDE, on an AMD Athlon 64x2 4600+, and it works just fine.

I am using KDE 4.4 from the PPAs on both machines.

Minaev, I have not yet tried moving libflashplayer.so to another location. I will try to do that soon, and let you know how things go.

---

### Post by wd5gnr on 2010-02-14
I have the same problem on a Quad Core AMD64 machine. No solution yet.

---

### Post by lovinglinux on 2010-02-14
> **wd5gnr said:**
> I have the same problem on a Quad Core AMD64 machine. No solution yet.

Still not working where. Now I can't even use it without the plugins.

KDE 4.4/Chromium latest build

---

### Post by cottfcfan on 2010-02-15
+1 same issue

---

### Post by wd5gnr on 2010-02-15
Too early to be sure, but it looks like turning off DNS prefetching (Wrench | Under the Hood) and restarting the browser may be the answer for my problem.

Anyone else try that?

---

### Post by cottfcfan on 2010-02-15
Just tried it makes no difference on my system.

---

### Post by james_xxx on 2010-02-15
Makes no difference here, either.

---

### Post by cottfcfan on 2010-02-16
Daily update for Chromium has come through, but problem still persists.

---

### Post by cottfcfan on 2010-02-18
Still having the issue, don`t know if anyone can help with this, but if I run from a terminal I get this error:

[3128:3424:72025193:ERROR:base/native_library_linux.cc(24)] dlopen failed when trying to open /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: libmozjs.so: cannot open shared object file: No such file or directory
[3128:3424:72096244:ERROR:base/native_library_linux.cc(24)] dlopen failed when trying to open /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: libmozjs.so: cannot open shared object file: No such file or directory

This is beyond me, but someone may be able to help.

---

### Post by james_xxx on 2010-02-18
cottfcfan,

Thank you for this post. I have to say that I am greatly embarrassed for not having run Google Chrome from the terminal myself as you did.

After reading the errors you received, I also ran Chrome from the command line, receiving the same errors.

This may be a little crude, but all I did was run:
```
sudo cp /usr/lib/xulrunner-1.9.1.8/libmozjs.so /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/
```

I then started Chrome (from Kickoff this time), and Lo and behold... it appears to be working!

I hope some others try this, too, and report back. If anyone knows of a better way to accomplish this, it would be good to hear about that, too.

I still do not get why Chrome was able to work for me consistently in Gnome, though. It seems really weird that this issue seems be affecting mostly folks using 64-bit Kubuntu Karmic, combined with a Quad-core CPU. (At least that is how I am perceiving what I have read.)

---

### Post by cottfcfan on 2010-02-19
Thanx James,

I followed your post and all seems well.
The only snag ive hit now is that when I "synchronize my bookmarks"
Chromium crashes!

edit:
Spoke too soon problems back again.

---

### Post by james_xxx on 2010-02-19
cottfcfan,

Problems are back again for me, too. 

It's odd, but I was able to start and restart Chrome several times just fine after making the copy of libmozjs.so. However after rebooting, things were back to where I had started.

I had also noticed in the past that I could sometimes get one run out of Chrome immediately after installing a new version, only to have it not working again the next time I tried to use it.

I will not be able to play around with it again until tonight. In the mean time, I am using an AMD 64x2 machine here at work with 64-bit Kubuntu Karmic, KDE4.4 and Chromium-browser working just fine.

---

### Post by james_xxx on 2010-02-19
Interestingly, when I run chromium-browser here at work from a terminal, I get this output:

```
:~$ chromium-browser
[3865:3879:1256284467:ERROR:base/native_library_linux.cc(24)] dlopen failed when trying to open /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: libmozjs.so: cannot open shared object file: No such file or directory
[3865:3879:1256459020:ERROR:base/native_library_linux.cc(24)] dlopen failed when trying to open /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: libmozjs.so: cannot open shared object file: No such file or directory

(npviewer.bin:3963): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
```

Largely the same as my machine at home, with the addition of the 'npviewer.bin' warning. Nevertheless, it seems to be working fine.

---

### Post by wd5gnr on 2010-02-19
I get nothing in the terminal. But I have also noticed that sometimes it will work great and then start doing the same old thing again. Makes it hard to tell if you are making progress or not.

---

### Post by User_Program on 2010-02-20
Try removing the following 

icedtea-6-jre-cacao
icedtea6-plugin
libaccess-bridge-java
libaccess-bridge-java-jni
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

Removing just openjdk-6-jre-lib should work too.

This could break some stuff on your system! (just warning you so I don't get blamed) Though I have NOT run into any problems on my system yet. Just covering my @

Then if you need a working java for chromium try installing 
enable multiverse then. 

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

Then add  
chromium-browser %U --no-sandbox --enable-plugins
to your launcher

In other words:
OpenJDK seems to be broken in Chromium or Chromium is broken in OpenJDK take your pick.

Hope this helps someone.

---

### Post by User_Program on 2010-02-20
Strange how something can work for an hour then once it's restarted it brakes again.  Disregard my earlier post.  Sorry.   I'm at a loss :confused:

---

### Post by james_xxx on 2010-02-20
> **User_Program said:**
> Strange how something can work for an hour then once it's restarted it brakes again.  Disregard my earlier post.  Sorry.   I'm at a loss :confused:

I am so with you on that, brother.

Would you buy any chance have Gnome or XFCE installed on your system? It's been a week or so since I've logged into a Gnome session, but seriously, each time I have, Chrome/Chromium has worked fine.

Could this somehow be a GTK/Qt issue? 

I would also love to know if this problem is only affecting those with Quad-core CPUs -- even though that just stands to add another dimension of weird to this whole matter.

I am really struggling to make sense out of it.

---

### Post by User_Program on 2010-02-21
I'm using GNOME now and posting from Chromium, everything running good. I also tested out some sites that I was having problems with and all is good in GNOME. 
Was just in KDE and had the lock up, freeze up and many chromium-browser instances running after shutting down.  I was only able to kill them.  I would like to say it's a KDE problem?  

I do have a quad core system.

---

### Post by cottfcfan on 2010-02-22
I don`t have a quad system, but this problem is definately only on KDE, and someone correct me if i`m wrong but only using 64bit.

---

### Post by wd5gnr on 2010-02-22
For the record, setting task CPU affinity (using taskset) to "put" chrome on one processor doesn't help. Affinity is inherited by child processes, so that *should* keep all the chrome processes on one CPU but it still crashes.

---

### Post by james_xxx on 2010-02-22
So, at this point this problem seems to show up on *certain* multi-core machines with 64-bit Kubuntu 9.10. 

I think that in this thread it would appear that there are individuals who have attested to having these problems on both Intel and AMD CPUs.

I think there is also attestation that on the machines where Chrome will not work in KDE, it nevertheless does work in Gnome.

I will mention again that chromium-browser works fine for me on my AMD Athlon 64x2 4600+ at work using KDE 4.4. I also use a single-core AMD machine at work with 64-bit Kubuntu 9.10 installed, using KDE 4.3.5. Google-chrome appears to be working well there, too. I have seen no issues on 32-bit installations.

Are there others out there experiencing these problems with systems other than those which are running 64-bit Kubuntu 9.10 on multi-core machines?

---

### Post by cottfcfan on 2010-02-23
It may be too early but I updated Chromium this morning to 5.0.336.0,
Ive been messing on it now for 30mins and all seems well.
 I`ll report back if I hit a problem.


EDIT - Spoke too soon, problem back!!!

---

### Post by Coder543 on 2010-02-23
I am running KDE 4.4.0 Netbook on my Aspire One, and chrome worked fine in gnome, however it now exhibits freezing and just a lack of good behavior. Using the command to disable plugins does resolve the issue, however. I would love to go back to chrome for my daily-use activities.

---

### Post by cottfcfan on 2010-02-23
Does anyone know if this has been posted or acknowledged as a bug?

---

### Post by wd5gnr on 2010-02-26
5.0.335.0 dev MAYBE works here. I say MAYBE because I've had it work for awhile before and then decide to go south. But I've been running it for 3 days and it seems ok.

---

### Post by james_xxx on 2010-02-26
OK, I once again removed google-chrome-beta tonight, and installed chromium-browser, along with chromium-codecs-ffmpeg and the language support package. 

The version I have is 5.0.338.0, build 40091.

It is still a no-go for me in KDE 4.4. After first trying to use chromium-browser in KDE, I logged out, and logged back in to an LXDE session. Chromium-browser worked better in LXDE than in KDE, but was slow, and eventually still locked up.

I then logged in to a Gnome session, and there Chromium is behaving as it should (as I expected).

---

### Post by wd5gnr on 2010-02-26
Ok so this is going to sound strange. I installed the beta and it worked. My system is very stable so I rarely reboot and my browser is always open. But I closed the browser and reopened it. BOOM. The problem  was back. No amount of restart and killall chrome would get it to load pages again.  I forced a reinstall from the .deb and it is working now.

So I _think_ the workaround (bad as it is) is to do this after closing the browser:

killall chrome
(repeat until you get "no process found")
sudo dpkg -i --force-all google-chromium....deb   <- use the right .deb file name here

Maybe? I don't know.

---

### Post by cottfcfan on 2010-02-28
I`m now using the 5.0.340 build, still no end to this problem.
Is this a chromium problem though?
If it works in Gnome 32 & 64bit, and KDE 32bit, is this a problem with the KDE64bit architecture?
If so where does this bug get posted?

---

### Post by cottfcfan on 2010-02-28
Just an update.
Is everyone having a problem here using Linux Mint or Kubuntu.
Ive just realised Chromium sticks in Mint KDE 32 & 64Bit, but not in Kubuntu.
 If your all finding the same, this could be a Linux Mint problem.

---

### Post by wd5gnr on 2010-02-28
I am not using Mint. Just Kubuntu. The "reinstall" fix seems to be working consistently for me.

---

### Post by cottfcfan on 2010-02-28
Think I might have solved this.
When Chromium is installed from the Repo, it also installs with it
"Chromium-Browser-Inspector" & "Chromium-codecs-ffmpeg".
Ive just installed Chromium-Browser without these 2 packages, and all seems to be working fine.
 I would appreciate someone else trying this to see if we get the same result.

Wd5gnr - Please check what you have installed.

---

### Post by Spyplane on 2010-03-01
I'm using Kubuntu and Linux Mint (both 64bit) and it was broken on both machines.   Once I uninstalled openJDK and installed sun's Java, both are fixed.   Thanks for the suggestion from whomever posted that!

---

### Post by Spyplane on 2010-03-02
Just kidding, like everyone else, mine is no longer working.

---

### Post by cottfcfan on 2010-03-02
I`m certain that this is a codec conflict.
I`ve reinstalled Kubuntu 64bit, and left out the Kubuntu-restricted-extras, and Chromium has worked perfectly now for days.
 I noticed that one of those extras is "iced-tea" something or other, which is the error that is thrown out when running Chromium in a Terminal.
 Try removing the Restricted-extras, and see if Chromium works then.
 If it does, like it has for me, then we`re narrowing down the problem.

---

### Post by Yasawas on 2010-03-03
Removing iced-tea worked for me, neither Chrome or Chromium would sync bookmarks prior to removing and most pages failed to load too.   Four or so trouble free minutes since though :)

Edit - I take it back too. Unresponsive, unable to resolve pages, but it'll work an odd time for no discernable reason. Maddening.

---

### Post by Spyplane on 2010-03-10
Adding a "-disable-flash" has fixed the problem for me.   You can add the flag to your /etc/chromium-browser/default file

---

### Post by james_xxx on 2010-03-10
Just to report back once more...

Using chromium-browser 5.0.350.0, along with the non-free ffmpeg codecs, the problem remains the same.

I did try running chromium-browser --disable-flash, but that did not help.

Each time I close chromium-brower, 'ps aux' shows several running chromium-browser processes. I usually pick one, and run 'kill -9 *pid*' to get rid of them.

Chromium-browser still runs fine in Gnome.

---

### Post by richieboy on 2010-03-10
i have the same problem.  i had been using chromium, chrome, and iron browser with no problems.  they only work intermittently now on kde, xfce, or openbox.  the problems only started two or three weeks ago.  i'm using an hpg60 laptop.

---

### Post by cottfcfan on 2010-03-11
I`m having no problems at all now.
After a clean reinstall without the kubuntu-restricted-extras, chromium has been working fine, and for over a week.
It must be some codec conflict that KRE is installing.

---

### Post by mmlevitt2 on 2010-03-12
I'm happy just killall chrome when too many chrome processes become present.

---

### Post by biriachan on 2010-03-13
After trying the various sugguestions in this thread to no prevail I found this bug report: [http://code.google.com/p/chromium/issues/detail?id=30457]("http://code.google.com/p/chromium/issues/detail?id=30457")

Comment 18, and 19 remarked removing gecko-mediaplayer fixed chrome/chromium, and also pointed to this bug report: [http://code.google.com/p/chromium/issues/detail?id=24507]("http://code.google.com/p/chromium/issues/detail?id=24507")

On my system (Kubuntu 64bit Karmic 9.10) removing the package fixed the issues for me as well.

I have been running/testing Chromium for the last 6 to 8 hours (multiple chromium and system reboots) with out any problems.

The package gecok-mediaplyer looks to be related to Firefox... so removing the package will most likely effect some features in Firefox.  I no longer use Firefox and have not tested how this will or will not effect the browser.

---

### Post by james_xxx on 2010-03-15
Biriachan,


I have not yet been able to test this extensively, but after removing gecko-mediaplayer on the machine that had been having issues with chromium-browser + KDE4, chromium-browser has seemed to work. I started, stopped and re-started chromium several times.

Tonight I'll get the chance to see whether or not it will work again after a reboot.

Many thanks for the helpful info!

*Update:*
OK, after rebooting a few times, chromium-browser is still working! It does seem slightly sluggish in comparison with how it runs on other machines yet, but at least it's functional.

---

### Post by bmxsummoner on 2010-03-17
i've got the 'aw, snap' on every page. :( i've been playing around, minus a few hiccups, with a fresh install of ubuntu (new to linux) for the past 3 days. but on the second day, iinstalled an update for chrome (or chromium) that i've been prompted with. and ever since i couldn't get a single page working on either browser. i've tried all the workarounds posted around the net and have been working at it for two days: clean reinstall, delete user data, diff. builds, (no gecko), etc. nothing's worked so far. i'm on a 32-bit system, karmic, with gnome, so it appears it's not limited to the 64ers.  

my chrome (on xp) experience has been better compared to firefox, and was too on linux. hope a solutions found soon.

---

### Post by Spyplane on 2010-04-05
Removing gecko-mediaplayer worked for me!

---

### Post by oshunter on 2010-04-18
Removing gecko-mediaplayer worked for me as well :)

---

### Post by Casper315 on 2010-04-23
Just a quick note,
   Chomium crashed for me when I installed Lucid with Gecko Media Player plug-in. Removing this plug-in ended the crashing. I installed the," mozilla-mplayer_3.55-2ubuntu1_i386.deb from Ubuntu Karmic and had NO conflicts or ill-effects. It works well in Firefox and does NOT seem to affect Chromium at all.
   I'm running the 32 bit version of Lucid Kubuntu KDE 4.4.2 with all applied updates (so far) on a Dell XSP M1330 with Nvidia Graphics card.

Thanks...  :)

---

### Post by Sefianix on 2010-05-02
I wanted to post a "thanks!" for this solution.  It solved the problem on my Kubuntu 10.04 system with Chromium.  I've had the problem since 9.10.  I may try out Chrome later.

Again, thanks!

---

### Post by ratcat on 2010-05-02
In Kubuntu 10.4 64 Chromium is excellent. Firefox displays unreadable type on the ubuntu site and garbage elsewhere. Netscape a little better. 64 bit is a puzzle. I sometimes think linux plays best on small screens, notebooks and all. And, why not qtconfig to set gtk fonts in Kubuntu? I get "unknown"

---

