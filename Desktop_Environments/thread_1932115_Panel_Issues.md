---
title: "Panel Issues"
date: 2012-02-26
forum: Desktop Environments
---

### Post by bman on 2012-02-26
I am using Ubuntu 11.10 with Unity and I can't add to panel.

I am using Alt-Right Click and nothing happens.

How do I add something to the panel?

---

### Post by Krytarik on 2012-02-26
> **bman said:**
> I am using Ubuntu 11.10 with **Unity** and I can't add to panel.

I am using Alt-Right Click and nothing happens.
Please see this earlier thread:

[http://ubuntuforums.org/showthread.php?t=1922589](http://ubuntuforums.org/showthread.php?t=1922589)

Regards.

---

### Post by bman on 2012-02-27
> **Krytarik said:**
> Please see this earlier thread:

[http://ubuntuforums.org/showthread.php?t=1922589](http://ubuntuforums.org/showthread.php?t=1922589)

Regards.

Alright so you add items by pretty much installing small applications.

How about removing the ones that are there already?

---

### Post by bman on 2012-02-27
Anyone? I need to get rid of some items.

---

### Post by Krytarik on 2012-02-27
> **bman said:**
> How about removing the ones that are there already?
> **bman said:**
> Anyone? I need to get rid of some items.
You know, sometimes it has a rather adverse effect to bump that fast - without adding any more details, or updating the status. ;-) (that is, I almost hadn't answered at all)

---

### Post by bman on 2012-02-27
What more details could I have added?

I need to remove items from the Panel. You know, the ethernet one, the mail one. I assumed it wouldn't matter which one.

And I bumped that quick, because these forums push down posts quite fast. I am sorry.

---

### Post by Krytarik on 2012-02-27
> **bman said:**
> What more details could I have added? ... You know, the ethernet one, the mail one. I assumed it wouldn't matter which one.
Given that you had already figured that all of those Indicators are essentially small apps, you could have easily concluded that it matters. - Well, it *does* matter. ;-)

> **bman said:**
> And I bumped that quick, because these forums push down posts quite fast. I am sorry.
Although not explicitly stated in the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") (forums staff, please do that, so we can actually build on that!), 'bump'ing threads in less then 24 hours is considered rude; plus, in Desktop Environments, the flow of threads is much slower than in other major sub-forums.

Addition: Oh, nice, you've just changed your Avatar - that makes you look much less aggressive! ;)

---

### Post by bman on 2012-02-29
Well it's been awhile now. No one has any idea?

I know you can do it, just how can I do it? Please & Thanks!

---

### Post by Frogs Hair on 2012-02-29
```
sudo apt-get remove indicator-name 
```

Mail= indicator-messages 
Sound = indicator-sound

The the indicators can be removed from the terminal or located and removed in the synaptic package manager if installed. I would not suggest removing the network indicator , but it's your choice. The changes will appear at restart.

---

### Post by Krytarik on 2012-02-29
Sorry, from your wording, I didn't take these items as your specific choice :P :
> **bman said:**
> You know, the **ethernet** one, the **mail** one. I assumed it wouldn't matter which one.
Adding to what *Frogs Hair* said, you can disable the Network Manager applet by running this command to make it visible in your "Startup Applications", and then disable it from there:
```
sudo sed -i s/NoDisplay=true/NoDisplay=false/ /etc/xdg/autostart/nm-applet.desktop
```

---

### Post by bman on 2012-02-29
> **Frogs Hair said:**
> ```
sudo apt-get remove indicator-name 
```

Mail= indicator-messages 
Sound = indicator-sound

The the indicators can be removed from the terminal or located and removed in the synaptic package manager if installed. I would not suggest removing the network indicator , but it's your choice. The changes will appear at restart.

Why would you not recommend removing the Network indicator? I still want my internet to work, and have the settings for all that, just not in the panel.

---

### Post by Frogs Hair on 2012-02-29
> **bman said:**
> Why would you not recommend removing the Network indicator? I still want my internet to work, and have the settings for all that, just not in the panel.

Just be sure you are removing the indicator and not the network manager as some have in the past . I have not removed the network indicator , so I can't tell you the correct package name without looking in synaptic .

---

### Post by bman on 2012-03-01
Well I found this in Synaptic, how would you know if it's the right thing I want?

---

### Post by Frogs Hair on 2012-03-01
Indicator- network is not installed on my 11.10 installation and I am not sure of what package to remove . There are a number of packages listed under network but I haven't found one with indicator in the description.

---

### Post by bman on 2012-03-01
You don't have Indicator-network installed, but do you have the icon in the panel at the right hand side? If not then that is probably the correct one.

*Just noticed my screenshot, that Indicator-network isn't installed lol

---

