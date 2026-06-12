---
title: "I'm over Unity. How do I change it?"
date: 2013-04-08
forum: Desktop Environments
---

### Post by Ice On Fire on 2013-04-08
Hey guys, 

I've got Ubuntu 12.10 setup at the moment. 

However, I am over the Unity DE as it gets in the way and sticks out too much for me. 

So, I want to change it - I did try Gnome with: ```
sudo apt-get install gnome-session-fallback
```

This gives the desired effect I am after - however, it has the bar at the bottom of the screen - which seems a little pointless. 

So, how do I replace the DE with something that just has the top bar and leaves the rest up to me?
I am also wanting to install Docky - along with some widgets - any suggestions on this?

Thanks guys

---

### Post by Frogs Hair on 2013-04-08
The bottom panel is removable with super key/windows key + Alt + Right Click or Alt + Right Click. You can open the software center and install Docky or GLX/ Cairo Dock. I have used GLX but, not Docky.

---

### Post by VanillaMozilla on 2013-04-08
Did you delete a panel or autohide?  I don't know how to get a new one, but it's easy to delete one.  Careful.

---

### Post by blackbird34 on 2013-04-08
When you Alt+Right click doesn't the little menu offer you to add a panel if you only have one?

BTW i've used Docky, it's good, straightforward, no fuss. Cairo Dock/GLX are good but have way too many options IMHO.

---

### Post by Frogs Hair on 2013-04-08
When you Alt Right you will see a menu with different options . When there no panel and you can move the cursor to the bottom and bring up the menu and select new panel.

---

### Post by markbl on 2013-04-08
apt-get install gnome-shell and then log in to GNOME session.

---

### Post by ibjsb4 on 2013-04-08
You can also see if any of this will work for you.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Ice On Fire on 2013-04-09
> **Frogs Hair said:**
> The bottom panel is removable with super key/windows key + Alt + Right Click or Alt + Right Click. You can open the software center and install Docky or GLX/ Cairo Dock. I have used GLX but, not Docky.

Ah, didn't know that - let me try it out, thanks! 

> **Frogs Hair said:**
> When you Alt Right you will see a menu with different options . When there no panel and you can move the cursor to the bottom and bring up the menu and select new panel.

Thanks for the visual. :D
> **markbl said:**
> apt-get install gnome-shell and then log in to GNOME session.

Yes, already done this bud - bar was / is still at the bottom. Appreciate the input though. 

> **ibjsb4 said:**
> You can also see if any of this will work for you.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Great, I will go through the links! :D

Thanks all!

---

### Post by markbl on 2013-04-09
> **Ice On Fire said:**
> 
Yes, already done this bud - bar was / is still at the bottom. Appreciate the input though. 

No you haven't spud, gnome-shell does not have a bottom bar. gnome-session-fallback that you are using is the old "classic" gnome. gnome-shell is the new UI for gnome 3.

---

### Post by Ice On Fire on 2013-04-09
Ah, sorry, wasn't paying attention while reading there... oops! 

Let me try it now. 

Thank you.

---

### Post by Ice On Fire on 2013-04-09
This is the error I get when trying:
 ```
sudo apt-get install gnome-shell
``` 

```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by markbl on 2013-04-09
That just means the automatic ubuntu update manager happened to be running at the same time you did that. Wait a minute and try again.

---

### Post by Ice On Fire on 2013-04-09
Sorry, still new to this whole Linux game. :)

It worked the second time around.

---

### Post by cmcanulty on 2013-04-09
In classic you can have as many or few panels as you like and put them on top, bottom, right, or left

---

### Post by Ice On Fire on 2013-04-10
In gnome-shell - I just get the wall paper - no menu, no bars, nothing. 

Is that normal? 

I'm running Ubuntu 12.10 in VMware Fusion on my MBP. I tried right cliking the bar, alt-right-click and nothing happens. Am I missing something here?

---

### Post by markbl on 2013-04-10
You say you get "no bars" but you also say you tried "clicking the bar".

What exactly do you see?

Read [https://help.gnome.org/users/gnome-help/stable/shell-introduction.html.en](https://help.gnome.org/users/gnome-help/stable/shell-introduction.html.en), 
[https://live.gnome.org/GnomeShell/Tour](https://live.gnome.org/GnomeShell/Tour), [https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by Ice On Fire on 2013-04-10
Sorry, what I meant to say is: 

In Gnome-Shell, all I see is the wallpaper image, nothing else. 
In Gnome-Session-Fallback, the top and bottom bars a visible, however alt-right-clicking them, does nothing. However, as I stated, maybe this is a VMware issue, rather than an Ubuntu issue. 

I will read the links provided, thank you.

---

### Post by ibjsb4 on 2013-04-10
> In Gnome-Session-Fallback, the top and bottom bars a visible, however alt-right-clicking them, does nothing. 

Try Super (window key) + Alt + right click

---

### Post by Ice On Fire on 2013-04-10
Okay, so I restored my Ubuntu to a previous snapshot version in VMware Fusion. I downloaded the gnome-shell and it asked me to select a default display manager. So I selected gdm (I Think) and I logged off and logged on with Gnome. Just the wallpaper show. No bars, menus or anything of the sort. 

What's causing this?

---

### Post by Ice On Fire on 2013-04-10
> **ibjsb4 said:**
> Try Super (window key) + Alt + right click

Don't have a Windows key. Using a MacBook Pro. However, this worked CMD + Alt + Right click. 

Panel now gone. Just the top bar is there. 

Thanks!! :P

---

### Post by cmcanulty on 2013-04-10
do gnome classic instead almost identical to gnome 2

---

### Post by TeamRocket1233c on 2013-04-10
You could try Cinnamon, E17, or MATE, as well. You have to add the PPAs for 'em in order to install 'em though, as they're not in the official repos, although Cinnamon will be in the official repos starting with 13.04.

> Cinnamon:
-------------------------------------------------------
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
-------------------------------------------------------
MATE:
-------------------------------------------------------
sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) quantal main"
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
sudo apt-get install mate-core
sudo apt-get install mate-desktop-environment
-------------------------------------------------------
E17:
-------------------------------------------------------
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
sudo apt-get install e17


---

### Post by Ice On Fire on 2013-04-10
> **TeamRocket1233c said:**
> You could try Cinnamon, E17, or MATE, as well. You have to add the PPAs for 'em in order to install 'em though, as they're not in the official repos, although Cinnamon will be in the official repos starting with 13.04.

Oh, awesome! 


Can I try multiple DEs without the need to reinstall the OS? 

Currently I am using Gnome Classic - removed the bottom panel and have Docky running. Loving it.

---

### Post by cmcanulty on 2013-04-10
yes just go to synaptic and install lubuntu desktop, xubuntu desktop etc. You will pull in a lot of extra apps though. Also on my laptop some interact weirdly but on my desktop they don't. But very easy to install or uninstall.

---

### Post by Ice On Fire on 2013-04-10
Thanks for that. 

I will just take a snapshot of the system now before I start with those extra DE's. I still don't know why Gnome-shell only loads the wallpaper? 
Is this desktop for terminal use only? 

I must say, Ubuntu is better without Unity. 

I really appreciate the help everyone!


Edit: I prefer using Terminal to install these packages - is the manager program better?

---

### Post by cmcanulty on 2013-04-10
no it just gives you a little more info and you can check whether you want all the additional things

---

### Post by TeamRocket1233c on 2013-04-10
> **Ice On Fire said:**
> 

Currently I am using Gnome Classic - removed the bottom panel and have Docky running. Loving it.


Cool. I'm using either a pretty much stock Cinnamon, MATE, or E17 myself, as I have all three DEs installed on my system, all three are flat-out awesome, especially E17 as it's pretty much the perfect blend of usability, eyecandy, and size, IMO.

---

### Post by Ice On Fire on 2013-04-10
> **TeamRocket1233c said:**
> Cool. I'm using either a pretty much stock Cinnamon, MATE, or E17 myself, as I have all three DEs installed on my system, all three are flat-out awesome, especially E17 as it's pretty much the perfect blend of usability, eyecandy, and size, IMO.

Will give those DE's a try once my interview is over on Friday. :)

---

### Post by TeamRocket1233c on 2013-04-10
Cool. :)

---

