---
title: "Problems with various desktop environments"
date: 2014-07-15
forum: Desktop Environments
---

### Post by Damien_Duran on 2014-07-15
Hey, I was wondering if someone could tell me what's going on with my desktop environments...

I am running Ubuntu 14.04 LTS on my ASUS laptop. Recently, I wanted to check out some other desktop environments ( kubuntu and xubuntu specifically ). I took the following steps to get each of these environments...

-kubuntu---------------------------------------------------------------
1. Installed desktop in terminal
```

sudo apt-get install kubuntu-desktop

```

2. Restarted computer

When my computer booted up, it immediately switched to kubuntu-desktop environment. I even noticed that instead of the normal boot up screen, the ubuntu logo, it was the kubuntu logo. Now at the login screen, I found a menu that apparently let me switch between ubuntu-desktop and kubuntu desktop. However, I noticed that when I logged in with Ubuntu, a slight delay in the start-up took place. Soon afterwards, the screen went hay-wire (flashing mouse, irrelevant applications booting up, and then of course the side panel on the left never showed up, and eventually it just froze. So I restarted my computer and tried once more, but this time I launched kubuntu-desktop. I tried fixing ubuntu-desktop environment by going into the terminal and typing:

```

sudo apt-get install ubuntu-desktop
sudo apt-get clean

```

I'm not sure if that did anything significantly or if something else occurred in the time being, but upon reboot I was able to get into Ubuntu with only the slight delay in start-up occurring.

Eventually, I realized that the fact that the kubuntu boot up bothered me, I wasn't sure why it replaced ubuntu (considering the main OS was still Ubuntu 14.04 LTS). I wasn't sure if this was a problem that I created or if this was normal. To clarify : I was mostly confused on why the kubuntu logo was shown when powering on the computer instead of the Ubuntu sign. **So that's my first problem : How do I switch Ubuntu back to my main desktop environment?**
------------------------------------------------------------------------

-xubuntu---------------------------------------------------------------
1. Installed desktop in terminal
```

sudo apt-get install xubuntu-desktop

```

2. Restarted computer

So this is where it got even weirder for me. I recalled that installing the kubuntu desktop environment replaced my ubuntu desktop environment. [B]So another question I have is : Why did the xubuntu desktop not replace my current kubuntu desktop upon installation of such?
[/B]
Also I realized that when I installed this desktop environment, in the menu on the login screen (mentioned earlier), not one, but two more options were listed - being xubuntu-session and xfce session. The two looked and worked similarly, so I'm confused. **Why did I get both of those desktops instead of just the one I installed (xubuntu)?**
------------------------------------------------------------------------


Now here is my last problem...
I have tried to remove kubuntu desktop environment, xubuntu desktop environment, and even xfce desktop environment. I got into the terminal and started trying to hack away at these things...

One method I used was:
```

sudo apt-get install ubuntu-desktop
sudo apt-get --purge remove [desktop name]-desktop
sudo apt-get autoremove

```

Restarted computer, and checked for results...of course : didn't remove the desired environment.

Another method was:
```

sudo apt-get --purge remove [desktop name]-desktop
sudo apt-get autoremove

```

The reason I tried this as an alternative was because I didn't think installing ubuntu-desktop was necessary, considering I already had it installed and functioning.

The last method was:
```

sudo apt-get remove [desktop name]-desktop
sudo apt-get autoremove

```

Of course, this didn't work either.

[B]So my last question : If I so desired to uninstall a desktop environment, how can I do it? (provided the following methods didn't work for me)
[/B]thank you so much!

---

### Post by amanchesterman on 2014-07-16
Hi, I'm not well qualified to answer your question because I'm still quite a beginner and I don't have a lot of technical knowledge; but having landed myself in a situation similar to yours some years ago by 'trying out' various desktops I can say three things that may help.

1. When you install a 'desktop', you are installing what is called a 'metapackage'. As I understand it, a metapackage isn't actually a program: rather, it's like a list of programs or apps that are bundled under the same name. It works well for installing stuff, but if you uninstall it, all that does is to remove the list -- it doesn't actually remove the programs you have installed. That's why your attempts to remove the desktops are having no apparent effect.

2. A 'desktop', as you probably realise, includes a whole bundle of programs: a file manager, a network manager, a clock etc. etc., as well as things like panels and menus. So in order to remove them you have to uninstall them one-by-one, and in order to do that you need a list of what exactly is included within each desktop package. I don't have that for 14.04 versions, but there are very helpful tutorials which explain the principle for earlier versions [url href="http://www.psychocats.net/ubuntu/pureubuntu"]here[/url] and [url href="http://www.psychocats.net/ubuntucat/tag/pure-ubuntu/"]here[/url]. I guess that if you look around a bit you will find the list for 14.04.

3. When you install two or more desktops, you can easily end up with two or more file managers, calculators, clocks, menus etc., and that can slow things down and doesn't give you the true experience of using a 'pure' version of kubuntu, xubuntu or whatever. I have found that a better solution is to create a separate partition for each desktop, but to have them all use the same /home partition. The partitition for each desktop doesn't need to be very big, unless you install lots of apps or programs with it: I have an old laptop with three 10 gig partitions, which seems to be ample for 'trying out' purposes. Using it, I can choose which desktop I want at startup, but whichever I use I can then access the same documents, photos etc., which sit in a separate (larger) partition of their own.

I hope this is some help, and that someone with more knowledge than myself will come along and help you to get your system back to the way you want it.

---

### Post by vanadium on 2014-07-16
To revert your login screen to that of ubuntu, issue the command
[code]
sudo dpkg-reconfigure lightdm
[code]
After that indeed, there is no other option than to remove individual packages. You may want to remove the KDE / Lubuntu applications that now also clutter your search results using Software Center. for practical purposes, this is all you need to do (probably) to have the stock Ubuntu experience again.

You may continue cleanup by removing all packages that start with "kubuntu" and perhaps also these that start with kde, although the latter may also uninstall any application you might have that uses kde libraries. As such not a big issue: just reinstall that application afterwards.

In theory, you might take a look at all dependencies of kubuntu-desktop in synaptic. However, you will notice that a lot of dependencies are more general packages that are in use in Ubuntu as well. Bottom line: a full cleanup to factory defaults after installing another desktop is as such not feasible, unless you were able to record what extra packages were installed when installing the other desktop. Psychocats has done this exercise as shown in a post above, but not for 14.04.

I suspect the dependencies of kubuntu-desktop are not basic operating system components. So in theory, one could boot to a recovery prompt, remove all the packages kde-desktop depends on without breaking the terminal environment, then install ubuntu-desktop to pull back in the packages required for ubuntu. Just an idea. Would not recommend that though, unless you want to experiment.

---

### Post by cmcanulty on 2014-07-16
this site might help you out
[http://www.psychocats.net/ubuntu/pureubuntu]("http://www.psychocats.net/ubuntu/pureubuntu")

---

### Post by Damien_Duran on 2014-07-16
Thanks for the good explanations. I appreciate it. I'll play with uninstalling individual packages one at a time, see where I can get. I may just completely strip my computer of everything an just install ubuntu, and add the kubuntu environment - given the fact I don't enjoy xubuntu. This whole situation has just got me tied up haha. So yeah - thanks again!

---

### Post by Damien_Duran on 2014-07-16
I ended up going to [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu) to see what I could find. Wanting to remove xubuntu I decided to put in the code given by psychocats.net. When I entered the string into my terminal, I got a couple errors that said some of the packages were not found. So I simply found those packages and removed them from the string, and entered it back into the terminal.

So I'm not sure if this is supposed to work for all 14.04 users or if it coincidentally worked for me, but here is the process (how to remove xubuntu desktop)  - if it can help anyone...

```

sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview alacarte bison blueman brltty-x11 catfish espeak exo-utils flex fonts-droid fonts-lyx gigolo gmusicbrowser gnome-system-tools gnome-time-admin gstreamer0.10-gnomevfs gthumb gthumb-data gtk2-engines-pixbuf indicator-application-gtk2 indicator-sound-gtk2 leafpad libbison-dev libdigest-crc-perl libexo-1-0 libexo-common libexo-helpers libfl-dev libgarcon-1-0 libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libglade2-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgstreamer-perl libgtk2-notify-perl libgtk2-trayicon-perl libgtkmathview0c2a libgtkspell0 libido-0.1-0 libindicate-gtk3 libintl-perl libjpeg-progs libjpeg-turbo-progs libkeybinder0 liblink-grammar4 libloudmouth1-0 libnet-dbus-perl liboobs-1-5 libots0 librarian0 libsexy2 libtagc0 libthunarx-2-0 libtidy-0.99-0 libtie-ixhash-perl libtumbler-1-0 libunique-1.0-0 libvte-common libvte9 libwv-1.2-4 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin libxfce4util-common libxfce4util6 libxfcegui4-4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl lightdm-gtk-greeter link-grammar-dictionaries-en m4 orage parole pastebinit pavucontrol pidgin pidgin-data pidgin-libnotify pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text python-configobj rarian-compat ristretto screensaver-default-images scrollkeeper shimmer-themes system-tools-backends tcl8.5 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman tumbler tumbler-common xbrlapi xchat xchat-common xfburn xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfwm4 xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers && sudo apt-get install ubuntu-desktop

sudo apt-get autoremove

```

Next, I just restarted my computer, and xubuntu-desktop environment was removed! It successfully worked so thanks again everyone!

---

