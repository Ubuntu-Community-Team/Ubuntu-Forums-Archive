---
title: "Weather Indicator Stops"
date: 2012-07-05
forum: Desktop Environments
---

### Post by Sevlor on 2012-07-05
I am running unity and I have the my weather applet running from start-up. However, sometimes the applet will periodically shut itself off. Is there any way to fix this? Is anyone having this happen to them as well? It is kind of annoying having to constantly restart the indicator.
Thanks ):P

---

### Post by Kanoa on 2012-07-26
I am having the same problem and have not found a solution as of yet...

---

### Post by RezPix on 2012-07-26
If your using 3d unity, how did you add the weather applet? I cannot find out how to do it. Thanks.

---

### Post by miguelpires on 2012-07-27
All my computers don't update the Weather, anyone have the same problem?

---

### Post by cappuccino_se on 2012-07-27
> **miguelpires said:**
> All my computers don't update the Weather, anyone have the same problem?

Yes, same problem here. Worked fine yesterday.

---

### Post by miguelpires on 2012-07-27
> **cappuccino_se said:**
> Yes, same problem here. Worked fine yesterday.
Are any bug submite for us to join?

---

### Post by skep on 2012-07-27
If you look in the logfile (~/.cache/indicator-weather.log), you can see that it can't reach a certain url:

> [Fetcher] 2012-07-27 03:17:06,854 - ERROR - Weather: error reaching url 'http://www.earthtools.org/...'

Looking at this url (or googling it), it seems like it has fallen into the hands of spammers and right now the whole website is empty (or 404). So maybe we just have to wait till its repaired..*if* that is the reason of the current problems..

---

### Post by Frogs Hair on 2012-07-27
I have been using this application on 12.04 with success. [http://www.webupd8.org/2010/12/my-weather-indicator-new-ubuntu-weather.html](http://www.webupd8.org/2010/12/my-weather-indicator-new-ubuntu-weather.html)

---

### Post by xx58 on 2012-07-28
:rolleyes: Today is Saturday July 28, 2012 and Weather Indicator[COLOR=Red] still not working.[/COLOR]

---

### Post by Frogs Hair on 2012-07-28
> **xx58 said:**
> :rolleyes: Today is Saturday July 28, 2012 and Weather Indicator[COLOR=Red] still not working.[/COLOR]

Which one ? Indicator-weather from the repository has been crashing for some users. I haven't had any problems with the one at the link I posted.

---

### Post by jacksonpollack on 2012-07-28
> **Frogs Hair said:**
> Which one ? Indicator-weather from the repository has been crashing for some users. I haven't had any problems with the one at the link I posted.

Indicator-weather does not work currently for the reasons outlined by skep above - it's not crashing, but being unable to retrieve any data. My-weather-indicator works fine.

I prefer indicator-weather since it uses system weather icons and not a custom set that clashes with the other indicators. Not a big deal, but hopefully earthtools.org is fixed son.

---

### Post by moribashi on 2012-07-28
Still not working for me either... :(

---

### Post by jacksonpollack on 2012-07-28
[https://bugs.launchpad.net/weather-indicator/+bug/1030322](https://bugs.launchpad.net/weather-indicator/+bug/1030322)

---

### Post by Oldhacker on 2012-07-29
I installed the indicator that Frog's Hair recomended and it not only works but suppies more information than the one that is undergoing problems!

Thanks for the useful link.

---

### Post by MrsUser on 2012-08-07
Both weather apps not working for me. The one from the repositories stopped working (indicator-weather). And the my-weather-indicator only gives a crash report dialog when trying to start it.

Using Ubuntu 12.04 64-bit

---

### Post by garyzw on 2012-08-07
Delete the my-weather-indicator directory under  ~/home/.config.  Then restart the program. Seems to be related  to wunderground.com weather service.

---

### Post by MrsUser on 2012-08-09
> **garyzw said:**
> Delete the my-weather-indicator directory under  ~/home/.config.  Then restart the program. Seems to be related  to wunderground.com weather service.
That worked! Thanks a lot. I'm happy again :)

---

### Post by shlema on 2012-08-30
Doesn't work for me, unfortunately. After removing /home/.config/my-weather-indicator it still crashes right after I start it.

---

