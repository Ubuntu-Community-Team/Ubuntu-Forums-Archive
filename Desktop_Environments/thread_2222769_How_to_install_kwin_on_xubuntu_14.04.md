---
title: "How to install kwin on xubuntu 14.04"
date: 2014-05-08
forum: Desktop Environments
---

### Post by danbuz on 2014-05-08
Hi guys, I would like to know how to install kwin effects on xubuntu 14.04 and how to completely remove it if I need after this..
I read somewhere that kwin is better than compiz which is still buggy..?

Thanks in advance!

---

### Post by vasa1 on 2014-05-08
But does Xubuntu use Compiz at all?

---

### Post by danbuz on 2014-05-08
> **vasa1 said:**
> But does Xubuntu use Compiz at all?

I read that it is possible to set compiz, but it is not recommended.

---

### Post by vasa1 on 2014-05-08
What problems do you face with the default Xubuntu? Do you *need* KWin?

---

### Post by vasa1 on 2014-05-08
You may want to look at [http://ubuntuforums.org/showthread.php?t=2186174](http://ubuntuforums.org/showthread.php?t=2186174) and the links provided there.

Depending on how experienced you are, you may want to think over the pros and cons of moving away from the default.

---

### Post by danbuz on 2014-05-08
> **vasa1 said:**
> What problems do you face with the default Xubuntu? Do you *need* KWin?


I like the DE, but I also like the nice effects which come with kwin or compiz :) Need is not the right word may be, but if it is possible to install it and it is not resource hungry, why not? :)

---

### Post by monkeybrain20122 on 2014-05-08
> **danbuz said:**
> I read that it is possible to set compiz, but it is not recommended.

Why not recommended? Compiz works fine on xfce. I have done it several times. kwin is tricky if can be done at all.

---

### Post by vasa1 on 2014-05-08
Here's a video by a guy who's gaga over Kwin: [https://www.youtube.com/watch?v=tEA_h0NBrG8](https://www.youtube.com/watch?v=tEA_h0NBrG8)

---

### Post by danbuz on 2014-05-08
This is ok with 14.04, right?

---

### Post by vasa1 on 2014-05-08
> **danbuz said:**
> This is ok with 14.04, right?
This is the thing: you'll be the pioneer :)
I don't know of links about experiences relating to what you're wanting.

---

### Post by luctor on 2014-05-08
I have a strange issue with kwin on Lubuntu
I installed kwin, the package you need is "kde-window-manager".
```
sudo apt-get install kde-window-manager
```
You can start kwin from a terminal or press [ALT-F2] , or in Lubuntu [SUPER+R]
```
kwin --replace
```
If I run it the first time, it runs great. You can customize kwin by right-clicking on a window title bar.
When I close kwin and run the default window-manager, in my case openbox-lubuntu (on xubuntu it would be "xfwm4 --replace") everythings reverts to normal.

Now If I** restart kwin, the desktop freezes**. I'm still able to move the mouse although I can't click anything and the screen is somewhat garbled. I can however still access the terminal with [ALT-F1] and then my only option is to **kill the xsession** and restart it.
```
sudo stop lightdm
sudo start lightdm
```

If I remove the hidden .kde directory
```
rm -rf .kde/*
```
I can run kwin again but all my customizations are gone
=-=-=-=-=-=-=-=-=-=-=-=
found this video, gonna see if it works on 14.04
[https://www.youtube.com/watch?v=A0xTiTUiIng](https://www.youtube.com/watch?v=A0xTiTUiIng)

---

### Post by vasa1 on 2014-05-08
> **luctor said:**
> I have a strange issue with kwin on Lubuntu
I installed kwin, the package you need is "kde-window-manager".
```
sudo apt-get install kde-window-manager
```
You can start kwin from a terminal or press [ALT-F2] , or in Lubuntu [SUPER+R]
```
kwin --replace
```
If I run it the first time, it runs great. You can customize kwin by right-clicking on a window title bar.
When I close kwin and run the default window-manager, in my case openbox-lubuntu (on xubuntu it would be "xfwm4 --replace") everythings reverts to normal.

Now If I** restart kwin, the desktop freezes**. I'm still able to move the mouse although I can't click anything and the screen is somewhat garbled. I can however still access the terminal with [ALT-F1] and then my only option is to **kill the xsession** and restart it.
```
sudo stop lightdm
sudo start lightdm
```

If I remove the hidden .kde directory
```
rm -rf .kde/*
```
I can run kwin again but all my customizations are gone
=-=-=-=-=-=-=-=-=-=-=-=
found this video, gonna see if it works on 14.04
[https://www.youtube.com/watch?v=A0xTiTUiIng](https://www.youtube.com/watch?v=A0xTiTUiIng)

Couple of points: the video you linked to requires installing more packages. Maybe that will help?
The guy also suggests not using the *--replace* trick and instead having kwin load in the first place. Let's know how you get on!

---

### Post by danbuz on 2014-05-09
> **vasa1 said:**
> This is the thing: you'll be the pioneer :)
I don't know of links about experiences relating to what you're wanting.

Ur smart guy, ha ? :) And for those who are not geeky and need something like "tutorial"?

I asked for one reason - the video is old and some things may be changed under the new LTS. Don't want to srcrew my system.. so don't spam next time!

---

### Post by mörgæs on 2014-05-09
Danbuz, please show some courtesy when people are helping you. 
If you believe something is spam the correct way of dealing with it is the 'report' button.

---

### Post by luctor on 2014-07-07
just have a look here
[http://www.youtube.com/watch?v=z5kiYjg3Rog](http://www.youtube.com/watch?v=z5kiYjg3Rog)

---

### Post by justme-jm765 on 2014-08-23
I've done this in Xubuntu 14.04, I simply installed Kwin from synaptic, then from terminal entered "kwin --replace", once I was sure it worked and I liked it I added that command to startup. I can uncheck it in session startup and the default wm will load on reboot instead. To configure Kwin options once installed and running simply right click a title bar (any title bar) More Actions - Window Manager settings. So far I haven't had any problems at all and I think it actually performs better in Xfce than it does in KDE.

---

### Post by vasa1 on 2014-08-23
> **justme-jm765 said:**
> I've done this in Xubuntu 14.04, I simply installed Kwin from synaptic ...
Can you clarify if you did a "full" install or the equivalent of **apt-get install --no-install-recommends**?
On my system, Lubuntu 14.04, a "full" install would pull in about 114 packages whereas the one without recommends would bring in 82.

---

### Post by vasa1 on 2014-08-23
Just in case anyone is wondering, Lubuntu is to move from LXDE to LXQt some time in the future and installing KWin may not require as many packages then.

In any case, if I understand correctly, there's a move on to [reduce KWin's dependencies]("https://groups.google.com/forum/#!msg/razor-qt/6VCUlJspUfc/vo3lE_Om5lcJ").

---

