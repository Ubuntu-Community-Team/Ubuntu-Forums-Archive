---
title: "Openbox-Ubuntu"
date: 2008-09-21
forum: Desktop Environments
---

### Post by jludeman on 2008-09-21
**[FONT="Verdana"]Openbox-Ubuntu[/FONT]**

**[FONT="Verdana"]Why do it?:[/FONT]**

1. Slowe(r) hardware.

My main desktop system is fairly old. It has a 1Ghz Athlon CPU with 512 MB of ram and a fairly new 80GB hard drive.

So I wanted a system that would be light on resources and hard drive space.
	
After the install I was so pleased with the results that I installed it on my newer faster laptop. On the slow system it's pretty zippy. On the laptop it's almost scarey.

2. Clean user interface with optional bell's and whistles.
	
Openbox has many ways to operate. Almost unlimited custom hot keys for frequently used programs.
	
Customizable right click menu. Hot key invoked custom menus.

Your choice of panels. I use gnome-panel

If you like desktop icons they are available through external means. I don't like anything on my desktop except a panel that I can turn on and off.

**[FONT="Verdana"][/FONT]The system plan:**

1. Clean alternate disk install.
2. Install Xorg and openbox.
3. Add repositories and software.
4. Update to the latest versions.

**[FONT="Verdana"][/FONT]How to do it:**

1. Download or otherwise get an iso or cd.

I use Xubuntu alternate cd exclusively because I will not be using XFCE or KDE or Gnome metacity.
It's a smaller download and has always worked for me.

2. Choose command line install from the cd menu.

3. After the install has completed you will have a basic command line linux system. Sudo apt-get install nano. Sudo nano /etc/apt/sources.list. Add the repositories you want or need. My working list is below.

4. Sudo apt-get install Xorg openbox openbox-themes obconf

5. Add all the software you want or need. This is very subjective and up to you. Below is my list of must have and nice to have software by category.

In most categories I have tried a bunch of stuff and these are my picks.

All of these fit on my custom live cd iso except openoffice suite.

6. In synaptic mark all upgrades and download them.

7. Use remastersys to create a live cd backup. If I had a place to upload mine I would be glad to do so.

8. Enjoy and tweak your new system!

Below are the scripts I use to toggle gnome-panel and conky. There are also fragments from my menu.xml. This file will be found in /home/yourusername/.config/openbox.

Congratulations!

Notes: 

I will be glad to answer questions and give help on this topic. Hardware issues are definitely not on topic. This includes conky which often requires hardware knowledge.

My sytem includes a wireless home lan. That is an option that requires another topic. Let me know if you want one posted. Lan questions here are off topic.

---

### Post by K.Mandla on 2008-09-22
Moved to Desktop Environments.

---

### Post by snowpine on 2008-09-22
Subscribed! I am a big Openbox fan. I use Crunchbang and SliTaz on my computers, which are two excellent distros based on Openbox. Looking forward to reading/sharing some good Openbox tips on this thread. :)

Here is my Openbox tip of the day. If you like jludeman's tutorial for minimal Ubuntu+Openbox, but you aren't really a do-it-yourself kind of person, or you want a "complete" install with Firefox, OpenOffice, etc., you can install Crunchbang from the command line. Follow steps 1 and 2 of the tutorial above (download iso, install command line), then try this: [http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation](http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation)

It will use more hard drive space than jludeman's tutorial (about 2gb, still less than full Ubuntu), but you'll have all the apps you need out-of-the-box. Obviously, if you have enough ram, it's easiest just to install Crunchbang from its Live CD, rather than dealing with the hassle of installing the CLI then running the script. :) For computers with less than 128mb of ram, though, Live CDs aren't an option.

---

### Post by lukjad on 2008-09-22
This sounds interesting. I'll check it out. Thanks!

---

### Post by jludeman on 2008-09-22
My first post was not complete. I hit post instead of preview while editing.

Thanks for the tip about the live cd. One of the reasons I undertook my project is because I needed a live cd with all my favorite apps.

My system may still be worthwhile for those that want a smaller system. My live cd ISO is around 490MB. Installed it runs about 

The following is a complete version of my original post with links and code boxes.

Openbox-Ubuntu

Why do it?:

1. Slowe(r) hardware.

My main desktop system is fairly old. It has a 1Ghz Athlon CPU with 512 MB of ram and a fairly	new 80GB hard drive.

So I wanted a system that would be light on resources and hard drive space.
	
After the install I was so pleased with the results that I installed it on my newer faster laptop. On the slow system it's pretty zippy. On the laptop it's almost scarey.

2. Clean user interface with optional bell's and whistles.
	
Openbox has many ways to operate. Almost unlimited custom hot keys for frequently used programs.
	
Customizable right click menu. Hot key invoked custom menus.

Your choice of panels.

If you like desktop icons they are available through external means. I don't like anything on 	my desktop except a panel that I can turn on and off. I prefer gnome-panel.

The system plan:

1. Clean alternate disk install.
2. Install Xorg and openbox.
3. Add repositories and software.
4. Update to the latest versions.

How to do it:

1. Download or otherwise get an iso or cd.

I use Xubuntu alternate cd exclusively because I will not be using XFCE or KDE or Gnome metacity.
It's a smaller download and has always worked for me.

2. Choose command line install from the cd menu.

3. After the install has completed you will have a basic command line linux system. Sudo apt-get install nano. Sudo nano /etc/apt/sources.list. Add the repositories you want or need. My working list is below.

```

# Remastersys
deb http://www.remastersys.klikit-linux.com/repository/ remastersys/ 

# wxWidgets/wxPython repository at apt.wxwidgets.org
deb http://apt.wxwidgets.org/ gutsy-wx main 
deb-src http://apt.wxwidgets.org/ gutsy-wx main 

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe 

deb http://security.ubuntu.com/ubuntu/ gutsy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security main restricted 

deb http://security.ubuntu.com/ubuntu/ gutsy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe 

deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse 

deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse 

deb http://archive.canonical.com/ubuntu/ gutsy partner 

deb http://packages.medibuntu.org/ gutsy free non-free 

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted 

```

There are additional repositories for wxPython, Remastersys. 

I got the latest wine from their site.[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")]
Swiftweasel and Swiftdove I got from Sourceforge.
[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=614543]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=614543")

4. Sudo apt-get install Xorg openbox openbox-themes obconf

5. Add all the software you want or need. This is very subjective and up to you. Below is my list of must have and nice to have software by category.

```
Packages:

Software that ends up on the gnome menu that is part of a larger package.

gnome-utils
gnome-games

Software list by gnome menu category:

Games:

Dosbox

Graphics:

GImageview
Gimp
Blender

Internet:

d4x - downloader for x - I'm on a phone line modem so I need this.
pan newsreader 
swiftweasel - fast firefox browser clone
swiftdove - fast thunderbird email clone
wifi-radar
uTorrent - runs under Wine - I know there are linux native torrent managers and I don't like any of them.

Office:

Gedit - text editor and more.
Gnumeric - for quick simple spreadsheets.
Abiword - reads rtf and Word docs
Open office - entire suite to be added after the main install. 

Programming:

Editra - still checking this one out
Geany - still checking this one out
ghex - hex editor
PyCrust 
PyShell
WxGlade
Xrced
(The compilers and such will be listed under non-menu items.)

Sound & Video:

Audacity
Gnome Mplayer - the best for streaming radio
Totem - just for the light show
VLC - the champ for videos
XMMS - don't bug me about this one - my favorite music player

System Tools:

disk usage analyzer - aka baobab - gnome-utils
file finder - aka gnome-search-tool - gnome-utils
gparted - partition editor
pcman - file manager - simply the best better than all the rest
synaptic - of course
terminal - gnome-terminal

Wine:

Get's it's own menu spot and very much deserves it. Currently using 1.0.
Wine programs:

games 
Programs I wrote for windows that I want and need.
calc98 - the best calculator on any system
Paintshop Pro - cause I've used it for years and there is no learning curve. I do use Gimp a lot though.
Video rippers and burners. Linux loses on this front.

Non menu items:

alacarte - menu editor
build-essential - for source installs
file-roller - needs rar unrar zip 
firehol - my favorite firewall
gdebi
gnome-app-install - optional
gnome-applets
gnome-netstatus-applet
gnome-panel
lynx - command line browser
nfs-kernel-server
python-wxgtk2.8 - from their website see my sources.list
remastersys - from their website see my sources.list

vi vim and perl - hate em all - wish they would just quit hogging my hard drive
```

In most categories I have tried a bunch of stuff and these are my picks.

All of these fit on my custom live cd iso except openoffice suite.

6. In synaptic mark all upgrades and download them.

7. Use remastersys to create a live cd backup. If I had a place to upload mine I would be glad to do so.

8. Enjoy and tweak your new system!

Below are the scripts I use to toggle gnome-panel and conky. There are also fragments from my menu.xml. This file will be found in /home/yourusername/.config/openbox.
```

#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
exec killall conky
else
exec conky

fi

```
```

#!/bin/sh

# click to start, click to stop

if pidof gnome-panel | grep [0-9] > /dev/null
then
exec killall gnome-panel
else
exec gnome-panel

fi

```

```
  <menu id="panels" label="Panels">
  <item label="Gnome Panel - toggle">
    <action name="Execute"><execute>/home/jim/scripts/gpanel-toggle.sh</execute></action>
  </item>
    <item label="Conky - toggle">
    <action name="Execute"><execute>/home/jim/scripts/conky-toggle.sh</execute></action>
    </item>
  </menu>
<menu id="system" label="System Tools">
  <item label="Terminal emulator">
    <action name="Execute"><execute>gnome-terminal</execute></action>
  </item>
  <item label="PCmanfm - Home">
    <action name="Execute"><execute>pcmanfm /home/jim/</execute></action>
  </item>
  <item label="Desktop Backgrounds">
    <action name="Execute"><execute>gnome-appearance-properties -p background</execute></action>
  </item>
  </menu>

```
Congratulations!

Notes: 

I will be glad to answer questions and give help on this topic. Hardware issues are definitely not on topic. This includes conky which often requires hardware knowledge.

My sytem includes a wireless home lan. That is an option that requires another topic. Let me know if you want one posted. Lan questions here are off topic.

---

### Post by lukjad on 2008-09-22
Ummm... I may have missed it, but do you have a link as to where the iso is?

---

### Post by jludeman on 2008-09-23
Actually I mentioned in the post that I had no place to upload it to. I have no site of my own.

If people are interested give me a few days and I will try to track down a site on the web where it can be at least temporarily available.

---

### Post by Atsuko on 2008-09-23
You could make a tracker of it and upload it [here](http://linuxtracker.org/).
Is it like Blackbox? I really like Blackbox and I'm doing a install right now on an old gateway and will need some thing like this to run a GUI on it.
Was going to do Blackbox.

---

### Post by snowpine on 2008-09-23
> **Atsuko said:**
> You could make a tracker of it and upload it [here](http://linuxtracker.org/).
Is it like Blackbox? I really like Blackbox and I'm doing a install right now on an old gateway and will need some thing like this to run a GUI on it.
Was going to do Blackbox.

Openbox is a lot like Blackbox. However, Blackbox is kind of outdated (last updated Nov. 2005) so I recommend Openbox instead.

---

### Post by eriqjaffe on 2008-09-24
> **snowpine said:**
> Openbox is a lot like Blackbox.In fact, Openbox is a fork of Blackbox.

---

### Post by cdwillis on 2008-09-24
I did a similar install to yours last week on my older laptop. If it runs this fast on an old machine I would be curious to see it really fly on a new computer.

---

### Post by urukrama on 2008-09-24
> **eriqjaffe said:**
> In fact, Openbox is a fork of Blackbox.

Openbox *was* a fork of Blackbox. The code has entirely been rewritten when it hit version 3.

---

### Post by jludeman on 2008-09-25
Update to making the iso. Remastersys does indeed make an iso from your system. The iso will not work on a custom system using openbox as a manager. It only works on stock gnome Ubuntu installs.

There is a do it yourself version [here.(http://help.ubuntu.com/community/InstallCDCustomization)]("http://help.ubuntu.com/community/InstallCDCustomization"). I will attempt to follow that guide as I really need a working iso for myself.

With virtualbox and all the compiling tools my iso is up to 554MB for a fully updated gutsy with the latest kernel. 

I'll post back with results.

---

### Post by jludeman on 2008-09-25
As it turns out the upgrade step of my install was a mistake. My system has quit functioning correctly. Possibly the kernel upgrade.

A brief search on the web leads me to believe that my upgrades are leading me to some sort of Hardy. A Hardy experiment is what lead me back to Gutsy in the first place. Hardy is very screwed up!

All that work in vain. Ubuntu is too fast of a release schedule. Debian is too slow a release schedule.

I'm about to give up on Ubuntu. Dapper to Gutsy I was pretty happy although there were a lot of bugs.

Now I'm about fed up with Ubuntu. I want my system to work and be fairly up to date.

Period.

---

### Post by snowpine on 2008-09-25
Sorry you lost all that work, but think of how much you've learned! I bet you can still salvage a lot of your configuration files and settings from the hard drive. Now that you mention it, a while back, Remastersys ate a Fluxbox build I was working on in a VM. I think Remastersys is probably the culprit.

You should take advantage of this setback and test out some Openbox Live CDs: SliTaz, Crunchbang, Boxbuntu, etc. to get some ideas. :)

---

### Post by jludeman on 2008-09-26
Thanks for the encouragement. Also the livecd information. Never heard of any of them but I'll check them out.

As to the culprit I see three possible bad boys.

1. Installing the new kernel during upgrade alters grub in a bad way.
(for me - I'm triple booting one version of gutsy, another version of gutsy and windows.)

2. Installing the iso in Virtualbox trespasses into the real world and disrupts grub.

3. Getting way too close to actual Hardy with all the other upgrades.

Definitely something real bad happened to Grub.

Lucky Things:

1. I had already downloaded and burned SuperGrub. No it did not let me boot to any linux partition. But it helped me figure out why.

2. I had already learned nano so I could fix some things.

3. I had just spent some time backing up my original system and was able to recover a new install pretty quickly.

4. I had written a bunch of notes in text files with the tips and traps I had learned so far.

Bad Things:

1. A lot of things get broken with a complete update of Gutsy or a new install of Hardy. Not just for me - check the web.

2. Some hassles and bugs that I already learned to work around as far back as Edgy are still there.

Good Things:

I tested the alternate install method found [here.(http://help.ubuntu.com/community/InstallCDCustomization)]("http://help.ubuntu.com/community/InstallCDCustomization")

It worked very well for me. The iso was a fair bit larger than remastersys.
Who cares? It was about 50MB larger. It worked.

I am really glad to hear about openbox-ubuntu live cd options.

---

### Post by bionnaki on 2008-09-28
or just dl/burn: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

installation via up-to-date ftp sources.

and then install xorg, openbox, etc.

---

### Post by jludeman on 2008-09-29
Some changes in thinking based on my experiences.

1.

I would now alter my manual install method. 

Here's how:

Use the xubuntu alternate install cd as usual. Do a full install of Xubuntu. Remove the applications and items you do not need or want.

That method is far less tedious than finding all the things you do need after a command line install.

That changed my install list some. I kept xfce4-terminal and never installed gnome terminal.

2.

Remastersys does work with a custom install. I apologize for saying it did not. It just takes a little more tweaking so an unexperienced user will have a decent experience with the live cd.

I'd like to thank fragadelic for his help on the forum at [http://www.linuxmint.com/forum/viewforum.php?f=83]("http://www.linuxmint.com/forum/viewforum.php?f=83")

3. 

Both boxbuntu and crunchbang are nice remasters of ubuntu for openbox fans. Neither use the best features of gnome as much as I prefer. I am continuing work on my version. It might be called gobxubuntu. (Gnome-Openbox-Xubuntu)

4.

My version is much heavier on programming tools. It also has the latest version of wine, swiftweasel, remastersys, and xmms. (xmms is no longer in the hardy repositories.)

5.

As soon as it is done I'll try to line up a site to host the usual documentation, description and screenshots. I'll also try to find somewhere to upload it so people could do torrent and iso downloads. 

I really like this system and I'd like to give others the chance to try it on a live cd.

---

### Post by jludeman on 2008-10-04
Using remastersys I've created a working iso and cd of the system.

The iso is about 600 MB. Tested and everything working.

Some features:

Wine 1.15
Virtualbox
Remastersys
Xmms
python-wxgtk2.8
nearly complete set of programming tools
almost the same application feature set as boxbuntu

There is really no need for another openbox - ubuntu based iso.

Except:

1.

I can't seem to convince people that gnome tools and openbox work really well together.

2.

The iso I've put together is smaller than kubuntu and ubuntu.

3.

The installed system is 1.9 GB. Smaller than kubuntu and ubuntu. More useful and less bloated.

I may release it on the web just so people can try a live cd of it. 

The live cd is faster than either ubuntu or kubuntu on my system. A little faster than xubuntu.

So many tools in such a small package.

I've used essentially the same system on two computers and a wireless network for over a year. Very stable, very usable.

If you want a Vista desktop you can get there. If you want the desktop out of your face it's built in.

Let me know.

I installed pretty much the same system on my now deceased pentium-2 333 mhz 128 mb ram system and it functioned adequately although in a slow but dignified way.:guitar:

---

### Post by urukrama on 2008-10-05
> **jludeman said:**
> There is really no need for another openbox - ubuntu based iso.

Everyone has different needs or wants. Many of the things you added to your iso I won't need, for example (VirtualBox, for starters). If I would want an Openbox Ubuntu install CD, I'd want it to be as bare as possible, so I can choose the applications I want and have the system running exactly what I'd like. The newest computer I use is about 7 years old, so it is important for me to keep things very light (no gnome-tools, for example). My iso would therefore be *a lot* smaller than the Ubuntu or Kubuntu isos.

But good luck with this. :-) I'm sure some users want an LiveCD like you've created. That's why it is nice to have choice.

---

### Post by jludeman on 2008-10-09
I agree that we don't need another niche in another niche within a fork of debian.

That said I've now arrived at a Hardy install which is a fair bit improved over Gutsy. Which in my imo is better than debian.

I only use vbox for testing iso. It does not work well as an alternate operating system on my aging computer.

My biggest problem that I wish somebody else would solve is that I'm stuck on a phone line for internet access. No Ubuntu version offers me openbox on the cd.

So days and days of downloading later I've got openbox working.

Since linux will work off a floppy why is the command line install of ubuntu about 300mb?

After Xorg why is it about 900mb?

These are not acceptable numbers for speed or hard drive usage.

Chunk some junk and get a live cd with openbox, a text editor, terminal emulator, a decent web browser, email, and basic system utilities in under 500mb installed?

Maybe a panel or two for user ease?

My hunk of junk computer runs gnome stuff just fine and other folks computers don't. I like the ease of use and integration of gnome.

Others might not.

If we really are talking small and light let's work out some common ground.

If I cut out gnome which is a decision I can easily live with, there is still too much junk on the sytem for an even worse system than mine.

Lighten up the whole thing.

A much better project than mine was. 

Beyond my skills at the moment.

One of the beautiful things about using linux day to day is that there are fifteen ways of doing anything.

That said linux is also about choice. I want nothing but python and c on my system. Anything that requires the myriad of scripting and programming languages can take a hike.

I don't need or want a manual on a useless obsolete scripting language or editor clogging my system up.

---

### Post by snowpine on 2008-10-10
Any Ubuntu installation is going to have a certain minimum "footprint" for the basic Ubuntu system. I do not think you are going to get your functional Ubuntu system with GUI and applications for under 500mb installed. Even Xubuntu, Fluxbuntu, Crunchbang, etc. require around 1.5-2gb of hard disk space for an install. You need to think outside the Ubuntu "box" if you really want a super-ultra-light system.

I keep repeating myself, but have you tried SliTaz yet? It will give you Openbox, panels, firefox, leafpad, etc. and it's only a 29mb download.

---

### Post by jludeman on 2008-10-12
I kinda skipped over slitaz after your suggestions. I'll check it again.

After spending some time on Windows 2000 pro today, I'll take Xubuntu, Ubuntu, but not Kubuntu over any of that waste.

I had to go to the dark side to earn groceries and gas. Not very productive with all the firewalls and spyware/malware/virus checkers. Not to mention the stupid update thing.

A modern gui text editor is what it is. No extra features needed.

I like notetab light in windows and gedit in linux. 

I can use nano no problem. Or whatever.

I got stuff to do so don't update me all the time.

All programming even in windows can be done from a text editor.

In linux I often have a bunch of terminals open. Command line is super functional. It's a line editor people!

Note: 

This is off topic. Every time I move up a notch with ubuntu I'm very unhappy if I do it on schedule.

I finally got hardy working (note the date) and it's the best ever.

Been the same with every release. Get it when it's time for the next one. No problem. Get it now - problem!

Anyway thanks for your help.

I'm thinking this thread might be dead.

---

