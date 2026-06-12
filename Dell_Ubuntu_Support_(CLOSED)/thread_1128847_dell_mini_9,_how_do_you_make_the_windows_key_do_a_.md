---
title: "dell mini 9, how do you make the windows key do a full screen?"
date: 2009-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shiningkenmonster on 2009-04-18
Back than in Oct/Nov of owning the dell mini 9 with Dell's custom Ubuntu on it. I would maximize my screen on openoffice and web browser (rebrand firefox) by just pushing the Windows logo button on my keyboard.

After The January updates it doesn't work anymore.

I read a post a while back about what do for my situation. someone told me to do this command line:

```
echo "keycode 115 = F11" > .Xmodmap

```

which made firefox maximize my screen. But not Openoffice.

However, due to the recent latest updates. The Windows key doesn't work anymore. Even running that command line doesn't work anymore.

What to do now to get my firefox to be more enjoyable by maximizing the screen? btw, there is no F11 key on all dell mini 9. I was thinking about flashing my bios

---

### Post by jaqrah on 2009-04-18
I don't know about the Dellbuntu version but in 8.10

System>Preferences>Keyboard Shortcuts

Scroll down until you find Window Management.  There you can change Maximize window to the Windows key (Super L).

If it is different in Dellbuntu, sorry.  I haven't used it for months.

---

### Post by shiningkenmonster on 2009-04-18
sorry, i wasn't clear. When I meant a Maximize screen I meant a Full Screen. Like the F11 button

---

### Post by jaqrah on 2009-04-18
Same directions previous post

there is a Toggle Full Screen (instead of Maximize window)which can be set to Windows key (Super L) :)

---

### Post by shiningkenmonster on 2009-04-18
oh thanks for helping. I just tried it. It only takes the bottom taskbar and the top Ubuntu logo menu bar away. It only toggles the browser. It still shows the Firefox orange bar(the theme color), URL bar, buttons and all the tabs.

I was looking for a F11 effect.

the Toggle Full Screen does make my internet experience a little bit better.

However it still takes up about 3/4 of an inch. Having a small 8.9 inch screen doesn't help too.

---

### Post by armandh on 2009-04-18
later bios updates allow for a F-11 and F-12 using the function key and a letter key [I forget which]

---

### Post by jaqrah on 2009-04-18
Third time is the charm?

Is it Maximus you are talking about?  Check in Synaptic Package Manager to see if that app is installed.

But I have to tell you, when I toggle Full Screen with Windows key, it really does go Full Screen for all apps except Firefox.  In Firefox, it removes everything but the toolbars (which I want).  Maybe our Firefoxes, are customised differently?

There is also a firefox add-on I would suggest. Compact Menu for Firefox

[https://addons.mozilla.org/en-US/firefox/addon/4550](https://addons.mozilla.org/en-US/firefox/addon/4550)

Just one less thing taking up screen space.

Sorry if I haven't found the right answer yet.

---

### Post by Kensoi on 2009-04-18
[http://ubuntuforums.org/showthread.php?t=1112215](http://ubuntuforums.org/showthread.php?t=1112215)

May Be Helpfull.

---

### Post by lswartz on 2009-04-18
F11 = Fn z
F12 = Fn x

---

### Post by rmjb on 2009-04-18
It seems that the maximus tool mapped the Windows key to Ctrl+Alt+f to do the full screen in Firefox and Open Office. This key combo does work in these apps, I checked.

An update to maximus broke this functionality though. I'm not sure how to get it back.

- rmjb

---

### Post by buzzware on 2009-04-18
I was able to get it to work by changing the key mapping in Maxumus to Super+L.  Works like it did with the Dell Ubuntu.  No other tweaks needed.

---

### Post by rmjb on 2009-04-20
How did you configure Maximus?

---

### Post by ugm6hr on 2009-04-20
> **lswartz said:**
> F11 = Fn z
F12 = Fn x

If you have BIOS v2-4, which are not technically supported for Dell Ubuntu.

BIOS v2 should be OK though.

Funny, my xmodmap command still works for FF.

---

