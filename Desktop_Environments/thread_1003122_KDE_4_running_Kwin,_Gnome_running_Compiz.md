---
title: "KDE 4 running Kwin, Gnome running Compiz"
date: 2008-12-05
forum: Desktop Environments
---

### Post by alingham on 2008-12-05
Hi guys

I'm sorry if this has already been asked - but I had a breif search and there's not a lot out there on this...

I've recently installed KDE 4.2 Neon (Nightly builds) following this guide: [http://hehe2.net/linux-general/try-kde-42-now-in-ubuntu/](http://hehe2.net/linux-general/try-kde-42-now-in-ubuntu/)

I am impressed with the look and feel of KDE. But it seems that I have a combination of Gnome and KDE running, which is fine, except for a few matters.

a) Gnome Screenlets runs in KDE 4, but I want Plasma to handle all widgets. So I have to stop Gnome Screenlets from running. Is there any way I can make it so that when I log into Gnome, the Screenlets work, but when I log into KDE they don't?

b) Compiz works great in Gnome along with Emerald, but in KDE I want the default Oxygen + KWin to be running. Is there anyway so that like a), when I log into Gnome that Compiz runs with the Emerald theme, whilst when I log into KDE that Kwin runs with the Kwin themes?

Any help on this would be great.

---

### Post by Wisp558 on 2008-12-07
You're asking a lot of the questions I want answered. I can't find a way to do this either. It's quite aggravating :(

---

### Post by nenadsuperzmaj on 2009-01-29
Wow, another thread with the questions asked I need an answer to, but no help yet.

How come no-one answered this yet?

Perhaps most of the people choose either KDE or Gnome. But I'd like them both for variety :)

---

### Post by celticbhoy on 2009-01-29
I also have both and would just like Gnome to run GDM, and KDE to run KDM.

---

### Post by nenadsuperzmaj on 2009-01-29
> **celticbhoy said:**
> I also have both and would just like Gnome to run GDM, and KDE to run KDM.

Well, weather you are using KDE or Gnome isn't determined until you actually choose it, and you can't choose it before either GDM or KDM is loaded :)

Perhaps there is a way to run either GDM or KDM depending on the last DE that was used the previos way the computer was used...

---

### Post by pritamps on 2009-01-29
There is one way to do this (from the terminal, don't know how a GUI would work). Basically, you are going to tell each program to start in only Gnome or only KDE:

Most autostart programs are located in one of the following two locations

```
1. ~/.config/autostart
2. /etc/xdg/autostart
```

Check in both those directories and you will see the file you are looking for. It will probably be in the form of a .desktop file. Find the program that you are looking for (say fusion-icon.desktop) and open it in the text editor of your choice. Then, to only start in Gnome, add

```
OnlyShowIn=GNOME;
```
to the end of the file. For KDE, you would add
```
OnlyShowIn=KDE;
```

In fact, you could even tell the program which desktop NOT to show up in. For example: 

```
NotShowIn=KDE;
```

To set the default window manager to kwin in KDE 4.2, do the following:

System Setting => Default Applications (in Personal) => Window Manager => Use the default KDE Window Manager (Kwin)

I hope that helps!
Enjoy!

---

### Post by nenadsuperzmaj on 2009-01-29
> **pritamps said:**
> There is one way to do this (from the terminal, don't know how a GUI would work). Basically, you are going to tell each program to start in only Gnome or only KDE:

Most autostart programs are located in one of the following two locations

```
1. ~/.config/autostart
2. /etc/xdg/autostart
```

Check in both those directories and you will see the file you are looking for. It will probably be in the form of a .desktop file. Find the program that you are looking for (say fusion-icon.desktop) and open it in the text editor of your choice. Then, to only start in Gnome, add

```
OnlyShowIn=GNOME;
```
to the end of the file. For KDE, you would add
```
OnlyShowIn=KDE;
```

In fact, you could even tell the program which desktop NOT to show up in. For example: 

```
NotShowIn=KDE;
```

To set the default window manager to kwin in KDE 4.2, do the following:

System Setting => Default Applications (in Personal) => Window Manager => Use the default KDE Window Manager (Kwin)

I hope that helps!
Enjoy!

Cheers pritamps, that seems to be on the right track. However I have a few questions.

What does "X-GNOME-Autostart-enabled=true" mean in these .desktop files?

Could it be that this line is making problems?

Can I start without Screenlets Deamon, but just the desired Screenlets themselves?

In neither of these two "autorun" folders is Emerald. Now, I know it is in some script, but I'm still confused about what script is run during the boot, during the Gnome, and during the KDE loading process...

Could you please shed some light on this matter?

---

### Post by pritamps on 2009-01-29
> **nenadsuperzmaj said:**
> Cheers pritamps, that seems to be on the right track. However I have a few questions.

What does "X-GNOME-Autostart-enabled=true" mean in these .desktop files?

Could it be that this line is making problems?

Can I start without Screenlets Deamon, but just the desired Screenlets themselves?

In neither of these two "autorun" folders is Emerald. Now, I know it is in some script, but I'm still confused about what script is run during the boot, during the Gnome, and during the KDE loading process...

Could you please shed some light on this matter?

Emerald won't come up if you neglect compiz, since emerald will be in the window-decorator option of ccsm. Also, if you set the window manager to kwin like I mentioned in KDE, emerald won't be a problem since kwin uses its own window decorator.

Sorry, I don't know what that line means, so I wouldn't change it. Adding the lines I mentioned would do the trick.

---

### Post by pritamps on 2009-01-29
> **nenadsuperzmaj said:**
> Cheers pritamps, that seems to be on the right track. However I have a few questions.

What does "X-GNOME-Autostart-enabled=true" mean in these .desktop files?

Could it be that this line is making problems?

Can I start without Screenlets Deamon, but just the desired Screenlets themselves?

In neither of these two "autorun" folders is Emerald. Now, I know it is in some script, but I'm still confused about what script is run during the boot, during the Gnome, and during the KDE loading process...

Could you please shed some light on this matter?

About the screenlets, I remember reading that the old version of screenlets needed you to start screenlets individually, but the new version doesn't. 

But I think the executables of each screenlet are located in one of the following two locations
```
1. ~/.screenlets
2. /usr/share/screenlets 
```

Each screenlet will have its own folder and a corresponding executable .py file which you can add to your startup programs list. Either by creating a desktop file in the autostart folder or through the sessions menu.

Hope that helps!

---

### Post by nenadsuperzmaj on 2009-01-29
I'm in KDE right now, and I've been messing with many config files, but something seems to be horribly wrong.

For example, that NotShowIn=KDE line worked fine for all but two screenlets. Their .desktop files are the same as the others.

No matter what I do, I cannot get KWin to work in KDE! 

When I run emerald with --replace option, it works. But kwin --replace shows UbuntuStudio theme which I installed in Gnome. I use it combined with Emerald window decoration in Gnome, but somehow proper Oxygen Kwin just can't be run...

Changing system settings wont help either. Choosing either of kwin, compiz or metaciy and hitting Apply has absolutley no effect...

I've found ~/.config/compiz/compizconfig/config that has sections for Gnome and KDE, as well as for KDE4 (which I use) but I'm not sure what do do with ir or with the Default.ini file in the same folder.

It bothers me that Screenlets' and compiz settings are spread to so many folders and text files that I can't figure them out. I suppose it would be much easier if all the setting concerning one piece of software were in a single file...but that is hardly going to happen...

Anyway, thanks for your efforts, pritamps. If some new idea hits you, hit me :p

---

