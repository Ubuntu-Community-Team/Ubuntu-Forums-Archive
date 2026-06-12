---
title: "HUD not working for Google Chrome? Is this normal"
date: 2012-06-21
forum: Desktop Environments
---

### Post by excetara2 on 2012-06-21
Hud won't work for google chrome. Is this normal and what apps will hud work with?

---

### Post by kc1di on 2012-06-21
> **excetara2 said:**
> Hud won't work for google chrome. Is this normal and what apps will hud work with?

what are you trying to do? 
if chrome is installed and you type google-chrome is should launch it. 

I personally use Chromium-browser it's in the ubuntu repository and works just as well as Chrome IMHO.

---

### Post by excetara2 on 2012-06-21
Yeah, I know about chromium. I mean the menu items working like in firefox? I'll see if they work in chromium.

---

### Post by vasa1 on 2012-06-21
> **kc1di said:**
> what are you trying to do? 
if chrome is installed and you type google-chrome is should launch it. 

I personally use Chromium-browser it's in the ubuntu repository and works just as well as Chrome IMHO.

HUD and Dash are different.

**Dash** is, among other things, for launching programs as you describe.

**HUD** is for easy access to menu items within a launched program and is most useful for deeply nested menu items (IMO).

Preference for Chromium-browser is not relevant and could lead to a whole A versus B type of thread rather than addressing OP's query.

---

### Post by excetara2 on 2012-06-21
Yes, HUD is for menu items like being able to close chrome or look at extensions or opening a new tab or etc...

Like in firefox you can type source or new tab to perform these menu actions. It doesn't recognize the chrome menu items when I've seen on some websites that it is supposed to be able to. Neither chrome nor chromium works in this regard as I've installed both to check. I've noticed it seems to only work with apps that integrate into the global menu.

Is there a way to get chrome working or is it supposed to work is my question??

---

### Post by excetara2 on 2012-06-21
I did uninstall the global menu at first install but now I have reinstalled it if that makes a difference.

---

### Post by vasa1 on 2012-06-21
I just logged into Unity 3D and HUD does work for Chrome. I'm on the latest Chrome stable
```
Google Chrome	19.0.1084.56 (Official Build 140965)
OS	Linux
WebKit	536.5 (@119244)
JavaScript	V8 3.9.24.29
Flash	11.2 r202
```

For example, after pressing the left alt key and typing **file**, I see options that involve File such as Open File, File Print, File New Tab, etc.

---

### Post by excetara2 on 2012-06-21
It doesn't work on mine. I have the latest chromium and google-chrome-beta (revision 20 something) because just to see if it would work. I did have google-chrome-stable prior which was that revision I believe. Any advice to look at why it's not work and what to do to get it working?? Can this be turned off? Uninstalling and reinstalling doesn't help of chrome.

---

### Post by vasa1 on 2012-06-21
> **excetara2 said:**
> It doesn't work on mine. I have the latest chromium and google-chrome-beta (revision 20 something) because just to see if it would work. I did have google-chrome-stable prior which was that revision I believe. Any advice to look at why it's not work and what to do to get it working?? Can this be turned off? Uninstalling and reinstalling doesn't help of chrome.
Sorry, I don't have any ideas. Does HUD work for you with other programs? Did it work with Chrome at any time for you?

As for turning it off, I've mostly found ways to disable the key that activates HUD. But preventing the HUD service from actually running, which it will do even if its key is disabled, is more complicated and I haven't looked at that.

---

### Post by kc1di on 2012-06-21
> **vasa1 said:**
> HUD and Dash are different.

**Dash** is, among other things, for launching programs as you describe.

**HUD** is for easy access to menu items within a launched program and is most useful for deeply nested menu items (IMO).

Preference for Chromium-browser is not relevant and could lead to a whole A versus B type of thread rather than addressing OP's query.
Thanks for the clarification. :)

---

### Post by excetara2 on 2012-06-21
I didn't deactivate HUD. I just deactivated the global menu which seemed to remove the menu items from interacting with hud in most programs. I am not sure if it ever worked with chrome. By the time I realized what the HUD did because use shortcut keys mostly anyway it wasn't working properly. I only installed 12.04 like a week ago.

---

### Post by zombifier25 on 2012-06-21
1. If you deactivate the global menu then HUD may not work.
2. I haven't touched Chrome much, but from the looks of it, it doesn't even use menus, so I guess HUD will not work on Chrome.

---

### Post by excetara2 on 2012-06-21
Yes, I was thinking that but I have re-enabled global menus and chrome seems to work on other peoples systems with hud and in some examples I've seen. Anyway, I'll just wait till HUD is more mature and assume something I did jimmy'ed it while messing with the install. Going to put 12.04 on my desktop soon and I'll see right after installation if it works with chrome.

---

### Post by vasa1 on 2012-06-21
> **zombifier25 said:**
> 1. If you deactivate the global menu then HUD may not work.
2. I haven't touched Chrome much, but from the looks of it, it doesn't even use menus, so I guess HUD will not work on Chrome.

I have said it works in an earlier post. :)
BTW, even the global menu works in Chrome :)
I use Chrome a lot :)

---

### Post by vasa1 on 2012-06-21
> **excetara2 said:**
> Hud won't work for google chrome. Is this normal and what apps will hud work with?
@excetara2, I'm putting up some images to show
[LIST]
[*]the "default" top left of Chrome
[*]the global menu appearing on hover
[*]the global menu working with Google Chrome and
[*]the HUD working with Chrome
[/LIST]
(That the performance of HUD isn't perfect is another issue. The lower items have nothing to do with Chrome and shouldn't be there, IMO. However, sadly, there's very little meaningful discussion about HUD here that I have come across.)

I don't know why HUD isn't working for you. You haven't answered my specific questions that I asked a couple of posts earlier. Anyway, if I come across anything potentially related, I'll post here.

Edit: Unfortunately, I don't know how to include the mouse cursor in a screenshot so you'll just have to believe me that I was hovering in pic #2.

---

### Post by excetara2 on 2012-06-22
Now it is working fine which is weird. Only thing I was messing with since was reinstalling the ati drivers because needed to create a new xorg.conf to enable dual screens. Maybe when I enabled ati driver originally something with that interfered. If not, then I'm not sure if it took a restart or four or five to recognize the menu items.

---

