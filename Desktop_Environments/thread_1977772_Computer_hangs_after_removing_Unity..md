---
title: "Computer hangs after removing Unity."
date: 2012-05-10
forum: Desktop Environments
---

### Post by Bramkaandorp on 2012-05-10
Without going into the why and whatfore of removing Unity, here's my proble.

I had removed the most basic parts of Unity some time ago, and am using Gnome-Shell quite happily.

However, I felt that it was a waste of space to have any Unity stuff on my computer, so I started looking for a more extensive removal command. Several of them did an admirable job with no issues.

The trouble for me started when I executed the line:

```
sudo apt-get autoremove --purge unity-*
```

After remmving all extra stuff that was left (through synaptic), and restarting, my screen said (still does) the following:

*CPUFreq Utilities: Setting ondemand CPUFreg governor...         [ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
*Stopping anac(h)ronistic cron                                   [ OK ]
*Stopping save kernel messages                                   [ OK ]
*Starting the Winbind daemon winbind
saned disabled; edit /etc/default/saned
*Starting anac(h)ronistic cron                                   [ OK ]

*Stopping anac(h)ronistic cron                                   [ OK ]

*Checking battery state...                                       [ OK ]

*Stopping System V runlevel compatibility                        [ OK ]

I've reinstalled Unity (through ctrl-alt-f1), but that didn't help.

I hoped there would be some kind of "restore" option in the installer (on the live-cd), but no dice.

I hope that's helpful, because I sure don't know what to do next.

---

### Post by wilee-nilee on 2012-05-10
To be honest removing unity and just going to synaptic to do cleanup is  not a good policy. The well known website psychocats run by a mod on  this forum has desktop removal scripts to just get the desktop you want,  gnome 3 alone is not even there. This can be done though and there  are random websites the claim their method works.

The good thing though is there is a remix of precise that is gnome 3  only I have it installed my self. Here is a link if you can't get this  fixed or just decide to get things done so you can move on.

[https://launchpad.net/ugr](https://launchpad.net/ugr)

The problem with removing the way you did is that unity is a plugin in  compiz, and all of this sits inside the gnome 3 desktop, so when you  start to remove stuff you have to know exactly what your doing or a person may have problems.

Hope this helps, if it was me as I weigh time of fix against just a  install and choose the fastest method, I would just install the remix  and call it a day.

---

### Post by Bramkaandorp on 2012-05-10
> **wilee-nilee said:**
> To be honest removing unity and just going to synaptic to do cleanup is  not a good policy. The well known website psychocats run by a mod on  this forum has desktop removal scripts to just get the desktop you want,  gnome 3 alone is not even there. This can be done though and there  are random websites the claim their method works.

The good thing though is there is a remix of precise that is gnome 3  only I have it installed my self. Here is a link if you can't get this  fixed or just decide to get things done so you can move on.

[https://launchpad.net/ugr](https://launchpad.net/ugr)

The problem with removing the way you did is that unity is a plugin in  compiz, and all of this sits inside the gnome 3 desktop, so when you  start to remove stuff you have to know exactly what your doing or a person may have problems.

Hope this helps, if it was me as I weigh time of fix against just a  install and choose the fastest method, I would just install the remix  and call it a day.

Serves me right for being too quick with software.

I don't think that I will do a clean install just yet. I still have lots of data on the computer, so I'd have to salvage that first.

If I do reinstall the computer, I'm sure I'll go to the psychocats site. I've gotten a lot of good info from them in the past, so it's definitely a good place to revisit. I might also try the Gnome 3 only distro, but then I'd have to know whether they have the same dependencies and such as Ubuntu, or whether it's a completely separate project.

Thank you very much for the info, it really helped me in evaluating the situation.

---

### Post by wilee-nilee on 2012-05-10
> **Bramkaandorp said:**
> Serves me right for being too quick with software.

I don't think that I will do a clean install just yet. I still have lots of data on the computer, so I'd have to salvage that first.

If I do reinstall the computer, I'm sure I'll go to the psychocats site. I've gotten a lot of good info from them in the past, so it's definitely a good place to revisit. I might also try the Gnome 3 only distro, but then I'd have to know whether they have the same dependencies and such as Ubuntu, or whether it's a completely separate project.

Thank you very much for the info, it really helped me in evaluating the situation.

That remix is using the same repos as the main release, it is the same minus the unity desktop, minus a few other apps like privacy and thunderbird.

I would do a side by install in your situation if possible and just drag you're data over. You can make a list what you actually have installed in the OS there now to look at as well, this command will dump a installed text in home.

```
dpkg --get-selections > installed-software
```

---

### Post by Bramkaandorp on 2012-05-10
> **wilee-nilee said:**
> That remix is using the same repos as the main release, it is the same minus the unity desktop, minus a few other apps like privacy and thunderbird.

What's so special about Thunderbird that it's not installed? I use it, so if I can't, that would be a major drawback.

> I would do a side by install in your situation if possible and just drag you're data over. You can make a list what you actually have installed in the OS there now to look at as well, this command will dump a installed text in home.

```
dpkg --get-selections > installed-software
```

If I'm correct, then I can also use that list to install programs afterward, right? Not that I would do so, since it might also remove some things, or add things which might muck up the works. I'll do that as soon as I've saved all my data (which I'm doing through the live disk). It might take some time, but it's worth it.

---

### Post by wilee-nilee on 2012-05-10
> **Bramkaandorp said:**
> What's so special about Thunderbird that it's not installed? I use it, so if I can't, that would be a major drawback.



If I'm correct, then I can also use that list to install programs afterward, right? Not that I would do so, since it might also remove some things, or add things which might muck up the works. I'll do that as soon as I've saved all my data (which I'm doing through the live disk). It might take some time, but it's worth it.

You would just install thunderbird, all the repos are the same as the regular release. Anything missing is a install a way.

Yes that list can be used as a reinstall, but if you run the whole thing you would have the set up you have that is broken. I would just look at it for the main apps you are missing and any thing you may have added that you forget.

The dependencies are listed as all the app names, when you install say thunderbird it picks up the dependencies automatically.

---

### Post by Bramkaandorp on 2012-05-11
> **wilee-nilee said:**
> You would just install thunderbird, all the repos are the same as the regular release. Anything missing is a install a way.

Yes that list can be used as a reinstall, but if you run the whole thing you would have the set up you have that is broken. I would just look at it for the main apps you are missing and any thing you may have added that you forget.

The dependencies are listed as all the app names, when you install say thunderbird it picks up the dependencies automatically.

I still wonder why they left Thunderbird out of the distro. Do they have Evolution as a replacement? That'd suck, since it's a nightmare to remove.

---

### Post by mc4man on 2012-05-11
your --purge unity-* removed the unity-greeter package & without the gtk-greeter installed & configured to be used then you've nothing for lightdm to 'load' for login

---

### Post by wilee-nilee on 2012-05-11
I would get to the net access recovery cli and install the gnome-shell if it was me.

---

### Post by Bramkaandorp on 2012-05-11
> **mc4man said:**
> your --purge unity-* removed the unity-greeter package & without the gtk-greeter installed & configured to be used then you've nothing for lightdm to 'load' for login

Good to know. Now I know exactly why I shouldn't do that in the future.


After reinstalling Ubuntu and replacing the .mozilla in my home folder with the folder from my backup. After that, whenever I start Firefox, it tells me that it's already running (which it wasn't. I hadn't started it yet.) and that I have to stop it or restart my system.

I suspect it's because some of the folders in the .mozilla folder have different rights (signified by lock icons). However, after changing the rights to where they are read-write the problem is still there.

So I'm going to have to put the folder in there again, but I'd have to know how to do that without having the rights screwed up.

The same is true for Thunderbird (after replacing the .thunderbird folder)

Any thoughts?

---

### Post by Bramkaandorp on 2012-05-11
> **wilee-nilee said:**
> I would get to the net access recovery cli and install the gnome-shell if it was me.

I already had Gnome-Shell installed before the computer went haywire, so that wouldn't help.

---

### Post by Bramkaandorp on 2012-05-12
Bump (because of post #10)

---

### Post by Bramkaandorp on 2012-05-13
Never mind. I solved it by typing "gksudo nautilus" in the terminal, and changing the rights of the entire hard disk and all files therein.

Consider this thread closed.

---

