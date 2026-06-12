---
title: "My Trusty Flashback w/Metacity tweaks and challenges"
date: 2014-04-27
forum: Desktop Environments
---

### Post by kansasnoob on 2014-04-27
I'm far from having this all worked out yet, thus the need for the word ***challenges*** in the title, but I began working on this during the [Trusty dev cycle]("http://ubuntuforums.org/showthread.php?t=2184682") so I suppose I should start with what I know, but **please be sure to browse this entirely before jumping in head first - [COLOR="#FF0000"]particularly the Challenges and Known Issues and please help if you can[/COLOR]**.

There are changes to be aware of since I wrote [my Precise Classic notes]("http://ubuntuforums.org/showthread.php?t=1966370"):

First, there has been [continual session renaming]("http://ubuntuforums.org/showthread.php?t=2185161") since Precise to accommodate the new GNOME Classic session which is actually a GNOME Shell session with some cherry-picked extensions running on top of the Mutter window manager. No PPA is needed to test the new GNOME Classic session in Ubuntu GNOME Trusty but WebUpD8 still has the [best description I've found]("http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html").

Second, [metacity settings have now been totally deprecated from gconf]("http://ubuntuforums.org/attachment.php?attachmentid=247909&d=1384744892") in favor of dconf/gsettings so you'll notice quite a number of changes  in the commands required to apply theming tweaks such as moving the window management buttons.

Third, and perhaps most importantly, while the "flashback" session is no longer directly supported by the GNOME developers Flashback w/Metacity will continue to be supported by Edubuntu dev and [these dedicated people]("https://wiki.gnome.org/Projects/GnomeFlashback").

**My personal focus is on the Flashback w/Metacity session** which is [supported by Edubuntu]("http://edubuntu.org/sites/default/files/docimages/install-precise/030-edubuntu-options-oneiric.png") and both Ubuntu and Edubuntu Trusty are supported for a full 5 years. I should however say that the Flashback w/Metacity session can also be installed in Ubuntu GNOME Trusty but it's only supported for 3 years.

So what's needed to get started? Well that's still the same as Precise. 

**Step #1**: Simply install 'gnome-panel':

```
sudo apt-get install gnome-panel
```

Yep, that's it. In spite of session renaming that still installs all of the dependencies required and it has [quite a small footprint]("http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986315#post12986315") in Ubuntu. The footprint in Ubuntu GNOME is a bit heavier because 'flashback' now uses 'unity-settings-daemon' and 'unity-control-center' instead of the GNOME versions of those same packages.

**Step #2**: Log out, [select the desired session]("http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682"), and log back in.

**Important Note**: DO NOT select GNOME Flashback (Compiz) in Ubuntu GNOME unless you've also installed the package 'compiz'!

**Step #3**: Enable the "[panel-run-dialog]("http://ubuntuforums.org/attachment.php?attachmentid=252566&d=1398598654")" which can be quite useful if you bork your panels and/or menus:

```
gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog "['<Alt>F2']"
```

**Step #4**: Consider what additional packages you may want.

'**indicator-applet**' and/or '**indicator-applet-session**' - as [an alternative]("http://ubuntuforums.org/showthread.php?t=1966370&page=2&p=11900657#post11900657") to 'indicator-applet-complete'

'**gnome-tweak-tool**' - because it's quite convenient for general theming tweaks such as [having the old-style icons appear on the desktop]("http://ubuntuforums.org/attachment.php?attachmentid=251605"), [setting the key sequence for killing X]("http://ubuntuforums.org/attachment.php?attachmentid=251606"), and [changing themes]("http://ubuntuforums.org/attachment.php?attachmentid=251607").

'**shiki-colors-metacity-theme**' - because it provides a rather [URL="http://ubuntuforums.org/attachment.php?attachmentid=249048&d=1388468652"]retro window management button theme
[/URL]
'**sensors-applet**' - [to display system temps]("http://ubuntuforums.org/attachment.php?attachmentid=249045&d=1388463838")

'**dconf-tools**' which provides the dconf Editor UI.

'**caffeine**' which serves as a replacement for 'gnome-inhibit-applet' so the screensaver can be disabled while viewing flash videos just by clicking on [the "coffee cup" in the panel]("http://ubuntuforums.org/attachment.php?attachmentid=252307&d=1398053559"). It must initially be launched from the Accessories menu, but it's not in the standard Ubuntu repos so if you want it you'll have to install [this PPA]("https://launchpad.net/~caffeine-developers/+archive/ppa") and update the repos:

**[COLOR="#FF0000"]UPDATE: The current build of Caffeine (2.7.1) does not work in flashback![/COLOR]** As a temporary workaround [I copied version 2.5 to my own PPA]("https://launchpad.net/~lbsolost/+archive/ppa").

```
sudo add-apt-repository ppa:lbsolost/ppa
```

```
sudo apt-get update
```

Of those I know I personally want 'indicator-applet' because I prefer using it along with the standard clock applet, 'gnome-tweak-tool', 'shiki-colors-metacity-theme', 'sensors-applet', 'dconf-tools', and 'caffeine'. I can do that in just one more command since I've already installed the caffeine PPA and updated the repos:

```
sudo apt-get install indicator-applet shiki-colors-metacity-theme sensors-applet dconf-tools caffeine gnome-tweak-tool
```

**Note**: If I'm starting with Ubuntu GNOME I additionally install 'light-themes' because ATM only the Ambiance theme seems to work well enough for my liking, and I believe you'll find that both 'gnome-tweak-tool' and 'dconf-tools' are already installed in Ubuntu GNOME.

I can then begin configuring the panels and desktop to my liking. I prefer just one panel at the bottom but there is no "one size fits all":

[ATTACH=CONFIG]252572[/ATTACH]

**Note**: In order to edit panel preferences and add or remove panel applets in Flashback w/Metacity you must press Alt while right-clicking the panel, and in Flashback w/Compiz you must press Alt+Super while right-clicking panel.

**There are still a few things that must be done using either the dconf Editor or via CLI** (the highlighted links show the actual position in the dconf Editor):

**Step #5**: [Move the window management buttons to the right]("http://ubuntuforums.org/attachment.php?attachmentid=252325&d=1398092959") if you wish:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

**Step #6**: [Disable the overlay scrollbars]("http://ubuntuforums.org/attachment.php?attachmentid=251984&d=1397309461") if you wish:

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

**Step #7**: [Disable the Unity webapps]("http://ubuntuforums.org/attachment.php?attachmentid=248456&d=1386605099") if you wish:

```
gsettings set com.canonical.unity.webapps integration-allowed false
```

**Step #8**: Restore the missing [menu]("http://ubuntuforums.org/attachment.php?attachmentid=252327&d=1398095646") and [button]("http://ubuntuforums.org/attachment.php?attachmentid=252328&d=1398095646") icons:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

That's about all I know so far.

**Challenges and Known Issues - [COLOR="#FF0000"]any help would be deeply appreciated[/COLOR]**

**#1**: This scares me the most - I've not found a truly reliable method of backing up and restoring a customized configuration, or even resetting all defaults to an out-of-box configuration. I'm sure I'll figure it out but I've borked things badly enough a few times that I've had to completely reinstall the OS, not a big deal for me but that would really make some people mad! I have figured out a few things:

**(a)** You can reset the panel configuration to it's defaults by running:

```
dconf reset -f /org/gnome/gnome-panel/
```

But that produces a false crash report so please don't file it. No log-out is needed but it takes at least one full minute for the panels to reset so please be patient.

**(b)** Optionally you can reset the panel configuration to it's defaults by running:

```
XDG_MENU_PREFIX="gnome-flashback-" gnome-panel --replace &
```

But that requires logging out or restarting via terminal or by the use of keyboard shortcut.

**(c)** You can reset most general theming and desktop tweaks to their defaults by running:

```
dconf reset -f /org/gnome/desktop/
```

**(d)** If you bork the Main Menu it can be launched using the command "alacarte" either in a terminal or [using the "panel-run-dialog"]("http://ubuntuforums.org/attachment.php?attachmentid=254695&d=1405273665") - no sudo is needed - then it can be [reset to the default configuration]("http://ubuntuforums.org/attachment.php?attachmentid=254696&d=1405273665").

(e) You can also [launch the dconf Editor using the "panel-run-dialog"]("http://ubuntuforums.org/attachment.php?attachmentid=254697&d=1405273665") if you know exactly what you're looking for. [Here's one example]("http://ubuntuforums.org/showthread.php?t=2217817") where I found it quite useful.

**#2**:  The LibreOffice menu icons load very slowly. I've just been removing all but the main LibreOffice menu item, but I suppose a bug report should be filed?

**#3**: Some (maybe most) keyboard shortcuts are not set to their respective defaults. This is where dconf Editor comes in handy. [Here's an example]("http://ubuntuforums.org/showthread.php?t=2217877&p=12993104#post12993104").

**#4**: Many of the themes I've tried have various problems. I'm sure the theme devs just need some time to catch up with the changes between GNOME 3.8 and 3.10.

---

### Post by malty on 2014-04-27
kn, the most stable tweak for me, so far, is a replication of my 12.10 environment.................

Global dark theme...on

Window theme...GnomishDark

Gtk theme.........GnomishDark

Icons................Azenis Icons (this gives the blue set)

Cursor...............Redglass

XScreensaver

App and filesystem menus are via icons

Problems so far, only two, when hovering the cursor over the far left top panel icons, flickering occurs, also Firefox can't integrate English (British) spellcheck set (Firefox bug?)

Otherwise, AOK, Amarok, XBMC, Nero linux et al all bedded in.

Keep up the good work, you are, as the yanks say, ma main man.

Oh, the Ubuntu software centre is still, as ever, hopeless.

Oh (2) any ideas on a "caps lock on" screen setting

---

### Post by kansasnoob on 2014-04-28
> **malty said:**
> kn, the most stable tweak for me, so far, is a replication of my 12.10 environment.................

Global dark theme...on

Window theme...GnomishDark

Gtk theme.........GnomishDark

Icons................Azenis Icons (this gives the blue set)

Cursor...............Redglass

XScreensaver

App and filesystem menus are via icons

Problems so far, only two, when hovering the cursor over the far left top panel icons, flickering occurs, also Firefox can't integrate English (British) spellcheck set (Firefox bug?)

Otherwise, AOK, Amarok, XBMC, Nero linux et al all bedded in.

Keep up the good work, you are, as the yanks say, ma main man.

Oh, the Ubuntu software centre is still, as ever, hopeless.

Oh (2) any ideas on a "caps lock on" screen setting

I have seen this:

> when hovering the cursor over the far left top panel icons, flickering occurs

But not always.

Otherwise I'm clueless right now :(

---

### Post by cedric5 on 2014-05-01
hello, 
so, now as I said,  with 14.04 running these are the issues I have left (also with a fresh user!)

- custom keybindings are not possible!!! as You pointed out in your first post - the gconf ones are ignored, BUT at my installation, the   custom ones in dconf,  in org.gnome.settings-daemon.plugins.media-keys which you can set in unity-system-settings keyboard  do not work either!
- login lasts 10+ seconds, also with new user, have not investigated this further until now, any hints to do so?
- the tooltips are not word-warped any more, making them hard to read if long text is written in there (a very special problem I must admit)

the issue with crashing indicator applets is gone with new user, but the cpufreq-applet crashes

> when hovering the cursor over the far left top panel icons, flickering occurs                      
that's definitely connected to the tooltips not warped, I have experienced this, too.

---

### Post by kansasnoob on 2014-05-01
> **cedric5 said:**
> hello, 
so, now as I said,  with 14.04 running these are the issues I have left (also with a fresh user!)

- custom keybindings are not possible!!! as You pointed out in your first post - the gconf ones are ignored, BUT at my installation, the   custom ones in dconf,  in org.gnome.settings-daemon.plugins.media-keys which you can set in unity-system-settings keyboard  do not work either!
- login lasts 10+ seconds, also with new user, have not investigated this further until now, any hints to do so?
- the tooltips are not word-warped any more, making them hard to read if long text is written in there (a very special problem I must admit)

the issue with crashing indicator applets is gone with new user, but the cpufreq-applet crashes


that's definitely connected to the tooltips not warped, I have experienced this, too.

Did you see these:

[http://ubuntuforums.org/showthread.php?t=2217877&p=12993104#post12993104](http://ubuntuforums.org/showthread.php?t=2217877&p=12993104#post12993104)

[http://ubuntuforums.org/showthread.php?t=2217817](http://ubuntuforums.org/showthread.php?t=2217817)

There's a lot I don't have figured out yet :(

---

### Post by jdallara on 2014-05-05
Hello,

  Just wanted to add my experience.  I just upgraded from Ubuntu 13.10 to 14.04.  I was running Gnome Flashback with 2 panels on the bottom of the screen.  After the upgrade, only the desktop was present with no panels.  I logged in using Gnome Flashback Compiz and got a top panel with nothing in it and a Unity side panel.  Removed gnome-panel, gnome-flashback and with the Gnome Flashback Compiz log in I got the top panel populated with icons.  Can't move, change, etc., the panel but it shows up.  Reinstalled gnome-panel and the blank panel came back.  This machine has been upgraded starting with 11.10 a couple of years back so I'm going to try a fresh install, probably have way too many ghosts hanging aroung in the closet.  I've been wanting to go from 32 to 64 bit anyhow, and this may just be the time.
  Question, I downloaded Ubuntu Gnome for a test drive.  It has a Unity side panel and a wierd pop out workspace manager on the right side.  Is that the DE or can it be changed to the 2 panel Gnome "Classic" that I prefer for its ease of use and speed?  Should I look at downloading Edubuntu or some other distro?

Thanks,

Jon

---

### Post by kansasnoob on 2014-05-06
> **jdallara said:**
> Hello,

  Just wanted to add my experience.  I just upgraded from Ubuntu 13.10 to 14.04.  I was running Gnome Flashback with 2 panels on the bottom of the screen.  After the upgrade, only the desktop was present with no panels.  I logged in using Gnome Flashback Compiz and got a top panel with nothing in it and a Unity side panel.  Removed gnome-panel, gnome-flashback and with the Gnome Flashback Compiz log in I got the top panel populated with icons.  Can't move, change, etc., the panel but it shows up.  Reinstalled gnome-panel and the blank panel came back.  This machine has been upgraded starting with 11.10 a couple of years back so I'm going to try a fresh install, probably have way too many ghosts hanging aroung in the closet.  I've been wanting to go from 32 to 64 bit anyhow, and this may just be the time.
  Question, I downloaded Ubuntu Gnome for a test drive.  It has a Unity side panel and a wierd pop out workspace manager on the right side.  Is that the DE or can it be changed to the 2 panel Gnome "Classic" that I prefer for its ease of use and speed?  Should I look at downloading Edubuntu or some other distro?

Thanks,

Jon

You should be able to reset the panels to the out-of-box default with either of these commands:

```
dconf reset -f /org/gnome/gnome-panel/
```

That produces a false crash report so please don't file it. No log-out is needed but it takes at least one full minute for the panels to reset so please be patient.

```
XDG_MENU_PREFIX="gnome-flashback-" gnome-panel --replace &
```

That one appears to require a "sudo reboot" :confused:

Having parts of Unity linger may be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1232299](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1232299)

The fix for that bug just hit the US repos a few hours ago.

Ubuntu GNOME offers a new Classic session at login but it's truly a gnome-shell session with some cherry picked extensions, it's not configurable like gnome-panel.

---

### Post by jdallara on 2014-05-06
Neither reset did any good.  I'm just going to do a fresh install.  As I  said I wanted to upgrade this machine to 64 bit anyhow.  I just hadn't  wanted to mess with the upgrade due to my disk configuration using raid 1  drives for / and the MBR.  Maybe the 14.04 installer supports raid  drives now?  Ubuntu-GNOME isn't going to do it, so I'll just use the  straight Ubuntu and try the gnome-panel approach.  Below is what I'm trying to achieve in 14.04.  The screenshot is my other system running 13.10 and I don't want to upgrade it until I know that gnome-panel will work :-)

Thanks, Jon

[ATTACH=CONFIG]252922[/ATTACH]

---

### Post by kansasnoob on 2014-05-06
> **jdallara said:**
> Neither reset did any good.  I'm just going to do a fresh install.  As I  said I wanted to upgrade this machine to 64 bit anyhow.  I just hadn't  wanted to mess with the upgrade due to my disk configuration using raid 1  drives for / and the MBR.  Maybe the 14.04 installer supports raid  drives now?  Ubuntu-GNOME isn't going to do it, so I'll just use the  straight Ubuntu and try the gnome-panel approach.  Below is what I'm trying to achieve in 14.04.  The screenshot is my other system running 13.10 and I don't want to upgrade it until I know that gnome-panel will work :-)

Thanks, Jon

[ATTACH=CONFIG]252922[/ATTACH]

What's the dock on the left?

---

### Post by jdallara on 2014-05-06
Not a dock, just the desktop.  Guess it wasn't the best screenshot to use.  Speaking of which, I was interested in Cairo after seeing some screenshots from CavsFan.  He's running it on 14.10 but their web site doesn't have anything past 13.10, with the last site update being in Oct. 2013.  Is Cairo supported or is it a grab the sources and try to see if it will compile?  Synaptic is showing a version 3.3.99-beta1.2 which isn't listed on the web site.  A little off topic I know, but a possible solution...

thanks, Jon

[ATTACH=CONFIG]252931[/ATTACH]

---

### Post by kansasnoob on 2014-05-06
AFAIK the Unity side panel should not appear in either of the flashback sessions.

Ubuntu GNOME uses GNOME Shell as the default DE but also offers a Classic session at login. That Classic session is in no way related to flashback or gnome-panel though.

If you're fully updated you might be able to gain a bit by renaming some of the hidden dots in home:

```
lance@lance-desktop:~$ ls -a
.              .dbus             .ICEauthority        .profile
..             deja-dup          .local               Public
.adobe         Desktop           .macromedia          Templates
.bash_history  .dmrc             .mozilla             .thunderbird
.bash_logout   Documents         .mozilla_BK          Videos
.bashrc        Downloads         .mozilla_OLD         .Xauthority
.cache         examples.desktop  Music                .xsession-errors
.compiz        .gconf            newegg_20140307.pdf  .xsession-errors.old
.config        .gstreamer-0.10   Pictures

```

Possibly .compiz, .config, .gconf, and .local - then rebooting :confused:

---

### Post by jdallara on 2014-05-06
Thanks for the pointers.  I think my system is just too messed up to bother with upgrading.  My only reason for trying to keep it as it was is because it is my only system with Windoz on it.  However, I now have Windoz running on VirtualBox on my other system so I think it is time to clean out this one.  I still won't upgrade my main system until these panel 'problems' are sorted out.  I definitely have Unity side panel running with Gnome-flashback Compiz.  My Gnome-flashback Metacity shows only the desktop with only a blank panel at the top of the screen.

Thanks again,

Jon

---

### Post by jdallara on 2014-05-06
This is a screen shot of my 14.04 system, Gnome-flashback Compiz.  That is Unity on the left side.  The top panel icons work but you can't do anything with the panel (add, remove icons, move panel, etc.)  The rest is the desktop.  It also takes several minutes on boot to bring everything up.

[ATTACH=CONFIG]252938[/ATTACH]

---

### Post by grumblebum2 on 2014-05-07
Compiz was recently updated.
> compiz (1:0.9.11+14.04.20140423-0ubuntu1) trusty; urgency=low

  [ Ryan Tandy ]
  * Fix gnome-flashback session starting Unity plugins. Change the
    profile back after processing settings upgrades. When changing
    profile, discard existing GSettings wrappers pointing to the old
    profile. (LP: #1232299)

---

### Post by kansasnoob on 2014-05-07
> **grumblebum2 said:**
> Compiz was recently updated.

I mentioned that in post #7.

---

### Post by ramakanta on 2014-05-18
> **jdallara said:**
> Not a dock, just the desktop.  Guess it wasn't the best screenshot to use.  Speaking of which, I was interested in Cairo after seeing some screenshots from CavsFan.  He's running it on 14.10 but their web site doesn't have anything past 13.10, with the last site update being in Oct. 2013.  Is Cairo supported or is it a grab the sources and try to see if it will compile?  Synaptic is showing a version 3.3.99-beta1.2 which isn't listed on the web site.  A little off topic I know, but a possible solution...

thanks, Jon

[ATTACH=CONFIG]252931[/ATTACH]

which code used for this Ubuntu environment ??? and in right side what code used for conkey ????

---

### Post by jdallara on 2014-05-24
Ubuntu 14.04 with Gnome shell, Vindsl Conkywx using Conkywx 2.0

---

### Post by ramakanta on 2014-05-28
> **jdallara said:**
> Ubuntu 14.04 with Gnome shell, Vindsl Conkywx using Conkywx 2.0

Actually I am not a expert in Linux  , please whit details ???

---

### Post by deadflowr on 2014-05-28
> **ramakanta said:**
> Actually I am not a expert in Linux  , please whit details ???

The session looks like gnome-classic, more than it looks like gnome-shell.

But the conky stuff can be found here
The [awesomest conky howto around]("http://ubuntuforums.org/showthread.php?t=1771033")

Unfortunately, the conkywx part is rather new, but paramvir posts extensively about it toward the end of the thread.
You can the get conkywx weather script [here]("http://foreverquest.blogspot.com/2013/04/conkywx-conky-weather-program-conkywx.html")
 Have fun.
(Most people do)

---

### Post by kansasnoob on 2014-06-15
I reported a bug regarding the Zukitwo theme [here]("https://bugs.launchpad.net/zukitwo/+bug/1330329") if someone else cares to verify ;)

---

### Post by kansasnoob on 2014-07-13
I noticed some broken links in my OP (probably due to a thread being closed) so I need to repost some screenshots.

First regarding the ability to edit the Main Menus via the menu itself:

[ATTACH=CONFIG]254694[/ATTACH]

Or via the "panel-run-dialog":

[ATTACH=CONFIG]254695[/ATTACH]

And how to restore the Main Menu defaults:

[ATTACH=CONFIG]254696[/ATTACH]

And how to open 'dconf-editor' using the "panel-run-dialog":

[ATTACH=CONFIG]254697[/ATTACH]

---

### Post by ramakanta on 2014-07-14
Your first screenshot remember my past memory as in ubuntu10.04 . how to  make like  this in Ubuntu 14.04 LTS as your first screenshot ??? thank you .

---

### Post by kansasnoob on 2014-07-14
> **ramakanta said:**
> Your first screenshot remember my past memory as in ubuntu10.04 . how to  make like  this in Ubuntu 14.04 LTS as your first screenshot ??? thank you .

Which "first screenshot"? The one in my OP or the one in that last post?

Are you already running a flashback session?

Edit: Just happened to think - if you click on a screenshot to expand it, then just click on it again and it will open in a new browser window. So just post the URL of that window and I'll know which screenshot you mean.

---

### Post by deadflowr on 2014-07-14
> **ramakanta said:**
> Your first screenshot remember my past memory as in ubuntu10.04 . how to  make like  this in Ubuntu 14.04 LTS as your first screenshot ??? thank you .

read post#1 in this thread.

I'm guessing you want to have your desktop look like the one in 10.04?

(Keyword is guess)

---

### Post by fontun on 2014-07-29
how could I open compositing_manager setting and other old metacity settings?
in fact I only need opacity effects

---

### Post by kansasnoob on 2014-07-29
> **fontun said:**
> how could I open compositing_manager setting and other old metacity settings?
in fact I only need opacity effects

It's in dconf-editor > org/gnome/metacity but there's almost nothing left:

[ATTACH=CONFIG]255134[/ATTACH]

---

### Post by ibjsb4 on 2014-07-29
I an not on gnome at the moment so I cannot verify, but I wonder if gconf-editor has any usable settings.

---

### Post by kansasnoob on 2014-07-29
> **ibjsb4 said:**
> I an not on gnome at the moment so I cannot verify, but I wonder if gconf-editor has any usable settings.

As my OP says:

> ...... metacity settings have now been totally deprecated from gconf in favor of dconf/gsettings .......

I tracked that [here]("http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12850034#post12850034") and [here]("http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12851127#post12851127").

---

### Post by ibjsb4 on 2014-07-29
Yep, figured as much.  Been several months since I messed with it as I have my system set up the way I like it.  Keep up the good work :)

---

### Post by fontun on 2014-07-29
> **kansasnoob said:**
> It's in dconf-editor > org/gnome/metacity but there's almost nothing left:

[ATTACH=CONFIG]255134[/ATTACH]
thank you very much ,it works

---

### Post by jdallara on 2014-08-01
Does anyone know where gnome-panel gets called?  I upgraded another one of my systems from 13.10 to 14.04, installed gnome-panel, logged out and back in, and got my desktop and nothing else.  The panels were missing.  Was able to <cntl><alt>T a term window and just for grins typed in 'gnome-panel' and everything showed up perfectly.  I've been searching all over the filesystem on my remaining 13.10 system but to no avail.  The gnome-panel invocation is in a start-up script or file some where, any ideas?

Thanks,

Jon.

---

### Post by kansasnoob on 2014-08-01
> **jdallara said:**
> Does anyone know where gnome-panel gets called?  I upgraded another one of my systems from 13.10 to 14.04, installed gnome-panel, logged out and back in, and got my desktop and nothing else.  The panels were missing.  Was able to <cntl><alt>T a term window and just for grins typed in 'gnome-panel' and everything showed up perfectly.  I've been searching all over the filesystem on my remaining 13.10 system but to no avail.  The gnome-panel invocation is in a start-up script or file some where, any ideas?

Thanks,

Jon.

I'm not sure but have you looked at the Challenges and Known Issues in my OP?

---

### Post by jdallara on 2014-08-02
Yes I have, and thank you for the concise instructions and the effort you have put into 'saving' this interface.  In my case, it looks like the login process is starting the window manager (lightdm) but gnome-panel isn't getting called.  I'm sure there are configuration and startup scripts, and either the gnome-panel command isn't in them or it is in the wrong place.  If I can find the files or scripts then I could compare my 13.10 system versus my 14.04 system and try to figure it out.  As a side note, I can only get the keyboard shortcuts to work with Compiz.  I can't get gnome-panel w/Metacity to allow me to bring up a term window or the <alt>f2 run panel.

Anyhow, thanks for the reply,
Jon.

---

### Post by kansasnoob on 2014-08-02
> **jdallara said:**
> Yes I have, and thank you for the concise instructions and the effort you have put into 'saving' this interface.  In my case, it looks like the login process is starting the window manager (lightdm) but gnome-panel isn't getting called.  I'm sure there are configuration and startup scripts, and either the gnome-panel command isn't in them or it is in the wrong place.  If I can find the files or scripts then I could compare my 13.10 system versus my 14.04 system and try to figure it out.  As a side note, I can only get the keyboard shortcuts to work with Compiz.  I can't get gnome-panel w/Metacity to allow me to bring up a term window or the <alt>f2 run panel.

Anyhow, thanks for the reply,
Jon.

I'm really stumped :redface:

I do know the release upgrade process to Trusty is buggy. I assume you were not offered the upgrade via update manager???

Please read:

[http://ubuntuforums.org/showthread.php?t=2236911&page=2&p=13088245#post13088245](http://ubuntuforums.org/showthread.php?t=2236911&page=2&p=13088245#post13088245)

I did complete the test I spoke of there and ran into more borkage:

[http://ubuntuforums.org/showthread.php?t=2236911&page=2&p=13088302#post13088302](http://ubuntuforums.org/showthread.php?t=2236911&page=2&p=13088302#post13088302)

---

### Post by kansasnoob on 2014-08-02
A quick review tells me that Saucy -> Trusty upgrades are still borked:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721)

They fixed Trusty -> Utopic [somewhat]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1350416"), but Saucy -> Trusty is only triaged :(

So I think fresh installs are the only game in town, and dual booters need to be very aware of this horrible installer bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by jdallara on 2014-08-02
Just a quick note.  I did use update-manager but I ran it manually from a term window.  After downloading 1.7G of files it threw so many error messages and messages about the system being left in a non-bootable state, I throught for certain that my system was toast.  But, it booted just fine into unity and everything seems to be running fine, except for some applications I have to run under wine.  Even conky worked.  I know part of the upgrade error messages are due to my running a full RAID system.  GRUB actually installed correctly on its own this time!  I'll check out the links this afternoon.

Thanks,

Jon.

---

### Post by jdallara on 2014-08-03
Decided to check out my installation log files and I found this in the apt.log file and I found the following:


```

Investigating (0) unity-control-center [ amd64 ] < none -> 14.04.3+14.04.20140604-0ubuntu1 > ( gnome )
Broken unity-control-center:amd64 Conflicts on gnome-control-center-unity [ amd64 ] < 1.3+13.10.20131004-0ubuntu1 > ( gnome )
  Considering gnome-control-center-unity:amd64 -1 as a solution to unity-control-center:amd64 38
  Added gnome-control-center-unity:amd64 to the remove list
  Fixing unity-control-center:amd64 via remove of gnome-control-center-unity:amd64
  MarkDelete gnome-control-center-unity [ amd64 ] < 1.3+13.10.20131004-0ubuntu1 > ( gnome ) FU=0
...
Investigating (0) unity-control-center-signon [ amd64 ] < none -> 0.1.7~+14.04.20140211.2-0ubuntu4 > ( gnome )
Broken unity-control-center-signon:amd64 Conflicts on gnome-control-center-signon [ amd64 ] < 0.1.7~+13.10.20130724.1-0ubuntu1 > ( gnome )
  Considering gnome-control-center-signon:amd64 6 as a solution to unity-control-center-signon:amd64 12
  Added gnome-control-center-signon:amd64 to the remove list
  Fixing unity-control-center-signon:amd64 via remove of gnome-control-center-signon:amd64
  MarkDelete gnome-control-center-signon [ amd64 ] < 0.1.7~+13.10.20130724.1-0ubuntu1 > ( gnome ) FU=0
...
Investigating (0) gnome-control-center-datetime [ amd64 ] < 13.10.0+13.10.20131023.2-0ubuntu1.1 > ( misc )
Broken gnome-control-center-datetime:amd64 Depends on indicator-datetime [ amd64 ] < 13.10.0+13.10.20131023.2-0ubuntu1.1 -> 13.10.0+14.04.20140415.3-0ubuntu1 > ( misc ) (= 13.10.0+13.10.20131023.2-0ubuntu1.1)
  Considering indicator-datetime:amd64 20 as a solution to gnome-control-center-datetime:amd64 -1
  Removing gnome-control-center-datetime:amd64 rather than change indicator-datetime:amd64
  MarkDelete gnome-control-center-datetime [ amd64 ] < 13.10.0+13.10.20131023.2-0ubuntu1.1 > ( misc ) FU=0
```

Looks like the update gutted only the core parts of gnome.  The other packages were left alone.  The following is the tail of my apt-term.log file:

```

jon@jon-desktop2:/var/log/dist-upgrade$ tail -150 apt-term.log 
File descriptor 69 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 70 (/dev/pts/16) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 71 (/dev/pts/16) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 73 (socket:[1514023]) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 132 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 190 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 3 (pipe:[2150349]) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 69 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 70 (/dev/pts/16) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 71 (/dev/pts/16) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 73 (socket:[1514023]) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 132 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 190 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26493: /usr/sbin/grub-probe
File descriptor 3 (pipe:[2150349]) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 69 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 70 (/dev/pts/16) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 71 (/dev/pts/16) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 73 (socket:[1514023]) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 132 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 190 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 3 (pipe:[2150349]) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 69 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 70 (/dev/pts/16) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 71 (/dev/pts/16) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 73 (socket:[1514023]) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 132 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 190 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26530: /usr/sbin/grub-probe
File descriptor 3 (pipe:[2150349]) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 69 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 70 (/dev/pts/16) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 71 (/dev/pts/16) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 73 (socket:[1514023]) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 132 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 190 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 3 (pipe:[2150349]) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 69 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 70 (/dev/pts/16) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 71 (/dev/pts/16) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 73 (socket:[1514023]) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 132 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
File descriptor 190 (/var/log/dist-upgrade/apt.log) leaked on vgs invocation. Parent PID 26567: /usr/sbin/grub-probe
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
File descriptor 3 (pipe:[2150349]) leaked on lvs invocation. Parent PID 26882: /bin/sh
File descriptor 69 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 26882: /bin/sh
File descriptor 70 (/dev/pts/16) leaked on lvs invocation. Parent PID 26882: /bin/sh
File descriptor 71 (/dev/pts/16) leaked on lvs invocation. Parent PID 26882: /bin/sh
File descriptor 73 (socket:[1514023]) leaked on lvs invocation. Parent PID 26882: /bin/sh
File descriptor 132 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 26882: /bin/sh
File descriptor 190 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 26882: /bin/sh
done
Setting up libdbusmenu-glib4:amd64 (12.10.3+14.04.20140612-0ubuntu1) ...
Setting up libdee-1.0-4:amd64 (1.2.7+14.04.20140324-0ubuntu1) ...
Setting up libunity-protocol-private0:amd64 (7.1.4+14.04.20140210-0ubuntu1) ...
Setting up libunity-scopes-json-def-desktop (7.1.4+14.04.20140210-0ubuntu1) ...
Setting up libunity9:amd64 (7.1.4+14.04.20140210-0ubuntu1) ...
Setting up libzeitgeist-1.0-1 (0.3.18-1ubuntu2) ...
Setting up session-migration (0.2.1) ...
Setting up gvfs-libs:amd64 (1.20.1-1ubuntu1) ...
dpkg: dependency problems prevent configuration of gvfs-daemons:
 gvfs-daemons depends on udisks2; however:
  Package udisks2 is not configured yet.

dpkg: error processing package gvfs-daemons (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs:amd64:
 gvfs:amd64 depends on gvfs-daemons (>= 1.20.1-1ubuntu1); however:
  Package gvfs-daemons is not configured yet.
 gvfs:amd64 depends on gvfs-daemons (<< 1.20.1-1ubuntu1.1~); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gvfs (>= 1.3.2); however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package nautilus (--configure):
 dependency problems - leaving unconfigured
Setting up evolution-data-server-common (3.10.4-0ubuntu1.1) ...
Setting up libgssdp-1.0-3 (0.14.7-1ubuntu1) ...
Setting up libgupnp-1.0-4 (0.20.10-1ubuntu1) ...
dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus (>= 1:2.91); however:
  Package nautilus is not configured yet.

dpkg: error processing package nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for ca-certificates (20130906ubuntu2) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Processing triggers for libgdk-pixbuf2.0-0:amd64 (2.30.7-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 plymouth-label
 dmsetup
 libdevmapper1.02.1:amd64
 libdevmapper-event1.02.1:amd64
 lvm2
 libsnmp-dev
 dbus
 dbus-x11
 gconf2
 libgnome2-common
 libgnome2-0:amd64
 libgnome2-bin
 libbonoboui2-0:amd64
 libgnomeui-0:amd64
 vim-gnome
 gconf-defaults-service
 libgconf2-dev
 gstreamer0.10-gconf:amd64
 mdadm
 brltty
 bluez
 systemd-services
 libpam-systemd:amd64
 pulseaudio
 libcanberra-pulse:amd64
 cups-daemon
 policykit-1
 python3-plainbox
 libparted0debian1:amd64
 parted
 udisks2
 liblvm2app2.2:amd64
 udisks
 python3-checkbox-support
 python3-checkbox-ng
 checkbox-ng
 checkbox-ng-service
 plainbox-provider-resource-generic
 plainbox-provider-checkbox
 checkbox-gui
 upower
 gnome-power-manager
 accountsservice
 language-selector-common
 aptdaemon
 language-selector-gnome
 lightdm
 gvfs-daemons
 gvfs:amd64
 nautilus
 nautilus-sendto
Processing was halted because there were too many errors.
Log ended: 2014-07-28  06:02:08
jon@jon-desktop2:/var/log/dist-upgrade$ 
```

From the error messages, there shouldn't be much of anything functional on the system, yet it is up and running fine. 
 		 			 				:confused:

Thanks,

Jon.

---

### Post by kansasnoob on 2014-08-03
I doubt such systems would update properly regardless. Looked to me like I was left with a mix of 13.10 and 14.04 packages so it would eventually end up posing serious security risks.

---

### Post by jdallara on 2014-08-04
Just a quick update.  I run software-updater last night to see what would happen.  It downloaded a few updated packages and then proceeded to install those packages along with others that it found laying around from the upgrade to 14.04.1.  It didn't fix my having to manually start gnome-panel.  I did finally get smart and put a term window link on my desktop so I'd always have access to it. The results after rebooting:

I can log in using gnome w/compiz.  Have to manually start gnome-panel.  I can only get 1 workspace to show in the workspace switcher.  org.gnome.desktop.wm.preferences num-workspaces is set to 6.  Keybindings work without gnome-panel running.  [Edit: org.compiz.integrated display-all-workspaces = true]

I can log in using gnome w/Metacity.  Have to manually start gnome-panel.  I have my 6 workspaces.  Keybindings only work after gnome-panel has been started.  (Can't <cntl><alt>t a term window to manually start gnome-panel.)

Jon.

---

### Post by u2nTu on 2014-08-18
Just did this upgrade from 12.04 to 14.04.1 and find kansasnoob advice remains the best (for years).

**Notes:**
[LIST]
[*]Verifying the button in Update Manager did not work. Boot was to an empty desktop with everything broken. Had to do a fresh install. 
[*]Did try Ubuntu GNOME, but the interface migration toward touch was too much. **Two products are needed: One touch, one conventional.** 
[*]Flashback w/ Metacity is indeed still the best for desktops and non-touch laptops (mine anyway). 
[*]Installed **Nemo** to get dual-pane file manager operation back. 
[*]Radiance theme is light, works fine, and nothing extra to install. My preferred theme. 
[*]Ctrl-alt-t to open terminal sometimes doesn't work. (It always did in 12.04.) 
[*]**.Xmodmap files no longer load automatically.** No workaround I've tried fixes this. 
[/LIST]
 Everything mostly runs the same as in 12.04, pretty happy about that. Thanks, kn, for continuing to point the way.

---

### Post by stoneguy on 2014-08-21
I finally completed a 12.04 Classic (with MATE 16 layered in) to 14.04 with MATE 18. The 1st part of the upgrade (after undoing some app-related PPAs) required working in Unity. When I finally got the MATE desktop, I couldn't see all of it. Basically there was a mismatch between the window and the viewport.

If your system has an Radeon graphics controller, this may be a helpful tip.

After some unsuccessful effortswith desktop tweaks, it occurred to me that the problem might be lower. Booting into Recovery mode and running X -configure showed that I was running the radeon driver. In 12.04, it had been the modeset driver. Then at boot the kernel lines were messing with the modeset parameter. During the upgrade, my video chip (6550D) was correctly detected when X is configured to use the radeon driver, but the modeset parameters were not not removed from the grub lines.

After removing modeset-related references in /boot/grubgrub.cfg and a couple of files in /etc/grub.d and rebooting, the desktop showed everything it should. Plus there's a whole  bunch more resolutions available on the Monitor tab than there were on 12.04.

---

### Post by Claus7 on 2014-08-30
Hello,

I would like to thank the OP and all the posts that were really helpful in order for the flashback session to become more functional.

the long story short: coming from maverick, trying to keep as much the configurations I had back then, after a sudden breaking of my hdd.

Problems: 
[LIST]
[*]unity and flashback/compiz are having blurry menus. I was able to see some solutions, yet they were applicable for nvidia graphics card and not ati. Luckily, flashback - metacity is crisp and clear, yet...
[*]...I can see that when I place my mouse cursor on top of application/places there is a blinking effect.
[*]The bottom panel bar becomes black, while set to transparent, on its own.
[*]Flash player does not work with firefox as it lags a lot. Chromium works without issues. This is not a specific metacity problem though.
[*]How do you unmount a hdd from your ubu box? The ability to right click and unmount it no longer exists on desktop. I go from the option disks, and then I power off the hdd, since unmount (from computer window - the one with an arrow pointing upwards) causes either the disk to be unmounted and not seen from computer window, or to be unmounted and seen. I do not know which is the safest way to do so, but the disk way, seems the safest.
[*]I cannot write click on a file and send it to my mobile phone via bluetooth. I have to open bleutooth, find the file and send it.
[*]I cannot use print screen while having from the top panel the applications option clicked. I suppose that I was able to do it on maverick.
[*]I think that it takes more time for trusty to boot.
[/LIST]

I have to admit that I liked the flashback/compiz version better, if it had not been for the blurry menus. I do not know why the OP chose metacity, since I cannot have the -simple- eye candy options I was using. Not so many, yet I liked how windows were displayed pressing the super+tab keys. Can this happen with metacity as well?

Sound recorder was dead, yet I was able to install audio recorder and everything is ok. I have no problems with sound.

I do not remember any other issue, yet a couple of weeks of usage cannot be compared with over 4 years experience.

And just to add that: going back to unity, apart from desktop and menus being blurry, the fonts are really small. Fonts were small in metacity as well, yet with gnome-tweak, I was able to adjust them the way I wanted. The problem is that going to unity and then back to metacity, the fonts of metacity become small as well.

I hope that I did not post something that is completely out of spirit with the OP.

Regards!

---

### Post by kansasnoob on 2014-08-30
> I hope that I did not post something that is completely out of spirit with the OP

Not at all :)

I can help with a few of those issues but it'll be several hours as I have some non-puter issues to deal with first.

---

### Post by Claus7 on 2014-08-30
Hello,

> **kansasnoob said:**
> Not at all :)

I can help with a few of those issues but it'll be several hours as I have some non-puter issues to deal with first.

I hope the best to the things you are trying to do and thank you for your comments. I will try things out in between, yet, taking into account that other things are running at the same time it will be difficult to tweak my system a lot.

edit: 
firefox still cannot perform with flashplayer, on the contrary opera works very well with the same flash 
player file
I was not able to create a: send to... option for my mobile to nautilus no matter what (using scripts)

Regards!

---

### Post by kansasnoob on 2014-08-31
Hi Claus7,

First of all a list of things that you should open new threads regarding because they're all separate issues:

(1) Compiz and your graphics chip - be sure to include the output of the following command so users will know exactly what graphics chip they're dealing with:

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

(2) Flash not working with Firefox

(3) Creating a: send to... option for your mobile to nautilus

(4) Fonts being too small with some DE's

Next I'll try to help with those things that I can one at a time.

---

### Post by kansasnoob on 2014-08-31
> I can see that when I place my mouse cursor on top of application/places there is a blinking effect.

I've seen that too but it seems to go away after the second or third reboot if I continue to use the flashback w/metacity session. I almost suspect a theme related issue because it's especially prominent using Adwaita.

> The bottom panel bar becomes black, while set to transparent, on its own.

Yes, again I suspect a theming issue. In my OP I said, "If I'm starting with Ubuntu GNOME I additionally install 'light-themes' because ATM only the Ambiance theme seems to work well enough for my liking". I've since found that the themes in the 'shimmer-themes' package work fairly well with metacity - no idea about compiz.

There are a lot of things that don't quite work as well as I'd like in Trusty :(

---

### Post by kansasnoob on 2014-08-31
Sorry for the long delay.

> I cannot use print screen while having from the top panel the applications option clicked.

True. The only way I've found around that is to launch the screenshot GUI from the menu, set the delay time long enough to give me time to display what I wish on the screen, and then just wait for it to snap the shot.

> I think that it takes more time for trusty to boot.

Yes, it's overall much buggier than Precise was.

> How do you unmount a hdd from your ubu box?

I apply these settings in GNOME Tweak Tool:

[ATTACH=CONFIG]256025[/ATTACH]

Then if I right-click the drive icon on the desktop I can eject:

[ATTACH=CONFIG]256026[/ATTACH]

Did I miss anything?

---

### Post by Claus7 on 2014-08-31
Hello *kansasnoob*!

Thank you for the answers and your directions. I decided to create a new [thread]("http://ubuntuforums.org/showthread.php?t=2242270") in order to post my problems and possible solutions, since:

i) there are a lot
ii) they will create a mess with your effort and solutions
iii) they will focus on compiz session instead of metacity

I was able to solve many of the issues that I had, yet still some need more experimenting. I will keep an eye to your thread. Maybe some of my proposals will be helpful for you too.

Just some quick answers to the issues above:
1) compiz was the issue with the blurry effects. Disabling opengl seems that has solved the issue
2) flash still is not at its best with firefox
3) no send to... mobile option yet
4) fonts were small in unity, which means that I had to change them via this desktop environment, which I won't do at the time being, since I do not want to affect my existing configuration

5) The blinking in question is gone from compiz. I do agree that lighter themes had less blinking in metacity.

6) About the bottom panel, I will change the transparency and see what I will get. The same effect is both on compiz and metacity.

EDIT: you did not miss anything! Thank you again for the previous post. It seems that we were writing simultaneously, which was resulted in my double post. Sorry about that. I'm keeping these answers as well. The delay thing I had not figured it out! Nice!
Also thank you for verifying that trusty takes a little bit more time to boot.

Happy flashback ubuntu-ing,
Regards!

---

### Post by claracc on 2015-07-31
Since I upgraded my ubuntu 12.04 to 14.04.2 I month ago, this excellent thread has been one of my top guides to put my gnome flashback desktop to work.


However, I have some problems with the desktop for which I haven't found a solution yet. One of them is the slow response (more than 2 minutes) from click on close button in certain windows till the action is made, as I address in my unanswered thread here: [http://ubuntuforums.org/showthread.php?t=2287526](http://ubuntuforums.org/showthread.php?t=2287526)


Any help or comment will be very welcome.

Regards

---

### Post by kansasnoob on 2015-07-31
> **claracc said:**
> Since I upgraded my ubuntu 12.04 to 14.04.2 I month ago, this excellent thread has been one of my top guides to put my gnome flashback desktop to work.


However, I have some problems with the desktop for which I haven't found a solution yet. One of them is the slow response (more than 2 minutes) from click on close button in certain windows till the action is made, as I address in my unanswered thread here: [http://ubuntuforums.org/showthread.php?t=2287526](http://ubuntuforums.org/showthread.php?t=2287526)


Any help or comment will be very welcome.

Regards

Are you running a flashback/metacity session or flashback/compiz? You can see by running:

```
echo $DESKTOP_SESSION
```

A metacity session will just show "gnome-fallback" whereas a compiz session will show "gnome-fallback-compiz". Compiz is known to slow things down drastically so I never use it.

If you're running a metacity session and it's still slow see if you can either run a flashback/metacity session as guest or create a new user and try a flashback/metacity session logged in as that new user to see if things are still slow. If things seem faster (better) in the new user acct something is probably gorfed in your personal settings in /home.

BTW you can just delete that new user once you're done testing.

---

### Post by claracc on 2015-08-01
Thank you Kansasnoob for your answer.

My desktop is a metacity one, no compiz.

I have done as you pointed and certainly in the account created for new user there is not any delay on close button in the details window or in the software center window. So it is clear there is something in the personal settings in my account.


What could I do to fix the problem?

Thank you very much and regards

---

### Post by kansasnoob on 2015-08-01
While booted into your normal session (not the new user session) post the output of:

```
ls -a
```

I'll try and explain how to whittle away at that. It's really not terribly complicated but it can be slightly time consuming.

BTW I have a busy weekend planned so please be patient :)

---

### Post by claracc on 2015-08-01
Thankyou very much Kansasnoob for you help.

I am not in a hurry so take your time, I understand you are busy.

Here, there is the output ( it is a big one) of the command ls -a:

```
clara@clara1:~$ ls -a
.                                      .inkscape
..                                     .java
.adobe                                 Juegos
aeat                                   .kde
AEAT                                   .kderc
.alsaplayer                            .kompozer.net
antigüedad CSIC                        Lego
.apport-ignore.xml                     Libros 
.aptitude                              .liferea_1.8
.asoundrc                              .lightscribe
.asoundrc.asoundconf                   .lltag
.assistant                             .local
audios_convertidos                     Lomejoresparati
.avogadro                              LooM CD
backup usb 80610-030611                lure of temptress
banco                                  .macromedia
.bash_history                          .mailcap
.bash_logout                           manifest.xml
.bashrc                                .marble
Biblioteca de calibre                  master CAP tecnologia 2014
bin                                    .mission-control
.bogofilter                            movie
.byobu                                 .mozilla
.cache                                 .mplayer
.camel_certs                           MSWlogo
.cddb                                  MSWLogo.desktop
.compiz                                MSWLogo.lnk
.compiz-1                              Música
.config                                .nbprofiler
.crash_report_checksum                 .netbeans
.crash_report_frames                   .netx
.crash_report_preview                  .netxrc
.crash_reportrc                        neumatica
Crocodile Technology 610 (ES).desktop  nuevo curriculo tecnologia
Crocodile Technology 610 (ES).lnk      pau electrotecnia
cumpleaños mar                         .pki
curso 2014-2015                        Plantillas
curso gimp                             problemas arranque ubuntu
.dbus                                  .profile
.debtags                               Público
.dia                                   .pulse
.dmrc                                  .pulse-cookie
Documentos                             .purple
.dvdcss                                .python-eggs
dwhelper                               .qt
.easytag                               .recently-used
educacion leyes concursos              .recently-used.xbel.ZMPN1U
Enlace hacia FolderSort.exe            .recently-used.xbel.ZP6I1U
Escritorio                             recibo CCOO_2014
.esd_auth                              .registry
Esquelas                               renta 2012
Evernote.desktop                       renta 2013
Evernote.lnk                           .ri-li.pref
.everpad                               .rpmdb
.evolution                             .scim
examples.desktop                       .scummvm
facturas ono                           .scummvmrc
facturas telefonica mama               Sony xperia m
facturas vodafone                      .speech-dispatcher
Festo Fluidsim.desktop                 .spumux
Festo Fluidsim.lnk                     .ssh
Firefox_wallpaper.png                  .stellarium
fontconfig                             .sudo_as_admin_successful
.fontconfig                            .synaptic
.fonts.conf                            tecnologiaelectricidad
.fuentes                               tema cursor grande
full throttle                          temporal
.gconf                                 .themes
.gconfd                                .thumbnails
.gegl-0.0                              .thunderbird
Geogebra                               Ubuntu One
.gimp-2.6                              .update-manager-core
.gimp-2.8                              .update-notifier
.gksu.lock                             .ure
.gnome                                 Vídeos
.gnome2                                .viminfo
.gnome2_private                        .visualvm
.gnupg                                 vlc-log.txt
.gpilotd                               .wapi
.gpilotd.pid                           .wicd
.gstreamer-0.10                        .wine
.gtk-bookmarks                         .Xauthority
.gvfs                                  .xine
hacienda 2011                          .xinput.d
.helix                                 .xinputrc
houston maria luisa                    .xprofile
hover.theme                            .xscreensaver
.ICEauthority                          .xscreensaver-getimage.cache
.icedteaplugin                         .xsession-errors
.icons                                 .xsession-errors.old
Imágenes                               zack mckraken
imágenes Gimp

```

Regards

---

### Post by kansasnoob on 2015-08-02
Sorry to take so long getting back to this. Back in my Precise notes I posted some general info regarding this:

[http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600](http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600)

In Trusty and beyond I've had the best luck using the CLI method by first going to System Settings > User Accounts and turning auto-login off. Then reboot to be sure all is well - that is you're able to login from the login screen. Then if all is well reboot again only when you get to the login screen instead of logging into the desktop open a TTY by pressing Ctrl + Alt +F1. Then you can login to a TTY session, run ls -a, and then use mv + hidden-dot name to rename the desired hidden dot. Is that clear as mud?

If you're not sure please ask first rather than blowing something up. Oh, and this would be an excellent time to create a full backup of your home folder before beginning. Of course there is no bad time to create a backup.

So looking at your output of ls -a the hidden dots I'd most suspect of possible borkage are highlighted in red here:

```
clara@clara1:~$ ls -a
.                                      .inkscape
..                                     .java
.adobe                                 Juegos
aeat                                   .kde
AEAT                                   .kderc
.alsaplayer                            .kompozer.net
antigüedad CSIC                        Lego
.apport-ignore.xml                     Libros 
.aptitude                              .liferea_1.8
.asoundrc                              .lightscribe
.asoundrc.asoundconf                   .lltag
.assistant                             **[COLOR="#FF0000"].local[/COLOR]**
audios_convertidos                     Lomejoresparati
.avogadro                              LooM CD
backup usb 80610-030611                lure of temptress
banco                                  .macromedia
.bash_history                          .mailcap
.bash_logout                           manifest.xml
.bashrc                                .marble
Biblioteca de calibre                  master CAP tecnologia 2014
bin                                    .mission-control
.bogofilter                            movie
.byobu                                 .mozilla
**[COLOR="#FF0000"].cache[/COLOR]**                                 .mplayer
.camel_certs                           MSWlogo
.cddb                                  MSWLogo.desktop
**[COLOR="#FF0000"].compiz[/COLOR]**                                MSWLogo.lnk
**[COLOR="#FF0000"].compiz-1[/COLOR]**                              Música
**[COLOR="#FF0000"].config[/COLOR]**                                .nbprofiler
.crash_report_checksum                 .netbeans
.crash_report_frames                   .netx
.crash_report_preview                  .netxrc
.crash_reportrc                        neumatica
Crocodile Technology 610 (ES).desktop  nuevo curriculo tecnologia
Crocodile Technology 610 (ES).lnk      pau electrotecnia
cumpleaños mar                         .pki
curso 2014-2015                        Plantillas
curso gimp                             problemas arranque ubuntu
.dbus                                  **[COLOR="#FF0000"].profile[/COLOR]**
.debtags                               Público
.dia                                   .pulse
.dmrc                                  .pulse-cookie
Documentos                             .purple
.dvdcss                                .python-eggs
dwhelper                               .qt
.easytag                               .recently-used
educacion leyes concursos              .recently-used.xbel.ZMPN1U
Enlace hacia FolderSort.exe            .recently-used.xbel.ZP6I1U
Escritorio                             recibo CCOO_2014
.esd_auth                              .registry
Esquelas                               renta 2012
Evernote.desktop                       renta 2013
Evernote.lnk                           .ri-li.pref
.everpad                               .rpmdb
.evolution                             .scim
examples.desktop                       .scummvm
facturas ono                           .scummvmrc
facturas telefonica mama               Sony xperia m
facturas vodafone                      .speech-dispatcher
Festo Fluidsim.desktop                 .spumux
Festo Fluidsim.lnk                     .ssh
Firefox_wallpaper.png                  .stellarium
fontconfig                             .sudo_as_admin_successful
.fontconfig                            .synaptic
.fonts.conf                            tecnologiaelectricidad
.fuentes                               tema cursor grande
full throttle                          temporal
**[COLOR="#FF0000"].gconf[/COLOR]**                                 .themes
**[COLOR="#FF0000"].gconfd[/COLOR]**                                .thumbnails
.gegl-0.0                              .thunderbird
Geogebra                               Ubuntu One
.gimp-2.6                              .update-manager-core
.gimp-2.8                              .update-notifier
.gksu.lock                             .ure
**[COLOR="#FF0000"].gnome[/COLOR]**                                 Vídeos
**[COLOR="#FF0000"].gnome2[/COLOR]**                                .viminfo
**[COLOR="#FF0000"].gnome2_private[/COLOR]**                        .visualvm
.gnupg                                 vlc-log.txt
.gpilotd                               .wapi
.gpilotd.pid                           .wicd
.gstreamer-0.10                        .wine
.gtk-bookmarks                         .Xauthority
.gvfs                                  .xine
hacienda 2011                          .xinput.d
.helix                                 .xinputrc
houston maria luisa                    **[COLOR="#FF0000"].xprofile[/COLOR]**
hover.theme                            **[COLOR="#FF0000"].xscreensaver[/COLOR]**
.ICEauthority                          **[COLOR="#FF0000"].xscreensaver-getimage.cache[/COLOR]**
.icedteaplugin                         .xsession-errors
.icons                                 .xsession-errors.old
Imágenes                               zack mckraken
imágenes Gimp

 
```

---

### Post by claracc on 2015-08-03
Thank you kansasnoob for the full explanation to rename some of the config hidden files in my home folder.

I have follow all the instructions but unfortunately , the close button in details window remain irresponsive (see attached, I could take the shoot after clicking on close button since window remains for a long time). When I click on close, the delay to perform action is more than 1 minute. There is not any delay in minimizing or maximizing button.

However, Software center window has a better behaviour and on close button it responds inmediatly.

Is there any other hidden config file which could I rename to fix the delay in close for the details window ?

Thanks in advance

---

### Post by claracc on 2015-08-03
I have had an added problem, thanks God, I had a backup of my /home/clara folder.

I have lost my mails and accounts in evolution. I don't know why, perhaps the .profile file?.

I have restored the home/clara folder and I have recovered the mails and accounts in evolution.

---

### Post by kansasnoob on 2015-08-03
Post the output of ls -a again so I can see what you've done so far.

Is the Details window in System Settings the only one that seems slow to respond? Or are other windows in System Settings effected?

One thing that might be going on is that when you first open System Settings > Details it triggers update-manager to check for updates. You'll see this when you first open that window in the lower right hand corner while still displaying Overview. So it's possible that the window refuses to respond until update-manager completes what it's doing. The speed with which update-manager completes it's task would be based on how fast your internet connection is and how many sources it's parsing.

In that case we may want to check your software sources so we'd need to look at:

```
cat /etc/apt/sources.list
```

And:

```
ls /etc/apt/sources.list.d
```

Or sometimes it's easiest to spot a problem with update-manager just by looking at the full output of:

```
sudo apt-get update
```

---

### Post by kansasnoob on 2015-08-03
> **claracc said:**
> I have had an added problem, thanks God, I had a backup of my /home/clara folder.

I have lost my mails and accounts in evolution. I don't know why, perhaps the .profile file?.

I have restored the home/clara folder and I have recovered the mails and accounts in evolution.

I don't use evolution but if memory serves correctly the profile might be at .local/share/evolution.

Don't worry though. That's why we used mv to just rename the old hidden dots. Everything is there, it'll just need to be renamed again.

Just as an example you'll see here I have a few backed up (renamed) .mozilla folders:

```
lance@lance-desktop:~$ ls -a
.                   Desktop          .hardinfo          .profile
..                  .dmrc            .hplip             .psensor
.adobe              Documents        .ICEauthority      Public
.apport-ignore.xml  Downloads        .local             Templates
Backups             .gconf           .macromedia        .thunderbird
.bash_history       .gksu.lock       .mozilla           Videos
.bash_logout        .gnome           .mozilla_20150727  .Xauthority
.bashrc             .gnome2          .mozilla_backup    .xsession-errors
.cache              .gnome2_private  .mozilla_OLD       .xsession-errors.old
.compiz             .gphoto          Music
.config             .gstreamer-0.10  Pictures
.dbus               .gvfs            .pki

```

So if I wanted to replace the current .mozilla with .mozilla_20150727 I'd first close Firefox (or work from tty before logging in) and rename the current .mozilla:

```
mv .mozilla .mozilla_maybe_borked
```

Then rename the .mozilla_20150727:

```
mv .mozilla_20150727 .mozilla
```

Once you find where .evolution is located you can use the same basic method to restore only that part of the hidden dot.

I'll be testing some Ubuntu GNOME 14.04.3 images later today so I'll have a look where .evolution resides.

```

```

---

### Post by kansasnoob on 2015-08-03
If It's the same as Evolution in Vivid what you need will be in the renamed .local/share:

[ATTACH=CONFIG]263601[/ATTACH]

So close Evolution, then just open your new .local > share and rename that evolution folder. Then open your old renamed .local_whatever_you_named_it > share, right-click evolution, select copy, and then paste your old evolution profile into the new .local > share. Clear as mud?

---

### Post by claracc on 2015-08-03
I have restored my /home/clara/ folder because of the problem with mails and accounts in evolution.

Anycase, here it is the ouyput of ls -a (I think it will be the same as before):

```
clara@clara1:~$ ls -a
.                                      imágenes Gimp
..                                     .inkscape
.adobe                                 .java
aeat                                   Juegos
AEAT                                   .kde
.alsaplayer                            .kderc
antigüedad CSIC                        .kompozer.net
.apport-ignore.xml                     Lego
.aptitude                              Libros 
.asoundrc                              .liferea_1.8
.asoundrc.asoundconf                   .lightscribe
.assistant                             .lltag
audios_convertidos                     .local
.avogadro                              Lomejoresparati
backup usb 80610-030611                LooM CD
banco                                  lure of temptress
.bash_history                          .macromedia
.bash_logout                           .mailcap
.bashrc                                manifest.xml
Biblioteca de calibre                  .marble
bin                                    master CAP tecnologia 2014
.bogofilter                            .mission-control
.byobu                                 movie
.cache                                 .mozilla
.camel_certs                           .mplayer
.cddb                                  MSWlogo
.compiz                                MSWLogo.desktop
.compiz-1                              MSWLogo.lnk
.config                                Música
.crash_report_checksum                 .nbprofiler
.crash_report_frames                   .netbeans
.crash_report_preview                  .netx
.crash_reportrc                        .netxrc
Crocodile Technology 610 (ES).desktop  neumatica
Crocodile Technology 610 (ES).lnk      nuevo curriculo tecnologia
cumpleaños mar                         pau electrotecnia
curso 2014-2015                        .pki
curso gimp                             Plantillas
.dbus                                  problemas arranque ubuntu
.debtags                               .profile
Descargas                              Público
.dia                                   .pulse
.dmrc                                  .pulse-cookie
Documentos                             .purple
.dvdcss                                .python-eggs
dwhelper                               .qt
.easytag                               .recently-used
educacion leyes concursos              .recently-used.xbel.ZMPN1U
Enlace hacia FolderSort.exe            .recently-used.xbel.ZP6I1U
Escritorio                             recibo CCOO_2014
.esd_auth                              .registry
Esquelas                               renta 2012
Evernote.desktop                       renta 2013
Evernote.lnk                           .ri-li.pref
.everpad                               .rpmdb
.evolution                             .scim
examples.desktop                       .scummvm
facturas ono                           .scummvmrc
facturas telefonica mama               Sony xperia m
facturas vodafone                      .speech-dispatcher
Festo Fluidsim.desktop                 .spumux
Festo Fluidsim.lnk                     .ssh
Firefox_wallpaper.png                  .stellarium
fontconfig                             .sudo_as_admin_successful
.fontconfig                            .synaptic
.fonts.conf                            tecnologiaelectricidad
.fuentes                               tema cursor grande
full throttle                          temporal
.gconf                                 .themes
.gconfd                                .thumbnails
.gegl-0.0                              .thunderbird
Geogebra                               Ubuntu One
.gimp-2.6                              .update-manager-core
.gimp-2.8                              .update-notifier
.gksu.lock                             .ure
.gnome                                 Vídeos
.gnome2                                .viminfo
.gnome2_private                        .visualvm
.gnupg                                 vlc-log.txt
.gpilotd                               .wapi
.gpilotd.pid                           .wicd
.gstreamer-0.10                        .wine
.gtk-bookmarks                         .Xauthority
.gvfs                                  .xine
hacienda 2011                          .xinput.d
.helix                                 .xinputrc
houston maria luisa                    .xprofile
hover.theme                            .xscreensaver
.ICEauthority                          .xscreensaver-getimage.cache
.icedteaplugin                         .xsession-errors
.icons                                 .xsession-errors.old
Imágenes                               zack mckraken
clara@clara1:~$ 

```

I followed the orders outlined and as you pointed, I didn't enter in the desktop but in tty1 by ctrl+alt+f1 (autologin is turned off)

There, I changed the name of the following hidden files:
```
.local
.cache
.compiz
.compiz-1
.config
.profile
.gconf
.gconfd
.gnome
.gnome2
.gnome2_private
.xprofile
.xscreensaver
.xscreensaver-getimage.cache
```

To the same name for each one but adding _OLD, then reboot, and enter in desktop. As I have forementioned software center window which had a littke delay on close button responds inmediatly to the close, but as before, the details window on close button takes a delay more than 1 minute.

About the checking for updates in this window, I see that in the bottom right the button changes in a few seconds from "checking updates" to "install updates".

Anycase, I have run ```
sudo apt-get update
``` and it takes about 15 seconds ( my cable net is 50 MB)

About the problem with evolution I tried to recover the mails and accounts copying back the files:
/home/clara/.local_OLD/share/evolution to /home/clara/.local/share/evolution
/home/clara/.gconf_OLD/apps/evolution to /home/clara/.gconf/apps/evolution

But it was not enough, I couldn't recover mails and accounts but only restoring /home/clara folder

Thankyou for your patience and your help

---

### Post by kansasnoob on 2015-08-03
Well I don't really think I can be of any additional help to you.

---

### Post by claracc on 2015-08-03
Anycase, your help has been very welcome and I have learnt a lot about configuration files for desktop.

I will try to rename the forementioned hidden files one by one, and then reboot,  in order to have al least the software center window responsive unless the details window responds with delay to close. Also, in this way I think I could restore mails and accounts in evolution if they are missed.

Regards

---

### Post by 10kJS on 2015-11-14
With step 2, am not seeing any Gnome foot or gear by login name to choose Gnome.  Installed, no previous Linux, 14.04 LTS.

---

### Post by v3.xx on 2015-11-14
> **10kJS said:**
> With step 2, am not seeing any Gnome foot or gear by login name to choose Gnome.  Installed, no previous Linux, 14.04 LTS.

Upper right corner of your screen

---

### Post by kansasnoob on 2015-11-14
> **10kJS said:**
> With step 2, am not seeing any Gnome foot or gear by login name to choose Gnome.  Installed, no previous Linux, 14.04 LTS.

Did you look at the screenshots here:

[http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682)

You can see there is a difference between the three common display managers.

---

### Post by 10kJS on 2015-11-14
Yes, I saw that.  It doesn't have any of those.  It only has the gear in the top right that says Suspend and Shutdown... before login and this menu image when logged in.  I suspect you don't have 14.04 LTS and they deleted it.  Not sure why more users aren't demanding this who dislike the Unity left and top corner launcher.

---

### Post by kansasnoob on 2015-11-14
> **10kJS said:**
> Yes, I saw that.  It doesn't have any of those.  It only has the gear in the top right that says Suspend and Shutdown... before login and this menu image when logged in.  I suspect you don't have 14.04 LTS and they deleted it.  Not sure why more users aren't demanding this who dislike the Unity left and top corner launcher.

How did you install gnome-panel?

---

### Post by 10kJS on 2015-11-14
Installed with apt-get as in image.  See the errors to try to install gnome-session and gnome-session-flashback now.

---

### Post by kansasnoob on 2015-11-14
OK, not sure why things are borked but that broken packages error is keeping metacity from installing.

Open the terminal and try running the following commands:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get -f install
```

That may provide some other info that will be helpful in troubleshooting the problem.

Another common command used to resolve package conflicts is:

```
sudo dpkg --configure -a
```

You may need to repeat any of the above commands to resolve the conflict, or more info may be needed.

---

### Post by 10kJS on 2015-11-16
Did the update and dist-upgrade.  Don't want to risk running the last two unless someone verifies it worked for them without corrupting Unity.  Looks like the same errors, see image.  My understanding was that they weren't needed anyway.  
There's a gnome-session or gnome-session-flashback project site though it looks like there are no stable installs, only compiles.  What are my other options?  If I install Gnome, could I still go back to Unity by selecting it at login?

---

### Post by kansasnoob on 2015-11-16
Installing the metapackage gnome installs all of the following and will likely blow things up:

```
argyll binfmt-support browser-plugin-gnash caribou caribou-antler cli-common
  desktop-base evolution evolution-common evolution-indicator
  evolution-plugins finger five-or-more fonts-cantarell four-in-a-row
  freerdp-x11 gawk gdm gedit-plugins gimp gimp-data gir1.2-accountsservice-1.0
  gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-gucharmap-2.90 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-rest-0.7 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-tracker-0.16 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gir1.2-zeitgeist-2.0 gir1.2-zpj-0.0 gjs gnash gnash-common
  gnome gnome-chess gnome-color-manager gnome-core gnome-dictionary
  gnome-documents gnome-games gnome-icon-theme-extras gnome-icon-theme-full
  gnome-klotski gnome-nettool gnome-nibbles gnome-online-accounts
  gnome-online-miners gnome-packagekit gnome-packagekit-data
  gnome-packagekit-session gnome-robots gnome-shell gnome-shell-extensions
  gnome-sushi gnome-tetravex gnome-themes-standard gnome-themes-standard-data
  gnuchess gnuchess-book grilo-plugins-0.2 gtk2-engines hamster-applet
  hamster-indicator iagno imagemagick imagemagick-common inkscape libamd2.3.1
  libappindicator0.1-cil libappindicator1 libavahi-ui-gtk3-0 libavresample1
  libbabl-0.1-0 libblas3 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libboost-program-options1.54.0 libboost-thread1.54.0
  libcamd2.3.1 libcaribou-common libcaribou-gtk-module libcaribou-gtk3-module
  libcaribou0 libccolamd2.8.0 libcholmod2.1.2 libcolord-gtk1
  libdbus-glib2.0-cil libdbus2.0-cil libdiscid0 libencode-locale-perl
  liberror-perl libevolution libfile-listing-perl libfont-afm-perl
  libgconf2.0-cil libgdict-1.0-6 libgdict-common libgdiplus libgdm1
  libgegl-0.2-0 libgfortran3 libgif4 libgimp2.0 libgjs0e libglade2-0
  libglib2.0-cil libgmime2.6-cil libgnome2-0 libgnome2-bin libgnome2-common
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgrilo-0.2-1
  libgsl0ldbl libgtk-vnc-2.0-0 libgtk2.0-cil libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkspell0 libgupnp-av-1.0-2
  libgupnp-dlna-2.0-3 libgvnc-1.0-0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libicc2 libidl-common libidl0
  libimdi0 libindicator7 libio-html-perl libiptcdata0
  libjavascriptcoregtk-1.0-0 libjemalloc1 liblapack3 liblinear-tools
  liblinear1 liblqr-1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl
  libmagick++5 libmagickcore5 libmagickcore5-extra libmagickwand5
  libmail-spf-perl libmediaart-1.0-0 libmng2 libmono-addins-gui0.2-cil
  libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.0-cil
  libmono-corlib4.5-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmozjs-24-0
  libmusicbrainz5-0 libmutter0c libnet-http-perl libnetaddr-ip-perl
  libnetpbm10 liborbit-2-0 liborbit2 libpst4 librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1
  libsigsegv2 libsofia-sip-ua-glib3 libsofia-sip-ua0 libsys-hostname-long-perl
  libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0
  libumfpack5.6.2 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwmf-bin
  libwww-perl libwww-robotrules-perl libxcb-xf86dri0 libytnef0
  libzapojit-0.0-0 lightsoff mono-4.0-gac mono-gac mono-runtime
  mono-runtime-common mono-runtime-sgen mutter-common netpbm nmap perlmagick
  python-appindicator python-gnome2 python-numpy python-pyatspi python-pyorbit
  python-wnck quadrapassel re2c rygel rygel-playbin rygel-preferences
  sa-compile sound-juicer spamassassin spamc swell-foop tali telepathy-rakia
  tomboy tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils
  transfig unoconv vinagre whois xserver-xephyr
0 upgraded, 263 newly installed, 0 to remove and 4 not upgraded.
```

I ran that as a test on Trusty with flashback/metacity running!

You have held broken packages. That has implications beyond just not being able to install 'gnome-panel' and its proper dependencies in that it could be preventing you from getting security updates, etc. So I'd recommend starting a new thread in the [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") section asking for help with broken packages.

---

### Post by kansasnoob on 2015-11-16
BTW I can see that apt is wanting to install an older version of gnome-session-common, 3.9.90-0ubuntu12 rather than 3.9.90-0ubuntu12.1, which leads me to believe that an upgrade was interrupted at some point and sometimes this command helps to resolve that:

```
sudo dpkg --configure -a
```

But you are running a broken system and there are no guarantees that things might not get worse before they get better.

None of the commands I posted are truly dangerous but sometimes breakage does get worse before it gets better.

---

### Post by kansasnoob on 2015-11-16
I just thought to look at the changelog and gnome-session-common was last updated in March:

> gnome-session (3.9.90-0ubuntu12.1) trusty; urgency=medium

  [ Tim Lunn ]
  * debian/patches/103_kill_the_fail_whale.patch: fix logic gnome-session
    should die at this point. This will fix LP: #1236749,
    LP: #1385572 and possibly various other strange bugs

  [ Ryan Tandy ]
  * debian/patches/git_add_disable_acceleration_option.patch: Backport
    upstream patch to add a --disable-acceleration-check command-line option.
    (LP: #1251281)
  * debian/gnome-session-bin.user-session.upstart: Disable acceleration check
    when launching a GNOME Flashback (Metacity) session.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Sat, 21 Mar 2015 15:49:36 +0300

When was Ubuntu installed? That might give us a clue as to how long ago apt got borked, then maybe looking at the logs would explain why things went awry.

---

### Post by u2nTu on 2015-11-16
Lurkingly following this, I must write:

@[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=2002677")10kJS, one of the great things about the Debian/Ubuntu branch of Linux (maybe others are the same?) is that they're so very easy to install from scratch, and generally without loss of your personal settings and files (as long as your home directory is copied over).

When the time spent trying to fix an install exceeds the time it would have taken to just re-install, the latter option is better. Now, this is for best time efficiency. If you're enjoying messing with it and learning as you go, enjoy on.

For my part, I would add that my two biggest gripes with 14.04 are: Nemo not quite being back to where Nautilus was in 12.04, and the continuing bug that keyboard remaps are not reloaded on resume-from-suspend. There's some occasional quirky behavior not seen with 12.04, but that's not too bad. If by the end of the year things are the same, I'll likely move back to 12.04 (see [KN's much-linked thread]("http://ubuntuforums.org/showthread.php?t=1966370") on that).

---

### Post by 10kJS on 2015-11-16
Take a look at the attached log and you might want to try to reproduce it.   I followed the sound troubleshooting [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure),  it had me re-install all kinds of things.  That might have corrupted it.  The issue was that it somehow got muted and it doesn't look like they even say to check that.  I appreciate your help.

Start-Date: 2015-10-02  08:32:39
Commandline: apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop linux-image-3.19.0-28-generic libasound2
Install: hplip:amd64 (3.14.3-0ubuntu3.4), cups-core-drivers:amd64 (1.7.2-0ubuntu1.6, automatic), ubuntu-desktop:amd64 (1.325), cups-daemon:amd64 (1.7.2
-0ubuntu1.6, automatic), thunderbird:amd64 (38.2.0+build1-0ubuntu0.14.04.1), totem-plugins:amd64 (3.10.1-1ubuntu4, automatic), cups:amd64 (1.7.2-0ubuntu1.6, automatic), bluez-cups:amd64 (4.101-0ubuntu13), printer-driver-postscript-hp:amd64 (3.14.3-0ubuntu3.4, automatic), totem:amd64 (3.10.1-1ubuntu4),
 cups-browsed:amd64 (1.0.52-0ubuntu1.5, automatic), printer-driver-gutenprint:amd64 (5.2.10~pre2-0ubuntu2, automatic), python-pycurl:amd64 (7.19.3-0ubuntu3, automatic), thunderbird-gnome-support:amd64 (38.2.0+build1-0ubuntu0.14.04.1), printer-driver-splix:amd64 (2.0.0+svn315-2fakesync1), totem-mozilla
:amd64 (3.10.1-1ubuntu4), printer-driver-hpcups:amd64 (3.14.3-0ubuntu3.4, automatic), unity-webapps-common:amd64 (2.4.17+14.04.20140416-0ubuntu1), system-config-printer-gnome:amd64 (1.4.3+20140219-0ubuntu2), pavucontrol:amd64 (2.0-2)
End-Date: 2015-10-02  08:32:52

Start-Date: 2015-10-02  08:32:57
Commandline: apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop linux-image-3.19.0-28-generic libasound2
Reinstall: ubuntu-desktop:amd64 (1.325), alsa-base:amd64 (1.0.25+dfsg-0ubuntu4), alsa-utils:amd64 (1.0.27.2-1ubuntu2), linux-sound-base:amd64 (1.0.25+dfsg-0ubuntu4), libasound2:amd64 (1.0.27.2-3ubuntu7), linux-image-3.19.0-28-generic:amd64 (3.19.0-28.30~14.04.1)
End-Date: 2015-10-02  08:33:17

---

### Post by 10kJS on 2015-11-16
This what I ran myself, in that log, might have corrupted it:

sudo apt-get remove thunderbird-gnome-support totem totem-mozilla totem-plugins unity-webapps-common
sudo apt-get install  totem-mozilla totem-plugins unity-webapps-common

---

### Post by kansasnoob on 2015-11-16
What does your sound issue have to do with the flashback session?

You really need to open your own new thread.

---

### Post by 10kJS on 2015-11-17
The sound issue site I gave had me re-install lightdm and ubuntu-desktop step 1C, don't ask me why.  Am trying the flashback support list, and [http://ubuntuforums.org/showthread.php?t=2303257&p=13392366#post13392366](http://ubuntuforums.org/showthread.php?t=2303257&p=13392366#post13392366).  I saw this about gnome-panel:

    It has been replaced in GNOME 3.x by default with GNOME Shell, which only works with the Mutter window manager.

I see them both available to install on the Software Center.  Has anyone tried here tried them on 14.04 LTS?

---

### Post by 10kJS on 2015-11-19
The solution is on the thread link on #78 here.  It wasn't a corrupted, only incompletely configured, install.  
IMO this thread could also mislead people as it looks like only gnome-panel is all that's required when I found that gnome-session-flashback is also required to get the logon screen icon to select GNOME.

---

### Post by kansasnoob on 2015-11-19
> **10kJS said:**
> The solution is on the thread link on #78 here.  It wasn't a corrupted, only incompletely configured, install.  
IMO this thread could also mislead people as it looks like only gnome-panel is all that's required when I found that gnome-session-flashback is also required to get the logon screen icon to select GNOME.

Ummm, gnome-session-flashback is a dependency of gnome-panel. I link to this in my OP:

[http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986315#post12986315](http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986315#post12986315)

That includes a detailed list of what gets installed on both Ubuntu and Ubuntu GNOME when 'gnome-panel' is installed.

You had held broken packages because at some point you turned off Recommended Updates.

---

### Post by 10kJS on 2015-11-19
As I remember, gnome-panel installed fine with no errors.  I deleted gnome-session-flashback and re-installed gnome-panel and it does install gnome-session-flashback so this thread doesn't need to correct that.

---

### Post by boriseto on 2016-04-12
Okay, I went through a lot of forum posts and topics and I wouldn't post if I was not desperate, but since this topic is the one with most recent updates about the gnome-fallback metacity DE, I just have to post the following question:

Is there a way to change the behaviour of the new window focusing? Because at the moment, if somebody writes me a message, it creates the window in the background and because of that it makes me miss messages. Or in other case, if I press "Open the location of the file" the nautilus window would open in background and I would have to switch to it manually.

---

