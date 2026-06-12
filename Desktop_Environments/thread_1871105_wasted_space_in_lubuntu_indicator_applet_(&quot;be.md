---
title: "wasted space in lubuntu indicator applet (&quot;benachrichtigungsfeld&quot;)"
date: 2011-10-28
forum: Desktop Environments
---

### Post by Bazon on 2011-10-28
hello,
in lubuntu, i always get a strange wasted space in the indicator applet. *("Benachrichtigungsfeld" in German, I'm not completly sure how it is called in English.)*
See attachment.

How can I get rid of this wasted space?

---

### Post by amjjawad on 2011-10-28
> **Bazon said:**
> hello,
in lubuntu, i always get a strange wasted space in the indicator applet. *("Benachrichtigungsfeld" in German, I'm not completly sure how it is called in English.)*
See attachment.

How can I get rid of this wasted space?

Hello Bazon,


[LIST=1]
[*]Right Click on LXPanel
[*]Panel Settings
[*]Panel Applets (tab 3)
[*]Check if there are spacers. If yes, double click on it and check the size of it. Default is 2
[/LIST]

---

### Post by amjjawad on 2011-10-28
A side note, I prefer to use [Absolute Beginners Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") Forum or [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") Forum :)
Just make sure to use [lubuntu] prefix and I see you did it already :)

Thank you!

---

### Post by Bazon on 2011-10-28
Yes, there are spacers (siced 4), but the don't cause the useless gap. resizing or replacing them doesn't change *that* gap.

The gap / wasted space moves with the "Benachrichtigungsfeld". *(Which is "System Tray" as I suppose according to your screenshot.)*

---

### Post by amjjawad on 2011-10-28
> **Bazon said:**
> Yes, there are spacers (siced 4), but the don't cause the useless gap. resizing or replacing them doesn't change *that* gap.

The gap / wasted space moves with the "Benachrichtigungsfeld". *(Which is "System Tray" as I suppose according to your screenshot.)*

Have you added that? it could be a System Tray OR Application Launch Bar. One way to find out: Move it up or down to see which type of Applets you have added.
Then, you could easily remove it and re-added it again.

What kind of applications is that anyway?

---

### Post by Bazon on 2011-10-28
No, I didn't added it, it was there by default. 
And by moving up/down, I'm really sure the gap is linked to "Benachrichtigungsfeld" / Sys-Tray: The gap moves with that element.

---

### Post by Bazon on 2011-10-28
Here is another screenshot (from my other lubuntu netbook) where you can see the wasted space again and what appelts are used.
("spacer" = "Abstand" - left of the thing I'm talking about.)

---

### Post by amjjawad on 2011-10-28
> **Bazon said:**
> No, I didn't added it, it was there by default. 
And by moving up/down, I'm really sure the gap is linked to "Benachrichtigungsfeld" / Sys-Tray: The gap moves with that element.

By default? what does it mean in English?

Ok, as I mentioned previously, please remove it and add it again. Let's see what could happen!

---

### Post by croque on 2011-10-28
Sounds like you may be encountering this problem:

[http://ubuntuforums.org/showthread.php?t=1869357](http://ubuntuforums.org/showthread.php?t=1869357)

If so, consider adding a comment to the bug report(s) over on Launchpad so it will get fixed quicker.

---

### Post by pjalegria on 2011-10-28
I had the same problem, i just solved with a fresh install

---

### Post by ac_d600 on 2011-10-28
I had this problem when I tried the Linux Mint Lxde version, thankfully
I have never seen it in Lubuntu.

What you could maybe do is create a new dock and delete the one that is
giving you trouble?

---

### Post by amjjawad on 2011-10-28
OK guys, slow down a bit :D
I need more information about that.

Can you produce it?
What version of Lubuntu you guys are using?
Have you updated your system after installation? 
```
sudo apt-get update && sudo apt-get upgrade
```

The more information you provide, the better.

Waiting for your feedback :)

---

### Post by croque on 2011-10-28
If it's the same problem described over in that other thread ([http://ubuntuforums.org/showthread.php?t=1869357](http://ubuntuforums.org/showthread.php?t=1869357)) then it seems to be related to the xfce power manager battery icon. When I turned off the battery icon, extra space was not added to the tray after every suspend.

I posted the details on how to disable the battery icon in that thread if you want to test it on your system.

@amjjawad I'm testing this on an eeepc 1005ha running a freshly installed and updated Lubuntu 11.10.

---

### Post by Bazon on 2011-10-29
Yes, for me it's definitly the thins with the power manager tray icon / suspend, too.
After some standbys the gap increased enormously.... 
(see screenshot).

I'll continue to write in the [other thread...]("http://ubuntuforums.org/showthread.php?p=11405263#post11405263")

---

### Post by amjjawad on 2011-10-29
> **Bazon said:**
> I'll continue to write in the [other thread...]("http://ubuntuforums.org/showthread.php?p=11405263#post11405263")

And please don't forget to update your thread as well :)

The other thread is linked now already so you just need to update your thread once you get some news :)

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-27
Hi I have another thread over here that is dealing with the same problem...
[http://ubuntuforums.org/showthread.php?t=2094366&page=2](http://ubuntuforums.org/showthread.php?t=2094366&page=2)  I will post this in the linked thread as well

---

### Post by overdrank on 2012-12-27
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

