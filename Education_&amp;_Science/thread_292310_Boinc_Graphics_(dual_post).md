---
title: "Boinc Graphics (dual post)"
date: 2006-11-03
forum: Education &amp; Science
---

### Post by autocrosser on 2006-11-03
I have a interesting "problem"--I want to display my Boinc Seti graphics in the Xwindow & would really like it to be a screensaver. 

The Debian Boinc Wiki indicates that graphics in the Xwindow is possible by:  xhost +local:

However, this worked one for me in Dapper & will not work in Edgy--I've talked to the developer of Xscreensaver & the maintainer of the Boinc Wiki & both have no ideas how to make this happen. I have contacted xorg-request list about this.

Any ideas anyone?

See: [http://wiki.debian.org/BOINC#head-ab...2bc2ff2b39e471]("http://wiki.debian.org/BOINC#head-abe25fe53a0df8c3f22f1e472d2bc2ff2b39e471")

I also posted this in the General area, but due to the speed of posting there--I thought that a second post would be helpful:-k

If anyone in talking about this--Please contact me--I am looking for the (a) way to do it--

---

### Post by braveerudite on 2007-04-22
This is something I'm very interesting in getting to work as well. Anyone?

---

### Post by mac.ryan on 2008-02-14
Don't know if you worked around the problem with Gutsy and following releases already, but here it is how I did:

```
sudo xhost +si:localuser:boinc
```

Cheers.

---

### Post by marquee moon on 2008-02-19
I run the climate prediction model on gutsy (Ubuntu 7.10) via BOINC & can &#8220;show graphics&#8221; if I type the following script into the terminal window: 

xhost +local:

At present, I need to type this in every time I login. Can I add the above text to a file so that it executes on startup?

Also interested in finding out if it can be adapted to be a screensaver.

---

### Post by mac.ryan on 2008-02-19
Somewhere I read that there was some concerns in adding the user local directly (this - apparently - is why it is disabled by default). For this reason, I preferred to add the user boinc instead.

As for making automatically load the command, I see two possibilities: either modifying the launcher of boinc-manager (you can put an "&" between the two commands and they will be executed in succession), either adding the command in an appropriate script in the folder /etc/init.d (What script it depends by your needs).

As for the screensaver, I have no clue.

Best luck!

---

### Post by scorptig on 2008-03-13
> **mac.ryan said:**
> Don't know if you worked around the problem with Gutsy and following releases already, but here it is how I did:

```
sudo xhost +si:localuser:boinc
```

Cheers.

Ok did following based on information obtained in forum

this command in your System-Preferences-Sessions-Startup Programs:
```
/usr/bin/xhost +local:
```

```
sudo xhost +si:localuser:boinc
```


Now where is the Seti Screensaver I have Boinc working, Seti is running within Boinc Manager, but no where do I see Screensaver within Screen preferences.

So  Yes, I'd appreciate more information, I like the Seti Screensaver.

Thanks in advance for any assistance.

---

### Post by ChrisC on 2008-08-11
I'm running BOINC on Ubuntu 8.04/hardy and can't get graphics to work.  I've tried both xhost commands above.  I did have it working in 6.06/Dapper.  Any tips?

I just want to be able to see the graphics manually (e.g. via "Show Graphics" button) once in a while, not run as a screensaver.  I want to see what the AstroPulse graphics look like :)

---

### Post by JohnnyVW on 2008-08-16
> **ChrisC said:**
> I'm running BOINC on Ubuntu 8.04/hardy and can't get graphics to work.  I've tried both xhost commands above.  I did have it working in 6.06/Dapper.  Any tips?

I just want to be able to see the graphics manually (e.g. via "Show Graphics" button) once in a while, not run as a screensaver.  I want to see what the AstroPulse graphics look like :)

I can't get it to show Astropulse either.  I can get Boinc to show me SETI@Home and Climate Prediction just fine by using xhost +local:

Hmmm....

---

