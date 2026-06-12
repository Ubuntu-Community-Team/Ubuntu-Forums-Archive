---
title: "Firefox is slow."
date: 2006-01-08
forum: Desktop Environments
---

### Post by Edho on 2006-01-08
Not just a feeling..

In Win Xp i use "MyIE2" webbrowser, it's a shell over MS-IE6 and uses his engin.
(Tabbed browsing ,mouse gestures ,pop-up-killing)
And fast!

Firefox under Ubuntu is a lot slower.
I did the tuning , about:config,... with a little better result.

Still, the speed-difference is remarkable.

Suggestions?
Maybe i try a other browser, like Opera or...??

(Ubuntu-Gnome desktop)

Thank You.
Edho.

---

### Post by lnostdal on 2006-01-08
try: [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/) 
that made firefox faster than IE here (at least 1.5, which is faster than 1.0.*)

---

### Post by aysiu on 2006-01-08
I think you should try to determine where the problem lies.

If Firefox works fine in Windows on the same computer, it's something with the way you configured it in Ubuntu.

If Firefox works better with another Ubuntu user (go ahead and create a new one), then something's wrong with your user profile.

If another browser (Opera, Konqueror, Epiphany, Dillo) works faster, then maybe Firefox is just slow.

---

### Post by handy on 2006-01-08
Have you checked to see that:

**Menu:  System/Administration/Networking**

Double click on your ethernet card usually **eth0** is the **Connection Settings:**  is **DHCP**  ?

Unless of course you do have a **Static IP Address** that is.

If this setting is not right, it **will** slow down the initial connection to **every** server, once your there the speed is normal...

I hope this can help you,

handy

---

### Post by Edho on 2006-01-09
Thanks,

Fasterfox works with preloading links in the background.
Often a waste of bandwith?

My settings, dhcp..etc... are good.The same like in WinXP.

I think it's browser-related, maybe firefox(from Ubuntu-cd)) is not that fast.

Example:
Clicking a link in Xp needs 1 second to load.
With Firefox 2...3 seconds.

Later, when i have more knowledge Ubuntu/Linux ,will try Opera9.

---

### Post by handy on 2006-01-09
Hey what's a couple of seconds between friends?

handy

---

### Post by Edho on 2006-01-09
Hey what's a couple of seconds between friends?
-------------------------------------------

True!

But i like meeting my friends ASAP. :D :razz:

---

### Post by byoon on 2006-01-09
The version of Firefox in Breezy is definitely slow.  I installed 1.5 and it is much, much faster.  The only problem is that the Totem plugin will not work.  I installed MPlayer and its corresponding plugin and everything worked fine.

I expect Dapper to use a current release of Firefox and fix this horrendous speed problem.  Until then, here is the link that should help you...

[http://www.ubuntuforums.org/showthread.php?t=79283]("http://www.ubuntuforums.org/showthread.php?t=79283")

---

### Post by towsonu2003 on 2006-01-09
and here is the wiki link for the lazy users ;) 

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by IYY on 2006-01-09
I'd suggest using Konqueror. I find it to be a lot faster, and always use it on my older computers (whenever Dillo is just not enough, that is).

---

### Post by lnostdal on 2006-01-09
[QUOTE=Edho]Thanks,

Fasterfox works with preloading links in the background.
Often a waste of bandwith?
[/QUOTE]

you can turn off that part of Fasterfox

---

### Post by TZRick on 2007-02-02
Hello everyone!

Here's a problem for the gurus in here:

I installed Edgy around October, running Opera 9 and Firefox. Things worked very well back then. What I have noticed is that over the past 3-4 weeks, whenever I have multiple tabs open in either browser, activity slows down **considerably**. I mean, the hard-drive light is on blinking like crazy (telling me that maybe paging is going on?) and control-to-screen lag seems to be like 2 minutes. As I am writing this on my WinXP Home laptop running 5 open tabs in Opera 9, I have two tabs (YouTube and Weather.com) open in Firefox on my Edgy machine (specs below) and have been waiting for about five minutes to get the weather.com page to close, so the performance can go back to normal.

Any suggestions?

Thank you in advance for your assistance!

Specs of Ubuntu machine (Dell 4100):
PIII 850Mhz, nVidia GeForce II GTS 32MB, 60GB HDD, 384MB RAM, 10/100 3Com Ethernet Card.

---

### Post by towsonu2003 on 2007-02-02
> **TZRick said:**
> Hello everyone!

Here's a problem for the gurus in here:

I installed Edgy around October, running Opera 9 and Firefox. Things worked very well back then. What I have noticed is that over the past 3-4 weeks, whenever I have multiple tabs open in either browser, activity slows down **considerably**. I mean, the hard-drive light is on blinking like crazy (telling me that maybe paging is going on?) and control-to-screen lag seems to be like 2 minutes. As I am writing this on my WinXP Home laptop running 5 open tabs in Opera 9, I have two tabs (YouTube and Weather.com) open in Firefox on my Edgy machine (specs below) and have been waiting for about five minutes to get the weather.com page to close, so the performance can go back to normal.

Any suggestions?

Thank you in advance for your assistance!

Specs of Ubuntu machine (Dell 4100):
PIII 850Mhz, nVidia GeForce II GTS 32MB, 60GB HDD, 384MB RAM, 10/100 3Com Ethernet Card.
Try (for firefox) with a clean profile to see if it helps. [Here instructions]("https://wiki.ubuntu.com/MozillaTeam/Bugs?action=show&redirect=DebuggingFirefox#head-fa398dbbff0621c74659f3a1303dfde9b46f221b").. Other than that, I'm not sure how to handle these performance issues. I opened a few bugs on websites hanging firefox, and I'm still waiting for answers to those. 

Also keep an eye on memory usage (you can use top, conky [a search on the forums will provide good threads for that], or System > Administration > System Monitor [check "show all processes]) and try identifying what's using excessive memory, if any.

---

### Post by kevinlyfellow on 2007-02-02
Are you still running breezy?  There used to be a pango problem in the first few releases and according to your info, you are running breezy.  If thats the case, then 

in /etc/environment put in
MOZ_DISABLE_PANGO="1"

---

### Post by TZRick on 2007-02-02
Okay,

So you might think I'm kinda nuts for not trying this earlier, but anyway...

I ran the Software Updater and installed something like 41 updates, including for Firefox and Opera 9. Then, I restarted the PC.

Now, everything works fine. A moment ago, I had Opera open with about 7 windows. I then opened Firefox as well and opened a couple of tabs there. Memory seems to be stable at 50% usage.

Everything seems to be as it should be. When I first tried Ubuntu, I could not believe that a modern operating system can actually run so well on this old PC (minus the fancy 3D stuff of course!)! (go find new friends Vista!!!) I mean, it really is mind-blowing. In addition, I am running gDesklets for CPU, Network, Uptime, Weather and a fancy OSX-styled bar! Not only that, I am using xcompmgr for the nice drop shadows, etc. Before the current problem, I was even running Standford's Folding@Home software, where the CPU would be constantly at 100%, but there was virtually no lag when it came to running user applications...DVD movies included! I want to make sure the machine is stable prior to running Folding@Home, but so far so good for now.

Thanks again for the help! For the record, I still did delete and create a profile for Firefox.

---

