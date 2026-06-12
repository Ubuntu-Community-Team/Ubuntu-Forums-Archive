---
title: "Problems in installing LightDM"
date: 2011-09-19
forum: Desktop Environments
---

### Post by zedixal on 2011-09-19
Hi,

I'd like to know if there is currently a *safe* way to install LightDM on Xubuntu
I added the [LightDM PPA]("https://launchpad.net/%7Elightdm-team/+archive/ppa") repo and did

```
sudo apt-get install lightdm lightdm-theme-webkit lightdm-theme-gnome
```and selected lightdm as the default login manager

BUT

All my attempts ended up in a mess:
1) a win95-like GUI
OR
2) a totally blank screen (probably because I dared to uninstall gdm)

I was aware of [this thread]("http://ubuntuforums.org/showthread.php?t=1618314") but I hoped that after some months things were going better...

---

### Post by raja.genupula on 2011-09-19
use ctrl+alt+f1
then do this one by one 

```
sudo stop lightdm
```

```
sudo start lightdm
```

---

### Post by zedixal on 2011-09-19
Thank you raja.genupula, I somewhat restored my desktop!

I did Ctrl+Alt+F1, and a login prompt appeared (nice trick BTW). After login I typed

```
sudo stop lightdm
```and the output was

```
lightdm stop/waiting
```Then I did

```
sudo stop lightdm
```then one or two flashes of logs, and in a couple of seconds a blank screen again :shock:
The second time, after stopping lightdm I managed to reinstall gdm:

```
sudo apt-get install gdm
```and rebooted. Ctrl+Alt+F1 and

```
sudo stop lightdm
sudo start gdm
```and whoaa! - a working desktop again. I uninstalled lightdm 

```
sudo apt-get remove --purge lightdm
```and selected gdm as the default login manager

```
sudo dpkg-reconfigure gdm
```The most annoying thing was that I had to manually start gdm every time. So I added a line to /etc/rc.local

```
start gdm
```My desktop was a little shaggy after the experience (system font shrinked, compositing disabled), but now is more or less the same as before.

In conclusion,

I suppose that lightdm needs some more refining to work in Xubuntu.

---

### Post by raja.genupula on 2011-09-19
i am glad that you have solved your issue , i think we can enable compositing from window manager , are you getting any errors while doing enable of it ?

---

### Post by zedixal on 2011-09-20
No, luckily I aint got any error message!

---

### Post by garvinrick4 on 2011-09-20
@zedixal
 Do not forget to go to software sources and remove the check mark off of your ppa installed.
You do not need anything lightdm since reverted back to gdm.
And FYI
```
sudo /etc/init.d/gdm restart
``````
sudo /etc/init.d/lightdm restart
```will do the trick of stopping and starting gdm or lightdm. (just a preference thing) Enjoy your Ubuntu.

---

### Post by zedixal on 2011-09-20
TY garvinrick4, still learning here

I think I can mark the thread as solved :)

---

### Post by garvinrick4 on 2011-09-20
> TY garvinrick4, still learning here
We are all zedixal, each and everyone. You enjoy your Ubuntu.

---

