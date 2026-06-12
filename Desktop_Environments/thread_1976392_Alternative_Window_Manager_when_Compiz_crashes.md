---
title: "Alternative Window Manager when Compiz crashes"
date: 2012-05-08
forum: Desktop Environments
---

### Post by AleCes on 2012-05-08
Hi there,

In Compiz there's an option in Crash Handler that allows an alternative Window Manager to start whenever Compiz crashes. But which one? I don't know any. Could you please suggest one?

Thanks

---

### Post by LewisTM on 2012-05-08
Metacity would be the logical choice.
```
metacity --replace
```
Cheers!

---

### Post by Enigmapond on 2012-05-08
Mutter would also be ok...

---

### Post by AleCes on 2012-05-08
Hi Lewis and enigmapond,

Software Center shows I have metacity but not mutter. May I ask you what's the difference? Anyhow, I don't require particular performances, I just want a minimal environment that allows me to **orderly** shut down programs and the system without loss of data, instead of resorting to catastrophic hard resets.

Thanks

---

### Post by Enigmapond on 2012-05-08
Then just use metacity. Mutter is the new one for gnome-shell.

---

### Post by AleCes on 2012-05-08
OK, I would like to familiarize with it in case of an actual crash, is there a way to start it manually?

Thanks

---

### Post by LewisTM on 2012-05-08
> **AleCes said:**
> OK, I would like to familiarize with it in case of an actual crash, is there a way to start it manually?

Thanks
Again
```
metacity --replace
```

---

### Post by AleCes on 2012-05-08
:roll: LOL :mrgreen:

Thanks

---

### Post by AleCes on 2012-05-08
OK, there's a still a problem. I tried to execute metacity --replace in a terminal and... gulp! The side bar and upper bar of Unity disappear and there's nothing that replace them!!! I'm forced to execute a hard reset! Hardly a backup window manager!

---

### Post by LewisTM on 2012-05-08
Unity depends on Compiz to run.
Execute Ctrl-C in the terminal to terminate Metacity, then 'compiz --replace &' to restore compiz.
So it's really a last resort feature so you can save your work, hardly a fallback WM.
Unity2D would work with Metacity but I don't think you can have both flavors of Unity installed. I may be wrong, I use Xfce :popcorn:

---

### Post by AleCes on 2012-05-09
How can I save my work if there is no window manager? I thought I'd get something like the old GNOME or XFCE in Lubuntu, with an upper bar containing all the menus. This way I can't even find the button for the shutdown, I'm still forced to rely on the hard reset.

---

### Post by zombifier25 on 2012-05-09
Run these commands (after starting metacity):
[code]unity-2d-panel &
unity-2d-shell &
[code]
Theoretically, it should start the Unity 2D shell. I haven't tried it though (urrently on LXDE)

---

### Post by AleCes on 2012-05-09
> **zombifier25 said:**
> Run these commands (after starting metacity):
[code]unity-2d-panel &
unity-2d-shell &
[code]
Theoretically, it should start the Unity 2D shell. I haven't tried it though (urrently on LXDE)
Hi zombifier25!

All right, so Window Manager Command Line should looke like this:

metacity --replace & unity-2d-panel & unity-2d-shell

Correct?

---

### Post by LewisTM on 2012-05-09
So I was wrong, you CAN have both Unities :P
The command would be 
```
metacity --replace & unity-2d-launcher & unity-2d-panel
```

---

### Post by AleCes on 2012-05-09
> **LewisTM said:**
> So I was wrong, you CAN have both Unities :P
The command would be 
```
metacity --replace & unity-2d-launcher & unity-2d-panel
```

OK, but pardon my ignorance, what's the need for metacity if I have to start also unity2d? I thought metacity would be a stripped-down window manager, like XFCE, I'm puzzled. :-k

---

### Post by LewisTM on 2012-05-09
I think you are mistaking a window manager with a desktop environment.
A window manager only does that, manage the looks and placement of windows. It doesn't provide the panels, tools, icons, buttons etc. that make a desktop environment.
Metacity is a window manager simpler than Compiz. It will run Unity-2D (part of the DE) and can even be set to run under Xfce and GNOME. Compiz can be also used to manage windows in Xfce (I use it) but the default WM is Xfwm4, again a simpler, faster WM.
Complicated? Maybe. Modular? Yes.
You can replace a WM on the fly. You can't switch DE without logging out and picking a different session.
A nice tool that could be useful for you is fusion-icon. It sits in the system tray and lets you switch between installed window managers or restart them, if need be.

Cheers!

---

### Post by AleCes on 2012-05-09
Besides, metacity +unity2d doesn't work, it gives me some error messages which unfortunately I cannot copy/paste because there is no side panel. It's true the upper bar appears but the shut-down doesn't work so, again, I'm stuck with the hard reset.

Anyway, I checked whether Unity2d is installed, yes it is: Unity 2d, its panel and shell are reported as installed.

---

### Post by AleCes on 2012-05-09
> **LewisTM said:**
> I think you are mistaking a window manager with a desktop environment.
A window manager only does that, manage the looks and placement of windows. It doesn't provide the panels, tools, icons, buttons etc. that make a desktop environment.
Metacity is a window manager simpler than Compiz. It will run Unity-2D (part of the DE) and can even be set to run under Xfce and GNOME. Compiz can be also used to manage windows in Xfce (I use it) but the default WM is Xfwm4, again a simpler, faster WM.
Complicated? Maybe. Modular? Yes.
You can replace a WM on the fly. You can't switch DE without logging out and picking a different session.
A nice tool that could be useful for you is fusion-icon. It sits in the system tray and lets you switch between installed window managers or restart them, if need be.

Cheers!

OK, now I finally understand, at least. But, it's a vicious circle: how can I log out and re-log in if there's no desktop environment? :biggrin: That affects also your suggestion of making use of fusion-icon: if the DE crashes, there won't be any system tray.

---

### Post by Simian Man on 2012-05-09
If compiz crashes often enough that you need a backup window manager on hand, I wouldn't personally use compiz at all.  Why not just run Unity in 2D mode or something else that isn't so fragile?

---

### Post by AleCes on 2012-05-09
> **Simian Man said:**
> If compiz crashes often enough that you need a backup window manager on hand, I wouldn't personally use compiz at all.  Why not just run Unity in 2D mode or something else that isn't so fragile?

Hi Simian Man,

No, it doesn't crash normally, only when I tease Compiz :tongue: with strange options that sometimes don't work. Otherwise it's just fine, but I'd like to test its limits without having to resort to an innumerable amount of hard resets. Hope you'll understand.

Greetings

---

### Post by LewisTM on 2012-05-09
It's not the DE that crashes, it's compiz. So the icon is still usable. I just tried it by manually killing compiz. I lose the window borders, title bars and the ability to move them or type in them but not to interact with elements.

Not sure about the error but you should never have to hard reset unless the system is completely frozen.
You can type Ctrl-Alt-F1 to enter a virtual screen in text mode, where you can log in and run some commands like 
```
DISPLAY=:0 compiz --replace
```
Then Ctrl-Alt-F7. Or 
```
sudo reboot
```
Or you can follow this [guide]("http://kember.net/articles/reisub-the-gentle-linux-restart") which tells you to press Alt and SysRq (which is the Print Screen key) while slowly typing REISUB to reboot your machine gracefully.

---

### Post by AleCes on 2012-05-09
OK, I installed fusion but I just have a blue icon on the side bar (not the notification zone as expected) that always says installation in progress and I cannot do anything with it. ](*,)

About CTRL+ALT+F1, is there a way to put these into a command line so that when compiz crashes it restarts automatically? Maybe Unity 2d didn't work well because first one has to make sure Compiz is killed?

---

### Post by stinkeye on 2012-05-09
When your messing with ccsm and compiz fails to load properly,
usually you just need to reload with ctrl+alt+t
to bring up a terminal and run
```
compiz --replace & disown
```

Wait 30 secs or so...
If still doesn't load, bring up the terminal and set compiz back to defaults with
```
unity --reset & disown
```

---

### Post by AleCes on 2012-05-09
> **stinkeye said:**
> When your messing with ccsm and compiz fails to load properly,
usually you just need to reload with ctrl+alt+t
to bring up a terminal and run
```
compiz --replace & disown
```Wait 30 secs or so...
If still doesn't load, bring up the terminal and set compiz back to defaults with
```
unity --reset & disown
```

Thanks stinkeye, that explains lots of things, but I still don't understand what's the use for that blue icon of Compiz Fusion on my sidebar, which does nothing. Shouldn't it be placed on the notification zone instead? And shouldn't it allow me to switch between metacity and compiz? :roll:

---

### Post by LewisTM on 2012-05-09
It doesn't seem like the fusion-icon runs well in Ubuntu 12.04 with Unity.
Trying different things with WMs and Unity2D/3D only brings me more confusion. I will apologize for the mess and go back to Xubuntu which at least makes sense to me.

---

### Post by stinkeye on 2012-05-09
> **AleCes said:**
> Thanks stinkeye, that explains lots of things, but I still don't understand what's the use for that blue icon of Compiz Fusion on my sidebar, which does nothing. Shouldn't it be placed on the notification zone instead? And shouldn't it allow me to switch between metacity and compiz? :roll:
That's an old icon for gnome-panel applets that needs to be added to the 
whitelisted applets using dconf-editor to appear in the sys-tray of the unity panel.(Old applets can cause problems if enabled)
Not really much use anymore because once you switch to metacity as the window
manager you lose the unity panel and launcher, as Unity is a plugin for compiz.

The gnome-panel was used in metacity and compiz before.

---

### Post by AleCes on 2012-05-09
> **stinkeye said:**
> That's an old icon for gnome-panel applets that needs to be added to the 
whitelisted applets using dconf-editor to appear in the sys-tray of the unity panel.
Not really much use anymore because once you switch to metacity as the window
manager you lose the unity panel and launcher, as Unity is a plugin for compiz.

The gnome-panel was used in metacity and compiz before.

Yeah, as I was saying. Just curious: which DE is it possible to load on top of metacity? Maybe GNOME?

And to conclude: which command line do you suggest I should add to Crash Handler > Alternative Window Manager? compiz --replace & disown is a too hard too swallow for me because it erases all customization: under normal conditions, if something is screwed and I have to reboot, Compiz automatically turns the "guilty" package off, so I don't think a tabula rasa is necessary. 

Thanks

---

### Post by stinkeye on 2012-05-09
The crash handler plugin isn't enabled by default so I wouldn't even
worry about it and disable it.
I have messed alot with ccsm and the two previous commands always get me out of it.

If your stuck with no terminal 
Hold down ctrl+alt and press and release the SysReq (print) key 
then while still holding down ctrl+alt press and release k.
This will take you back to the login screen.

> Yeah, as I was saying. Just curious: which DE is it possible to load on top of metacity? Maybe GNOME?
Unity uses compiz as the window manager....**Ubuntu** session.
Unity 2d uses metacity as the window manager...**Ubuntu 2d** session.
Gnome-shell uses mutter as the window manager...**Gnome** session.

**compiz --replace & disown** doesn't erase previous customization.
**unity --reset & disown** does.

When you have ccsm set up how you like, in ccsm at the bottom left, click on preferences and then the export button.
Save your profile as **myCCSM.profile** (or whatever) and then when needed use the import button to load your saved ccsm profile.

---

### Post by AleCes on 2012-05-09
Hi,

I shut down Compiz on purpose and, indeed there's no way to get the terminal opened without Compiz. Are you sure it's possible to get back to the login screen in the worst-case scenario, namely, when the window borders disappear and you cannot even write inside boxes nor switch between windows? CTRL+ALT+F1 is the last resort but I noticed it's impossible to restart Compiz from there as if it were just a full-screen terminal, it just doesn't work.

So, you deem it useless to add something like compiz --replace & disown in Crash Handler? Wouldn't it get me out of trouble most of the times without the need for me to do anything?

---

### Post by stinkeye on 2012-05-09
If you want to use the crash handler use as the command
```
metacity --replace
```
**& disown** is just used in the terminal to disassociate a running command so 
you can close the terminal.
I have never used the crash handler so have no idea if it creates it's own problems.


What I find useful is **kupfer** to have access to programs
[ATTACH]217614[/ATTACH] 


and **easystroke** mouse gestures to run commands
[ATTACH]217615[/ATTACH]


If you find you can't type in the terminal, try right clicking in the terminal to show the menu popup then you should be able to type.

Just running **compiz --replace** works 99% of the time and if not
then run **unity --reset**

---

### Post by AleCes on 2012-05-10
> **stinkeye said:**
> If you want to use the crash handler use as the command
```
metacity --replace
```**& disown** is just used in the terminal to disassociate a running command so 
you can close the terminal.
I have never used the crash handler so have no idea if it creates it's own problems.


What I find useful is **kupfer** to have access to programs
[ATTACH]217614[/ATTACH] 


and **easystroke** mouse gestures to run commands
[ATTACH]217615[/ATTACH]


If you find you can't type in the terminal, try right clicking in the terminal to show the menu popup then you should be able to type.

Just running **compiz --replace** works 99% of the time and if not
then run **unity --reset**
Yeah, but metacity alone won't provide me with a working desktop environment. I crashed Compiz on purpose to test the Crash Handler and it effectively started metacity but this alone doesn't suffice because no terminal can be started without a desktop environment. Unity 2d should be started afterwards, but I cannot find a way to make it happen.

```
metacity --replace & unity-2d-launcher & unity-2d-panel
```only gives me the upper panel but still no sidebar. Can you suggest some better alternative?

---

### Post by stinkeye on 2012-05-10
> **AleCes said:**
> Yeah, but metacity alone won't provide me with a working desktop environment. I crashed Compiz on purpose to test the Crash Handler and it effectively started metacity but this alone doesn't suffice because no terminal can be started without a desktop environment. Unity 2d should be started afterwards, but I cannot find a way to make it happen.

```
metacity --replace & unity-2d-launcher & unity-2d-panel
```only gives me the upper panel but still no sidebar. Can you suggest some better alternative?
the command **unity-2d-launcher** has changed to
```
unity-2d-shell
```

---

### Post by AleCes on 2012-05-10
> **stinkeye said:**
> the command **unity-2d-launcher** has changed to
```
unity-2d-shell
```

Wonderful!!! I simulated a crash and with ```
metacity --replace & unity-2d-shell & unity-2d-panel
``` Crash Handler started Unity 2d, I can see the sidebar, the upper panel and the window borders. Almost nothing seems to have changed, no data was lost, no application was closed.

Thanks for all the pieces of informations you and others provided me with. I didn't know there existed so many ways to revive a seemingly dead desktop :lolflag:

---

### Post by foo-nix on 2013-03-24
[FONT=arial, sans-serif]I needed to fix my window manager from a tty, since none of the terminals allowed to have focus, so I did:

- ALT+CTRL+F1
- logged in
- executed this command:
sudo DISPLAY="localhost:0.0" metacity --replace

in order to get around the "cannot open display error"

The [/FONT][FONT=arial]"localhost:0.0" may as well be [/FONT][FONT=arial]"localhost:1.1", [/FONT][FONT=arial]"localhost:1.0", [/FONT][FONT=arial]"localhost:0.1" or any two numbers, to be honest I am clueless about the exact syntax, but if you have multiple xsessions (or however they are called) started, consider try-all-and-error to determine the number, or maybe someone smarter than me can add sense to this.[/FONT]

---

