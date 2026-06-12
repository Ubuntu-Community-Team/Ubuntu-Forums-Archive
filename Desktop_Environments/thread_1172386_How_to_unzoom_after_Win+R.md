---
title: "How to unzoom after Win+R?"
date: 2009-05-28
forum: Desktop Environments
---

### Post by Dakkus on 2009-05-28
Hi! Often having to switch between two computers, I easily end up pressing Win+R instead of Alt+F2. This causes a disaster on my screen.

I found a bug report regarding the problem:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220939](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220939)

In that bug report it is mentioned that there is a way out of the problem, but unluckily it is not mentioned, what the way out is. At least googling for:
"win+r" ubuntu

didn't bring up anything useful. Adding "unzoom" to the search phrase didn't help either.

So, what are the secret buttons I have to press on my keyboard in order to return to normality without rebooting?
Also, because I surely am not the first one having this usage impairing problem, it would be nice if the page that is found with the above search term would include the actual spell for reverting the mistake.

---

### Post by coffeecat on 2009-05-28
The third post of the launchpad thread tells you (indirectly) what to do. This is a function of Compiz. It's nothing to do with Ubuntu specifically, nor of Gnome. Look in CompizConfig Settings Manager > Accessibility > Enhanced Zoom Desktop. Under the Zoom Area Movement tab you'll see that Super+R (Super=Windows key) is assigned to "Fit zoomed area to window". If this is bothering you, either disable that function, or disable Enhanced Zoom Desktop.

There is, however, a way to reverse Super+R if you don't want to disable any of your Compiz settings. Having zoomed with Super-R, press Super-E, which will give you Expo view, select your desktop (if necessary), and then press enter.

---

### Post by mrog on 2009-05-28
Well, that was fun. I tried it - not knowing what would happen - and experienced your joy.

Anyway, here's how to fix it. 

1. Press <Alt>F2
2. Enter gconf-editor
3. Go to: apps/compiz/plugins/ezoom/allscreens/options
4. Either change "fit_to_window_key" to "Disabled" or change "zoom_out_key" to "<Super>l" if you think this feature could ever be beneficial to you.

---

### Post by rklk on 2009-06-06
I found out that you could also use super+mouse-scroll to zoom out by default ;)

---

### Post by monkeyking on 2009-07-14
> **rklk said:**
> I found out that you could also use super+mouse-scroll to zoom out by default ;)

Thanks mate

---

### Post by weasel5i2 on 2011-07-26
Hello,

If you hit WIN+1 it should also restore the zoom foobar caused by WIN+R.
I learned this the hard way as well.

Regards,
  weasel5i2

---

