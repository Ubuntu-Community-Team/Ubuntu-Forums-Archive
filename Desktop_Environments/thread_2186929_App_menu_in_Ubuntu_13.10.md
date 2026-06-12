---
title: "App menu in Ubuntu 13.10"
date: 2013-11-09
forum: Desktop Environments
---

### Post by ardchoille422 on 2013-11-09
The menu bar in Ubuntu 13.10 shows an app menu when you mouse-over the menu bar, but moving the cursor away causes the menu to disappear. I would like to learn how to make that app menu visible all the time regardless of mouse-over state. How can I do this?

---

### Post by cariboo on 2013-11-09
What you are asking about is called a global menu, and changes depending on which application on your desktop has focus. The way it works is by design. It would be confusing if it was there all the time, and you accidentally switched focus to another window, and you clicked on a menu item, and got something you didn't expect.

All software included in a default installation, is open source, so if you feel something needs to be changed, you can do it yourself, by downloading the source packages.

---

### Post by ardchoille422 on 2013-11-10
> **cariboo907 said:**
> What you are asking about is called a global menu, and changes depending on which application on your desktop has focus. The way it works is by design. It would be confusing if it was there all the time, and you accidentally switched focus to another window, and you clicked on a menu item, and got something you didn't expect.

All software included in a default installation, is open source, so if you feel something needs to be changed, you can do it yourself, by downloading the source packages.

Unfortunately I'm nowhere near as skilled as the regular developers so changing it myself is not a possibility.

---

### Post by ardchoille422 on 2013-11-10
Is there a bounty program for Ubuntu apps? I'd be willing to pay someone to add my request as a user option:
globalmenu-visibility: always leave visible

---

### Post by 3rdalbum on 2013-11-10
> **ardchoille422 said:**
> Is there a bounty program for Ubuntu apps? I'd be willing to pay someone to add my request as a user option:
globalmenu-visibility: always leave visible

The option would never make it upstream into Unity - its developers don't add features and options because a small number of people might use them, it's too much work to maintain every little option. If implemented by someone else, the next version of Unity that came out would not work with the option and you'd be back to square one.

However there's a bit of a hacky way to do what you want, and it involves thinking laterally. Install the Compiz-config Settings Manager (CCSM) and open it. Click on the Unity plugin. There's an option for how long to display the global menu after starting a program, and another option for how long the fade-out animation should be. Simply set these to insanely-high values, like 10,000,000 milliseconds (over two hours) and you've basically got what you want. As long as you use a menu at least once every two hours you'll always see the global menu bar.

Note that these options are not considered to be "user-facing" and might not be present in later versions of Ubuntu; they're basically only there to make it easier for the developers to tweak.

---

### Post by ardchoille422 on 2013-11-10
> **3rdalbum said:**
> The option would never make it upstream into Unity - its developers don't add features and options because a small number of people might use them, it's too much work to maintain every little option. If implemented by someone else, the next version of Unity that came out would not work with the option and you'd be back to square one.

However there's a bit of a hacky way to do what you want, and it involves thinking laterally. Install the Compiz-config Settings Manager (CCSM) and open it. Click on the Unity plugin. There's an option for how long to display the global menu after starting a program, and another option for how long the fade-out animation should be. Simply set these to insanely-high values, like 10,000,000 milliseconds (over two hours) and you've basically got what you want. As long as you use a menu at least once every two hours you'll always see the global menu bar.

Note that these options are not considered to be "user-facing" and might not be present in later versions of Ubuntu; they're basically only there to make it easier for the developers to tweak.

Thank you very much for this information. It sounds like should just get used to the way the menu currently works, no problem.

---

### Post by johnny.5 on 2013-12-10
> **cariboo907 said:**
> What you are asking about is called a global menu, and changes depending on which application on your desktop has focus. The way it works is by design. It would be confusing if it was there all the time, and you accidentally switched focus to another window, and you clicked on a menu item, and got something you didn't expect.

All software included in a default installation, is open source, so if you feel something needs to be changed, you can do it yourself, by downloading the source packages.

It hasn't caused problems for Apple users over the years so why exactly would a Unity user not be able to handle an always visible menu bar? Even if a user was confused by the global menu concept, I fail to see how hiding it prevents the scenario you have described. Hiding important and frequently used UI elements is what is confusing. I like unity, I think it's great and I like it's original ideas such as the searchable menus with the alt key, but it's clear where the ideas driving it are coming from and the source doesn't hide their menus. This should be an option which is readily available to the user, it's clearly a matter of preference. Hiding things for the sake of hiding them doesn't help me or apparently the OP either.

---

### Post by mpmistr on 2013-12-10
> **johnny.5 said:**
> It hasn't caused problems for Apple users over the years so why exactly would a Unity user not be able to handle an always visible menu bar? Even if a user was confused by the global menu concept, I fail to see how hiding it prevents the scenario you have described. Hiding important and frequently used UI elements is what is confusing. I like unity, I think it's great and I like it's original ideas such as the searchable menus with the alt key, but it's clear where the ideas driving it are coming from and the source doesn't hide their menus. This should be an option which is readily available to the user, it's clearly a matter of preference. Hiding things for the sake of hiding them doesn't help me or apparently the OP either.


It is an unfortunate 'feature' which I highly doubt they will ever change. KDE offers a global menu plasmoid that work with Qt and Gtk apps, which is always visible. Other DEs used to but I do not believe XFCE/MATE global menus work any longer.

---

### Post by deadflowr on 2013-12-10
Here's something coming down the pipe 
[http://www.omgubuntu.co.uk/2013/11/unity-trusty-global-menu-switch?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2013/11/unity-trusty-global-menu-switch?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Though it is for the dev release as of now, it is something and hopefully the devs of the easier to use control panel apps like unity-tweak-tool, ubuntu tweak and unsettings(if that still works) will implement it into their apps.

I doubt this feature will make it into any of the currently released versions, but at least something like this is a start.
For those with a sour taste of global menu.

---

### Post by johnny.5 on 2013-12-10
Yeah, I figured as much. I've been waiting for this option to become a standard part of Unity with every new release when in fact it's only gotten worse in that it's not even possible in recent versions, at least that I'm aware of. I understand some people may prefer it but I find it kind of annoying, just me though. I'm admittedly primarily an Apple user so I'm no stranger to the paradigm being presented in Unity; I like it along with the Unity only bells and whistles but I stumble upon these threads from time to time in search of any newly discovered ways to get the global menu to stay visible. Anyway, I mean no offence to anyone but the "it's too confusing" argument just sounds like an excuse made up to justify Canonical's stubbornness on this functionality. :)

---

### Post by buzzingrobot on 2013-12-11
Adding an option in 14.04 to switch between the global menu and an in-app menu seems useful.  But, the OMGUbuntu article makes the common mistake of equating the author's preferences with those of every Ubuntu user.  The cliche says Linux is about choice, but that does not mean developers have any obligation to offer all choices in all products.

The global menu in OS X does not hide when it loses focus, as in Ubuntu. As in Ubuntu, the menu changes as the focus moves from app to app. (As it must, of course.) In Ubuntu, I find that a menu that's visible only when I need to use it works as well as the OS X approach.

Since the global menu, along with the Launcher, scopes and HUD are integral to Unity, users who dislike them should simply exercise their ability to choose another distribution.

---

### Post by Frogs Hair on 2013-12-12
The Unity revamped PPA has disable auto-hide, but it wasn't updated for releases after 12.04.
[https://launchpad.net/~ikarosdev/+archive/unity-revamped](https://launchpad.net/~ikarosdev/+archive/unity-revamped)

---

