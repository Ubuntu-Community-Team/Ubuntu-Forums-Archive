---
title: "A few questions about KDE4"
date: 2008-10-19
forum: Desktop Environments
---

### Post by Moonfrost on 2008-10-19
Hey everybody, as the title says I have a few questions about KDE4.
I used KDE4 when it came out but then I switched back to Gnome, now I took the plunge again and like KDE4 more than before and it also received a few updates that made it more stable.

1) How can I update KDE4 (If I can at all, I have 4.0.3) to 4.1? I tried looking everywhere but I can't (I have Hardy Heron 8.4.0.1) find it on the repos or anything (that's why I installed 4.0.3 instead), would I have to wait for Intrepid Ibex in order to be able to install 4.1 from the repos?

2) Is it better if I want to use KDE4 now to install Kubuntu the next time? I figured because it probably comes better implemented with Kubuntu-specific functions than if I just install it using normal Ubuntu, but I want somebody else's opinion.

3) How do I add a volume control icon/widget to my panel on KDE?

4) I have icons on my Desktop (duh!) but some of them are actually files, can I delete them directly without deleting just the icon and having to start up dolphin just to delete the file from the Desktop directory?

5) Is there any way to make pictures preview themselves when they are on the Desktop as with Gnome?

6) How can I make thing I connect (like a memory card/sd card, or when I insert a CD) to appear as Desktop icons as on gnome so I can access them whenever I want without having to click the notification before it disappears?

That would pretty much be it for now so if anybody can answer any of these it would be appreciated, thanks!

---

### Post by doorknob60 on 2008-10-20
> 
1) How can I update KDE4 (If I can at all, I have 4.0.3) to 4.1? I tried looking everywhere but I can't (I have Hardy Heron 8.4.0.1) find it on the repos or anything (that's why I installed 4.0.3 instead), would I have to wait for Intrepid Ibex in order to be able to install 4.1 from the repos?

Best way IMO is to upgrade to Intrepid Beta, it worked well for me. If you want it in Hardy go here: [https://launchpad.net/~kubuntu-members-kde4/+archive](https://launchpad.net/~kubuntu-members-kde4/+archive)

> 
2) Is it better if I want to use KDE4 now to install Kubuntu the next time? I figured because it probably comes better implemented with Kubuntu-specific functions than if I just install it using normal Ubuntu, but I want somebody else's opinion.

Ubuntu+KDE=Kubuntu, simple as that (assuming you install the kubuntu-desktop metapackage in Intrepid or the kubuntu-kde4-desktop metapackage Hardy)

> 
3) How do I add a volume control icon/widget to my panel on KDE?

Add Kmix to your Autostart (It's in System Settings > Advanced Tab > Autostart IIRC)

> 
4) I have icons on my Desktop (duh!) but some of them are actually files, can I delete them directly without deleting just the icon and having to start up dolphin just to delete the file from the Desktop directory?

I think this changed significantly since KDE 4.0.3, upgrade and it should work fine, I never used that old of KDE4 (without major issues and immediately switching back to Gnome) so I'm not sure.

> 
5) Is there any way to make pictures preview themselves when they are on the Desktop as with Gnome?
I don't think so, at least not that I know. Upgrading to 4.1.x might help, but I don't think I had previews on the Desktop either (I might have in Dolphin though).

> 
6) How can I make thing I connect (like a memory card/sd card, or when I insert a CD) to appear as Desktop icons as on gnome so I can access them whenever I want without having to click the notification before it disappears?

Add the 'New Device Notifier' plasmoid to your desktop or panel, then you can click it and it shows all the plugged devices. Might need to upgrade to 4.1.x first though.

Hope I helped, I use Openbox right now so it's from memory, and laziness to boot into KDE or go to another computer :-P

---

### Post by Moonfrost on 2008-10-20
> **doorknob60 said:**
> Best way IMO is to upgrade to Intrepid Beta, it worked well for me. If you want it in Hardy go here: [https://launchpad.net/~kubuntu-members-kde4/+archive](https://launchpad.net/~kubuntu-members-kde4/+archive)



Ubuntu+KDE=Kubuntu, simple as that (assuming you install the kubuntu-desktop metapackage in Intrepid or the kubuntu-kde4-desktop metapackage Hardy)


Add Kmix to your Autostart (It's in System Settings > Advanced Tab > Autostart IIRC)


I think this changed significantly since KDE 4.0.3, upgrade and it should work fine, I never used that old of KDE4 (without major issues and immediately switching back to Gnome) so I'm not sure.


I don't think so, at least not that I know. Upgrading to 4.1.x might help, but I don't think I had previews on the Desktop either (I might have in Dolphin though).



Add the 'New Device Notifier' plasmoid to your desktop or panel, then you can click it and it shows all the plugged devices. Might need to upgrade to 4.1.x first though.

Hope I helped, I use Openbox right now so it's from memory, and laziness to boot into KDE or go to another computer :-P

Thanks a lot for all the answers! seems 4.1 brings quite a lot of updates to the table so instead of updating now I will make a fresh installation of Intrepid Ibex next week when it comes out, thanks!.

---

### Post by meho_r on 2008-10-20
In case you change your mind, here's KDE 4 repo (version 4.1.2). Add it in your sources.list (/etc/apt/sources.list):

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

deb-src http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

---

### Post by meho_r on 2008-10-20
Oh, that's the same as doorknob60 provided (just "hardy" one). Sorry :(

---

### Post by Moonfrost on 2008-10-20
> **meho_r said:**
> In case you change your mind, here's KDE 4 repo (version 4.1.2). Add it in your sources.list (/etc/apt/sources.list):

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

deb-src http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

I tried updating with these repos, everything went well until one of the packages failed to install (it supposedly was broken, I think it was the kde edu package or something like that, not important) so the whole thing stopped. Okay, I removed that package which is not needed and then tried to upgrade again, again everything went well until one of the packages failed "again" so I don't know what's wrong. So I thought I could log out, go back to Gnome and just uninstall kde and re-install this time installing 4.1.2 directly, but when I tried to log in a blue screen with a small white-background terminal window appears with my username on the top left corner.

It seems X didn't start but I figure that it should show a normal black screen (the whole screen not just the corner) with normal terminal commands and such but no. I typed sudo reboot and rebooted the PC and tried logging in using KDE again, the same thing came up so I don't know what's wrong.

I'm now typing this from my Windows partition because I can't access Ubuntu at all.

---

