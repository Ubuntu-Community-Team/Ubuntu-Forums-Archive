---
title: "Gnome-panel clock applet crashes the panel with Hardy"
date: 2008-04-30
forum: Desktop Environments
---

### Post by Zeedok on 2008-04-30
I am enjoying my new Hardy 8.04 upgrade so far, but I have noticed that the 'clock' applet, with the new world clock etc is now crashing my panel.

I have a number of panel applets (deskbar, sticky notes, volume, network manager etc) and they seem to be working fine, but when I click on the clock applet, instead of opening, the whole panel freezes and I have to kill the process in system monitor.  Once I do that it opens again and works fine, until I click on the clock applet again!

I am running compiz fusion, emerald and preload (in case that is relevant) and I have reinstalled gnome-panel via synaptic to no avail.  I'm not sure if this is 'bug'-report worthy, or whether I have mucked up some setting.

I would appreciate any suggestions that might solve this for me.

---

### Post by Zeedok on 2008-05-01
Bump - anyone??

---

### Post by brimlar on 2008-05-01
I've experienced this problem as well.  I was just about to go looking for other threads here.

I've been killing gnome-panel (which then automatically restarts itself) to get past the freeze, personally.

---

### Post by Zeedok on 2008-05-02
Thanks for the reply, it gets lonely without even a 'me too' response. I have been killing gnome panel as well. Surely there is a clever super user who can help? Even if you guys viol it is worth a bug report, please give me your suggestions!

---

### Post by brimlar on 2008-05-02
Some people are saying that the Google Calendar plugin in Evolution is causing some freezes, so I disabled the Google plugin in Evolution just to see if it has an impact.

---

### Post by JanLN on 2008-05-02
I removed Evolution, and that solved the problem. I am using Mozilla Thunderbird as my mailprogram.

---

### Post by AldenIsZen on 2008-05-02
I have noticed issues when trying to get the Google Calendar to work, which still doesn't...

---

### Post by Zeedok on 2008-05-02
Thanks Guys - I think we've found the problem.  By 'unchecking' my google calendar in evolution my problem is solved.  The clock/weather applet no longer crashes my panel.  I must say I don't use evolution that much anyway - more a fan of gmail and google calendar, just tried to hook up gCal to 'see if I could'.

I think this is worth a bug report - I'll do that now.

Thanks again for your help.

---

### Post by Zeedok on 2008-05-02
Actually - it already seems to have been reported:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/202569](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/202569)

and

[https://bugs.launchpad.net/ubuntu/+bug/221754](https://bugs.launchpad.net/ubuntu/+bug/221754)

One person reckons that deleting and reinstalling the google calendar in evolution fixes the problem - I might try that.

Thanks again for everyone's input

---

### Post by Zeedok on 2008-05-08
I have resurrected this problem, somehow.

I was using the mail applet on AWN, which seemed to cleverly set up all my Gmail accounts in Evolution with a single click and now the panel crashes again.  This time however, unchecking doesn't seem to fix the problem.

I think I saw that this bug was being fixed, I've updated my system (there was an evolution update included) but no success.

Can anyone help?

---

### Post by Zeedok on 2008-05-08
I think the update has actually worked.  I found that the crashes stopped after I unchecked, then rechecked my google calendar in evoultion.

Now when I click on the panel applet it can take a few seconds to open, but it does not seem to crash.

Go figure.

---

### Post by Hayjumper on 2008-05-10
I've been having this problem for a week or two now, just found this thread myself.  I found when opening Evolution and clicking on the Calendars tab, a policykit window opened asking me to authenticate.  I clicked "always allow", and now I can click on the time/date and the calendar/locations applet is properly displayed, no freeze, even after I closed Evolution.

I am going to reboot & will edit this post if the problem reoccurs, but I suspect the authentication dialog was the problem & it should work always now.

---

### Post by PRGUY85 on 2008-05-19
Had same problem, fixed it by unchecking the Google Calendar box.  Any idea how to incorporate google calendar to the ubuntu desktop?

---

### Post by edrex on 2008-08-18
Thanks PRGUY85, great sleuthing! Solves [#213944]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/213944").

> **PRGUY85 said:**
> Had same problem, fixed it by unchecking the Google Calendar box.  Any idea how to incorporate google calendar to the ubuntu desktop?

---

### Post by chimiasanchi on 2008-10-02
> **Zeedok said:**
> I think the update has actually worked.  I found that the crashes stopped after I unchecked, then rechecked my google calendar in evoultion.

Now when I click on the panel applet it can take a few seconds to open, but it does not seem to crash.

Go figure.

i had the same experience. I never would have thought that would work. thanks!

---

### Post by DeadlyDave on 2009-08-07
I would not have considered that google calendar in evolution was the problem since the problem occurs when evolution isn't active.  I unchecked google calendar, though, and lo and behold the clock applet doesn't crash now!  Thank you.

---

