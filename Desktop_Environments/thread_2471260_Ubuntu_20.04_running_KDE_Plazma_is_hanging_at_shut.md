---
title: "Ubuntu 20.04 running KDE Plazma is hanging at shutdown or hibernation"
date: 2022-01-24
forum: Desktop Environments
---

### Post by mike430 on 2022-01-24
Aloha!! ...wish i were in Hawaii...

Installed Ubuntu 20.04 and have used Gnome with this installation for quite some time. Recently installed KDE Plasma to try and found myself using it more frequently. One quirk that I have come across is that my system hangs either when I shutdown/restart or awake from hibernation. It's odd because there is really no pattern as to which one it will be. Me thinks from the logs that it may be a splash screen I am using, but removed and used the default and get same behavior. 

Gnome works fine and have no issue per my shutdowns/restarts or hibernation. 

Any ideas?

Thanks -Mike

---

### Post by mike430 on 2022-01-26
Anyone???

---

### Post by DuckHook on 2022-01-26
Mixing DEs is known to cause potential issues. The problem is that, even within the same distro, different flavours use slightly different configs. Many forum members mix DEs with no apparent problems, so it isn't a given, but I learned quite some time ago to not do this.

My motto is: keep your base install as close to its pristine default install state as much as humanly possible. I go to an even inhuman extent by hiving off most apps into containers so that they don't reside on my main install. Some would consider that excessive, but so far, I've been able to upgrade my main install without a hitch going back to Trusty. That's around 6 or 7 network upgrades by now and I attribute the ease and lack of problems to how pristine my installation always is.

When I want to explore different flavours or even distros, I do so in either VMs or Containers. This way, they have no impact on my base system. Were I to switch flavours, I would install that flavour from scratch, just to avoid the sort of configuration conflicts that might be the cause of your issues. I no longer have the energy to chase down obscure misconfigurations or to do the sort of detective work needed to unravel such self generated mysteries.

Unfortunately, since you've installed an alternate DE, there's no going back. DEs are a one way process and there's little you can do to unscramble that egg. I deal with this topic in the sticky linked in my sig: "The Best 'buntu Flavour"

I hope that another forum member can jump in here with a solution, but I think your best bet is to back up your data and install a pristine Kubuntu, then stick with that (which means, don't go layering Gnome or LXQT or Budgie on top).

---

### Post by mike430 on 2022-01-26
Thanks Duck for your time and the response. Certainly makes a lot of sense. I have used Gnome for years so really have never explored much in terms of other desktop environments. With that said, is it possible to install KDE Plasma at the time of a fresh new Ubuntu install in lieu of Gnome? or do I have to go with a different form of Linux that installs KDE Plasma by default. Ideally would like to continue using Ubuntu 20.04 LTS with KDE Plasma. Thanks.

---

### Post by DuckHook on 2022-01-26
It's a breeze to do what you want. What you are using is called plain Ubuntu or vanilla Ubuntu. The KDE flavour is called Kubuntu. It comes as a download and is installed in the same way as vanilla. It's a separate install though. You cannot get to it from the Gnome install media.

Please do have a look at the aforementioned link in my sig. It will explain what you need to know with sufficient background so that you understand and are not just following a recipe.

Good Luck and Happy Ubuntu-ing!

---

### Post by SeijiSensei on 2022-01-26
[http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/) for Kubuntu 20.04

The packagers for Kubuntu have caught up with the Ubuntu packagers.  Now there's a preview release for 22.04 as well: [http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

You might consider installing one of these into a KVM virtual machine and giving it a test drive. There will be new applications for many functions like dolphin for file management.

---

