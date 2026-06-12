---
title: "Firefox really slow rendering some pages"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Arlo on 2006-09-27
Firefox renders some pages really slowly, to the point where it locks up (no doubt a XUL thing as the renderer struggles).

Could someone visit:

[http://www.pbs.org/cringely/pulpit/pulpit20060922.html](http://www.pbs.org/cringely/pulpit/pulpit20060922.html)

and let me know if you can scroll up and down the page at normal speed?

I have seen it on a couple pages, google spreadsheet (which is not fast to begin with) is completely unusable.

I have gentoo installed on the same machine and it works fine. I also have used the same version of Firefox on a windows xp machine without issue.

Any ideas?

Thanks much

-Arlo-

---

### Post by LotsOfPhil on 2006-09-27
I have no problems on that site. If you don't have a lot of themes/extensions, you might try uninstalling and reinstalling firefox.

---

### Post by nathanbriggs on 2006-09-27
there is a rumoured memory leakage of firefox under ubuntu -but I am afraid thats all I know a rumour :)

---

### Post by uboltun on 2006-10-24
I have exactly the same problem. I have Tab Mix Plus, Flash Block , Google Sync and English Lang Pack installed. When I run top I noticed that Xorg use a lot of CPU. I have noticed this behaviour on several websites including google spreadsheet. I think it should be related to java scripts on some webpages.

---

### Post by kerry_s on 2006-10-24
> **Arlo said:**
> Firefox renders some pages really slowly, to the point where it locks up (no doubt a XUL thing as the renderer struggles).

Could someone visit:

[http://www.pbs.org/cringely/pulpit/pulpit20060922.html](http://www.pbs.org/cringely/pulpit/pulpit20060922.html)

and let me know if you can scroll up and down the page at normal speed?

I have seen it on a couple pages, google spreadsheet (which is not fast to begin with) is completely unusable.

I have gentoo installed on the same machine and it works fine. I also have used the same version of Firefox on a windows xp machine without issue.

Any ideas?

Thanks much

-Arlo-

That page worked fine for me and only took a little over 6 seconds to load->

---

### Post by uboltun on 2006-10-24
> **kerry_s said:**
> That page worked fine for me and only took a little over 6 seconds to load->

I noticed when I turn of images from pbs.org rendering works fine. But with images on it is kind of slow , especially , when I move the FF window.

---

### Post by dcstar on 2006-10-25
> **uboltun said:**
> I noticed when I turn of images from pbs.org rendering works fine. But with images on it is kind of slow , especially , when I move the FF window.
There are a few things you should check with any issues like this:

[LIST=1]
[*]Is Direct Rendering working? (run "glxinfo" in a terminal)?
[*]Are you running the best kernel for your CPU (***not*** the default 386 one)?
[*]Are you running a version of Firefox optimised for your CPU ([www.getswiftfox.com](www.getswiftfox.com))?
[/LIST]

---

### Post by uboltun on 2006-11-30
> **dcstar said:**
> There are a few things you should check with any issues like this:

[LIST=1]
[*]Is Direct Rendering working? (run "glxinfo" in a terminal)?
[*]Are you running the best kernel for your CPU (***not*** the default 386 one)?
[*]Are you running a version of Firefox optimised for your CPU ([www.getswiftfox.com](www.getswiftfox.com))?
[/LIST]

I hope this is helpful.
Video etc work without any problems and I am setisfied with performance. So Direct Randering shouldn't be the problem. 
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 PRO Generic
OpenGL version string: 2.0.6065 (8.29.6)

I am running the kernel version optimized for my CPU. Swiftfox doesn't make any difference , and currently I have Firefox 2.0 installed.
:~$ uname -r
2.6.15-27-686

I experiance this slow down only on certain webpaged like google spreadsheets. By the way Google-Docs work without problems. I also had this problem on two different computer all running Ubuntu. One of them was with the kernel compiled and completely optimized and Direct randering enabled. So that is probably not the problem.

---

### Post by non-free on 2006-11-30
Swiftfox is non-free software. It takes away a freedom that Firefox has. The freedom to redistribute. It cant be included in the repositories. Dont use it if you prefer free as in freedom software.

---

### Post by juantovarm on 2006-12-01
Same thing was happening to me. Using Dapper and worse on Edgy with firefox 1.5 and 2 from ubuntu. I then decided to install firefox 2 directly from [www.mozilla.org](www.mozilla.org) following these instructions (MANUAL INSTALL) didn't take me more than 10 minutes, downloading included 

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Now, firefox runs real smooth

---

### Post by doctorberen on 2006-12-20
Arlo,

Have you solved this problem already? 

Google spreadsheets has been running to a crawl using Firefox 2.0 on Ubuntu 6.10.

But when I use the Windows version of Firefox 2.0 with the exact same extensions, the same spreadsheet is snappy.

---

### Post by superm1 on 2007-01-01
> **doctorberen said:**
> Arlo,

Have you solved this problem already? 

Google spreadsheets has been running to a crawl using Firefox 2.0 on Ubuntu 6.10.

But when I use the Windows version of Firefox 2.0 with the exact same extensions, the same spreadsheet is snappy.
Google spreadsheet crawls on all of the Ubuntu 6.10 machines I've tried.  Also, try clicking on a hidden comment in digg.  You will see how slow it expands.  Now go over to a windows box and do the same thing. Very very snappy.

---

### Post by towsonu2003 on 2007-01-02
have similar / same problem myself... I got very frustrate when I visited digg.com from Windows. So quick to render, and scrolls so smoothly... gr

I found a bug report here (for digg.com only) and posted my comments and voted: [https://bugzilla.mozilla.org/show_bug.cgi?id=328319](https://bugzilla.mozilla.org/show_bug.cgi?id=328319)

---

### Post by superm1 on 2007-01-02
> **towsonu2003 said:**
> have similar / same problem myself... I got very frustrate when I visited digg.com from Windows. So quick to render, and scrolls so smoothly... gr

I found a bug report here (for digg.com only) and posted my comments and voted: [https://bugzilla.mozilla.org/show_bug.cgi?id=328319](https://bugzilla.mozilla.org/show_bug.cgi?id=328319)
I added comments and voted too :)

---

### Post by towsonu2003 on 2007-01-02
> **superm1 said:**
> I added comments and voted too :)

thanks :)

---

