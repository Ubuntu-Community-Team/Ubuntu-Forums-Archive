---
title: "LXPanel Settings - Get Back &quot;Power&quot; Icon"
date: 2012-06-23
forum: Desktop Environments
---

### Post by Shadius on 2012-06-23
Hey everybody! :)

In my journey to find a lighter Desktop Environment, I installed LXDE, and it works very fast. However, while I was customizing the LXPanel, I accidentally removed the "Power" icon and now my panel looks like this: see screenshot. How do I get back that icon?

---

### Post by Dennis N on 2012-06-23
One method: Use the terminal - You can get the original default panel back with:

```
lxpanelctl restart
```

which will include the shutdown button. Any changes you made will have to be redone.

---

### Post by Shadius on 2012-06-23
> **Dennis N said:**
> One method: Use the terminal - You can get the original default panel back with:

```
lxpanelctl restart
```

which will include the shutdown button. Any changes you made will have to be redone.

Didn't work. :(

---

### Post by black veils on 2012-06-24
you should be able to right-click the panel, find where to add items/plugins to it, and look for the power add-on or an indicator.

---

### Post by Shadius on 2012-06-24
I've tried to find something related to "Shutdown", "Power"..etc, but nothing.

---

### Post by black veils on 2012-06-24
oh that button, i thought you meant the one with battery, for power settings.

it might be called Session

---

### Post by Shadius on 2012-06-24
> **black veils said:**
> oh that button, i thought you meant the one with battery, for power settings.

it might be called Session

:lolflag: Yeah, the button that let's you log out, shut down, switch user..etc.

---

### Post by Shadius on 2012-06-24
Here's a screenshot of what is available to me when I try adding an application. No "Session", no "Shutdown", no "Power". I haven't a clue. :(

---

### Post by black veils on 2012-06-24
what system do you have - how did you acquire the lxpanel? do you have ubuntu and just install the panel, or do you have lxde?

if you just have the panel, i suggest completely uninstalling it, using Synaptic, then installing again.

---

### Post by Shadius on 2012-06-24
> **black veils said:**
> what system do you have - how did you acquire the lxpanel? do you have ubuntu and just install the panel, or do you have lxde?

if you just have the panel, i suggest completely uninstalling it, using Synaptic, then installing again.

I have LXDE on Ubuntu. I installed LXDE using the Ubuntu Software Center. I was thinking of uninstalling LXDE and reinstalling it again, as a last resort. You suggest I do that?

---

### Post by black veils on 2012-06-24
there are different packages for installing lxde, don't know what you used, maybe you could try lubuntu-desktop instead? then as usual, choose your session from the login screen.

---

### Post by Shadius on 2012-06-24
> **black veils said:**
> there are different packages for installing lxde, don't know what you used, maybe you could try lubuntu-desktop instead? then as usual, choose your session from the login screen.

The only thing I did was go to Ubuntu Software Center, typed in LXDE, only one result showed, and I installed it. That's exactly the steps that I did in getting LXDE. After installing it, I logged out of my Ubuntu with GNOME Classic (No effects) Desktop Environment and logged into LXDE. Will installing *lubuntu-desktop* replace my *ubuntu-desktop*? I don't want that. Hope I made everything clear. :) Appreciate the help.

---

### Post by black veils on 2012-06-24
use Synaptic to install either

lxde

or

lubuntu-desktop


it won't remove your ubuntu desktop, they are just other desktop sessions, different packages are available for the lxde desktop environment.

---

### Post by vasa1 on 2012-06-24
> **Shadius said:**
> Didn't work. :(

What happened? Was there any response in the terminal? Error message? Anything?

---

### Post by Shadius on 2012-06-24
> **vasa1 said:**
> What happened? Was there any response in the terminal? Error message? Anything?

Nope, nothing at all. 
```
shadius@shadius-5410US:~$ lxpanelctl restart
shadius@shadius-5410US:~$ 

```

That's all I get. I used **Ctrl+Alt+T** to open up Terminal. I don't know if that makes a difference.

---

### Post by vasa1 on 2012-06-24
> **Shadius said:**
> Nope, nothing at all. 
```
shadius@shadius-5410US:~$ lxpanelctl restart
shadius@shadius-5410US:~$ 

```

That's all I get. I used **Ctrl+Alt+T** to open up Terminal. I don't know if that makes a difference.

And I assume you did a restart of your computer after that, or at least logged out and back in? Some things need a log out and log in. Others need a reboot.

---

### Post by Shadius on 2012-06-24
> **vasa1 said:**
> And I assume you did a restart of your computer after that, or at least logged out and back in? Some things need a log out and log in. Others need a reboot.

Yupp, logged out, logged back in. Tried it again, rebooted. Still didn't work.

---

### Post by kalehrl on 2012-06-24
Type this command as normal user:
```
 mv ~/.config/lxpanel/Lubuntu/panels/panel ~/
```
Then, restart lxpanel with:
```
lxpanelctl restart
```
It works on normal Lubuntu (lxde) so it may work on Ubuntu with lxde as well.

---

### Post by seppalta on 2012-06-24
Have you checked the **logout** desktop file in **/usr/share/applications **for correctness?   That it includes LXDE among the systems allowed?  You can also just create a new desktop file with** exec=lxde-logout**.  [http://douwil7.100webspace.net/linux/Tuning.html#11](http://douwil7.100webspace.net/linux/Tuning.html#11)

---

### Post by VinDSL on 2012-06-24
Let's try a quick n' dirty screencast...  ;)

[INDENT][HOWTO: VinDSL adds a "Shutdown" icon to LXPanel]("http://vindsl.com/video/vindsl-howto-add-lxpanel-shutdown.zip")[/INDENT]

---

### Post by Shadius on 2012-06-25
> **VinDSL said:**
> Let's try a quick n' dirty screencast...  ;)

[INDENT][HOWTO: VinDSL adds a "Shutdown" icon to LXPanel]("http://vindsl.com/video/vindsl-howto-add-lxpanel-shutdown.zip")[/INDENT]

Really appreciate your efforts here VinDSL, but I don't have that "Shutdown" icon to add. :( I got fed up and just uninstalled LXDE, but I still see the options **LXDE**, **GNOME/Openbox** and **Openbox** are present in the login screen. Why are they still there and how do I get rid of them?

---

### Post by VinDSL on 2012-06-25
> **Shadius said:**
> I got fed up and just uninstalled LXDE, but I still see the options **LXDE**, **GNOME/Openbox** and **Openbox** are present in the login screen. Why are they still there and how do I get rid of them?
Not sure about that.

I quit trying to config LightDM a long time ago.

It's like playing with nitroglycerin!  LoL!  :D

---

### Post by Shadius on 2012-06-26
> **VinDSL said:**
> Not sure about that.

I quit trying to config LightDM a long time ago.

It's like playing with nitroglycerin!  LoL!  :D

:lolflag: Thanks for the help anyway VinDSL. Now I just want to get rid of LXDE completely. My LightDM is a mess with those entries. Eyesores.

---

### Post by Shadius on 2012-06-26
Here's something weird. I uninstalled LXDE via Ubuntu Software Center and it shows that it is uninstalled, but Synaptic Package Manager shows related packages of LXDE. :confused: Why wasn't everything that was installed, uninstalled? 

I've attached screenshots to make things clear. I've marked the packages related to LXDE for complete removal.

---

