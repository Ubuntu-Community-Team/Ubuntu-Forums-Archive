---
title: "Ubuntu 11.04 gnome3 installation removed visual effects"
date: 2011-05-01
forum: Desktop Environments
---

### Post by bhupinderjitbawa on 2011-05-01
I have just intalled ubuntu 11.04 ..then i tried to replace unity...
first installed gnome3 and then removed unity...but when i logined ..it says ubuntu unable to login login failed logout..
when i use user defined login..i m able to login but no visuals..visual comes like window 95 on gnome3 environment...

any solution?

---

### Post by slooksterpsv on 2011-05-01
Make sure you do the following:

sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard

Did you do it from the Gnome3 PPA? If so you do need to do:

sudo apt-get dist-upgrade

It's easier than doing it piece by piece.

How did you install it? Like what were the steps you took?

---

### Post by bhupinderjitbawa on 2011-05-01
I have installed ubuntu 11.04 from downloaded iso image.
then i imported PPA..

```
sudo add-apt-repository ppa:gnome3-team/gnome3
apt-get update
apt-get install gnome-shell
```

then i restarted as said restart required..but when i tried to login it didnt allow me to.
now i m able to login using user defined session and there is working gnome3 but there are very bad visuals..windows dont have maximize and minimize button..and they have rectangle like hard shape as in window 95.

i thought unity had been broken so from synaptic i removed it.
but no solution...

---

### Post by slooksterpsv on 2011-05-01
> **bhupinderjitbawa said:**
> I have installed ubuntu 11.04 from downloaded iso image.
then i imported PPA..

```
sudo add-apt-repository ppa:gnome3-team/gnome3
apt-get update
apt-get install gnome-shell
```

then i restarted as said restart required..but when i tried to login it didnt allow me to.
now i m able to login using user defined session and there is working gnome3 but there are very bad visuals..windows dont have maximize and minimize button..and they have rectangle like hard shape as in window 95.

i thought unity had been broken so from synaptic i removed it.
but no solution...

Ahh there's the issue, you have to do:

sudo apt-get dist-upgrade

So that it resolves dependencies of Gnome 3; it removes the Gnome 2 stuff and installs the Gnome 3 libraries. Just installing Shell leaves bits and pieces and only installs bits and pieces, which makes for a failed install of Gnome 3. After you do the dist-upgrade, do this:

sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard

---

