---
title: "Firefox crashing alot?"
date: 2009-04-16
forum: General Help
---

### Post by Daremo_06 on 2009-04-16
I am having issues with firfox abruptly quitting as if I had killed it.  It happens on various pages, such as facebook, youtube, random forums, it doesnt seem to have a pattern other than perhaps flash/shockwave related maybe?

I realize that I don't really have alot of information as far as specific errors, so intially what I would like to know is what things should I collect to properly troubleshoot what could be causing this.  I know there is the error log in firefox's tools menu.  What other locations/logs should I be looking in and posting information from to help determine what the cause is?

I am currently on Intrepid x64 with the most recent firefox release (I believe its the most recent...).

Thanks!

---

### Post by andonato on 2009-04-16
I don't have any advice on a fix (sorry) but just wanted to say that I've abandoned Firefox completely on my Hardy installation due to such problems. Opera behaves much more nicely on my system.

---

### Post by Zill on 2009-04-16
Problems *can* be caused by extensions, rather than Firefox itself.

I suggest you systematically disable or (preferably) uninstall your extensions to find the culprit.

If Firefox continues to crash with no extensions installed then please repost with more information, such as the url it crashed on etc.  Also advise if it repeatedly crashes on the same url or can you sometimes run the same url with no errors.

---

### Post by ajgreeny on 2009-04-16
Check that you have the most up to date flash for your system as that seems to be the cause of many FF freezes and crashes.  Go direct to Adobe if you prefer and download the correct .deb version there.

---

### Post by codeseer on 2009-04-16
You an run this from the terminal and create a new profile that doesn't have any of the old settings or addons installed to it for testing:

```

firefox -profilemanager -no-remote

```

This is what I always do first when I encounter a reoccuring Firefox issue, because I have like 40 addons and custom configure Firefox. If it doesn't crash in the new profile, that lets you know it's a configuration issue in the profile or an addon issue. If it does continue to crash, it lets you know that there's a high level configuration issue or a plugin, like Flash, is to fault.

PS: Zill, your avatar rocks! :)

---

### Post by VastOne on 2009-04-19
> **codeseer said:**
> You an run this from the terminal and create a new profile that doesn't have any of the old settings or addons installed to it for testing:

```

firefox -profilemanager -no-remote

```

This is what I always do first when I encounter a reoccuring Firefox issue, because I have like 40 addons and custom configure Firefox. If it doesn't crash in the new profile, that lets you know it's a configuration issue in the profile or an addon issue. If it does continue to crash, it lets you know that there's a high level configuration issue or a plugin, like Flash, is to fault.

PS: Zill, your avatar rocks! :)

Tied this and my main crash site for FF worked...(Yahoo mail)

So I disabled everyone of my Add ons and Yahoo mail still crashed.  

Cannot figure this one out...but not to worried, I rarely use Yahoo mail, but MLB.com and ESPN.com crash as well

VastOne

Edit - Upon further checking, the crash of yahoo mail still happened and I finally traced it to an illegal instruction regarding a known issue with the AMD64 CPU Family 15 LAHF in 64-bit mode that is chronicled all over the net.  Hardware issue means a newer cpu in the very near future as there does no appear to be a resolution in sight...

---

### Post by codeseer on 2009-04-19
Then it's a plug-in or a setting that got altered by an addon. You could try disabling the plug-ins on a separate tab from where you view the addons. If that doesn't work, then your best option is to just move your addons to another profile and use that.

---

### Post by Zill on 2009-04-19
> **VastOne said:**
> ...Cannot figure this one out...but not to worried, I rarely use Yahoo mail, but MLB.com and ESPN.com crash as well...

The three sites you have mentioned all seem to use the Flash player.

I suggest you test your Flash installation with the following sites and if these fail to run correctly then reinstall Flash to get it working properly.

[http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/")

[http://www.adobe.com/products/flash/about/]("http://www.adobe.com/products/flash/about/")

[http://www.google.com/support/youtube/bin/answer.py?answer=56115&topic=10560]("http://www.google.com/support/youtube/bin/answer.py?answer=56115&topic=10560")

---

### Post by umechanism on 2009-04-19
I just posted this  [http://ubuntuforums.org/showthread.php?t=1130397](http://ubuntuforums.org/showthread.php?t=1130397)

It solved it for me.  Maybe it will solve it for you as well.

---

### Post by VastOne on 2009-04-21
> **Zill said:**
> The three sites you have mentioned all seem to use the Flash player.

I suggest you test your Flash installation with the following sites and if these fail to run correctly then reinstall Flash to get it working properly.

[http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/")

[http://www.adobe.com/products/flash/about/]("http://www.adobe.com/products/flash/about/")

[http://www.google.com/support/youtube/bin/answer.py?answer=56115&topic=10560]("http://www.google.com/support/youtube/bin/answer.py?answer=56115&topic=10560")

These 3 work perfectly

Did you see this?


Edit - Upon further checking, the crash of yahoo mail still happened and I finally traced it to an illegal instruction regarding a known issue with the AMD64 CPU Family 15 LAHF in 64-bit mode that is chronicled all over the net. Hardware issue means a newer cpu in the very near future as there does no appear to be a resolution in sight...VastOne

New hardware ordered!

---

### Post by Rackstar on 2009-04-21
You should also look at this thread:
[http://ubuntuforums.org/showthread.php?t=1100823&page=3](http://ubuntuforums.org/showthread.php?t=1100823&page=3)

---

### Post by Dileeshvar on 2009-04-21
> **umechanism said:**
> I just posted this  [http://ubuntuforums.org/showthread.php?t=1130397](http://ubuntuforums.org/showthread.php?t=1130397)

It solved it for me.  Maybe it will solve it for you as well.

Hi I did check out your thread but it wont solve my problem wt next ??
really bugging me :(

---

