---
title: "switch to xubuntu?"
date: 2008-05-04
forum: Desktop Environments
---

### Post by msutton86 on 2008-05-04
So I've been using ubuntu for about a year now, and I absolutely love the usability of ubuntu. After playing with different distros though I've noticed a good performance boost.  I was reading about xubuntu and heard the performance is much better. I'm just not sure it would make a big difference because it's still all the bloated ubuntu distro.  has anyone ever seen a big difference in performance between ubuntu and xubuntu?  If not it may be time to graduate to a different distro.

---

### Post by aysiu on 2008-05-04
If you want a big performance difference, try IceWM or Fluxbox.

---

### Post by agim on 2008-05-04
In which distros did you notice a performance boost? I have used Xubuntu, snappier than Ubuntu, but you will get more mileage from a window manager like the ones mentioned above.
I also like Openbox window manager

---

### Post by msutton86 on 2008-05-05
Mainly noticed the boost in fluxbox.  I think i'm gonna go with that and all that is, is 'sudo apt-get install fluxbox' right?  I am at work right now and really wanting to do this. right now is about the time I wish I enabled vnc over ssh. :(

---

### Post by aysiu on 2008-05-05
Well, that's it to get Fluxbox installed, but you may have to do some configuring afterwards.

A ton of people swear by Fluxbox here, but I've always found IceWM easier to configure, and I've created a guide for it: [http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

---

### Post by sports fan Matt on 2008-05-05
Id also think it depends on the specs of your computer :)

---

### Post by sports fan Matt on 2008-05-05
on a side note, im trying icewm now :)

---

### Post by msutton86 on 2008-05-05
K I installed fluxbox and am working on icewm.  Got fluxbox partially configured and am really digging it.  hopefully icewm doesn't take too long to install.  Guess we'll find out.  Thanks!

*update*
icewm seems to rock! it's even more responsive than fluxbox.  Thanks a lot for the link and turning me to it.

---

### Post by urukrama on 2008-05-06
Xubuntu is no longer very fast. If you want a fast Ubuntu system, do a [command line install]("http://www.psychocats.net/ubuntu/minimal"), and install Openbox, Fluxbox or Icewm (or something similar). I've always been partial to Openbox -- it just feels a lot more polished. If you want to give Openbox a try, follow the link in my signature.

---

### Post by gatewayasteroid on 2008-05-06
> **urukrama said:**
> Xubuntu is no longer very fast. If you want a fast Ubuntu system, do a [command line install]("http://www.psychocats.net/ubuntu/minimal"), and install Openbox, Fluxbox or Icewm (or something similar). I've always been partial to Openbox -- it just feels a lot more polished. If you want to give Openbox a try, follow the link in my signature.

*in medio stat virtus*

```
sudo apt-get install xorg xfce4 slim ristretto mousepad squeeze xfce4-terminal thunar-volman xfce4-mcs-plugins-extra xfce4-cpugraph-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-systemload-plugin tango-icon-theme epdfview

```

---

### Post by sixdrift on 2008-05-06
For what its worth...

My mains run stock Ubuntu (Hardy), but I have been running xubuntu on an old Toshiba laptop (650 MHz and only 384 MB RAM) since sometime last fall. No other "regular" GUI'd distro comes close to the perf of xubuntu on it. Just upgraded to Hardy and it still holds its own.

I like the lack of fluff and the get down to business feel of Xubuntu. On that old machine, I just want to do what I need done, I don't need fluff.

With that said however, if you want all out speed and are willing to sacrifice a lot of usability, go try Puppy (which is not regular IMHO, but it is fast) :neutral:

I guess it depends on what you are trying to do as to whether its worth pulling out that next little iota of performance. :confused:

---

### Post by the8thstar on 2008-05-06
If you go for a lighter WM, how do you get to the applications you used to see in Applications, Places and System (gnome menu)?

---

### Post by msutton86 on 2008-05-06
> **the8thstar said:**
> If you go for a lighter WM, how do you get to the applications you used to see in Applications, Places and System (gnome menu)?

I've noticed in most of the programs/applications menus, if you go to system or some similar menu it will have the gnome control panel. You wont wanna use some of the preferences since it's not gnome. you should be able to use most of the utilities.  I'm sure this is bad practice but it's all I know working with new environments thus far.

The one thing I can't figure out is how to find wireless networks in iceWM and fluxbox.  Does anyone know how to add an icon to the panel that will let me select a network?  In most cases I've been going into gnome logging out and switching back to fluxbox or icewm.

---

### Post by urukrama on 2008-05-07
> **the8thstar said:**
> If you go for a lighter WM, how do you get to the applications you used to see in Applications, Places and System (gnome menu)?

The most popular window managers (Icemw, Fluxbox, Blackbox, Openbox, Pekwm, etc.) have their own menus that you can easily edit to your needs.

---

### Post by stream303 on 2008-05-07
> **the8thstar said:**
> If you go for a lighter WM, how do you get to the applications you used to see in Applications, Places and System (gnome menu)?

If you regularly switch desktops / window managers, be sure to download the
"menu" package in synaptic or apt-get.  It tries to synchronize the programs you use into the menu systems of others.  Not always successful, but it helps.

---

### Post by sipickles on 2008-05-07
Xubuntu managed to resurrect an old laptop we had at work. (WinXP had killed it in a morass of broken links and erroneous registry nonsense).

I admit, the performance was impressive.

Until I saw Xubuntu had no network support. I mean, wtf? Few computers are autonomous nowadays.

Its like saying, 'Xubuntu has no internet access' or 'Xubuntu cannot use office documents'

Network access is FUNDAMENTAL.

If I wanted speed without a network, I'd install Win95!

Wake up Xubuntu team ;)

---

### Post by Person98 on 2008-05-07
what do you mean by network support? I am using xubuntu i am connected to a wireless network, if you mean filesharing with other computers you can always install nautilus instead of thunar will give you samba. If you don't want to use nautilus then there is a tutorial on this thread: [http://ubuntuforums.org/showthread.php?t=304131]("http://ubuntuforums.org/showthread.php?t=304131") hope it helps, and i much prefer xubuntu, I find it is more customizable through the GUI settings manager and it works brilliantly with xinerama. As for preformance boost it uses slightly less ram but both seem equally as snappy to me, but I am running it on pretty decent hardware.

---

### Post by brallan on 2008-05-07
is this the best way to install xubuntu (in ubuntu hardy 8.04)?:

```
sudo apt-get install xubuntu-desktop
```

I tried xubuntu years ago and realised it was considerably less user-friendly, so wound up sticking with ubuntu. Now i feel forced to try it again. I'm hoping i can figure out how to install xubuntu from synaptic and try it out before making a complete switch.

In our comunal house we-ve got machines, limited to 256MB RAM...```

:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           249        244          4          0          1         66
-/+ buffers/cache:        176         72
Swap:          494        133        360

```

but up till the hardy upgrade I was pretty happy. I wonder if whether the system recs of ubuntu quoted in the website are accurate for Hardy:> System Requirements

Ubuntu is available for PC, 64-Bit and Mac architectures. At least 256 MB of RAM is required to run the desktop install CD. Install requires at least 4 GB of disk space. 

I think its pushed my machines over the edge.

---

### Post by Person98 on 2008-05-07
Yeah that is the way to go, when you get to the log in screen you can click the session button and it gives you a list of options like xfce session or gnome.

---

### Post by sixdrift on 2008-05-07
> 
Until I saw Xubuntu had no network support. I mean, wtf? Few computers are autonomous nowadays.

Its like saying, 'Xubuntu has no internet access' or 'Xubuntu cannot use office documents'


When I installed Xubuntu the first time on my old laptop, it immediately recognized my NetGear wifi card and configured it. It took me 3 minutes to hunt down the paper I wrote down the WEP key on and then I was online.

It also immediately recognized my on-board ethernet and had that configured too. And I have had no problems with SMB access either.

Worked for me with very little effort.

---

### Post by msutton86 on 2008-05-08
> **sipickles said:**
> Until I saw Xubuntu had no network support. I mean, wtf? Few computers are autonomous nowadays.


I installed xubuntu on an old toshiba satellite two weeks ago and BLAM it worked amazing.  Had lack of sound but network was flawless.  what version did you use?

---

### Post by gatewayasteroid on 2008-05-12
> **sipickles said:**
> 

Until I saw Xubuntu had no network support. I mean, wtf? Few computers are autonomous nowadays.

Its like saying, 'Xubuntu has no internet access' or 'Xubuntu cannot use office documents'

Network access is FUNDAMENTAL.



Xubuntu had no WHAT???!!! Are you kidding?

> 
If I wanted speed without a network, I'd install Win95!

Wake up Xubuntu team ;)

I would say "Wake up, sipickles ;)"

:lolflag:

---

### Post by sml on 2008-06-08
> **msutton86 said:**
> So I've been using ubuntu for about a year now, and I absolutely love the usability of ubuntu. After playing with different distros though I've noticed a good performance boost.  I was reading about xubuntu and heard the performance is much better. I'm just not sure it would make a big difference because it's still all the bloated ubuntu distro.  has anyone ever seen a big difference in performance between ubuntu and xubuntu?  If not it may be time to graduate to a different distro.

Hmmm ... you need to provide more information.

Are you running an old PC with low RAM?
Do you have a high-spec PC and want max CPU performance for CPU intensive tasks?
Do you want a snappy window-manager / desktop-manager?

Anyway you have to define the context of 'performance' for this thread.

---

### Post by sml on 2008-06-08
> **msutton86 said:**
> I installed xubuntu on an old toshiba satellite two weeks ago and BLAM it worked amazing.  Had lack of sound but network was flawless.  what version did you use?

This is an example of guy defining 'performance' as requiring a low memory footprint for an old PC with low RAM.

---

### Post by timzak on 2008-06-09
I think he means that Thunar does not support browsing network shares.  While there are workarounds (like using Nautilus), I do agree that Xubuntu *should* support this out of the box.

> **sipickles said:**
> Xubuntu managed to resurrect an old laptop we had at work. (WinXP had killed it in a morass of broken links and erroneous registry nonsense).

I admit, the performance was impressive.

Until I saw Xubuntu had no network support. I mean, wtf? Few computers are autonomous nowadays.

Its like saying, 'Xubuntu has no internet access' or 'Xubuntu cannot use office documents'

Network access is FUNDAMENTAL.

If I wanted speed without a network, I'd install Win95!

Wake up Xubuntu team ;)

---

