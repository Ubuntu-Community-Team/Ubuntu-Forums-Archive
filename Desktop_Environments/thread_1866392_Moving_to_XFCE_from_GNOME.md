---
title: "Moving to XFCE from GNOME"
date: 2011-10-21
forum: Desktop Environments
---

### Post by RylosFan on 2011-10-21
I recently installed xubuntu-desktop as GNOME has officially failed me.  Though I was running Lucid with GNOME 2.3, I don't plan on going back to GNOME given the simply awful performance I experienced through recent updates in addition to Unity and GNOME 3 appearing to be bigger headaches with less functionality.  

I'd like to maintain as clean a system as possible, removing any unwanted/unnecessary software and services.  By all appearances, the XFCE metapackage seems to have at least disabled GNOME components while in an XFCE session (as I would expect) but it's a nagging feeling having unused desktop binaries just sitting there.

[LIST]
[*]**To remove all things GNOME, will I risk breaking some dependencies?**
[*]**Does anyone have any tips for a recent XFCE convert?**
[/LIST]

I know it's a noobish question and I do appreciate this community's efforts immensely.

---

### Post by 3Miro on 2011-10-21
Those guys have the commands to add/remove different desktop environments:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Make sure you pick the command for your distribution, the default commands are for 11.10, if you have 10.04 you have to select it at the top of the page.

---

### Post by LewisTM on 2011-10-21
You can definitely remove all gnome desktop/session packages, panels, applets (but keep the indicator plugins).

I suggest you keep Nautilus, it's still handy in some situations where Thunar falls short. Just [set it]("https://wiki.archlinux.org/index.php/GNOME_Tips#Stop_Nautilus_drawing_the_desktop") not to draw the desktop.

In 11.10 you will have to pick a theme supporting Gtk3 like greybird otherwise all of your new Gtk3 apps like Synaptic or Software-center will look ugly.

Here's a (short) list of non GNOME substitutes:
evince -> evince-gtk/epdfview
totem -> SMplayer/VLC/Parole
brasero -> xfburn
gnome-terminal -> xfce4-terminal
gedit -> medit/leafpad
eog -> ristretto/gthumb
file-roller -> xarchiver/squeeze
banshee -> gmusicbrowser
evolution -> thunderbird

That's just to speed up the system as none of these GNOME apps are inherently evil.

I found that dock applications like AWN or Cairo-Dock can really jazz up your desktop without the insanity of Unity or Gnome-shell.

Good luck and have fun!:)

---

### Post by RylosFan on 2011-10-21
Great!  Thanks for the responses so far!

---

### Post by RylosFan on 2011-10-21
I was curious about the indicator plugins as it would appear from what I've observed on my desktop (DropBox, Network Manager applet, etc.) that they are able to output to XFCE's notification panel(?).  I know that XFapplet provides this functionality but, as indicated in the previous statement, everything appears to already be working.

Am I correct in thinking that if I remove the gnome-applet package that it will break the indicators I currently have?  Or are the plugins fully compatible with both GNOME panel and XFCE panel?

---

### Post by scania_gti on 2011-10-21
Me too escape from Ubuntu to Xubuntu ;)
Try that psychocats method, but... Xubuntu after all anyway stay buggy and slow.
Until reinstall from Xubuntu CD.
And first time installing from CD - instalation was stopped... :D 
But second time was succesfull - Xubuntu remove all other soft, but my personal data and folders of removed software - leave in his places :)
Xubuntu working faster, than Ubuntu, Firefox more easy working with flash, and eating less RAM.

---

### Post by LewisTM on 2011-10-21
I think that the plugins are not tied to the DE. XFCE can display them if you include the indicator applet in one of your panels.

Removing GNOME stuff won't break anything. The only things I kept are the GNOME keyrings and the gvfs framework for use with Thunar, Gigolo - and Nautilus.

---

### Post by TBeholder on 2011-10-23
> **LewisTM said:**
> I suggest you keep Nautilus, it's still handy in some situations where Thunar falls short. Just [set it]("https://wiki.archlinux.org/index.php/GNOME_Tips#Stop_Nautilus_drawing_the_desktop") not to draw the desktop. Does not work for me: Nautilus still paints over the screen unless launched with --no-desktop, but setting arguments in "preferred applications" changes nothing.

> **LewisTM said:**
> Here's a (short) list of non GNOME substitutes:
evince -> evince-gtk/epdfview
gedit -> medit/leafpad

That's just to speed up the system as none of these GNOME apps are inherently evil.  In fact gedit is kinda cool, what with syntax coloring and extra plugins. I'd propose as replacements respectively
**xpdf** (slim and adjustable, allows control over font rendering, e.g. to turn blurring off) and
**mousepad** (split off leafpad for better printing support and IMO has better controls).

> **RylosFan said:**
> Am I correct in thinking that if I remove the gnome-applet package that it will break the indicators I currently have?  Or are the plugins fully compatible with both GNOME panel and XFCE panel? A good question, BTW. Gnome indicators show more. But i remember some bad interference between WM and panel applets when i tried to use xfce under gnome Ubuntu, so just in case will check it when nothing else runs.

---

### Post by Harry.k on 2011-10-23
I wouldn't recommend removing the gnome packages. Some of them may come in handy. If system resource consumption is your problem, occasionally try the command live interface.

---

### Post by LewisTM on 2011-10-24
> **TBeholder said:**
> Does not work for me: Nautilus still paints over the screen unless launched with --no-desktop, but setting arguments in "preferred applications" changes nothing.

Funny, for me I used to go to gconf-editor and turn it off in two places:

1. /apps/nautilus/preferences
2. /desktop/gnome/background

But now, in Oneiric, these keys have no effect and Nautilus does not draw the desktop, ever. Perhaps it now realizes it's not running in GNOME and shouldn't take over the desktop.

Also Mousepad seems to have ceased development so Leafpad is back as the *de facto* editor in Xubunutu and can print fine. medit can also highlight syntax just like gedit.

---

### Post by dave0109 on 2011-10-24
> **LewisTM said:**
> In 11.10 you will have to pick a theme supporting Gtk3 like greybird otherwise all of your new Gtk3 apps like Synaptic or Software-center will look ugly.

Yeah, that's a real shame, as although the greybird theme is OK, I really like the MurrinaCrystal ones. But as you point out, certain apps don't appear to be fully theme-able.

---

### Post by Flymo on 2011-10-24
About a year back I re-tasked an Acer Revo desktop and needed to switch from the Ubuntu Netbook version of Lucid (10.04) to XFCE4.

iirc, we just grabbed the XFCE4 meta-package in Synaptic, and chose XFCE4 at login after rebooting.  Do recall it was very easy.

Granted that the Mutter/Clutter netbook environment is not Gnome, but these Revos use an Atom CPU and are pretty sensitive to bloat.  It now scampers along about as well as you can expect with an Atom, and it can't do that with Gnome in our experience.

---

### Post by ufugu on 2011-10-24
Long-time Xfce lover here. 

Since you're asking for tips as a new convert from GNOME, here's one:  walk through every tab and option in every pane of the system settings.  

That's the fastest way to get a handle on what any DE can do when you are switching.  GNOME, KDE, obconf, Mac, Windows etc. have overlap with basic preferences, but they all give you very different configuration options when you start digging down deeper and the options you find really define the capability of the GUI.

---

### Post by mlnease on 2011-10-24
> **RylosFan said:**
> I recently installed xubuntu-desktop as GNOME has officially failed me.  Though I was running Lucid with GNOME 2.3, I don't plan on going back to GNOME given the simply awful performance I experienced through recent updates in addition to Unity and GNOME 3 appearing to be bigger headaches with less functionality.  

I'd like to maintain as clean a system as possible, removing any unwanted/unnecessary software and services.  By all appearances, the XFCE metapackage seems to have at least disabled GNOME components while in an XFCE session (as I would expect) but it's a nagging feeling having unused desktop binaries just sitting there.

[LIST]
[*]**To remove all things GNOME, will I risk breaking some dependencies?**
[*]**Does anyone have any tips for a recent XFCE convert?**
[/LIST]

I know it's a noobish question and I do appreciate this community's efforts immensely.
I'm no expert but I think it's a good question (that got some good answers).  I'm switching to Xfce for the reasons you mention above and have had a few challenges on the way that seem to be working themselves out.

A related question:  Are there any Xfce or Xfce related packages in existing repositories that I should install to improve Xfce desktop environment?

If you're interested, there's a lot of Xfce graphical software available [here]("http://xfce-look.org/index.php?xcontentmode=15x25x36x39x60x100x102x410x411x412x413x414x420x430x470x480").  I haven't tried it yet but am really looking forward to it.  I have a feeling this may become a popular thread for those who feel similarly about Unity and Gnome.

---

### Post by LewisTM on 2011-10-24
> **mlnease said:**
> I'm no expert but I think it's a good question (that got some good answers).  I'm switching to Xfce for the reasons you mention above and have had a few challenges on the way that seem to be working themselves out.

A related question:  Are there any Xfce or Xfce related packages in existing repositories that I should install to improve Xfce desktop environment?


xfce4-goodies would be the first thing that comes to mind.
Then all Thunar plugins.
I'm a big fan of cairo-dock, a single app that will allow you to replace the boring taskbar, launchers and desklets with something more modern-looking. If you're into that sorta thing.

---

### Post by mlnease on 2011-10-24
> **LewisTM said:**
> xfce4-goodies would be the first thing that comes to mind.
Then all Thunar plugins.
I'm a big fan of cairo-dock, a single app that will allow you to replace the boring taskbar, launchers and desklets with something more modern-looking. If you're into that sorta thing.
Thanks!  Got xfce-goodies (though not sure how to make use of them yet)  and all Thunar plugins.  And thanks, also got Cairo-dock which is most  impressive, though I'm usually *not* really into the modern-looking sorta thing (old guy).  Not sure if I'll use it but nice graphics and beats the *hell *out of Unity.

At this point I think I'm most interested in changing themes, icons and  so on--the defaults are pretty ugly.  I found a bunch of them [here]("http://ubuntuforums.org/Thanks%21%20%20Got%20xfce-goodies%20%28though%20not%20sure%20how%20to%20make%20use%20of%20them%20yet%29%20and%20all%20Thunar%20plugins.%20%20And%20thanks,%20also%20got%20Cairo-dock%20which%20is%20most%20impressive,%20though%20I%27m%20usually%20not%20really%20into%20the%20modern-looking%20sorta%20thing.%20%20Old%20guy.%20%20Not%20sure%20if%20I%27ll%20use%20it%20but%20nice%20graphics%20and%20beats%20the%20hell%20out%20of%20Unity.%20%20At%20this%20point%20I%20think%20I%27m%20most%20interested%20in%20changing%20themes,%20icons%20and%20so%20on--the%20defaults%20are%20pretty%20ugly.%20%20I%20found%20a%20bunch%20of%20them%20here%20http://xfce-look.org/index.php?xcontentmode=15x25x36x39x60x100x102x410x411x412x413x414x420x430x470x480") but gather they're based on Emerald, which is no longer supported and may be unstable?  Can you advise me on this or on how to get other Xfce themes, icons etc. that'll be stable and work well in Ubuntu (especially Oneiric+)?

Thanks Again,

mike

---

### Post by LewisTM on 2011-10-24
You can find a number of icon themes in the Software Center (unhide the technical items).
For the xfwm window themes, I'm no expert, I use Compiz and GTK themes. I don't see many in the repos.
Cheers!

---

### Post by LewisTM on 2011-10-25
> **mlnease said:**
> A related question:  Are there any Xfce or Xfce related packages in existing repositories that I should install to improve Xfce desktop environment?


I just discovered Synapse. It's a clone of GNOME Do but does not need GNOME. I was looking for something like that ever since the Deskbar applet got dumped.
Find any kind of item without needing Unity. Bind it to a shortcut key in XFCE and enjoy!

---

### Post by mlnease on 2011-10-25
Thanks again for all your posts, most helpful!  I must thank you again for Cairo Dock--the more I look at it, the better I like it.  I can see little reason at the moment to bother with panels in Xfce with Cairo.  As I wrote before, I'm usually *not* really into the modern-looking sorta thing and whiz-bang graphics really aren't my bag either, but hey--this thing *really* works.

---

### Post by weezyrider on 2011-10-25
Just curious - using 10.10, thinking about upgrading, but Unity is ugly! 

Number one - I prefer text to icons. Number 2, I don't want a theme per se, I want a plain gray desktop with no animation, no anything. Number 3, I like the task or menu bar or whatever you call it on the top with straight menus. I can find stuff faster if list can be alphabetized, and no icons in the way. 

Damn Windows and Apple for thinking everything has to be "pretty"  Some of us aren't gamers , some just believe that the OS should run in the background so you don't even notice it. Which means no animations and nothing flashing or moving. I've always used a plain desktop. If you want those, fine, but not everyone does. 

I'm new to Ubuntu, the commands are strange but the process of command line is not. I started with DOS. Those screens were white on blue. Simple and effective.

---

### Post by rattskjelke on 2011-10-26
What are Thunar plugins? I don't see anything with a name like that in the repos.

---

### Post by Rodney9 on 2011-10-27
> **rattskjelke said:**
> What are Thunar plugins? I don't see anything with a name like that in the repos.

Just search for thunar in Synaptic and you will see Media tags plugin for Thunar file manager and Archive plugin for Thunar file manager plus a few more.

---

### Post by malspa on 2011-10-27
> **ufugu said:**
> Long-time Xfce lover here. 

Since you're asking for tips as a new convert from GNOME, here's one:  walk through every tab and option in every pane of the system settings.  

That's the fastest way to get a handle on what any DE can do when you are switching.  GNOME, KDE, obconf, Mac, Windows etc. have overlap with basic preferences, but they all give you very different configuration options when you start digging down deeper and the options you find really define the capability of the GUI.

This is a really good tip. It's a really good way to get a handle on where things are and what you can do in Xfce (and, as ufugu said, other DEs and WMs, too).

Even for people like me who actually like Unity and GNOME Shell, Xfce is an awesome DE, and even well worth adding to your existing installation, in my opinion. I'm writing from Xfce in SalineOS, but before I installed that distro, I always added Xfce myself; I haven't yet used Xubuntu, and Saline is the first distro that I've installed that came with Xfce by default.

Perhaps slightly off-topic, in Ubuntu 10.04 I found that xfce4-panel is a nice panel to use with Openbox. Makes me wonder how it would look if used with Unity...

---

### Post by nerderello on 2011-10-28
I'm in the process of moving away from Gnome (even Gnome Classic in Gnome 3 isn't very good)

I found that, after installing 11.10 I got the Gnome wallpaper in XFCE, and if I right clicked on this desktop I got the Gnome set of options complete with the Gnome appearance application.

What I had done, in Gnome, was select, in the Gnome Tweak tool (shown as Advanced Settings) in the Desktop 'tab', the slider to turn ON "Have file manager(Nautilus) handle the desktop". I slide this to OFF and now get the XFCE wallpaper and desktop as wanted.

Thought I'd mention this in case anybody else bumps into it.

---

### Post by mlnease on 2011-11-07
> **nerderello said:**
> I'm in the process of moving away from Gnome (even Gnome Classic in Gnome 3 isn't very good)

I found that, after installing 11.10 I got the Gnome wallpaper in XFCE, and if I right clicked on this desktop I got the Gnome set of options complete with the Gnome appearance application.

What I had done, in Gnome, was select, in the Gnome Tweak tool (shown as Advanced Settings) in the Desktop 'tab', the slider to turn ON "Have file manager(Nautilus) handle the desktop". I slide this to OFF and now get the XFCE wallpaper and desktop as wanted.

Thought I'd mention this in case anybody else bumps into it.
Thanks for this--it sounds like an ideal workaround.  Unfortunately navigation in the new GDE is a mystery to me--it may sound stupid, but can you tell me just how to get to 'the Gnome Tweak tool (shown as Advanced Settings)'?  I did log out and back into the GDE but was defeated by the graphics.

Thanks in advance.  

**EDIT**  I found I had to install it first, from Ubuntu Software Center(?--now I can't find *that*--never mind, found it.)  Then I found Advanced Settings in Applications > Other > Advanced Settings.  Found the slider, slid it to 'Off'.  So far I see no change in my desktop options.  Am I missing something?

Thanks again for the tip.

---

### Post by Flymo on 2011-11-17
Suspect it depends on what/how the XFCE wallpaper config came about.  

I have no experience of mixing XFCE with Gnome3 so cannot elaborate. 
Hope someone comes up with a more helpful reply!

---

### Post by BobMarleyy on 2011-11-17
In Xubuntu (xfce desktop) there is a program running called xfdesktop. When I close this, the background becomes grey and right-clicking does not work. Restarting it gives me my background back and the right-click menu is available again. So try running xfdesktop. I think xfdesktop should replace gnome-desktop or something.

If you are moving away from gnome, you could try a clean install of Xubuntu (next time).

Cheers,
Bob

---

### Post by mlnease on 2011-11-18
Thanks, Bob, Flymo and All,

I've made a really genuine effort to force Oneiric (after doing the same thing with Natty) to perform half as well as Lucid with GNOME 2 (Bob, I think your advice to switch to Xubuntu was probably a good one).  But I'm done.  I've switched to LinuxMint, which performs pretty much exactly as I want it to OTB.  I keep my beloved Lucid on a separate partition till such a time as Canonical reverses its recent (and in my opinion, disastrous) changes of course or stops supporting Lucid to the point that it's no longer practical.

I do this with great regret.  I really love this OS, community and forum and have had a great time with Ubuntu.  I was as devoted as a devotee nerd can be, I guess.  Nearly fanatical.  Damn!  I hate to leave it.  But I have no interest at all in a cheap (well, *free*, to be fair) imitation of a proprietary Apple product that presumes to tell me what I should want and makes the grave mistake of assuming that the same DE will work across smart phones, tablets and desktops *and* that, in the future, everyone's going to be jabbing away with their fingers at huge, bobbling, weaving, pulsing icons screaming APPS APPS APPS on a greasy touch screen.  That's a non-starter, in my opinion.  I'll keep an eye on this forum to see whose prgnostication is correct.

Thank you all for your time and patience and especially *all* the Ubuntu developers--including those with whom I categorically disagree--for a once splendid free OS.  These have been great years.

---

### Post by IcyEyeG on 2011-11-19
I'm thinking of going Linux Mint 12 for my desktop (once it goes final), because I think that Xubuntu would need some additions to make it a true alternative to a Gnome 2.x Ubuntu:
- Needs some more plugins to match the gnome 2.x applets that are currently missing (Trashcan, system monitor, Applications/Places/System menu, Force-quit application, Connect to server, etc.);
- Needs better support for Nautilus;
- Support for compiz, without loosing xfwm4 windows borders.

I still think that Xubuntu holds the potential of becoming the alternative distro for those want a Gnome 2.x look and feel.  At least [you can make it look that way]("http://ubuntuforums.org/showpost.php?p=11421305&postcount=37").

---

### Post by LewisTM on 2011-11-19
I agree that Xubuntu, at least in its default configuration, is too minimalistic for a GNOME power user. However, all those limitations can be remedied quite painlessly.
> **IcyEyeG said:**
> 
- Needs some more plugins to match the gnome 2.x applets that are currently missing (Trashcan, system monitor, Applications/Places/System menu, Force-quit application, Connect to server, etc.);

The trashcan can be added to the desktop. *EDIT: There IS a trash applet for Xfce panels. As well as many, many more.*
xfce4-taskamanger is akin to the System Monitor, the latter can be installed without GNOME. The Places menu can be added in the panel (xfce4-places plugin or just xfce4-goodies). 
Bind xkill to a keystroke to kill any application, or use an advanced dock application.
Connect to a server using Gigolo+gvfs-backends. Yes, Gigolo lacks gvfs by default and its name is unintuitive. 
> **IcyEyeG said:**
> 
- Needs better support for Nautilus;

Nautilus can be configured to leave the desktop alone and works just as well as in GNOME. It can be set as the default file manager if you prefer. I find Thunar to be way faster.
> **IcyEyeG said:**
> 
- Support for compiz, without loosing xfwm4 windows borders.

If you run compiz then you should install Emerald and use its decoration themes which are much prettier than xfwm4.

What worries me more are the blatant packaging mistakes made by the Xubuntu team.
1. Packaged the Xfce volume control daemon which is icompatible with Pulseaudio, installed in all *buntu distros,
2. No way to edit menus (solution [here]("http://ubuntuforums.org/showthread.php?t=1875258")).
3. Gigolo packaged without gvfs-backends to connect to network locations
4. Mailto handler is broken in 64-bit Xubuntu (solution [here]("http://ubuntuforums.org/showthread.php?t=1878018"))
5. The keyboard layout applet sometimes forgets its settings.
 (brutal solution [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/548631/comments/31"))
Nothing is ever perfect on a Linux desktop. I would be curious to hear your impressions on Mint 12.

---

### Post by mikodo on 2011-11-19
This is a very informative thread, for Gnome2 refugees. LewisTM et al; Thanks!

---

### Post by 3Miro on 2011-11-19
Since people seem to read this thread, I should put a comment on a theme trick that I learned from Arch's tutorials.

If you are running XFCE and you want to use a theme that doesn't have GTK3 support, then all GTK3 apps will look horribly. You can fix this by adding a sym-link to any GTK3 theme inside your .config

```

cd ~/.config
ln -s /usr/share/themes/<theme name>/gtk-3.0/ gtk-3.0
```

<theme name> is the name of a theme that does have GTK3 support.

If you want to use a different theme, all you need to do is delete the existing sym-link and replace it with a new one. You can either run:
```
rm -fr ~/.config/gtk-3.0
```
or use Thunar (hit Ctr + H to see the hidden folders).

Note that the GTK3 theme may still be incompatible with your GTK2 theme, meaning that things may still be ugly. If you pick say a light theme for GTK3 and a dark theme for GTK2, then the result may be irritating to the eyes, but at least you will not have the ugly default theme.

---

### Post by mikodo on 2011-11-25
Bumpitiy-do; any more tips anyone?

---

### Post by mlnease on 2011-11-28
> **BobMarleyy said:**
> In Xubuntu (xfce desktop) there is a program running called xfdesktop. When I close this, the background becomes grey and right-clicking does not work. Restarting it gives me my background back and the right-click menu is available again. So try running xfdesktop. I think xfdesktop should replace gnome-desktop or something.

If you are moving away from gnome, you could try a clean install of Xubuntu (next time).

Cheers,
Bob
Hi Bob,

Probably my last post on this topic.  I thought your idea ('If you are moving away from gnome, you could try a clean install of Xubuntu (next time')) was a good one (and it was, I think, well worth trying).  So after having switched to Mint I deleted that partition, installed Xubuntu and tried Xfce desktop there.  I configured and tweaked for most of a day, then blew it away and reinstalled Mint *11*--***not* 12**--and I couldn't be happier.  I hope Ubuntu will catch up someday because I'm deeply attached to it and give it up with the utmost reluctance.  Well, things change, eh?

Best wishes.

---

### Post by mikodo on 2011-11-29
> **mlnease said:**
> Hi Bob,

Probably my last post on this topic.  I thought your idea ('If you are moving away from gnome, you could try a clean install of Xubuntu (next time')) was a good one (and it was, I think, well worth trying).  So after having switched to Mint I deleted that partition, installed Xubuntu and tried Xfce desktop there.  I configured and tweaked for most of a day, then blew it away and reinstalled Mint *11*--***not* 12**--and I couldn't be happier.  I hope Ubuntu will catch up someday because I'm deeply attached to it and give it up with the utmost reluctance.  Well, things change, eh?

Best wishes.

Makes me sad, to read of a person with commitment to Ubuntu, having come through effort to make today's Ubuntu still appealing to him, only to reach this decision...  :(

Good Luck mlnease!

---

### Post by mlnease on 2011-11-29
> **mikodo said:**
> Makes me sad, to read of a person with commitment to Ubuntu, having come through effort to make today's Ubuntu still appealing to him, only to reach this decision...  :(

Good Luck mlnease!
Thanks, Mikodo--it *is* sad but who knows what the future holds?  Maybe I'll see you around here yet.

Best Wishes,

mike

---

### Post by dangmc on 2011-12-03
> **3Miro said:**
> Those guys have the commands to add/remove different desktop environments:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Make sure you pick the command for your distribution, the default commands are for 11.10, if you have 10.04 you have to select it at the top of the page.

I tried this for 11.04_amd64 with this result:E: Unable to locate package libstlport4.6ldbl
E: Couldn't find any package by regex 'libstlport4.6ldbl'

Any suggestions?

---

### Post by 3Miro on 2011-12-03
> **dangmc said:**
> I tried this for 11.04_amd64 with this result:E: Unable to locate package libstlport4.6ldbl
E: Couldn't find any package by regex 'libstlport4.6ldbl'

Any suggestions?

Are you sure you picked the command for the right version of Ubuntu? Here is the one for 11.04:

[http://www.psychocats.net/ubuntu/purexfcenatty](http://www.psychocats.net/ubuntu/purexfcenatty)

---

### Post by cmcanulty on 2011-12-03
I have installed xfce4 on my 11.10 ubuntu on which I usually use gnome classic-no effects. I am getting used to xfce as I fear classic is a dead end. But WHY go backwards in functionality to gnome 3? The few things I miss in xfce-I can't figure out how to disable caps lock and a few other customizations. Any icon can be just dragged to panels, it is a bit tricky-you have to hold icon there until a white box appears then it will stick.I don't think anything will be as perfect as gnome 2 for me but xfce is pretty close. So I am keeping my options open. Learning xfce while trying classic and also some mint options. I would really hate to leave the ubuntu community in fact I tried to leave as I hate this new direction so much but decided to wait and see.

---

### Post by mike555 on 2011-12-04
> **cmcanulty said:**
>  The few things I miss in xfce-I can't figure out how to disable caps lock and a few other customizations.

  To stop CapsLock in Xubuntu   11.10   (changing it to Shift without lock)

   open leafpad , put in;

      !
! Swap Caps_Lock and Shift_L
!
remove Lock = Caps_Lock
keysym Caps_Lock = Shift_L


 then save as "   .nocaps   " in your home folder (notice the dot)   then open Settings Manager and  then Sessions and startup, Application Autostart tab, click add ,  name it "nocaps " or what ever you want, then in Command box type ;  
    "  xmodmap /home/mike/.nocaps  " without the quote marks  (changing mike for your user name) make sure your new startup is checked and log out and back in ..........

---

### Post by ManualSparrow on 2011-12-04
I personally have used XFCE since 10.10 (back in the Gnome 2 days) and still find it a lot easier to customize than Gnome/KDE/Unity.

I used to keep Nautilus around, but mostly it just caused problems. Thunar works pretty well (automount is nice), but what I've been using lately is Marlin from the [elementaryOS]("http://www.elementaryos.org") team. To install, you'll need to pull in some dependencies and add the Elementary PPA (read about doing that [here]("https://launchpad.net/~elementary-os/+archive/daily")).

Another XFCE trick is binding the middle-click and right-click menus to keyboard shortcuts: Just go to 'Settings'>'Keyboard'>'Application Shortcuts' and bind 'xfdesktop --windowlist' to something like 'Alt-Menu' (that's the middleclick) and 'xfdesktop --menu' to, say, Ctrl-Menu.

I'm using [Tint2 Panel]("http://code.google.com/p/tint2/") instead of a dock or XFCE panel because with the above shortcuts + Synapse bound to the Menu key, I really don't need launchers - just indicator applets and a way to switch windows. The Tint panel is also cool because you can put the windows from each desktop in a separate box, combining the workspace switcher and application switcher into one panel element. If you like a more traditional desktop setup, the XFCE panel is great, though - a lot of great accessories are available in the xfce4-goodies package.

---

### Post by bluexrider on 2011-12-04
> **RylosFan said:**
> I recently installed xubuntu-desktop as GNOME has officially failed me.  Though I was running Lucid with GNOME 2.3, I don't plan on going back to GNOME given the simply awful performance I experienced through recent updates in addition to Unity and GNOME 3 appearing to be bigger headaches with less functionality.  

I'd like to maintain as clean a system as possible, removing any unwanted/unnecessary software and services.  By all appearances, the XFCE metapackage seems to have at least disabled GNOME components while in an XFCE session (as I would expect) but it's a nagging feeling having unused desktop binaries just sitting there.

[LIST]
[*]**To remove all things GNOME, will I risk breaking some dependencies?**
[*]**Does anyone have any tips for a recent XFCE convert?**
[/LIST]

I know it's a noobish question and I do appreciate this community's efforts immensely.

good reference [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by matt3839 on 2011-12-04
> **ManualSparrow said:**
> I personally have used XFCE since 10.10 (back in the Gnome 2 days) and still find it a lot easier to customize than Gnome/KDE/Unity.

I used to keep Nautilus around, but mostly it just caused problems. Thunar works pretty well (automount is nice), but what I've been using lately is Marlin from the [elementaryOS]("http://www.elementaryos.org") team. To install, you'll need to pull in some dependencies and add the Elementary PPA (read about doing that [here]("https://launchpad.net/%7Eelementary-os/+archive/daily")).

Another XFCE trick is binding the middle-click and right-click menus to keyboard shortcuts: Just go to 'Settings'>'Keyboard'>'Application Shortcuts' and bind 'xfdesktop --windowlist' to something like 'Alt-Menu' (that's the middleclick) and 'xfdesktop --menu' to, say, Ctrl-Menu.

I'm using [Tint2 Panel]("http://code.google.com/p/tint2/") instead of a dock or XFCE panel because with the above shortcuts + Synapse bound to the Menu key, I really don't need launchers - just indicator applets and a way to switch windows. The Tint panel is also cool because you can put the windows from each desktop in a separate box, combining the workspace switcher and application switcher into one panel element. If you like a more traditional desktop setup, the XFCE panel is great, though - a lot of great accessories are available in the xfce4-goodies package.
I've found that tint2, while fantastic for lighter setups like Openbox (I would probably be using such if I didn't want Xfce), is a lot more difficult to configure than xfce4-panel, even with the GUI. The configuration file's layout bugs me to no end, personally.

---

### Post by cmcanulty on 2011-12-04
OK thanks!

---

### Post by ManualSparrow on 2011-12-04
> **matt3839 said:**
> I've found that tint2, while fantastic for lighter setups like Openbox (I would probably be using such if I didn't want Xfce), is a lot more difficult to configure than xfce4-panel, even with the GUI. The configuration file's layout bugs me to no end, personally.


This is true. For those that like docks, I'd also recommend Plank (a stripped down version of the popular Docky). You can install it with


```
sudo add-apt-repository ppa:ricotz/docky
sudo apt-get update
sudo apt-get install plank

```


When I tested out Cairo-Dock it used 65 MB of RAM - Plank uses 17.

---

### Post by matt3839 on 2011-12-04
> **ManualSparrow said:**
> This is true. For those that like docks, I'd also recommend Plank (a stripped down version of the popular Docky). You can install it with


```
sudo add-apt-repository ppa:ricotz/docky
sudo apt-get update
sudo apt-get install plank

```
When I tested out Cairo-Dock it used 65 MB of RAM - Plank uses 17.
<20MB for a dock sounds excellent, thanks a whole ton for the tip! :D

---

### Post by ManualSparrow on 2011-12-05
Also, the default theme is a bit unusual. You can edit it with ```
leafpad ~/.config/plank/theme/dock.theme
``` Find the TopPadding entry and change it to ```
TopPadding=0
``` for a look similar to the default Docky HUD theme.

---

