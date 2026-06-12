---
title: "No date/time indicator in xubuntu"
date: 2012-08-20
forum: Desktop Environments
---

### Post by hampsterstory on 2012-08-20
I just installed xubuntu 12.04 parallel to xubuntu 11.10 ... But I can't get the date/time indicator to work in both of em ...
xfce4-indicator-plugin is installed ... the message and sound indicator is working!
please help me!

---

### Post by black veils on 2012-08-20
[SIZE=2]does this help:

scroll to the header [/SIZE][B][SIZE=2]Multiple Boot Systems Time Conflicts
[/SIZE][/B][https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by hampsterstory on 2012-08-20
uhm ... No ...  I'm sorry, my post is quite confusing ... :-|

I don't think it has something to do with the multiboot system, because the date/time indicator has never worked on the old system before.

It was my hope that the problem solves itself when a new version of ubuntu comes out ... But it appears that the *xfce4-indicator-plugin* isn't working with the* date/time indicator* ...

---

### Post by Toz on 2012-08-20
> **hampsterstory said:**
> I just installed xubuntu 12.04 parallel to xubuntu 11.10 ... But I can't get the date/time indicator to work in both of em ...
xfce4-indicator-plugin is installed ... the message and sound indicator is working!
please help me!

Is the DateTime plugin available as a choice to add to the panel? Or is it missing. If its missing, make sure that the **xfce4-datetime-plugin** package is installed. If it is installed but is not loading, can you post back the contents of your ~/.xsession-errors file:
```
pastebinit ~/.xsession-errors
```
...and post back the link that is generated.

Maybe something in there can help identify the source of the problem.

---

### Post by hampsterstory on 2012-08-20
The date/time **plugin** of the xfce panel is working fine, but I want to exchange it for the date/time **indicator**, because of it's integration of the calendar of evolution. 

However, I did upload the *.xsession-errors* here: [http://paste.ubuntu.com/1157863/](http://paste.ubuntu.com/1157863/)

There are several ones resembling this in the file: 
```
(xfce4-indicator-plugin:1768): xfce4-indicator-plugin-DEBUG: Excluding module: libdatetime.so
```As you can see the indicator is installed (as well as the gtk2-module), but this might be the reason why I can't get it to work! Is there any way to force the indicator-plugin to load a specific indicator-module.

Thanks for your help :)

---

### Post by Toz on 2012-08-20
I'm not able to test this, but what if you removed xfce4-datetime-plugin?

---

### Post by hampsterstory on 2012-08-21
OK ... I experimented with some package configurations ...

```
sudo aptitude -y install xfce4-datetime-plugin_ orage_ indicator-datetime-gtk2+ indicator-applet+ 
```After this reconfiguration and restarting the indicator-plugin on a fresh xubuntu-system, the datetime-indicator appears!

Any idea how to change the order of the indicators?! Right now the clock is between network-manager and sound-indicator and it looks kinda strange that way!

---

### Post by Toz on 2012-08-21
> **hampsterstory said:**
> Any idea how to change the order of the indicators?! Right now the clock is between network-manager and sound-indicator and it looks kinda strange that way!

I haven't tested it, but maybe this ([http://www.webupd8.org/2011/06/how-to-change-application-indicators.html]("http://www.webupd8.org/2011/06/how-to-change-application-indicators.html")) will also work on Xubuntu?

---

### Post by hampsterstory on 2012-08-22
> I haven't tested it, but maybe this ([http://www.webupd8.org/2011/06/how-t...ndicators.html]("http://www.webupd8.org/2011/06/how-to-change-application-indicators.html")) will also work on Xubuntu?This only works for the objects **in** the application-indicator. I tried it out, but it's not working on Xubuntu! However, I wanted to change the order of the indicators itself, since on Xubuntu it always seems to be: [Message][Sound][Date/Time][Application] This configuration looks rather ridiculous, because the application-indicator loads all kinds of applets and the time is somewhere in between.

But I managed to find out that my sole problem seems to be the application-indicator. I don't need it, it was just coming with the date/time indicator. But removing it via synaptic lets the date/time indicator vanish too ... So I got sick of the non-configurability of the indicators and simply deleted the application-indicator-libraries:
```
/usr/lib/indicators/7/libapplication.so
/usr/lib/indicators3/7/libapplication.so
```And now it's working: NO application-indicator BUT date/time-indicator!

Thanks for your help!!

BTW: If anyone has more elegant solutions, I'd be interested in those too ... ;)

---

