---
title: "what will happen on upgrades 11.10?"
date: 2011-08-30
forum: Desktop Environments
---

### Post by ottosykora on 2011-08-30
I now installed in addition to the full install of ubuntu 11.04, also the xubuntu-desktop

Well, it is not as nice as gnome2 but can be used, thought some very important things are missing.

Now Q:
what will now happen when it comes to upgrade to 11.10?

Will the xubuntu be upgraded to 11.10 and what ever is left from the 11.04 ubuntu (gnome2 desktop, unity etc) will stay in place as it is now.

OR

will the xubuntu be upgraded to 11.10 and all the ubuntu rest too?

Note: I have installed the xubuntu desktop and the ubuntu-desktop was removed, thought I still have now the ubuntu classic still in the boot menu.

---

### Post by 3Miro on 2011-08-30
When you make an upgrade, everything that is installed is being upgraded. XFCE will be updated to the latest version of XFCE, which is the same 4.8 with bug fixes. Gnome will be upgraded from Gnome 2 to Gnome 3 and Unity will ge upgraded to the latest version. 11.10 will come with Gnome 3 + Unity as default.

The XFCE part of the upgrade should be smooth. The Gnome 2 to Gnome 3 part may be problematic. I would recommend a clean install and you must absolutely backup all important data before upgrade. Sometimes upgrades don't work and just break the system.

If you remove ubuntu-desktop only, you will not remove Gnome 2. The ubuntu-desktop package is just a meta package designed to help install Gnome, but by itself, it doesn't do anything. If you want to remove Gnome 2 from your current version, then I suggest you look at this tutorial:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

If you remove Gnome 2, then you will not upgrade Gnome on the next release and the upgrade will be less risky. However, every upgrade has some risk.

---

### Post by ottosykora on 2011-08-31
hmm, yes understand half way.

I was told, that when I would like to upgrade 11.04 to 11.10 ubuntu, I need the metapackage (which I still did not 100% understand what it is for) called ubuntu-desktop on my computer.

From that, somehow I thought, that when this packet is missing, the ubuntu part is not going to be updated, nut the xubuntu part only, as  Ihave now xubuntu-desktop instead of ubuntu-desktop.

I am not after removing gnome2, just I thought when I have xubuntu-desktop metapack and not ubuntu-desktop metapck, only the xubuntu part will be updated or so.

---

### Post by snowpine on 2011-08-31
You're over-analyzing it. Simple: Everything you have installed will be updated from 11.04 to 11.10 version.

---

### Post by Enigmapond on 2011-08-31
> **snowpine said:**
> You're over-analyzing it. Simple: Everything you have installed will be updated from 11.04 to 11.10 version.

But I wouldn't do that just yet....unless you like bug hunting. It's only an Alpha release.

---

### Post by snowpine on 2011-08-31
"will be" = future tense  :)

---

### Post by ottosykora on 2011-08-31
yes snowpipe, I am just doing some experiments to be partially ready for the end of the world, when all gnome2 things will be lost.

I was over analyzing, but I got some many advises about all that, so it is rather confusing. For example someone told me, that if I want update ubuntu, I would need the metapack ubuntu-desktop on my system otherwise it will not work or so.

---

### Post by Enigmapond on 2011-08-31
> **ottosykora said:**
> yes snowpipe, I am just doing some experiments to be partially ready for the end of the world, when all gnome2 things will be lost.

I was over analyzing, but I got some many advises about all that, so it is rather confusing. For example someone told me, that if I want update ubuntu, I would need the metapack ubuntu-desktop on my system otherwise it will not work or so.

Not true...have no idea where you got this information but it probably wasn't here. As stated...when you upgrade, regardless of what's on your desktop...everything just upgrades to the new version...end...zip...finito, fin konetz!..  :)

Oh & Cheers!

---

### Post by snowpine on 2011-08-31
> **ottosykora said:**
> For example someone told me, that if I want update ubuntu, I would need the metapack ubuntu-desktop on my system otherwise it will not work or so.

This statement is false.

Xubuntu users should be able to upgrade Xubuntu 11.04 to Xubuntu 11.10 without installing ubuntu-desktop.

---

### Post by ottosykora on 2011-08-31
well it was here 
[http://ubuntuforums.org/showthread.php?t=1831011](http://ubuntuforums.org/showthread.php?t=1831011)

answer #8


so from that I thought that only what has metapack will be dealt with...

still no idea what that meta thing is for

---

### Post by snowpine on 2011-08-31
A "metapackage" is a package that provides no functionality itself, but installs a bunch of other packages as "dependencies." In other words it is an easy way for developers to bundle related software together. 

You can read exactly what other packages ubuntu-desktop depends upon here: [http://packages.ubuntu.com/natty/ubuntu-desktop](http://packages.ubuntu.com/natty/ubuntu-desktop)

---

### Post by 3Miro on 2011-08-31
ottosykora, what is it that you want to do?

Psychocats have tutorials on how to install or remove different DE on your system. Their information is accurate and reliable.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

If you have already installed ubuntu-desktop, then you can remove it and still use Gnome (and Unity). It is possible that an upgrade from 11.04 to 11.10 does require ubuntu-desktop to be installed, but this is only if you want to use Gnome (going from Gnome 2 to Gnome 3). 

If you want to use XFCE, then you don't need ubuntu-desktop at all.

---

### Post by ottosykora on 2011-08-31
I may not be expressing myself clear , as I think all do misunderstand me completely.

No, I do not want remove gnome

I have installed ubuntu 11.04, with all it offers.

Then as a backup, I have installed over it the packet xubuntu-desktop.

The installation via synaptic, did as first ***remove*** the metapacket ubuntu-desktop, before it went to install the rest.

This gave me the oportunity to log in under xubuntu and ubuntu gnome as well as unity.

As I got the info that in order to upgrade ubuntu from 11.04 to 11.10, I have to have the now removed packet ubuntu-desktop (metapacket only), 
I thought when I reinstall the meta packet ubuntu-desktop from repository, only then the whole ubuntu gnome2 system will be replaced by the gnome3/unity.

Now my question was, if I do not reinstall the now removed meta packet ubuntu-desktop, will the whole ubuntu be upgraded to whatever gnome3 and uninty version, or will this not be done due to missing meta ubuntu-desktop and only the xubuntu will be updated because of the presence of the meta xubuntu-desktop now.

is this now understandable or what can I more explain?

What does happen when the metapcket some-buntu-desktop is present during upgrade?
What does happen when the metapacket some-buntu-desktop is not present during upgrade?

---

### Post by snowpine on 2011-08-31
If a package is installed, it will be updated.
If a package is not installed, it will not be updated.

You can have both xubuntu-desktop and ubuntu-desktop installed if you like.

---

### Post by ottosykora on 2011-09-01
>You can have both xubuntu-desktop and ubuntu-desktop installed if you like.<

it used to be like this earlier, but now it is not possible.
When installing xubuntu-desktop, the ubuntu-desktop is removed automaticaly and I tried now opposite , when ubuntu-desktop is installed, the xubuntu-desktop is removed.

Here I mean the metafile called this way. The installer simply removes the other one and does not apparently allow to have more then one installed.

Try yourself, it really works this way.

Therefore I still do not see the exact functions behind all this metapackets.

---

### Post by snowpine on 2011-09-01
I did not realize xubuntu-desktop and ubuntu-desktop are mutually exclusive (it's been a while since I used *buntu).

Nevertheless, as has been mentioned several times, the only purpose of a "metapackage" is to install a list of other packages. Removing the metapackage will not remove the packages that were installed along with that metapackage.

---

### Post by 3Miro on 2011-09-01
ubuntu-desktop doesn't install anything by itself, so  you haven't really uninstalled any programs. All the Gnome packages that are installed on your system will be upgraded to Gnome 3. 

However, the upgrade process will require running some conversion scripts to change the settings and such from Gnome 2 to Gnome 3. It is possible that the Update Manager requires ubuntu-desktop to be installed to run those scripts. It is possible for the lack of ubuntu-desktop to break your upgrade.

However, I think this is unlikely. If you want to play it safe (or probably overly safe), you can install ubuntu-desktop back. xfce on 11.04 and 11.10 would be essentially the same, so this should be the safest option.

---

### Post by Copper Bezel on 2011-09-02
Edit: Scrubbed, misread something.

---

### Post by ottosykora on 2011-09-02
the current situation is, I went to synaptic, installed ubuntu-desktop, which in turn did remove the xubuntu-desktop and xubuntu-notifyd what ever this one was for.

Well will see what comes in future.

So far manged the xubuntu to look and work almost as the ubuntu does.

But when they will change also the nautilus and all addons with it, well then bad luck.

---

### Post by hhh on 2011-09-02
> **ottosykora said:**
> xubuntu-desktop and xubuntu-notifyd what ever this one was for.
It was for notification popups. Don't worry, it was removed because Gnome under Ubuntu wants to use notify-osd instead, which Xfce will use also.

> **ottosykora said:**
> But when they will change also the nautilus and all addons with it, well then bad luck.
Yes, Gnome wants Nautilus and Xfce wants Thunar, to have both environments installed means you will have both file managers installed too. This gets messy because Nautilus also handles drawing the desktop in Gnome but Xfce does it another way. Personally, I would just choose one environment and stick with it, it doesn't make much sense to spend half your time in Gnome and half in Xfce.

> ... xubuntu-desktop... some very important things are missing.
Name some. I haven't found anything that you can do in Gnome that you can't do in Xfce, although I do use nautilus-elementary to make dealing with other partitions and removable media easier.

---

### Post by ottosykora on 2011-09-02
>Name some. <

one for me is the seahorse addon to nautilus, which does  not exist for thunar.
Other people are using other addons for nautilus, there are so many, and also they know already that  those addons will not  be available when all goes gnome3.

---

### Post by 3Miro on 2011-09-02
Nautilus vs Thunar is philosophical question at its heart. I want my file manager to move, rename and autorun files. If I need extra functionality, I call a different program. The result is that Thunar is lightning fast, while Nautilus can be a bit slow to load.

It is possible to use Nautilus under xfce, it will be a bit heavy as it will load a lot of gnome libraries, but it should work just fine.

---

### Post by grahammechanical on 2011-09-03
Has anyone here looked at this?

[http://www.xubuntu.org/node/49]("http://www.xubuntu.org/node/49")

Xbuntu is already upgrading to 11.10. There is a beta release. See what they are doing.

Regards.

---

### Post by hhh on 2011-09-03
> **ottosykora said:**
> >Name some. <

one for me is the seahorse addon to nautilus, which does  not exist for thunar.

So use Nautilus in Xfce, as 3miro said. That's what I do, I run Nautilus Elementary. The only problem is that Nautilus wants to draw the desktop, but Xfce's xfdesktop wants to do the same. There are a couple of ways to solve this. I want Xfce's menu, which xfdesktop also provides, so I prevent Nautilus from taking over. ...

1) Install nautilus and gconf-editor

2) In the Run dialog (Alt+F2) run gconf-editor

3) Navigate to apps>>nautilus>>preferences and disable "show_desktop"

4) Navigate to desktop>>gnome>>background and disable "draw_background" and close gconf-editor

5) In the Run dialog, run gksu gconf-editor and enter your password

6) Disable the same two preferences as before

7) Open Thunar, go to Edit>>Preferences>>Advanced and disable "Enable Volume Control", close Thunar

8 ) In a terminal, run xfce4-settings-manager, go to Sessions and Startup>>General, enable "Prompt on logout"

9) In the same manager, go to "Application Autostart", under Thunar change "Restart Style" to "Never", click the "Quit Program" button to kill Thunar, click the "Save Session" button and exit.

10) Run Nautilus once to start the Nautilus daemon.

11) Exit your session, check the box in the exit manager for "Save session for future logins"

That's it. You can use your plugin(s) at will. Nautilus will now mount your CDs, DVDs, USBs, other drives, etc... You won't see icons on the desktop for the drives (since xfdesktop is handling that) but you will see them in Nautilus. You can disable the "Save session for future logins" now if you want. You can't remove Thunar without removing Xfce, but that shouldn't be a deal breaker for most people.

Oh, and if your icon set provides them, you'll see the cool logos on your Documents, Downloads, Music, Pictures, Public, Templates and Videos folders.

---

### Post by mikodo on 2011-09-03
hhh, 

Thanks for the clearly written guide.

:P

---

### Post by hhh on 2011-09-03
Not a problem. :^)

---

### Post by rigel4 on 2011-09-03
I am running 11.10 Beta 1, without much problem, only one app crash so far. Loving it.
I wonder if anyone knows if I will be able to upgrade from beta 1 to the finished release?

---

### Post by hhh on 2011-09-03
@rigel, huh, Lightdm instead of GDM, I had read about that switch but didn't realize it was already here. I already switched from Mousepad to Leafpad. I don't use Bluetooth, so no problem there. Places is now Lenses? 3 terminals in the menus? Whatever...
[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview)

You are already on track to get the final release. Just continuing with upgrades will bring you through RC to Release, AFAIK.

---

### Post by mikodo on 2011-09-03
> **hhh said:**
> 

You are already on track to get the final release. Just continuing with upgrades will bring you through RC to Release, AFAIK.
+1, the way it is supposed to work.

I usually do a fresh install, less chance of messing things up. Just bring my ~/ partition during the install from previous.

---

### Post by ottosykora on 2011-09-04
> **3Miro said:**
> Nautilus vs Thunar is philosophical question at its heart. I want my file manager to move, rename and autorun files. If I need extra functionality, I call a different program. The result is that Thunar is lightning fast, while Nautilus can be a bit slow to load.

It is possible to use Nautilus under xfce, it will be a bit heavy as it will load a lot of gnome libraries, but it should work just fine.

I am more and more realizing, that my english language is probably getting to bad, simply not understandable, as what ever I write here, nobody seems to understand a word of it-


I know I can install nautilus under xface

I am running nautilus also under xface

It is the addons that might be a problem *in the future*

When the whole ubuntu will move to be based on gnome3 libs, the nautilus will be and the addons will have to be too.


Therefore many addons might then not be available for the 'new' nautilus.

I was not talking about nautilus, I was talking about an addon called ***seahorse***, which I would miss very much as there is not of  much real alternative around for that. 


hmmm, I am getting old I know, but which part of it is written so bad so nobody can understand it? 
I am not native english speaker, so sorry for using somehow too complex or otherwise strange expressions.

---

### Post by hhh on 2011-09-04
@ottosykora, your English is poor, but it's more that your thoughts are muddled. It doesn't take English skills to see that Xfce is not xface. You didn't mention Seahorse until page three. Finally...
> *in the future*
Sorry, fresh out of my future predicting pills.

---

