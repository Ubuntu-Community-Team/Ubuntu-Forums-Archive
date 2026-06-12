---
title: "Installing Chromium (browser)?"
date: 2009-04-14
forum: General Help
---

### Post by Intrepid Ibex on 2009-04-14
Hi,

I really like the new browser [Google Chrome](www.google.com/chrome) in Windows, but when I install [Chromium](https://launchpad.net/~chromium-daily/+archive/ppa) in my xubuntu, it doesn't seem to start :???:.

When I run: ```
chromium-browser
``` through terminal, it seems to give me this error:

```
[5280:5280:537573550:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090418r14008/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(148)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
[5280:5280:537585401:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090418r14008/build-tree/src/chrome/browser/process_singleton_linux.cc(34)] Not implemented reached in bool ProcessSingleton::NotifyOtherProcess() don't know how to notify other process about us.
```


I have these installed (yes, the packages are the latest versions, becuase I just did a dist-upgrade):

```
chromium-browser
python-tlslite
msttcorefonts
```
And yes, the packages are the correct ones.

---

### Post by ddarsow on 2009-04-14
Chrome is not (yet) available for LInux and does not run under Wine, so...it is not going to work.

---

### Post by paradigm2 on 2009-04-14
> **Intrepid Ibex said:**
> Hi,

I really like the new browser Google Chrome, but it doesn't seem to start :???:

Running chromium-browser through terminal seems to give this error:

```
[5512:5512:606068686:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090414r13668/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(157)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
Illegal instruction

```

On mine it does that as well in a terminal window, however after about5 - 30 seconds it SHOULD pop up another window with the actual browser in it.

I have it running on y machine right now which uses the Jaunty beta (9.04)

Here is the output I get right as the window pops up:

```

[29170:29170:21163904796:ERROR:/build/buildd/chromium-browser-2.0.174.0~svn20090410r13520/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(157)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
[29170:29170:21164194708:ERROR:/build/buildd/chromium-browser-2.0.174.0~svn20090410r13520/build-tree/src/chrome/browser/metrics/metrics_service.cc(701)] Not implemented reached in static std::string MetricsService::GenerateClientID()
[29170:29170:21164474608:ERROR:/build/buildd/chromium-browser-2.0.174.0~svn20090410r13520/build-tree/src/chrome/browser/tab_contents/web_contents_view_gtk.cc(74)] Not implemented reached in virtual void WebContentsViewGtk::CreateView()
[29170:29170:21164599232:ERROR:/build/buildd/chromium-browser-2.0.174.0~svn20090410r13520/build-tree/src/chrome/browser/renderer_host/render_widget_host_view_gtk.cc(203)] Not implemented reached in virtual void RenderWidgetHostViewGtk::DidBecomeSelected()
[29170:29170:21164599653:ERROR:/build/buildd/chromium-browser-2.0.174.0~svn20090410r13520/build-tree/src/chrome/browser/tab_contents/web_contents_view_gtk.cc(184)] Not implemented reached in virtual void WebContentsViewGtk::RestoreFocus() --  need to restore the focus position on this page.
[29170:29170:21164602828:ERROR:/build/buildd/chromium-browser-2.0.174.0~svn20090410r13520/build-tree/src/chrome/browser/gtk/infobar_gtk.cc(67)] Not implemented reached in void InfoBar::AnimateOpen()

```

It does work for me however it is not as it is on windows.  Going to options still crashes.  As does cutting and pasting most of the time.  But I am able to brose forums and visit most pages.

If you keep having problems you might try installing the the debug headers and the test suite as well from the same repository.  Also it has been mentioned elsewhere that a certain font package needs to be installed.

Once you add in the repository though it will grab nightly builds and they seem to be getting better with each passing week (a few weeks ago there were no tabs)!

added: hmmm.  I do notice I do nto get the "illegal instruction portion".  Also you have the build right after mine (I do not update it daily)

---

### Post by paradigm2 on 2009-04-14
> **ddarsow said:**
> Chrome is not (yet) available for LInux and does not run under Wine, so...it is not going to work.

The pre-alpha (version for linux native -- no wine) works a little bit now but I would in no way recommend it for normal use right now.  It is more of a curiosity thing.  Maybe in a few weeks it will be stable enough to not crash every 30 minutes.

---

### Post by Intrepid Ibex on 2009-04-15
Well actually I am using [Chromium](https://launchpad.net/~chromium-daily/+archive/ppa), not [Google Chrome](www.google.com/chrome).

I did try to wait for Chromium to open but it didn't make any difference.

So am I understanding this right? Chromium (link above) is available in some form in linux but it doesn't work with it, hMmMmMm :-k.

**ps.** don't get me wrong, I'm more than a normal user :KS.

---

### Post by LowSky on 2009-04-15
did you install it using the packages or by the repos?
I sugges the repos if you can use them, they will keep the program updated

Also the the programs is very beta and is still in the daily build phase, so it can break or work day to day.Best is to purge the prgram and reinstall

---

### Post by Dougie187 on 2009-04-15
It's not even beta. You can't expect it to work at all. Hell, it's not even alpha. It's pre-alpha. If you want it to work, you should wait and see when they release it. Until then, you most likely just have to deal with any issues that arise from using it. You might drop the dev's a message about the errors you get, in case they don't already know about them, it could help out the development.

---

### Post by paradigm2 on 2009-04-15
> **Intrepid Ibex said:**
> Well actually I am using [Chromium](https://launchpad.net/~chromium-daily/+archive/ppa), not [Google Chrome](www.google.com/chrome) .

I did try to wait for Chromium to open but it didn't make any difference.

So am I understanding this right? Chromium (link above) is available in some form in linux but it doesn't work with it, hMmMmMm :-k.

**ps.** don't get me wrong, I'm more than a normal user :KS.

Yes chromium is available for linux but does not work very well yet.  I found the link to it from searching these forums.  The link went to a blog post which then specified the line to add for the repository.

I will see if I can find it later.  For now it is tax time. :(

Anyway chromium for linux worked on my laptop, but not on my desktop (older, both running 9.04 beta).  For the desktop it would show the message and then 30 seconds later throw up a crash report.  On the laptop it shows the message then about 5 seconds later the chromium browser pops up and is basically functional.

---

### Post by paradigm2 on 2009-04-15
> **Dougie187 said:**
>  You might drop the dev's a message about the errors you get, in case they don't already know about them, it could help out the development.

It seems at this point they don't even want bug reports because it is so early in the game.  The following is part of the message you see on the defaul homepage when using chromium for linux:

> 
Please don't file bugs:

At this point there are so many gaping holes that finding bugs is not the problem and dealing with them is just a distraction.


For the curious who cannot get it to run, here is the entire default homepage:

> 
This browser is not ready yet!

This is a pre-alpha build of Chromium on Linux. It is woefully incomplete.

It's ‘Chromium’, not ‘Google Chrome’:

Chromium is an open source browser project. Google Chrome is a browser from Google, based on the Chromium project. This is a build of Chromium. No versions of Google Chrome for Linux will exist until Google makes an official release.

Please don't file bugs:

At this point there are so many gaping holes that finding bugs is not the problem and dealing with them is just a distraction.

Blogging about it is not helpful:

Chromium's problem is not a lack of media attention, but an excess of it. Coverage encourages people to try it out in this incomplete state which only creates negative first impressions. Also, dealing with misunderstandings/questions etc only distracts the team from the job of improving it.

Likewise, keep in mind that we won't see your comments if they're on a random blog somewhere.

How to help:

Chromium is an open source project, you are welcome to help out. We have documentation for developers as well as mailing lists and an IRC channel.


---

### Post by Intrepid Ibex on 2009-04-19
*Lowsky:* like the first message says, installed from the repositories.

*DOugie187:* yes, I know it is pre-alpha. But as for example Minefield is also pre-alpha but it works, so why shouldn't Chromium work too?

Well anyways, I tried running GC *(Google Chrome)* with Wine and POL (*PlayOnLinux* - basicly a open source copy of Cedega. Not as good as Cedega but at least easier to use) but there are problems:

[i]* version 1 is only available in online installer, which crashes

* version 2 Beta cannot be installed because the offline installer doesn't work even in Windows[/i]

So I tried portable versions of both of them (even though GC is already portable), but v1 only shows a blank screen or doesn't view any pages and v2 doesn't even start.

Conclusion: I'm going crazy with this.

---

### Post by Intrepid Ibex on 2009-04-21
Now I have a new error:

```
ali@ali-laptop:~$ chromium-browser 
[5280:5280:537573550:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090418r14008/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(148)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
[5280:5280:537585401:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090418r14008/build-tree/src/chrome/browser/process_singleton_linux.cc(34)] Not implemented reached in bool ProcessSingleton::NotifyOtherProcess() don't know how to notify other process about us.
```


However:

```
ali@ali-laptop:~$ **sudo** chromium-browser 
[5503:5503:824625192:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090418r14008/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(148)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
Illegal instruction
```


So with sudo ´Process Singleton´ force-notifies other processes about themselves(?). Or does it skip the notifying? Well, whatever it does I still had no luck starting Chromium. Not even when I tried purging/reinstalling the latest daily build of Chromium.

It shouldn't be that hard to create a working GUI for the chromium engine :o

**E:** the sudo thing was just a test with the pre-alpha browser Chromium (linux version). Never run browsers with root (sudo) privileges. It allows harmful sites to harm your linux.

---

### Post by Intrepid Ibex on 2009-05-16
Finally got this working with little tweaks ;).

---

### Post by smilingfrog on 2009-05-19
After some searching on the internet, I have come to the conclusion that some computers will not be able to run chromium on linux. The current chromium builds use SSE2 specific instruction sets, which some older processors do not support. 

[http://en.wikipedia.org/wiki/SSE2#Notable_IA-32_CPUs_not_supporting_SSE2]("http://en.wikipedia.org/wiki/SSE2#Notable_IA-32_CPUs_not_supporting_SSE2")

If you have a cpu in that list, linux chromium will fail for you, because your cpu can't handle it.

More info here:[http://code.google.com/p/chromium/issues/detail?id=9007]("http://code.google.com/p/chromium/issues/detail?id=9007")

```
It seems chromium is built from the core to depend on SSE2. There does not appear to
be a non-SSE2 branch, so I suppose anyone with an old Athlon or Coppermine P3 will
have to deal with not being able to run the software.

Welcome to obsolescence, my friends.
```

Hopefully there will be a work-around, but until then, maybe time to upgrade...

---

### Post by djuliette on 2009-05-19
I got it to run on my laptop. Ubuntu 9.04 64-bit. I installed it from the repos and I had to run a script from here:

[http://code.google.com/p/chromium/wiki/LinuxBuild64Bit](http://code.google.com/p/chromium/wiki/LinuxBuild64Bit)

to get the 32 bit libraries, and it has to be run with sudo.  I haven't been running it long, but it seems to be running fine for me.

---

### Post by paradigm2 on 2009-05-20
> **smilingfrog said:**
> After some searching on the internet, I have come to the conclusion that some computers will not be able to run chromium on linux. The current chromium builds use SSE2 specific instruction sets, which some older processors do not support. 

[http://en.wikipedia.org/wiki/SSE2#Notable_IA-32_CPUs_not_supporting_SSE2]("http://en.wikipedia.org/wiki/SSE2#Notable_IA-32_CPUs_not_supporting_SSE2")

If you have a cpu in that list, linux chromium will fail for you, because your cpu can't handle it.

More info here:[http://code.google.com/p/chromium/issues/detail?id=9007]("http://code.google.com/p/chromium/issues/detail?id=9007")

```
It seems chromium is built from the core to depend on SSE2. There does not appear to
be a non-SSE2 branch, so I suppose anyone with an old Athlon or Coppermine P3 will
have to deal with not being able to run the software.

Welcome to obsolescence, my friends.
```

Hopefully there will be a work-around, but until then, maybe time to upgrade...

Thanks this information is consistent with my experiences.  The laptop where chromium does work is a newer processor.  The old desktop on which it does not is a old 750 mhz cpu which is not supported.  However another computer I have is a Pentium 4 and it does work rather well.

About my previous comments in this thread, Chromium is much better now as far as stability.  I ran it for nearly an entire day without a crash.  The main issue now for me is no options menu yet although they recently implemented a TODO stub so it is likely coming soon.

---

### Post by smilingfrog on 2009-12-09
As an update, Google Chrome now installs on Ubuntu using the instructions on this thread, or [via instructions at this link]("http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html").

---

