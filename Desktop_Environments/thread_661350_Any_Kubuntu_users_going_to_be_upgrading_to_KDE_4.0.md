---
title: "Any Kubuntu users going to be upgrading to KDE 4.0 in 3 days time?"
date: 2008-01-07
forum: Desktop Environments
---

### Post by Rob500 on 2008-01-07
As the title suggests, anyone gonna be upgrading to KDE 4.0? I for one am looking forward to it :)

---

### Post by Shmifty on 2008-01-08
Definitely, I know its not going to be perfect, but that in itself is half the fun.

---

### Post by fish2ways on 2008-01-08
Sure will.

---

### Post by nocturn on 2008-01-08
How will you be upgrading? Compile it yourself or will there be any experimental packages when 4.0 comes out?

---

### Post by kvonb on 2008-01-08
-

---

### Post by Rob500 on 2008-01-08
I tried a stripped down and modified Kubuntu live CD with KDE 4.0 Beta 2 included and I did find one or two weak links. I do like the interface but the menu bar is quite big. Hopefully the final release will have a feature to shrink the size, or at least cover it up with maximised windows.

---

### Post by bashveank on 2008-01-08
I'll probably wait for 4.0.1 or so, just so that I get the full package.

---

### Post by dontgetshocked on 2008-01-09
I will definitely be upgrading.Although kde is not quite as mature** yet,** it is the preferred choice of many a geek.I have seen the latest reviews and they are quite good.Think everyone will be pleased.I believe KDE is the future of linux.

Freedom to choose - "Linux", the peoples operating system"

---

### Post by psychicdragon on 2008-01-09
> **nocturn said:**
> How will you be upgrading? Compile it yourself or will there be any experimental packages when 4.0 comes out?
There's a repo with the rc2 packages linked from kubuntu.org. I presume someone will build packages of the final release. 

That said, I have no intention of upgrading. The quality of the rc2 release was abysmal.

---

### Post by getaceres on 2008-01-09
I will install it and see how it goes.
I was a KDE user until Compiz came out and it was not working well with KDE. Also, as it was freezed in KDE 3.5 while GNOME was evolving, I switched to GNOME but I have high expectations in KDE4. I know KDE 4.0.0 may be nothing more than a rude beta but I think KDE 4.1 or 4.2 will be more like the Desktop we (old KDE users) were expecting.

---

### Post by harold4 on 2008-01-09
I'll be leaving 3.5.8 on the laptop while upgrading a desktop to 4.0.

---

### Post by Rob500 on 2008-01-09
Is there any way to undo changes, like *cough* System Restore in Windows? I know I can just back stuff up and reinstall Kubuntu if I need to but I don't wanna be wasting time doing this.

---

### Post by kuja on 2008-01-09
> **Rob500 said:**
> Is there any way to undo changes, like *cough* System Restore in Windows? I know I can just back stuff up and reinstall Kubuntu if I need to but I don't wanna be wasting time doing this.

At least for Gutsy and Hardy, I do believe KDE4.0 will only be available as *seperate* packages(ie: kde4base instead of kdebase, ark-kde4 instead of ark, etc), with a seperate config directory (~/.kde4). If this is still the case later then I see no reason why there would be any danger in trying it to find out what's going on with it.

I *personally* think, based on some of the things I've read, that KDE 4.0.0 will still be more for developers that wanted to wait until release than a full blown release and we still won't see many of the goods till much later (4.1, 4.2, etc)

---

### Post by perrantrevan on 2008-01-09
So I've got a mixture of KDE3.58, KDE4 RC2 tied together with Compiz Fusion!

The RC2 packages have been recently upgraded on the quiet and so seem to work better than before.

I had a few issues with the way properties of the .desktop files were configured in the start menu but am now using the KDE4 versions of Dolphin, Ksysguard, Konsole and Konqueror in my KDE3.58 session.

You would think that having the KDE4 libraries might slow things down but the launch time for these programs seems much faster than the old versions. Plus the Oxygen icons/widgets just make KDE3.5 seem ancient and ugly. I upgraded my nvidia driver using Envy as there is a bug with scrollbars under the older drivers that uses up a lot of CPU power. 

I've also tried running kwin-kde4 in a KDE3.58 session (run kwin-kde4 --replace). Works great and you can run system-settings to enable the Desktop Effects if you like. They are quite workable but noticeably not as polished as Compiz Fusion.

I found it was best to create a separate user account for running KDE4 as a session, otherwise the desktop icons form the /Home/Desktop folder really clutter the Plasma workspace. Compiz Fusion seems to work as well as it does under KDE3.5. So expect minor issues with the pager and systray.

So, if you have the time for a little bit of tweaking, you don't need to fully change to a KDE4 DE. Just run the main programs under KDE3.5.

---

### Post by Sokraates on 2008-01-10
I've been using KDE4 as my primary desktop since RC2 (tested it before with mixed results) and I am actually very please with the stability and overall polish of the looks and apps. Even compositing works fine on my trusty HP nx6110 (1.6 GHz, 512 MB RAM).

I've read that some people encountered massive issues with crashes, fortunately I've only seen the occasional crash and/or weirdness here and there. Nothing serious.

KDE4 creates a new config-directory under ~/.kde4. On the first login it copies the Desktop-folder (and more?) from you ~/.kde-directory. So you won't endanger your profile by trying KDE4 out.

What vexes me most is that a LOT (yes, that has to be written in capital letters) of visual configuration options are still missing. The problem simply is that Plasma has been started late and it shows. Plasma as a whole is not easily configured. The patch that allows easy resizing (not scaling, as now) will unfortunately not make it into the final version. Also some widgets are suboptimal and (like the rest of Plasma) not (easily) configurable. E.g. the battery status widget displays all battery slots, even if you only use one. So I always have one full and one empty battery. Furthermore some SystemSettings-modules have not yet been ported. Oh, and Adept won't work, as well.

I'm grateful for Kubuntu Hardy not being an LTS. This way the Kubuntu-devs can concentrate on KDE4, adding all the patches they see fit as soon as they want and maybe also adding that extra Kubuntu-touch. 

Apart from that, the desktop is impressive. I like it so much, actually, that I'm willing to put up with all the annoyances I've described above. WINE, DOSBox, Amarok (for KDE3), OpenOffice, Firefox ... they all work excellently, so there's no reason for me not to keep using KDE4.

For all those who wonder how to easily install KDE4: follow [these instructions]("http://kubuntu.org/announcements/kde4-rc2.php"). Though you will probably have to reinstall everything tomorrow. :)

---

### Post by Sokraates on 2008-01-10
> **perrantrevan said:**
> So I've got a mixture of KDE3.58, KDE4 RC2 tied together with Compiz Fusion!

The RC2 packages have been recently upgraded on the quiet and so seem to work better than before.

I had a few issues with the way properties of the .desktop files were configured in the start menu but am now using the KDE4 versions of Dolphin, Ksysguard, Konsole and Konqueror in my KDE3.58 session.

You would think that having the KDE4 libraries might slow things down but the launch time for these programs seems much faster than the old versions. Plus the Oxygen icons/widgets just make KDE3.5 seem ancient and ugly. I upgraded my nvidia driver using Envy as there is a bug with scrollbars under the older drivers that uses up a lot of CPU power. 

I've also tried running kwin-kde4 in a KDE3.58 session (run kwin-kde4 --replace). Works great and you can run system-settings to enable the Desktop Effects if you like. They are quite workable but noticeably not as polished as Compiz Fusion.

I found it was best to create a separate user account for running KDE4 as a session, otherwise the desktop icons form the /Home/Desktop folder really clutter the Plasma workspace. Compiz Fusion seems to work as well as it does under KDE3.5. So expect minor issues with the pager and systray.

So, if you have the time for a little bit of tweaking, you don't need to fully change to a KDE4 DE. Just run the main programs under KDE3.5.

That's quite the Chimera you've created. :)

The clutter on the desktop bugged me, too, until I started to clean it up. That's when I found out that I'm just one of those messy persons who use their desktop as a folder for random stuff they're too lazy to put in the proper ones.

---

### Post by ErikTheRed on 2008-01-10
I'll definitely be upgrading tomorrow. The RCs were a little rough but I still have some hope. I think by the time 4.1 rolls around it'll be in really great shape and hopefully Amarok 2 will be out as well.

---

