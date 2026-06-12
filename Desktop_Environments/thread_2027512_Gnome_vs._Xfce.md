---
title: "Gnome vs. Xfce"
date: 2012-07-16
forum: Desktop Environments
---

### Post by BlackJack on 2012-07-16
GNOME VS. XFCE

I have the following system:

Dell Latitude D630
4GB RAM
80 GB Hard Drive
Quadro NVS 135M
Ubuntu 12.04 LTS

I have been running the Gnome Classic desktop, sorry but I really do not like Unity. I much prefer a nice organized menu to the Dash. Even if you filter the results, you still have a screen full of icons all over the desktop to look through. Then, the dash doesn't seem to be able to filter on Windows applications installed under Wine. Yes,, I know the goal is to get away from Windows altogether, but there are some apps that I need, such as MS Project, MS Visio and Cisco Packet Tracer. I just find working with a traditional menu to be easier and more comfortable. Personally I wish that tablets and smart phones would move towards a menu rather than everything else moving towards scattered icons all over the desktop – but that is just me..

Anyway, I decided to take a look at Xfce so I installed the Xubuntu-desktop and found some interesting things.

1. The system seems to boot-up much slower now. My Windows 7 machine, which used to boot-up slower than Ubuntu, even though it is a much newer and faster machine, now boots much faster than my Ubuntu machine since installing Xubuntu-desktop.
2. In Xfce the file manager, Thunar I think it is, does not have Computer as a “place”. Not a big issue I guess since all your devices are automatically mounted with an icon to then on the desktop, and you can still go to them from within the file manager, but it is another one of those “it's just me” things.
3. I really like the panel at the bottom of the screen, I think I have heard it referred to a “dock” or “docky”. I guess it is similar to the Launcher in Unity, but it just seem so much nicer to me (my daughter mentioned that it looks a lot like the Mac she has at school).
4. I LOVE the way that the wheel on the mouse will scroll through the workspaces in Xfce.
5. I also like the way that I can call up the menu just by right clicking on the desktop, I don't think Gnome does that.
6. I was also unable to find any utility in Xfce that will give you system information, similar to the System tab in the Gnome System Monitor.
7. Not a big fan of the Office options that come with XFCE. I don't care for AbiWord, and I like having a full office suite like Libre Office gives you.

So, these are my first impressions. I like some aspects of both Gnome Classic and Xfce. Now, I have a couple of questions that I hope somebody will be able to answer for me.

1. Why would the boot-up process be be slower after installing the Xubuntu-desktop? I was under the impression that Xfce was supposed to be faster than Gnome, but in any case, it is slower just to boot-up, before logging in and loading the desktop environment.
2. Regardless of whether I load Gnome or Xfce, all apps seem to run fine. Thats good, but is there any way to install just one, or the other, and then add the features that you like without having to load the entire alternate desktop environment?
3. Under Gnome, when you add the Application Indicator to the panel it still shows the Bluetooth indicator even though Bluetooth has been disabled in BIOS and the Bluetooth Manager is not being loaded. Is there anyway to get rid of this? I would do away with the full Application Indicator all together, but it is the only way I have been able to get the battery state to show up, there is apparently a known bug that prevents the power indicator from showing up based on the Power Management applet itself. This is not a problem under Xfce.
4. When the system finishes its boot-up sequence and brings up the login screen there is a system sound that sounds like bongo drums. I would like to disable this, it is annoying to me, as well as those around me. Unfortunately, I have been unable to find any system setting for this under either Gnome or Xfce and the settings for mute and volume on the login screen itself are not persistent, when I mute it, or turn the volume all the way down, it is back to ¾ volume the next time I go to login. Any ideas?


I have been thinking about and even looking at Ubuntu for some time, but have never spent a whole lot of time with it because there were so may Windows based applications that I needed, but would not run under Linux. I have now gotten to a point where most (MS Project is the last one that I am still having issues with) of the applications I need will run under Linux and I am trying to spend more time on Ubuntu with the idea of moving my newer system to it (I am planning on using my Ubuntu system for my next project as a test to see if I am ready for the switch).

So any insight or advise would be greatly appreciated.

Thanks.

---

### Post by amanchesterman on 2012-07-16
I don't know if this will help, but I have Xubuntu (previously 10.10, now 12.04) and it is silent at start up and login. The fact that your computer still plays the Ubuntu bongo drums (your Q.4) makes me wonder if it is somehow loading both Gnome Classic and Xfce, thus taking longer to boot (your Q.1). You say you installed Xubuntu-desktop, did you uninstall Gnome at the same time?

As for the office applications (your comment 7) I agree about AbiWord, I have uninstalled it and use the LibreOffice suite instead.

---

### Post by LewisTM on 2012-07-16
+1 about the GNOME components loading. If you are happy with Xfce I encourage you to wipe GNOME by running Pyschocat's pure Xfce [command]("http://www.psychocats.net/ubuntu/purexubuntu").

You can install components of each DE. For example you can install Nautilus or GNOME System Monitor and run them in Xfce. Some packages might want to bring in other stuff so run this in a terminal:
```
sudo apt-get install <package> --no-install-recommends
```

The Computer location is still available in Thunar. Enter computer:// in the location bar (if visible) or by pressing Ctrl-i. I agree that it's not used very much.

If you really like the bottom dock, what you can do is remove it (yep!) and replace it with Cairo-Dock which is more dynamic and will show running applications à la MacOSX. That way you won't need the top panel task buttons and you can use that space for other things.

Enjoy!

---

### Post by BlackJack on 2012-07-16
amanchesterman and LewisTM,

Thanks for the quick responces.

No, I didn't uninstall Gnome. I was under the impression, mistakenly maybe, that the underling kernel and drivers were the  same and the desktop environment related “stuff” was not loaded until you selected the desktop you wanted to use and logged in.

Is there Gnome specific or Unity specific or Xfce specific “stuff” that is loaded before your select the desktop and login? If so, can I uninsall Unity, Unity 2D and the Unity 2D Panel to make the boot process go faster without adversely affecting Gnome? I would really like to keep Gnome Classic as an option for now.

LewisTM,

When I get to that point, what does the “--no-install-recommends” do? My understanding is that when you install a package it will automatically install dependencies, does it also install optional things that you do not need?

Thanks again.

---

### Post by LewisTM on 2012-07-16
I don't have enough experience switching back and forth between DEs to have a definite answer.

You can have a look in the Xfce Settings manager/Session and Startup/Application Autostart. Disable any GNOME component and see if that helps.

In fact I think - and this is purely hypothetical - that it's the switching that causes your problem. There is a Ubuntu component called ureadahead that examines the boot process (even post-login events) and creates a profile to speed up subsequent boots. If you constantly change what's loaded after login (the DE) then ureadahead can't do its job properly. That's why it's best to stick to a single DE. Can someone prove me wrong?

Some GNOME packages recommend other GNOME packages to be installed alongside. If you want to avoid cascading dependencies you should use that command switch. It won't make a huge difference, just save some disk space and keep things tidy.

---

### Post by 3Miro on 2012-07-16
I uses Ubuntu-Tweak to disable the login sound. It is annoying especially on a laptop.

The XFCE bottom panel is more like the old Gnome 2, then Unity or Docky.

The scroll to change desktop is an option that I cannot live without (although you can set it in Unity, KDE and LXDE, but not Gnome 2 and Gnome 3).

You can use Gnome-system monitor in XFCE as well as many other Gnome programs.

Glad you enjoy XFCE, I switched back in 9.10, long before Unity or Gnome-shell and I love XFCE.

---

### Post by Peripheral Visionary on 2012-07-17
Take the Xubuntu 12.04 LiveCD for a test drive. It has some "Gnome stuff" in it (Xfce and Gnome both rely on GTK), enough to make it easier for "ordinary" desktop users, but not enough to slow it way down.

**Xubuntu is NOT just Ubuntu with Xfce added in!** It's a different mix that I find quick and responsive even on my 8-year-old Dell Dimension. Silent, very fast boot-up, infinitely configurable.

Of course the LiveCD experience is slower than the installed experience, but it will give you an idea of how different Xubuntu is from Ubuntu with "xubuntu-desktop" added onto it. It's a whole 'nother animal!

---

### Post by alonesurvivor on 2012-07-18
Well, i love Gnome 2, but new unity and gnome 3, Mate, Gnome Shell and Cinnammon Sucks. 

You can recreate the Gnome 2 desktop with Xfce, is cool.

But now i have Lubuntu, with Lxde obviously,is simple and faster.

---

### Post by TenPlus1 on 2012-07-18
Am running Xubuntu 12.04 on my laptop which is fast, and Lubuntu on my desktop which is v.fast...

---

