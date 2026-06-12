---
title: "Unity and Compiz issue"
date: 2012-03-12
forum: Desktop Environments
---

### Post by schrammbo on 2012-03-12
I want to reduce the size of the icons for the unity launcher and when I enable the compiz unity plugin manager and adjust the settings I end up with 2 launchers on the left hand side of the screen.  

One is the original launcher and the other is the one enabled by compiz.  How do I get rid of the original and only display the one in compiz?

---

### Post by typhoon_tip on 2012-03-12
This is a very weird issue... Instead of using compiz to adjust the size of the icons, can you try Ubuntu Tweak and see if the effect is the same:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Download the .deb for your version and install it.

---

### Post by schrammbo on 2012-03-12
I installed both ubuntu tweak and myunity.  Neither of which revealed any obvious way to change the size of the launcher.  

My unity said that I was running in Ubuntu 2d mode which was news to me.  

I attached a screenshot of what is happening when I use compiz

---

### Post by wacky_sung on 2012-03-12
I think that work with the same issue of Unity with Gnome. No doubt about it.Personally i don't think Unity can work well on difference environments.

---

### Post by enterdavertex on 2012-03-12
Forget the compiz with unity, too much bug for this desktop environement.

---

### Post by rg4w on 2012-03-12
> **enterdavertex said:**
> Forget the compiz with unity, too much bug for this desktop environement.
Which one should go?

Some devs like to portray the conflicts between the two as being Compiz' fault, yet as noted on the unity-dev list Compiz generally worked well before the advent of Unity.

---

### Post by grahammechanical on 2012-03-12
And this is still present when you log out and back in? And when you reboot?

Compiz Config Settings Manager has never done that to me. And I have used it to alter the size of the icons and to make the top panel transparent.

Where you get problems with CCSM is when you activate some of the special effects. I use wobbly windows. That works fine. I cannot say about the other effects but they are risky.

In 12.04 we will get a warning whenever we run CCSM that it can break the desktop. And the method of adjusting icon size is also in System Settings - Appearance utility. So, we do not need CCSM to make that adjustment.

There have also been many updates to Compiz (the window manager) in 12.04.

Regards.

---

### Post by azkraja on 2012-03-12
I faced this problem when i installed CCSM, after that i totally UN-installed CCSM and than i installed"MyUnity" this works for me, and no bug after that.

---

### Post by stinkeye on 2012-03-12
Sounds to me like your in the **ubuntu-2d** session and have 
run **compiz --replace** to load compiz as the window manager and thus 
enabled the unity plugin.
Unity-2d will run in metacity or compiz so you have 2 launchers.


Run...
```
metacity --replace
``` 
to replace compiz with metacity, the default window manager for the **ubuntu-2d** session.

Log out and select ```
Ubuntu
``` as the session at the greeter screen.
Once your logged in check your session
```
echo $DESKTOP_SESSION
```
and your window manager
```
wmctrl -m 
```
eg
```
glen@Precise:~$ **echo $DESKTOP_SESSION** 
[COLOR="Purple"]ubuntu[/COLOR]

glen@Precise:~$ **wmctrl -m**
Name: [COLOR="purple"]Compiz[/COLOR]
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```


To change the launcher icon size in ccsm....

---

### Post by schrammbo on 2012-03-12
@[grahammechanical]("http://ubuntuforums.org/member.php?u=1087323") - yes this occurs when I log out and log back in and reboot.

@stinkeye - Despite having my login session set to ubuntu it is switching to ubuntu-2d during login.  

After running wmctrl -m the output was identical to your output

> ame: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF


I am running an NVidia Geforce 7300 which for some reason I cannot get it to work in 3D mode.  If someone has a fix for that then I am open to try it

So it sounds like I need to add compiz --replace to the startup sessions programs

---

### Post by Krytarik on 2012-03-12
> **schrammbo said:**
> I am running an NVidia Geforce 7300 which for some reason I cannot get it to work in 3D mode.  If someone has a fix for that then I am open to try it
There you go:

[http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

> **schrammbo said:**
> So it sounds like I need to add compiz --replace to the startup sessions programs
No, you should *remove* it from your "Startup Applications", as it seems like it's run through that; or at least disable the Unity Plugin via CCSM, if you can't get the regular Unity session to run but want to use Compiz as your window manager.

Regards.

---

### Post by schrammbo on 2012-03-12
@Krytarik - This seems to have worked.  I am not a veteran of Linux so I am not sure why it worked but glad that it does.

The work around that I had come up with was to login to gnome classic having set the startup programs to run
> compiz --replace

and 

> nohup unity

This was producing the same effect that appears to have worked with your information.  I am sure there were differences I just had not come across them.  When I run 

> echo $DESKTOP_SESSION

I am now getting Ubuntu and not Ubuntu-2d

---

