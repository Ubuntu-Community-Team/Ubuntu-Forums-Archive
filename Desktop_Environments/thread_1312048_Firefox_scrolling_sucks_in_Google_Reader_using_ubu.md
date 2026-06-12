---
title: "Firefox scrolling sucks in Google Reader using ubuntu 9.10"
date: 2009-11-02
forum: Desktop Environments
---

### Post by Wanas on 2009-11-02
I installed ubuntu 9.10 2 days ago but I have a problem with the firefox, Slow scrolling (its like slow rendering) while using google reader and it eats the cpu usage.

It was just fine while using it on ubuntu 9.04 its not the best but good enough to read my news.

I have tried to install ubuntu from the Mozilla ppa daily builds or trying prism but the same.
I have tried to install opera and epiphany they work better !!
I have tried flock from the tar.bz2 and It works fine too
here a video talking about my problem but with GMail.
[http://www.youtube.com/watch?v=mF3rYMEbIOw](http://www.youtube.com/watch?v=mF3rYMEbIOw)

My computer details:
- CPU: Intel core 2 due 3.00 GHZ 
- Ram: 3 GB
- VGA: nvidia 6200 LE 512 MB
- OS: Ubuntu 9.10
- Firefox: 3.5.5

---

### Post by Kushkah on 2009-11-02
Do you have the nvidia restricted driver enabled?  Firefox scrolling always looked a little odd for me with the default driver.

---

### Post by Wanas on 2009-11-03
I dont know how to enable it :(
I have installed the driver through this ppa [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa) to install the last 190.42 nvidia driver ;)
and the compiz is working fine and 3D games too

---

### Post by Kushkah on 2009-11-04
Go to System > Administration > Hardware Drivers and make sure that the nvidia one is enabled.

---

### Post by tobiasly on 2009-11-05
> **Wanas said:**
> I installed ubuntu 9.10 2 days ago but I have a problem with the firefox, Slow scrolling (its like slow rendering) while using google reader and it eats the cpu usage.

It was just fine while using it on ubuntu 9.04 its not the best but good enough to read my news.

Same here. I was on 8.10 and did a fresh install of 9.10. I've tried disabling desktop effects, disabling pango, disabling all plugins (ubuntu extension, flash, etc.), deleting my firefox profile (so it creates a fresh one), switching gnome themes, using proprietary NVidia drivers from Synaptic, using proprietary drivers from NVidia site, using open drivers etc. etc.

There is something just seriously wrong with FF 3.5 in Karmic. Firefox has never been nearly as snappy for me in Ubuntu as it is on Windows with similar hardware but this is just unusable.

FWIW I'm using x86_64 version with NVidia 8500GT GPU.

---

### Post by bgc on 2009-11-05
I agree. Firefox and sound are killing me in Karmic. Firefox doesn't feel as responsive as FF3, which it just shouldn't be. Sound, what can I say, some apps work, some don't, and I ended up going through a lot of trial and error to get mpd to work...

---

### Post by Wanas on 2009-11-05
I have tried to download prism.tar.gz (stand alone application) and its working much better, I think the problem with the firfox karmic koala release

---

### Post by amsecret on 2009-11-08
i have this problem too . can anyone help ?

---

### Post by Bealer on 2009-11-08
Got the same problem here. It's been happening I think since 9.04. I'm on 9.10 now. 

It used to work perfectly before. Scrolling intense javascript based sites seems to cause the problem. I also have issues with flash sites, makes scrolling even worse.

As far as flash is concerned I think it's due to flash itself. Causes my CPU to jump up and over 60%, sometimes even 100%. 

The JavaScript though, I have no idea.

---

### Post by Wanas on 2009-11-14
bump

---

### Post by beesblaas on 2009-11-24
I also have this problem since I have upgraded to Ubuntu 9.10 
The scrolling is absolutely terrible.

Long Pages with a complex layout has jerky scrolling, and when you use the "go back" key,
it does not respond quickly, etc. It is tremendously irritating. It seems like it has trouble assembling the page, and it would not let you do anything till it is finished.

Using "System Monitor", I also find that my CPU regularly goes to 100%, and all I am using is firefox.

When I do: System > Administration > Hardware Drivers,
it says  "No propriety drivers are in use on this system"

Anyway, This problem is not about hardware. It was not as bad with 9.04.

Please help.

PS: an example of such a bad website: [http://au.yahoo.com/](http://au.yahoo.com/)
At this moment there are 3 adobe files (.swf) for this site. ( 2x swf "object" and 1x "embed").
If I check with my system monitor while this site's tab is open, I get 100% CPU usage all the time. 
If I switch the browser window to another tab/site, (this site is still in a tab, but not visible), the CPU drops to 20% as normal

PS: It is not shockwave flash, it is Javascript, see my following entry

---

### Post by LoveNix on 2009-11-24
If you are getting 'No proprietary drivers installed' then you have the 'default' drivers installed with your system. You don't mention your video card, but if it is nVidia, you need to install the nVidia drivers.

---

### Post by Wanas on 2009-11-24
> **LoveNix said:**
> If you are getting 'No proprietary drivers installed' then you have the 'default' drivers installed with your system. You don't mention your video card, but if it is nVidia, you need to install the nVidia drivers.

Its not related to the drivers at all it looks like its problem with the karmic firefox pack :(
I have tried standalone prism (prism.tar.gz) and it works more better

---

### Post by Usufruct on 2009-11-24
I am unable to reproduce this issue with Karmic x64, nVidia 190.42, and Firefox 3.5.5.

---

### Post by beesblaas on 2009-11-25
I am running Ubuntu 9.10 with Firefox 3.5.5
and my card is an ATI Radeon 9200 PRO. (capable of full 3D acceleration)

Since I get "No propriety drivers are in use on this system", I assume I'm using the Ubuntu built-in driver  ?

If I type: glxinfo |grep vendor
I get :
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

I found some info to use the Open Source driver for ATI here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I dont know if it will help to install this driver,
and anyway, I did not have this problem before, and all I did was change to from Ubuntu 9.04 to 9.10

PS: I never changed the driver, this is obviously not the issue.

---

### Post by digiSal on 2009-11-26
Its not just in Firefox. 

I get the same results in Chromium and the latest Opera.

I need to look into the nvidia drivers since i get the no proprietary drivers message as well. 

Sal

---

### Post by Wanas on 2009-11-26
> **digiSal said:**
> Its not just in Firefox. 

I get the same results in Chromium and the latest Opera.

I need to look into the nvidia drivers since i get the no proprietary drivers message as well. 

Sal

Working here just fine on opera, epiphany and stand alone prism (.tar.gz)[not from the repos]

---

### Post by entwoska on 2009-11-30
> **Bealer said:**
> Got the same problem here. It's been happening I think since 9.04. I'm on 9.10 now. 

It used to work perfectly before. Scrolling intense javascript based sites seems to cause the problem. I also have issues with flash sites, makes scrolling even worse.

As far as flash is concerned I think it's due to flash itself. Causes my CPU to jump up and over 60%, sometimes even 100%. 

The JavaScript though, I have no idea.


Exactly the same problem here. I disabled all Flash from loading with the Firefox FlashBlock add-on but I realized that Javascript caused problems too !!

For example, this Javascript clock uses 50% of my cpu..

[http://toki-woki.net/p/scroll-clock/](http://toki-woki.net/p/scroll-clock/)

This is ridiculous and very frustrating since I have this problem from Jaunty.. thought Karmic would solve this issue :( Ubuntu 8.10 was fine.

Flash is also a disaster, but it seems to be the case for everyone..

(I use the default drivers and have an ATI HD3450 card, no effects on)

I'm using Ubuntu since Dapper Drake and slowly thinking of migrating to something else for the first time in 3 1/2 years.

---

### Post by bgc on 2009-12-01
I have the same issue you mention. Loading the java clock, I average about 50% CPU in use...

This is with intel graphics and no effects on.

---

### Post by beesblaas on 2009-12-12
I have eventually proven **it is JAVASCRIPT for me, not Flash. **

First, open the system monitor to see how your PC is being over-worked:  
[B]System > administration > system monitor, 
pick the "resources" tag[/B], then it shows an ongoing graph of yor CPU usage  

Then I opened this example of a site which is a problem in a window next to the system monitor: [http://au.yahoo.com/#](http://au.yahoo.com/#)  
The CPU would be on 100% usage almost all the time.  
I first tried to switch off Flash, because I thought this was the problem, but it made no difference: 
Firefox > Edit > Preferences > Main > Manage Add-ons > Plugins, disable shockwave flash.  

**However, the following worked: Firefox > Edit > Preferences > Content, unclick the "Enable JavaScript".  **
The CPU would immediately drop from 100% to normal levels.  

The question is - how does disabling Javascript affect your browsing? Well, some mouse-click menus dont work, but mostly it is OK, Gmail defaults to something without Javascript and it is OK. Writing this response stuffed up all the formatting.
So I will see how I go without it, when I can.

---

### Post by SuckerBlood on 2009-12-18
Any solution? Any suggestion?

It remained until the next version of Ubuntu?? :confused:

The people says that with the most recent updates of Firefox (alfas) it is corrected. Why don't compare the code?

---

### Post by beesblaas on 2009-12-23
[FONT=Arial][SIZE=2]**New Fix/work-around.**

I found this fix, and it worked for me:

[http://cretaceouslabs.com/blog/2009/11/gnome-firefox-dead-slow/](http://cretaceouslabs.com/blog/2009/11/gnome-firefox-dead-slow/)

also described here:

[http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/comment-page-1/#comment-4711](http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/comment-page-1/#comment-4711)

Essen[/SIZE][/FONT][FONT=Arial][SIZE=2]tially, you edit the file xorg.conf, there is a graphics configuration setting which is screwed up with the new ubuntu.
[/SIZE][/FONT][FONT=Arial][SIZE=2]Option "AccelMethod" "XAA"

There is a minor issue though: The fix stuffs up System Monitor, which loads too slow to use. Dont know why,
but I dont need to use it now that I dont have the problem any more. 
and anyway, you can type "top" in a terminal window for a process report.
Will keep you updated if there are any issues.[/SIZE][/FONT][SIZE=2][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
[/SIZE]

---

### Post by Wanas on 2009-12-23
> **beesblaas said:**
> [FONT=Arial][SIZE=2]**New Fix/work-around.**

I found this fix, and it worked for me:

[http://cretaceouslabs.com/blog/2009/11/gnome-firefox-dead-slow/](http://cretaceouslabs.com/blog/2009/11/gnome-firefox-dead-slow/)

also described here:

[http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/comment-page-1/#comment-4711](http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/comment-page-1/#comment-4711)

Essen[/SIZE][/FONT][FONT=Arial][SIZE=2]tially, you edit the file xorg.conf, there is a graphics configuration setting which is screwed up with the new ubuntu.
[/SIZE][/FONT][FONT=Arial][SIZE=2]Option "AccelMethod" "XAA"

There is a minor issue though: The fix stuffs up System Monitor, which loads too slow to use. Dont know why,
but I dont need to use it now that I dont have the problem any more. 
and anyway, you can type "top" in a terminal window for a process report.
Will keep you updated if there are any issues.[/SIZE][/FONT][SIZE=2][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
[/SIZE]

Actually I have the same X11.conf by default having the same line (Option "AccelMethod" "XAA") and nothing is changed for me and firefox scrolling is still slow and eats 80% of my cpu while scrolling.

---

### Post by beesblaas on 2009-12-24
> **Wanas said:**
> Actually I have the same X11.conf by default having the same line (Option "AccelMethod" "XAA") and nothing is changed for me and firefox scrolling is still slow and eats 80% of my cpu while scrolling.

Maybe we have more than one problem. Have you tried disabling the Javascript in Firefox, as described by me before in this thread ?

So you already had the "fix" in xorg.conf by default.
Just to be 110% sure that the fix in your xorg.conf is in effect, you can run the update of your xorg.conf file in a terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

Apart from that, I then also had to log off the session and back in to see the change.

---

### Post by sigurnjak on 2009-12-25
[https://addons.mozilla.org/en-US/firefox/addon/5846](https://addons.mozilla.org/en-US/firefox/addon/5846)

I use this and it is great . If you read comments there is a post with some custom settings to get you started .

---

