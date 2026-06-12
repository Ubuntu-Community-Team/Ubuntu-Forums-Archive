---
title: "Multiple monitors - but question really is how I get admin privileges"
date: 2009-02-21
forum: General Help
---

### Post by rjstep3 on 2009-02-21
I have an nvidia card, quite powerful, and two monitors connected to it.

Using someone's helpful post, I found how to download and install the nvidia drivers. I learnt how to go to System - Administration - nvidia Xserver settings. There I saw that I could configure the second monitor (which was without any image) apply changes and have the glories of two monitors. That's the good part.

Problem!! I tried to save changes to X Configuration file and bingo!! the usual problem with Linux - "Unable to remove old X config back file "/etc/X11/xorg.conf.backup".

I tried to go to that file using the file browser, but of course I cannot delete it because I do not have the right privileges.

So when I re-boot, the thing goes straight back to one monitor.

I had the same issue with Linux the last time I tried to use it - everything requires a password, or some mysterious way of finding some permission to do anything. It's a monitor, not a security breach, why can I not make changes to my own system?

So two questions: how can I save MY configuration to MY file without some irritating dialogue telling ME that I cannot do what I want to do? and secondly, how can I give myself full privileges so that I NEVER AGAIN have to enter passwords to do things with MY computer?

thanks
rjstep3

PS sorry to sound irritated, but I am - I got fed up with Linux last time because of this obsession with security. It's actually worse than Vista. Someone in Linuxland has to wake up to the possibility that there are many computers out there like mine that are individually owned, and do not need the obsessive security that Linux/Vista seek to impose.

---

### Post by sandyd on 2009-02-21
i'm going to throw up saying this, and other people are going to too, but.....

type this in terminal
```

sudo chmod 777 /etc/X11/xorg.conf
sudo chmod 777 /etc/X11/xorg*

```

no security on xorg.conf or xorg*

happy now?

---

### Post by dorkdork777 on 2009-02-21
Or you could [LINK REMOVED] run the entire system as root, but this is not without its dangers. **_Be warned!_**

---

### Post by cariboo on 2009-02-21
The easiest and least dangerous way to do what you need ist to run nvidia-settings as root. Press Alt-F2 and type:

```
gksu nvidia-settings
```

@dorkdork777

It is against forum policy to tell or link to a howto telling someone to enable root.

Jim

---

### Post by bodhi.zazen on 2009-02-21
> **dorkdork777 said:**
> Or you could run the entire system as root but this is not without its dangers. **_Be warned!_**

Please do not give this kind of advice, it is detrimental can causes breakage.

@ rjstep3 :

I understand you are frustrated , but you will need to learn how to manage Linux.

Linux uses permissions.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Ubuntu uses sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

configure your nvidia card with :

```
gksu nvidia-settings
```do NOT "merge" your xorg.conf (unselect that option on the pop up windows that appears when you save changes.


Like any OS, once you learn your way around it is really not any more difficult then any other OS, certainly the registry in Widnows is not user freindly or easy either.

---

### Post by dorkdork777 on 2009-02-21
My apologies, I'd completely forgotten. :oops: Link removed from my original post.

---

### Post by rjstep3 on 2009-02-21
Wow, that was quick, thanks everyone.

I have saved the new config, though I think I did merge the file rather than save afresh. Any how it seems to work - is there some way I can save again without merging?

I take on board the point about just getting used to the OS, but the learning curve is steep. I am going through Keir Thomas' book on Ubuntu at the moment, which I am sure will throw light on many things. The links given in the replies are also really useful, and the help files look exceptionally full.

Seriously, I know Linux is known as secure, but there has to be a limit. I don't think it should be impossible to run as root IF I WANT TO. This is not a corporate warhorse - it is my computer (which I use for work). The worst is that I would have to re-load the OS, hardly the work of many days (or even hours).

Anyway, rant over, and problem solved. It's been a long evening, and now it's nearly 2am, so tempers are fraying here at simple problems. Time to get some rest.

Pluses of Ubuntu are a great interface, and quick too, it has really restored the speed of use we lost with Windows bloatware.

thanks again everyone,

rjstep3

---

### Post by bodhi.zazen on 2009-02-21
> **dorkdork777 said:**
> My apologies, I'd completely forgotten. :oops: Link removed from my original post.

Thanks, I knew your intentions were good ;)

@rjstep3 : I think you have to separate your current frustration (which is understandable) from long term use and security.

Leaning a new OS takes time. This holds true of any OS. do not make the "classic" mistake of confusing "familiar" with "easy to use".

How long have you been using Windows ? 

Truth be told, these are basic skills in Linux and once you have say 6 months under your belt it will seem quite easy.

And yes, IMHO, Ubuntu is both easy to use and secure.

Finally, yes, just re-run nvidia settings (gksu nvidia-settings) and re-save (without merging). Of course, if it is not broken don't fix it.

---

### Post by 3rdalbum on 2009-02-21
> **rjstep3 said:**
> Seriously, I know Linux is known as secure, but there has to be a limit. I don't think it should be impossible to run as root IF I WANT TO.

Linux's security system (in particular, Ubuntu's implementation of it) is really becoming the norm with operating systems. If you want to thank anyone, thank the virus writers; they've forced operating systems to become this way.

Temporarily becoming root is easy, but only if you find out how :-)  Go to Synaptic Package Manager and install the "nautilus-gksu" package. Log out and log in again. Now, whenever you right-click a file or a folder, you will be able to choose "Open as Administrator". You may be prompted for your password, after which the file will open with root privileges, or the folder will open in a root file browser.

All other windows will stay as your normal user for safety, and any other windows spawned from your "running as root" window will also be root.

I should stress that this should be temporary only; don't try and run everything from your root-owned windows.

---

### Post by Mud.Knee.Havoc on 2009-02-21
> **bodhi.zazen said:**
> Please do not give this kind of advice, it is detrimental can causes breakage.


The poster removed the link, but you quoted him - link and all.  Maybe it's a good idea to remove it? :)

---

### Post by bodhi.zazen on 2009-02-21
Good point.

This issue comes up frequently, as do the consequences of "running as root".

So, just to be clear : This is not "forbidden knowledge" and if you are an experienced user you may run as root if you wish.

The problem is, it is playing with fire. Giving this advice to new users, thereby circumventing any instruction on things like permissions, results in burns ;)

We are trying to prevent burns here, not mandate how experienced users run their systems.

---

