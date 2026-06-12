---
title: "Firefox 11.0  F11 fulscreen shortcut problem"
date: 2012-04-08
forum: Desktop Environments
---

### Post by chaceos on 2012-04-08
I use lucid and I love it.
Before the upgrade made available for Firefox 10,  F11 key was exactly the same as View--> Fullscreen. Now F11 is not equal  to View ---> Fullscreen.

View---> Fullscreen is Fullscreen (hides menu-add on-location-bookmark toolbars & window title bar).
But F11 does only hide the title  bar of Firefox window. Of course F11 was a very useful shortcut and of  course not having a full screen is more preferable than going every time  to View---> Fullscreen.

Can anyone enlighten me?

The same problem was mentioned in a dead thread
( [http://ubuntuforums.org/showthread.php?t=1141724](http://ubuntuforums.org/showthread.php?t=1141724) )

I'm afraid I'm the second human on the internet having these isues :confused:

---

### Post by lovinglinux on 2012-04-08
Type **about:config** in the address bar to bring the advanced properties. Type *browser.fullscreen.autohide* in the filter, make sure the resulting preference is set to true. If not, double-click it.

If that doesn't solve the problem, start Firefox in safe mode:

```
firefox -safe-mode
```

If it works that way, then you have an extension preventing FF to enter fullscreen. It could be an extension bug or a feature you don't remember.

If you still can't get it to work, please post a screenshot of both conditions so I can take a look.

You could also try a clean profile:

```
firefox -P
```

---

### Post by chaceos on 2012-04-08
lovinglinux thank you very much

I tried all your suggestions but nothing.
- The browser.fullscreen.autohide option had already a TRUE value
- I tried firefox -safe-mode
- I tried a new clean profile 

In each attempt the same thing keeps happening. I don't believe there is a need for a screenshot, it is easy to describe:

1. F11 key is supposed to be a shortcut that you don't need to go to "Menu Bar" to click Fullscreen option.

2. When I go to "Menu Bar" and choose Fullscreen then the window maximizes and covers the full screen and the following hide:
       - Window Title Bar (the one with the close- max- minimize window buttons)
       - Menu Bar (File, Edit, View etc.  )
       - Bookmarks Toolbar
       - Location Bar with open tabs (re-appear if you put the mouse pointer on top of the screen)
       - Add-on Toolbar (on the bottom of the screen)

3. If I press the F11 key then the window maximizes and covers the full screen and the following hide:
       - Window Title Bar (the one with the close-max-minimaze window buttons)
       - Nothing else

Is a screenshot still needed?

---

### Post by lovinglinux on 2012-04-08
> **chaceos said:**
> lovinglinux thank you very much

I tried all your suggestions but nothing.
- The browser.fullscreen.autohide option had already a TRUE value
- I tried firefox -safe-mode
- I tried a new clean profile 

In each attempt the same thing keeps happening. I don't believe there is a need for a screenshot, it is easy to describe:

1. F11 key is supposed to be a shortcut that you don't need to go to "Menu Bar" to click Fullscreen option.

2. When I go to "Menu Bar" and choose Fullscreen then the window maximizes and covers the full screen and the following hide:
       - Window Title Bar (the one with the close- max- minimize window buttons)
       - Menu Bar (File, Edit, View etc.  )
       - Bookmarks Toolbar
       - Location Bar with open tabs (re-appear if you put the mouse pointer on top of the screen)
       - Add-on Toolbar (on the bottom of the screen)

3. If I press the F11 key then the window maximizes and covers the full screen and the following hide:
       - Window Title Bar (the one with the close-max-minimaze window buttons)
       - Nothing else

Is a screenshot still needed?

This is weird, because the default behavior for both is what you described on item 2.

I am not sure if this would show, but start Firefox through terminal and check if there is any error output when you access fullscreen from the menu. Also open the Firefox Error Console (CTRL+SHIFT+J) and check if it produces any error.

---

### Post by chaceos on 2012-04-09
> **lovinglinux said:**
> This is weird, because the default behavior for both is what you described on item 2.

I am not sure if this would show, but start Firefox through terminal and check if there is any error output when you access fullscreen from the menu. Also open the Firefox Error Console (CTRL+SHIFT+J) and check if it produces any error.


Nope. no errors, no messages
I agree, weird...

---

### Post by lovinglinux on 2012-04-09
Create a new Ubuntu account just for testing, logout, log with the testing account and check if the behavior persist. Test both Unity 2D and 3D. You can delete the test account afterwards.

---

### Post by chaceos on 2012-04-12
Hi, Sorry for the delay, I'm on a trip.

I have some news.
I had already an account that I do not use (just for guests), I checked it there and everything worked as it should, with no problems.

The only thing that found different, was that in the testing account firefox, you always see the "tab toolbar" even if you only have just one open.
In my problematic firefox, if you have only one tab open, it shows no "tab toolbar" you have to open a new tab to see the "tab toolbar".

Hope that the above helps a bit.

---

### Post by lovinglinux on 2012-04-12
> **chaceos said:**
> Hi, Sorry for the delay, I'm on a trip.

I have some news.
I had already an account that I do not use (just for guests), I checked it there and everything worked as it should, with no problems.

The only thing that found different, was that in the testing account firefox, you always see the "tab toolbar" even if you only have just one open.
In my problematic firefox, if you have only one tab open, it shows no "tab toolbar" you have to open a new tab to see the "tab toolbar".

Hope that the above helps a bit.


I think the source of the problem could be outside Firefox, since a new profile doesn't solve the problem, but a new account does.

If you are using a recent version of Ubuntu, try Unity 2D.

---

### Post by chaceos on 2012-04-12
AH, no I forgot to mention i have no unity. I'm with gnome as I said I have 10.04 lucid lynx.

---

### Post by lovinglinux on 2012-04-12
> **chaceos said:**
> AH, no I forgot to mention i have no unity. I'm with gnome as I said I have 10.04 lucid lynx.

Are you using Compiz?

---

### Post by chaceos on 2012-04-12
Hmm, I can't remember installing it, I didn't even know what it is before oggling after your post. But it seems that I have it installed, I checked it in synaptic and it was ther installed.

I don't have any visual effects enabled, if this helps.

thanx for your effort!

---

### Post by lovinglinux on 2012-04-12
Well, I believe it is some gnome setting messing full screen. If it was a serious issue, I would recommend deleting all gnome config files. But since this is a minor issue, I recommend just using F11.

---

### Post by chaceos on 2012-04-12
You mean use view-->fullscreen.

Anyway, problem solved!!! :D :) :D

I found out that the problem was that I had assigned F11 for gnome shortcut to fullscreen too.
So when I was pushing F11 the firefox window went fullscreen but in a gnome sense (just the window title bar). This was blocking the firefox fullscreen mode.
After assigning gnome fullscreen to alt+F11 firefox shortcut for fullscreen, F11 worked as it should.

Thank you very much lovinglinux! cu around

---

