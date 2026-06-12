---
title: "Parole Media Player won't play music CD"
date: 2014-05-20
forum: Desktop Environments
---

### Post by jrr2 on 2014-05-20
Newbie with Xubuntu 14.04

I inserted a pre recorded music CD in my pc and Parole Media Player automatically opened. When pressing play a notice came up that said:
"Error: GStreamer backened error 
could not handle CDDA URI"

Any suggestions?

---

### Post by calitropex on 2014-05-20
Hi,

Not sure if it helps exactly, but there seems to be a known bug with Parole ([https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1309951](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1309951)). Rather than recommending you start installing specific packages, try installing another music player (like Rythmbox etc) and seeing if you have any success that way.

---

### Post by jrr2 on 2014-05-20
> **calitropex said:**
> Hi,

Not sure if it helps exactly, but there seems to be a known bug with Parole ([https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1309951](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1309951)). Rather than recommending you start installing specific packages, try installing another music player (like Rythmbox etc) and seeing if you have any success that way.

Thanks, but that bug seems to be regarding video, and it seems that they already released a bug fix. I have taken all updates.

---

### Post by Dennis N on 2014-05-20
I get the same error with Parole and audio CDs. There are a few references on the web to this, such as:

[http://osdir.com/ml/ubuntu-users/2014-04/msg00625.html](http://osdir.com/ml/ubuntu-users/2014-04/msg00625.html)

None that I looked at have a solution for Parole. I suggest you install and use Audacious to play audio CDs. From the menu: 

Services > Play CD

---

### Post by jrr2 on 2014-05-22
> **Dennis N said:**
> I get the same error with Parole and audio CDs. There are a few references on the web to this, such as:

[http://osdir.com/ml/ubuntu-users/2014-04/msg00625.html](http://osdir.com/ml/ubuntu-users/2014-04/msg00625.html)

None that I looked at have a solution for Parole. I suggest you install and use Audacious to play audio CDs. From the menu: 

Services > Play CD

Thanks, helpful to know you have same problem. Yes, that link is the correct problem, but it doesn't seem to have officially been reported as a bug. Funny, just got a "parole" update from software updates, but it did not affect this issue.


Again, I am new to linux. The other thing I noticed was when inserting the CD and the icon appears on the desktop, it says it is "unmounted"--not overly clear on what that means, but could that be an issue too? 


Also, is there a way for me to report this Parole bug to Xubuntu? I'm assuming that they try and fix this sort of thing since it is the only media player that comes with Xubuntu.


I appreciate the suggestion to just install another player, but I can't believe that xubuntu would not address such a fundamental problem in the media player they so "proudly" chose. I've been impressed with Xubuntu and would be very disappointed if this is not addressed.

---

### Post by apsaras on 2014-05-22
I've submitted a bug report at

[https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384) 

If you think it's the same bug that affected you, then please click the "Does this bug affect you?" link at the top (and consider adding a reply if you have further helpful information). The more people it is known to affect, the more attention it is likely to get.

It's a strange bug to have because it's so basic. If you need a workaround right now, then you can probably install another music player.

---

### Post by Dennis N on 2014-05-22
Not really a bug, it's just an incorrect command. 

Here is how to get audio CDs to play:

In the Xubuntu Settings Window: Hardware > Removable Drives and Media > Multimedia Tab

In the Audio CDs section, change the Command to:  

[B][FONT=Courier New]parole --device=% cdda://[/FONT]
[/B]
It will now play an audio cd when one is inserted.

[http://xubuntu.fr/forum/viewtopic.php?f=2&t=2343](http://xubuntu.fr/forum/viewtopic.php?f=2&t=2343)

---

### Post by jrr2 on 2014-05-22
> **apsaras said:**
> I've submitted a bug report at

[https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384) 

If you think it's the same bug that affected you, then please click the "Does this bug affect you?" link at the top (and consider adding a reply if you have further helpful information). The more people it is known to affect, the more attention it is likely to get.

It's a strange bug to have because it's so basic. If you need a workaround right now, then you can probably install another music player.

Thanks. I agree, if everyone just installs something else, it won't get noticed. And, yes, that was my point about it being "so basic"-- if you include one media player and it can't even play a CD, that's a big problem!

Ironically, I'm having a bug with launchpad too. When I logged on to add to your report, it shows  my name and email and asks you to checkmark which one you want made public. Well, they both are checked and I can't uncheck my email. Does this happen to anyone else? To be clear: I don't want my email public.

---

### Post by Dennis N on 2014-05-22
@jrr2

See Post #7.

---

### Post by apsaras on 2014-05-22
> **jrr2 said:**
> Ironically, I'm having a bug with launchpad too. When I logged on to add to your report, it shows  my name and email and asks you to checkmark which one you want made public. Well, they both are checked and I can't uncheck my email. Does this happen to anyone else? To be clear: I don't want my email public.

I believe that's only the Launchpad system itself that is requiring your email address (for notifications, and possibly to help ensure you're a human, not a spam machine).

What gets divulged to other users is a separate matter and you can control that by going to "Change details" and selecting "Hide my email address from other Launchpad users".

---

### Post by apsaras on 2014-05-22
> **Dennis N said:**
> 
In the Audio CDs section, change the Command to:  

[B][FONT=Courier New]parole --device=% cdda://[/FONT]
[/B]
It will now play an audio cd when one is inserted.

Thanks for the reply, but after your suggested change it still fails for me in exactly the same way.

Incidentally, I get the same effect by typing

**parole --device=/dev/cdrom cdda://**

on the command line.

---

### Post by Dennis N on 2014-05-22
Are you sure you entered it correctly? Worked for me and the guy in France. Maybe copy and paste.

---

### Post by jrr2 on 2014-05-22
> **apsaras said:**
> I believe that's only the Launchpad system itself that is requiring your email address (for notifications, and possibly to help ensure you're a human, not a spam machine).

What gets divulged to other users is a separate matter and you can control that by going to "Change details" and selecting "Hide my email address from other Launchpad users".

Thanks. I went ahead and clicked it affects me too and now it says bug "confirmed."

About how many people need to do that before it gets their attention?

---

### Post by jrr2 on 2014-05-22
> **Dennis N said:**
> Not really a bug, it's just an incorrect command. 

Here is how to get audio CDs to play:

In the Xubuntu Settings Window: Hardware > Removable Drives and Media > Multimedia Tab

In the Audio CDs section, change the Command to:  

[B][FONT=Courier New]parole --device=% cdda://[/FONT]
[/B]
It will now play an audio cd when one is inserted.

[http://xubuntu.fr/forum/viewtopic.php?f=2&t=2343](http://xubuntu.fr/forum/viewtopic.php?f=2&t=2343)

I have not tried this, but it sounds like you are saying it is a "bug" in the xubuntu set up rather than Parole itself. I still think it's a good idea to report it. Maybe you can do so and add your suggestion to the report? Thanks.

---

### Post by Dennis N on 2014-05-23
> **jrr2 said:**
> I have not tried this, but it sounds like you are saying it is a "bug" in the xubuntu set up rather than Parole itself. I still think it's a good idea to report it. Maybe you can do so and add your suggestion to the report? Thanks.

Well, I don't take any credit for this solution. It was given on the French-speaking Xubuntu forum at the link. I tried it and it worked. Just passing it along. 

In both Xubuntu 12.04 and 13.04, Parole starts playing audio CDs automatically as it is supposed to (I checked). The command used in both that works is **[FONT=Courier New][COLOR="#FF0000"]parole --device:%d[/COLOR][/FONT]**. This is the same command that is given in 14.04 and does not work. Did something change in Parole for 14.04 to require a different command, and no one thought to change it from the old command in the settings? Could be. These guys have a lot to look at in their testing. Maybe no one thought to test CD play.

---

### Post by apsaras on 2014-05-23
> **Dennis N said:**
> Are you sure you entered it correctly? Worked for me and the guy in France. Maybe copy and paste.

Oops, you are right. I had just added **cdda://** and not noticed the change in the **--device** line. Now working fine, thanks.

---

### Post by Dennis N on 2014-05-23
Did you see that Parole has a menu item pointing to a bug reporting site?

Menu > Help > Report a Bug

Bug 10902 reported May 22 is this same problem. It has already been assigned to someone.

---

### Post by apsaras on 2014-05-24
> **Dennis N said:**
> Did you see that Parole has a menu item pointing to a bug reporting site?

Menu > Help > Report a Bug

Bug 10902 reported May 22 is this same problem. It has already been assigned to someone.

Good point. That looks like it is going to the Xfce guys, "upstream" of Xubuntu (which I think is what the Launchpad system caters for). I don't really know if the problem here is with Xubuntu, Xfwm or Xfce not invoking Parole correctly, or with Parole not handling input correctly, so maybe it's not a bad thing that these people see it too. Would you like to contribute the fix from the French site to this report? I already added it to the Launchpad report. (This hopefully helps people fix it and also people googling the bug and looking for workarounds.)

---

### Post by apsaras on 2014-05-24
> **jrr2 said:**
> Thanks. I went ahead and clicked it affects me too and now it says bug "confirmed."

About how many people need to do that before it gets their attention?

It's a bit of a lottery, depending on how active the developers are. But at least you clicking the "affects me too" button has raised its status to "confirmed".

---

### Post by Elfy on 2014-05-24
> **apsaras said:**
> It's a bit of a lottery, depending on how active the developers are. But at least you clicking the "affects me too" button has raised its status to "confirmed".

They are active.

I've added the xfce bug to the LP bug.

Works better for this type of issue if the bug's reported at [https://bugzilla.xfce.org](https://bugzilla.xfce.org) as well if you can then link them.

---

