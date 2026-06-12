---
title: "Missing checkboxes and button icons"
date: 2014-12-06
forum: Desktop Environments
---

### Post by fredrik.floren on 2014-12-06
[Running ubuntu 14.10 with unity]

After the latest firefox update, its icon went missing and tried to restore it. In the process, i.e., after changing themes, some other stuff went missing too. For example, the System Settings is looking very strange. See below. It's as if there's some problem with the boxes around the icons.
[ATTACH=CONFIG]258424[/ATTACH]

Also, there are check boxes and icons missing. See for example the Unity Tweak Tool below.
[ATTACH=CONFIG]258425[/ATTACH]

Notice the missing icon on the drop-down list. The same happens in other apps, e.g., Anjuta, the calculator, etc. Feels like a GTK thing?

I've tried resetting and reinstalling unity, resetting the icons, etc., but to no avail. 

I'd appreciate some suggestions and help.

Fred

---

### Post by ibjsb4 on 2014-12-08
Can't you change back to the original theme?

---

### Post by fredrik.floren on 2014-12-08
Well, that was a little too obvious to mention. Of course I did that. I also tried installing a different theme, namely numix. And there everything looks fine. I also tried reinstalling the ubuntu themes Radiance and Ambiance, but still no luck.

If the stock icons were messed up, I wouldn't see any of them. Now some "standard" (not really which are stock and not) are visible. And how can check boxes dissapear? 

This is driving me mad!!! Suggestions please!!

---

### Post by ibjsb4 on 2014-12-08
> **fredrik.floren said:**
> Well, that was a little too obvious to mention. Of course I did that.
In this forum the obvious has been overlooked, more than once, lots more than once.  I have solve problems in the pass with the obvious answer that for some reason the poster could not see.

also
> Feels like a GTK thing?
That gave me the impression your skill level was 'new to ubuntu'.

Good luck

---

### Post by TinkerTaylor on 2014-12-09
Thank you for your reply.

> **ibjsb4 said:**
> In this forum the obvious has been overlooked, more than once, lots more than once.  I have solve problems in the pass with the obvious answer that for some reason the poster could not see.

That's a very good point and I should have provided that information up front. But the attached pictures actually show the default theme. 


> **ibjsb4 said:**
> That gave me the impression your skill level was 'new to ubuntu'.

I was under the impression that GTK provided some stock, or standard, icons and gui elements and that the defualt ubuntu theme was using those. If that is not the case, I would gladly be corrected. 


> **ibjsb4 said:**
> Good luck

Thank you!

---

### Post by mc4man on 2014-12-09
> **TinkerTaylor said:**
> Thank you for your reply.



That's a very good point and I should have provided that information up front. But the attached pictures actually show the default theme. 




I was under the impression that GTK provided some stock, or standard, icons and gui elements and that the defualt ubuntu theme was using those. If that is not the case, I would gladly be corrected. 




Thank you!
Are you & the op the same person, if so why?
In any event what ppa's are you or you two using?

---

### Post by fredrik.floren on 2014-12-10
We're the same :p I'm not sure why the nick is different. I logged in from different computers but with the same account. Didn't do anything different on the two occasions...

Anyways, I've tried to extract the PPAs:

```
/etc/apt/sources.list:deb http://se.archive.ubuntu.com/ubuntu/ utopic main restricted
/etc/apt/sources.list:deb-src http://se.archive.ubuntu.com/ubuntu/ utopic main restricted
/etc/apt/sources.list:deb http://se.archive.ubuntu.com/ubuntu/ utopic-updates main restricted
/etc/apt/sources.list:deb-src http://se.archive.ubuntu.com/ubuntu/ utopic-updates main restricted
/etc/apt/sources.list:deb http://se.archive.ubuntu.com/ubuntu/ utopic universe
/etc/apt/sources.list:deb-src http://se.archive.ubuntu.com/ubuntu/ utopic universe
/etc/apt/sources.list:deb http://se.archive.ubuntu.com/ubuntu/ utopic-updates universe
/etc/apt/sources.list:deb-src http://se.archive.ubuntu.com/ubuntu/ utopic-updates universe
/etc/apt/sources.list:deb http://se.archive.ubuntu.com/ubuntu/ utopic multiverse
/etc/apt/sources.list:deb-src http://se.archive.ubuntu.com/ubuntu/ utopic multiverse
/etc/apt/sources.list:deb http://se.archive.ubuntu.com/ubuntu/ utopic-updates multiverse
/etc/apt/sources.list:deb-src http://se.archive.ubuntu.com/ubuntu/ utopic-updates multiverse
/etc/apt/sources.list:deb http://se.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://se.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu utopic-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu utopic-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu utopic-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu utopic-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu utopic-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu utopic-security multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu utopic partner
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu utopic main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu utopic main
/etc/apt/sources.list:deb http://repository.spotify.com stable non-free # disabled on upgrade to trusty disabled on upgrade to utopic
/etc/apt/sources.list.d/inizan-yannick-ubuntu-development-utopic.list:deb http://ppa.launchpad.net/inizan-yannick/development/ubuntu utopic main
/etc/apt/sources.list.d/inizan-yannick-ubuntu-development-utopic.list.save:deb http://ppa.launchpad.net/inizan-yannick/development/ubuntu utopic main
/etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.distUpgrade:deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
/etc/apt/sources.list.d/numix-ubuntu-ppa-utopic.list:deb http://ppa.launchpad.net/numix/ppa/ubuntu utopic main
/etc/apt/sources.list.d/pmjdebruijn-darktable-release-saucy.list.distUpgrade:deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu saucy main
/etc/apt/sources.list.d/sander-vangrieken-vaapi-trusty.list:deb http://ppa.launchpad.net/sander-vangrieken/vaapi/ubuntu utopic main # disabled on upgrade to utopic
/etc/apt/sources.list.d/sander-vangrieken-vaapi-trusty.list.distUpgrade:deb http://ppa.launchpad.net/sander-vangrieken/vaapi/ubuntu trusty main
/etc/apt/sources.list.d/sander-vangrieken-vaapi-trusty.list.save:deb http://ppa.launchpad.net/sander-vangrieken/vaapi/ubuntu utopic main # disabled on upgrade to utopic
```

How exactly does a stock app (like gedit) find its icons? And where in the file structure can I see installed icons?

---

### Post by mc4man on 2014-12-10
This ppa does have gtk-3.14 while utopic is on 3.12 - 
[https://launchpad.net/~inizan-yannick/+archive/ubuntu/development](https://launchpad.net/~inizan-yannick/+archive/ubuntu/development)
If inclined maybe try ppa-purge on it. Ask you you don't know how..
(- slightly off topic probably
I see you used my multimedia ppa for trusty. I have tried to make it obvious on the ppa page that it was not for users intending to upgrade to 14.10. Guess you missed that..  Don't think it's the issue here & may not have affected you depending on what you installed from there.

---

### Post by lisati on 2014-12-10
> **fredrik.floren said:**
> We're the same :p I'm not sure why the nick is different. I logged in from different computers but with the same account. Didn't do anything different on the two occasions...

We don't normally allow multiple accounts for users. Amongst other things, it can get a little bit confusing for those trying to help. If you would like administrative assistance getting your accounts sorted out, feel free to start a thread in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123").

---

### Post by fredrik.floren on 2014-12-11
> **mc4man said:**
> This ppa does have gtk-3.14 while utopic is on 3.12 - 
[https://launchpad.net/~inizan-yannick/+archive/ubuntu/development](https://launchpad.net/~inizan-yannick/+archive/ubuntu/development)
If inclined maybe try ppa-purge on it. Ask you you don't know how..

Thanks! That was it! I purged that PPA and thus downgraded to gtk-3.12. Now everything looks like it should. I was actually only after the newer Anjuta build in that PPA and overlooked that it also upgraded gtk-3. 

Follow up question: Is it possible to only upgrade select packages of a PPA? I usually use Synaptic if there's a way there?

> **mc4man said:**
> 
(- slightly off topic probably
I see you used my multimedia ppa for trusty. I have tried to make it obvious on the ppa page that it was not for users intending to upgrade to 14.10. Guess you missed that..  Don't think it's the issue here & may not have affected you depending on what you installed from there.

Oh, that was a long time ago when I was trying to get graphics hardware accel going. Yes, I missed that...

---

### Post by mc4man on 2014-12-11
> **fredrik.floren said:**
>  

Follow up question: Is it possible to only upgrade select packages of a PPA? I usually use Synaptic if there's a way there?



.
Sometimes you can,  sometimes not.
In this case maybe, you'd need to re-add the ppa
Then open synaptic, reload your source & see if Anjuta installs without upgrading gtk. It  looks like it will though it may need to use  the libgdl packages from that ppa 
(or will if you haven't already installed the utopic versions of libgdl

If it does install without newer gtk then test it. If all ok then disable or remove the ppa from your sources

---

