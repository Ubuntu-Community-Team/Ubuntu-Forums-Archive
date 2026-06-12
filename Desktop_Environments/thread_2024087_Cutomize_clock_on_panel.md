---
title: "Cutomize clock on panel"
date: 2012-07-13
forum: Desktop Environments
---

### Post by yoramdavid on 2012-07-13
Hi all,

I have Ubuntu 12.04 gnome-classic (no effects).
I would like to customize the way the date and time on the clock is displayed.
Ideally, I would like to have those in two lines, the date on top and the time on the bottom.

All I found are old threats that point to gconf-editor then &#8220;Apps > Panel > Applets > Clock_Screen* > Prefs&#8221;

Well, on the gconf-editor there is no such thing as Applets, not in normal user, nor in sudo mode.

I also followed this threat: [http://ubuntuforums.org/showpost.php?p=11818848&postcount=11](http://ubuntuforums.org/showpost.php?p=11818848&postcount=11)
Nothing happens when I run the commands


Any help is appreciated.

Thank you.

---

### Post by stinkeye on 2012-07-13
Those commands work here in my gnome classic session on 12.04

Can't really remember now, but I think on 11.10 you still use gconf-editor as it was still a gnome applet.
Have a look around at **gconf-editor > /apps/panel/applets**
for your date/time applet.
Same method....change format to custom then put in your custom format.

Back to original question, this blog has some custom code for
a two line date/time.
[**_[COLOR="DarkRed"]http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing-ubuntu-9-10-karmic-koala[/COLOR]_**]("http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing-ubuntu-9-10-karmic-koala")
See #7

---

### Post by yoramdavid on 2012-07-13
> **stinkeye said:**
> Those commands work here in my gnome classic session on 12.04

Can't really remember now, but I think on 11.10 you still use gconf-editor as it was still a gnome applet.
Have a look around at **gconf-editor > /apps/panel/applets**
for your date/time applet.
Same method....change format to custom then put in your custom format.

Back to original question, this blog has some custom code for
a two line date/time.
[**_[COLOR="DarkRed"]http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing-ubuntu-9-10-karmic-koala[/COLOR]_**]("http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing-ubuntu-9-10-karmic-koala")
See #7

Thank you.
I have Ubuntu 12.04 not 11.10 (I added that info on my threat).
I installed dconfeditor and there seem to be some options in it, but whatever I do there does not change anything.

I saw that threat before, if only I could find where to insert that code... but the place they say to look at does not exist on my gconf.

Something must be overwriting what I do on dconf or with the command line.

---

### Post by kansasnoob on 2012-07-13
> Ideally, I would like to have those in two lines, the date on top and the time on the bottom.

I don't know how to do that but thought I'd share a wee bit of knowledge. In both Oneiric and Precise there are two different clock options for the classic session. The clock that is part of either 'indicator-applet-complete' or 'indicator-applet-session', and the standard clock applet.

I posted a screenshot somewhat displaying the difference in Precise here:

[http://ubuntuforums.org/showpost.php?p=11900657&postcount=12](http://ubuntuforums.org/showpost.php?p=11900657&postcount=12)

For a bit better explanation look at step #2 here for Precise:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Or, for Oneiric look at step #2 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

Note: the difference is that a PPA was required in Oneiric to install (or reinstall) 'indicator-applet', 'indicator-applet-complete', or 'indicator-applet-session', but NOT in Precise.

Sorry I couldn't provide a better answer but thought that might help a little bit :)

---

### Post by yoramdavid on 2012-07-13
> **kansasnoob said:**
> I don't know how to do that but thought I'd share a wee bit of knowledge. In both Oneiric and Precise there are two different clock options for the classic session. The clock that is part of either 'indicator-applet-complete' or 'indicator-applet-session', and the standard clock applet.

I posted a screenshot somewhat displaying the difference in Precise here:

[http://ubuntuforums.org/showpost.php?p=11900657&postcount=12](http://ubuntuforums.org/showpost.php?p=11900657&postcount=12)

For a bit better explanation look at step #2 here for Precise:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Or, for Oneiric look at step #2 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

Note: the difference is that a PPA was required in Oneiric to install (or reinstall) 'indicator-applet', 'indicator-applet-complete', or 'indicator-applet-session', but NOT in Precise.

Sorry I couldn't provide a better answer but thought that might help a little bit :)

Thank you kansasnoob,

I added both the "complete indicator applet" and the "clock applet" and they both show the same time and date format.
I followed the second threat after I installed Ubuntu 12.04.

Thanks again.

---

### Post by stinkeye on 2012-07-13
> **kansasnoob said:**
> I don't know how to do that but thought I'd share a wee bit of knowledge. In both Oneiric and Precise there are two different clock options for the classic session. The clock that is part of either 'indicator-applet-complete' or 'indicator-applet-session', and the standard clock applet.

I posted a screenshot somewhat displaying the difference in Precise here:

[http://ubuntuforums.org/showpost.php?p=11900657&postcount=12](http://ubuntuforums.org/showpost.php?p=11900657&postcount=12)

For a bit better explanation look at step #2 here for Precise:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Or, for Oneiric look at step #2 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

Note: the difference is that a PPA was required in Oneiric to install (or reinstall) 'indicator-applet', 'indicator-applet-complete', or 'indicator-applet-session', but NOT in Precise.

Sorry I couldn't provide a better answer but thought that might help a little bit :)

Yeah you're right.
I dont use classic and I was just having a look and the 
**indicator complete ** will work with the gsettings.
Uses unity indicator.

I put in this code for a 2 line format and increased the panel height to 36.
```
gsettings set com.canonical.indicator.datetime time-format custom && gsettings set com.canonical.indicator.datetime custom-time-format '<sup><span rise="1000" font_desc="Droid Sans 9" color="#ffffff" weight="bold">%a %d %b</span></sup>%n<sub><span rise="6000" font_desc="Droid Sans 10" color="#ffffff" weight="bold">%I:%M %p</span></sub>'
```

---

### Post by yoramdavid on 2012-07-13
> **stinkeye said:**
> Yeah you're right.
I dont use classic and I was just having a look and the 
**indicator complete ** will work with the gsettings.
Uses unity indicator.

I just logged off from gnome-classic and logged on on Unity 2D (3D is not available) and the time displays different there. It displays as it is set in [http://ubuntuforums.org/newreply.php?do=newreply&p=12099197&nojs=1#helpmenuthe](http://ubuntuforums.org/newreply.php?do=newreply&p=12099197&nojs=1#helpmenuthe) regional settings, ie: Friday 13 July, 12:20:59 (that is how we display the date in Portugal)
In gnome-classic the month comes after the day, ie: Friday July 13, 12:20:59, why would that be??
I once had a bug after an update where my system got in Chinese, programs and all, everything, would that be a trace of that?
I still have a Chinese entry (greyed out) on the language support I cannot get rid off.

Cheers.

---

### Post by yoramdavid on 2012-07-14
Nobody?

I am starting to think it is a bug.

---

### Post by yoramdavid on 2012-07-15
Perhaps there is a package which could substitute the clock applet?

---

### Post by stinkeye on 2012-07-15
All three sessions...
[LIST]
[*]Ubuntu
[*]Ubuntu 2d
[*]Gnome Classic (using the indidator complete applet)
[/LIST]
display whatever [COLOR="red"]I use[/COLOR] with...
```
gsettings set com.canonical.indicator.datetime **custom-time-format** '[COLOR="Red"]%a %b %e, %l:%M %P[/COLOR]'
```
after setting time-format to custom
```
gsettings set com.canonical.indicator.datetime **time-format** custom
```

---

### Post by yoramdavid on 2012-07-16
Thank you, it is not the case on my system, nothing I do or change via the command lines, gconf or dconf, changes a thing.

---

