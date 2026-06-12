---
title: "Hide unity-2d-panel from cairo taskbar?"
date: 2012-03-09
forum: Desktop Environments
---

### Post by Heliotropen on 2012-03-09
I'm running ubuntu 12.04 beta 1 (because I like the global menu).

I use the unity 2d login (because I hate hate the unity launcher.)  

I have removed the launcher(chmoded the unity shell), changed from metacity to compiz, and installed cairo dock, and so on... 

Now the only problem I have left to make my system run decent(and to look like I want it to), is to hide the unity-2d-panel from the cairo task bar.  

[IMG]http://img221.imageshack.us/img221/1113/arbejdsomrde1001rmgb.png[/IMG]

**So my question is: **
Is there a way(an setting, app, a hack or similar) to either, make the(perhaps any) program(unity-2d-panel) run hidden from a given taskbar?

Or is there a way to exclude a program running in the taskbar from the cairo taskbar? :confused:
 
Thnx 
Helio

---

### Post by Frogs Hair on 2012-03-09
Trying to understand

> I use the unity 2d login (because I hate hate the unity launcher.)


Unity 2D has a launcher ?  

> I have removed the launcher(chmoded the unity shell), changed from metacity to compiz, and installed cairo dock, and so on. 

Understood 

```
 hide the unity-2d-panel from the cairo task bar.
```

This is where is I get confused . Do you mean Hide the top panel? 

> s there a way(an setting, app, a hack or similar) to either, make the(perhaps any) program(unity-2d-panel) run hidden from a given taskbar?

 Or is there a way to exclude a program running in the taskbar from the cairo taskbar? :confused: 

 Confused - So am I .

---

### Post by Heliotropen on 2012-03-09
In the older version of ubuntu, the launcher(the dock at the left, and yes you are forced with that one in the 2d fallback version also) was called "unity-2d-launcher", and you could remove it (by eleminating access to run the file) with:

sudo chmod -x /usr/bin/unity-2d-launcher

in 12.04, unity-2d-launcher is not there anymore ... so I experimented... 

And if you sudo chmod -x /usr/bin/unity-2d-shell

The Launcher(dock) disapears, while the panel is still there... as far as I have experienced in the short time I have played with this: unity-2d-shell is only the launcher (I'm not missing any other funktions I have noticed when I do it like this anyways) ... 

So my guess is that in 12.04(could be wrong)"/usr/bin/unity-2d-shell" = "/usr/bin/unity-2d-launcher" + "the dash"(NOTE: I have replaced the dash with "slingshot", about the best and most similar app I could find(though could only find an older version) and then I'm also running synapse, so I only use slingshot for browsing aps and synapse for most actual functions of the dash)

> This is part of Unity 2D and can not run as a standalone application outside
 of the Unity 2D environment. The components included are:
 * Dash: an overlay over the desktop to provide quick access to
         various categories of applications.
 * Launcher: displays in a panel at the left of the screen a list of running
             and favorite applications as well as highlighting their notifications.

[https://launchpad.net/ubuntu/precise/+package/unity-2d-shell]("https://launchpad.net/ubuntu/precise/+package/unity-2d-shell")

ANYWAYS: I'm trying to find a way, to hide a running program from the "taskbar", - OR just from the "cairo dock" "taskbar" - so the ugle icon at the button is removed from the bar ... :) 

**So in short, yes I mean hide the top panel :)** 

unity-2d-panel is the top panel, as far as I know off :) 

- Helio

---

### Post by Heliotropen on 2012-03-09
I just want to say, that I have found a temporary solution:

1. I make the process to a luncher (right click "make it a launcher")
2. I move the launcher to it's own seperate dock. 
3. Move the dock outside of the screen, and makes it hidden ... 

I works in practise ... but I'm not going to stamp this thread solved yet, because I'm still looking for the "optimal solution" = to exclude the exact program from either the taskbar(and hence automatically the cairo task bar), or atleast totally from the cairo taskbar :) 

- Helio

---

### Post by Krytarik on 2012-03-09
> **Heliotropen said:**
> I have removed the launcher(chmoded the unity shell), changed from metacity to **compiz**, and installed cairo dock, and so on... 

Now the only problem I have left to make my system run decent(and to look like I want it to), is to **hide the unity-2d-panel from the cairo task bar**.
You can use Compiz' "Window Rules" plugin to achieve that, adding it to its "Skip taskbar" setting; and maybe also to "Skip pager", to also hide it from the Alt+Tab switcher. Obviously, you need "CompizConfig Settings Manager" to set that up.

One more advice, though: I'd rather use the dedicated Cairo Dock session, or a custom one, and add Unity 2D Panel to your "Startup Applications"; because, how you've set it up currently, the Unity 2D Launcher will pop up again once its package is upgraded, and also, you've probably another unwanted process running currently: Unity 2D Spread.

Regards.

---

### Post by Heliotropen on 2012-03-09
> **Krytarik said:**
> You can use Compiz' "Window Rules" plugin to achieve that, adding it to its "Skip taskbar" setting; and maybe also to "Skip pager", to also hide it from the Alt+Tab switcher. Obviously, you need "CompizConfig Settings Manager" to set that up.

One more advice, though: I'd rather use the dedicated Cairo Dock session, or a custom one, and add Unity 2D Panel to your "Startup Applications"; because, how you've set it up currently, the Unity 2D Launcher will pop up again once its package is upgraded, and also, you've probably another unwanted process running currently: Unity 2D Spread.

Regards.

Thnx man that is awesome feedback ... 

I will try it out, I already use "CompizConfig Settings Manager", - but did not know about the ""Window Rules" plugin" 

unity-2d-spread - can you give a few words about what that process does? (I removed the launcher by experimenting, and is rather new to unity, - so I don't really know about all the elements running) 

Thnx man! 

I will consider trying out your cairo suggestion also, though right now it's all running rather stable, fast and actually I have allot more power on the battery now than I had running xfce, and gnome 3.

With your cairo dock suggestion I will lose the "global menu right? (I want to keep that one :) )

- Helio

EDIT: The compiz "windows rules" plugin worked. so thnx again man! :)

---

### Post by Krytarik on 2012-03-09
> **Heliotropen said:**
> unity-2d-spread - can you give a few words about what that process does?
Replicating the referencing method you yourself have used earlier :P :
> The Unity 2D spread allows you to display a quick thumbnailed view of open
 windows so you can quickly and effectively choose which one you want to
 switch to. It is part of Unity 2D and can not run as a standalone application
 outside of the Unity 2D environment.Source: [https://launchpad.net/ubuntu/precise/i386/unity-2d-spread](https://launchpad.net/ubuntu/precise/i386/unity-2d-spread)

> **Heliotropen said:**
> With your cairo dock suggestion I will lose the "global menu right? (I want to keep that one :) )
I know; that's the very reason why you are running the Unity 2D session in the first place. ;-) And I happily concluded that with running the panel that's usually hosting the Global Menu, you'd also get that in any other session; but now I think that might not be true, because the Unity 2D session itself might be setting the variable reg. that - in that case, just set it yourself to *any* session :P :
```
echo 'UBUNTU_MENUPROXY=1' | sudo tee /etc/X11/Xsession.d/81ubuntu-menuproxy
```

---

### Post by Heliotropen on 2012-03-09
> **Krytarik said:**
> Replicating the referencing method you yourself have used earlier :P :
Source: [https://launchpad.net/ubuntu/precise/i386/unity-2d-spread](https://launchpad.net/ubuntu/precise/i386/unity-2d-spread)


I know; that's the very reason why you are running the Unity 2D session in the first place. ;-) And I happily concluded that with running the panel that's usually hosting the Global Menu, you'd also get that in any other session; but now I think that might not be true, because the Unity 2D session itself might be setting the variable reg. that - in that case, just set it yourself to *any* session :P :
```
echo 'UBUNTU_MENUPROXY=1' | sudo tee /etc/X11/Xsession.d/81ubuntu-menuproxy
```


So in other words it's a metacity function? xD

I was wrong in my last post by the way ... the taskbar fix did not work :D cairo finds it anyways :d sry (thought I had delted the 2 dock I made) ... 

> I know; that's the very reason why you are running the Unity 2D session in the first place. 
Kind of spot on ... though I think unity 2d like this also runs very nice on my machine actually ... I think I might like it better than xfce, even without the global menu :) 

I don't understand your last step :) 

But I do appriciate your help ... :)

Thnx again man
Helio

Helio

---

### Post by Krytarik on 2012-03-09
> **Heliotropen said:**
> So in other words it's a metacity function? xD
Wah!? :eek: :D - No, not really; as stated in its description on Launchpad, it's providing the feature to choose between multiple instances of an app, but it also provides the Workspace Switching feature. However, at least in Precise 12.04, it's only invoked by demand, that is, when you click in the Launcher on the icon of any app that has multiple instances running, or on the Workspace Switcher icon. I've just tested both of these in a Live ISO, to give a definitive answer. :P

> **Heliotropen said:**
> I was wrong in my last post by the way ... the taskbar fix did not work :D cairo finds it anyways :d sry (thought I had delted the 2 dock I made) ...
That would be too bad; that setting works for every panel and dock I'm either using or have access to right now, that is, AWN, Gnome Panel, and ADeskBar - make sure it's set up correctly.

> **Heliotropen said:**
> I don't understand your last step :)
That would just set the variable controlling if Global Menu is used or not to ON, for *all* sessions ;-) - provided that the needed "indicator-appmenu" process is running, at least for the Unity Panel.

---

### Post by Heliotropen on 2012-03-09
> **Krytarik said:**
> Wah!? :eek: :D - No, not really; as stated in its description on Launchpad, it's providing the feature to choose between multiple instances of an app, but it also provides the Workspace Switching feature. However, at least in Precise 12.04, it's only invoked by demand, that is, when you click in the Launcher on the icon of any app that has multiple instances running, or on the Workspace Switcher icon. I've just tested both of these in a Live ISO, to give a definitive answer. :P


That would be too bad; that setting works for every panel and dock I'm either using or have access to right now, that is, AWN, Gnome Panel, and ADeskBar - make sure it's set up correctly.


That would just set the variable controlling if Global Menu is used or not to ON, for *all* sessions ;-) - provided that the needed "indicator-appmenu" process is running, at least for the Unity Panel.


Okay, I have blocked it just in case (windows switching and several apps still work)... (:

Sadly I want to use cairo, and not the others(I really like it), take it uses it own stuff to find what is running, - so I will just use the other trick until I find an other solution. 

To be honest I'm not really into unity 2d yet, I have played with it for a few days, after switching from xfce, - I had a belive that compiz(or metacity) somehow was involved in the global menu :) but guess not then, it's all done by the panels("indicator-appmenu") it self? (: 

Thnx again, it's nice with someone so knowledgeable about this things... (:  
- Helio

---

### Post by Krytarik on 2012-03-09
> **Heliotropen said:**
> I had a belive that compiz(or metacity) somehow was involved in the global menu :) but guess not then, it's all done by the panels("indicator-appmenu") it self?
Yup, the window managers really don't have anything to do with Global Menu. ;-)

---

### Post by Heliotropen on 2012-03-09
Awesome that changes everything ... 
I will do as you advised whenever I'm going to re-install then... :)

- Helio

---

