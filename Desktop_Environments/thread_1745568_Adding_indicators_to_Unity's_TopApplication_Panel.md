---
title: "Adding indicators to Unity's Top/Application Panel"
date: 2011-05-01
forum: Desktop Environments
---

### Post by jackn on 2011-05-01
I like Unity, and I appreciate Canonical's work in making the desktop cleaner-looking and more intuitive.

I think that being able to customize the top/application(?) panel would be very powerful. By this, I mean both adding and removing indicators.

I guess the developers are aware of this, and it's easier said than done. I don't know.

Personally, I miss the weather and CPU temperature applets of the old Gnome layout.

I tried to apply the best [guide]("http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/") I've found to modifying the top panel, to no avail. 

After I followed the instructions for the addition of three different indicators (weather, cpu frequency and CPU and RAM % usage), my top panel remained the same.
I don't know whether the indicators should show up right away or only upon restart. I did restart, though.

For both the weather and CPU frequency indicators, the terminal said:
[INDENT]Failed to fetch gzip:/var/lib/apt/lists/partial/fr.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch[/INDENT]
I don't know how to get around this.

Thanks,
jackn

---

### Post by johnnyredshirt on 2011-05-02
This is one of the problems I have with unity too. I'd be very happy to be able to put those same applets on the top bar (just as I have in gnome for a few years already) unless this some how messes up the "Bold New Paradigm of Unity" (and the fanboy angels sing alleluia ;} ).

---

### Post by jackn on 2011-05-02
OK, but let's be good about it.
First, I do like the new interface. I find it intuitive, elegant and more in line with the latest hardware.
Then, if you like, you can keep the Gnome layout.

Finally, as you can see from the link provided in the first post, the developers are thinking of it.
I do hope more indicators will become available and that the panel becomes fully customizable. 
In the meantime, an Alt-Tab toggle to see the Xsensors window with the CPU temperature, which I used to have as an applet, is not the end of the world.

And I'll go on trying to use the indicators featured in the link in the first post. My failure to install three of them was the main reason for the post. 
Help anyone?

Thanks, 
jackn

---

### Post by Copper Bezel on 2011-05-02
[_WebUpD8_]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html") has an item for indicators. That's separate from the old panel applets. Apparently, the weather indicator needs to be installed, but it's in the repos as indicator-weather.

---

### Post by jackn on 2011-05-02
Thanks, Copper.

Ok, learnt a bit.
As Copper says, can allow any application to reside in the panel. The 'GUI' part of the guide referred to in the previous post is easy (scroll down).
Here is a comprehensive [guide]("http://askubuntu.com/questions/29553/how-can-i-configure-unity") to configuring Unity, including a few points about the panel. It includes the above point on the whitelist for the panel and other, graphical aspects. But I'm left wondering about removal of indicators...

It turns out the CPU usage indicator I referred to in the initial post did get downloaded and installed, except it doesn't automatically sit on the panel.
This I realized from an Askubuntu [post]("http://askubuntu.com/questions/29903/what-happened-to-the-weather-app-in-the-panel"), in which it happened to another user. 
Perhaps then indicators should go right to the panel. It could either be the default, or it could ask the user whether to do so.

And. Launching 'Skype', for example, immediately put an icon in the panel. So, it seems, if an application has an indicator feature, launching it will place one on the panel. It is necessary, though, to launch/open an app/indicator, not just to install it.

I am left with one big q: how to remove things from the panel?... While trying to find out, I've accumulated four different CPU usage indicators on the panel... 

How do you remove indicators, either those you add or those that come in by default?

Thanks for all of this input.
jackn

---

### Post by johnnyredshirt on 2011-05-02
Apologies for the sarcasm. I just learned about 'indicators' myself and I'm wondering how to remove them as well. Another little quibble i have is that I'm an 'auto-hider' and I'd like that ability too.

---

### Post by jackn on 2011-05-02
Some more headway.
I could remove the extra Sysmonitor (% CPU usage) indicators by restoring the whitelist (see previous posts on modifying panel) to default. This did not happen right away, I had to restart, too.
Don't know whether restarting would have eliminated the indicators by itself, though I can't see why it should.
Then, I again changed the whitelist back to 'all', added the Sysmonitor indicator by clicking on it from the dash, and all was well.

Further, it is easy to download and install other indicators from the Ubuntu Software Center (contrary to adding repos, etc, as suggested in the guide in the first post). This way, I now have the weather and the cpufrequency indicators installed. 
The Ubuntu Software Center is a model of user-friendliness, I must say.

I was able to place the weather indicator on the panel. It's clear and useful.
Two issues remain.
[LIST]
[*]I cannot place the cpufrequency indicator on the panel. While it is installed and I can click on it from the dash, and the whitelist is set on 'all'... no cigar. Likewise, couldn't place the hp-systray indicator (featured in the default whitelist) on the panel.
[*]More importantly, I still don't know how to remove default indicators... (the whitelist, it seems, only applies to indicators which the panel does not feature by default).
[/LIST]

OK, so the panel is pretty satisfactory now, and the ability to customize it has improved.
I guess it's easier said than done... but a drag and drop MO would be welcome. Likewise, being able to freely move the indicators along the panel, ordering them setting space between them, would be handy.
Also, perhaps mutiple instances of the same indicators should either be blocked or warned about.
I think I might drop Launchpad a line. What do you think?

Redshirt, what's a 'auto-hider', anyway?

---

### Post by johnnyredshirt on 2011-05-02
I like all of my bars, docks and menus set to auto hide to maximize screen space. I mostly use ubuntu on my msi u230 netbook, 12.1" screen is bigger than some others, but I like to use it all.

As far as the cpufreq indicator I got it working after creating a launcher then adding it to startup.

---

### Post by stinkeye on 2011-05-02
You'll eventually find suitable customizations for Unity.

On Maverick I used to have the panel full of cpu,temp,mem and netspeed applets so I could see them when the window was maximized.

Now I just use conky and toggle it's above/below properties using a
wmctrl script bound to a mouse gesture.

---

### Post by johnnyredshirt on 2011-05-02
Dude, you can remove indicators in synaptic package manager. I just un-installed the indicator-me and voila.

---

### Post by stinkeye on 2011-05-02
> **johnnyredshirt said:**
> Dude, you can remove indicators in synaptic package manager. I just un-installed the indicator-me and voila.

Congratulations on discovering synaptic's package removal capabilities .....dude. :cool:

---

### Post by johnnyredshirt on 2011-05-02
Heh, yep I'm a noob. Well spotted... Dude;}

ps Colin Hay rocks. Put some shrimp on the barbie for me. BTW how much does a Holden Maloo cost?

---

### Post by stinkeye on 2011-05-02
> ps Colin Hay rocks.
Ye, did you know he got sued for stealing the flute melody from an
old Aussie school song “Kookaburra Sits in the Old Gum Tree”.
They got 5%.


> Put some shrimp on the barbie for me
I would rather put Barbie on my.......

> BTW how much does a Holden Maloo cost?
No idea, I drive little mitsubishi 4 cylinder. :shock:
:tongue:

---

### Post by jackn on 2011-05-02
> **johnnyredshirt said:**
> 
As far as the cpufreq indicator I got it working after creating a launcher then adding it to startup.

By 'creating a launcher', do you mean adding it to the launcher?

In my case, after installing indicator-cpufreq, it doesn't show in the dash.
It shows in the filesystem:
jackn@$:~$ ls -l /usr/bin/indicator-cpufreq 
-rwxr-xr-x 1 root root 3495 2011-02-27 10:44 /usr/bin/indicator-cpufreq
When I try to launch it, however, the system hangs.
Upon Ctrl c:
```
jackn@$:~$ /usr/bin/indicator-cpufreq
^CTraceback (most recent call last):
  File "/usr/bin/indicator-cpufreq", line 82, in <module>
    gtk.main()

```
So this looks like a specific problem with this indicator, unrelated to panel customization.
Anyone knows how to get it to launch?
The above result obtains after a reinstall.

Thanks,
jackn

---

### Post by jackn on 2011-05-03
> **stinkeye said:**
> Congratulations on discovering synaptic's package removal capabilities .....dude. :cool:

What I personally needed to realize here, Stinkeye, is that indicators needed to be installed and removed as independent pieces of software.

This is by no means obvious. I even think it's odd and inconvenient.

I'd expect indicators to be an independent feature of a piece of software. Thus, displaying the indicator would be independent of the function of that software. 
For example, Google Desktop search could be desired or not, per se, for its search function. 
Once installed and running, its indicator could be placed on the panel or not.
Indeed, I have exactly this issue. 
I have a Google Desktop search indicator on my panel. I don't want it. I could uninstall the whole software, which would remove the indicator, I think. 
I do want the search, however, and not the indicator... 
AFAIK, there's no independent software for this indicator which could be removed, while leaving Google Desktop search installed.

Likewise, I have a double sound indicator. I can't remove one of them.
I can't 'unistall sound'...

I think both of the above unwanted indicators landed on the panel through some unintended keyboard shortcut hits while I was using the dash.
In any case, I didn't mean to place them there.

It would be nice to be able to just drag and drop the indicators. Alternatively, a right-click option would do.
At this point, customizing the panel is an unwieldy process.
It's not the end of the world, but it would be nice to review it.

jackn

---

### Post by Copper Bezel on 2011-05-03
Generally, the applications themselves will have the option to display or not display the systray indicator. It *is* a somewhat messy system, particularly when third party apps with dubious need for systray space don't offer an option not to display their indicators. However, the basic idea is that the systray simply displays a tray icon for each icon that asks nicely. I agree that a GUI blacklist would be *heavenly*, but this is by no means a new problem (and one that Unity makes some attempt to solve, if not a fully satisfactory one.)

Are the sound indicators' menus identical? I *think* - and this is tentative and second-hand, because I'm about to boot into Natty for the first time - that Unity's panel actually specifies the Sound Menu in one specific position on the panel but blacklists it from the indicator applet area, and whitelisting all indicators allows it to appear in the applet area with your other tray applications while it's still being called specifically elsewhere. I can duplicate the behavior under similar circumstances in 10.10.

---

### Post by jackn on 2011-05-03
> **Copper Bezel said:**
> 
Are the sound indicators' menus identical? I *think* - and this is tentative and second-hand, because I'm about to boot into Natty for the first time - that Unity's panel actually specifies the Sound Menu in one specific position on the panel but blacklists it from the indicator applet area, and whitelisting all indicators allows it to appear in the applet area with your other tray applications while it's still being called specifically elsewhere. I can duplicate the behavior under similar circumstances in 10.10.

Yes, identical sound indicators. 
One of them is the default one, between the wireless and mail indicators.
The other one was suddenly born one day, while I had the Dash on. According to you, this has nothing to do with the Dash, but rather with my whitelisting 'all'. Perhaps.
You can see it's a mess.

Again, it's not the end of the world. It's about allowing Unity to be as good as it promises to be, and integrating its behaviour throughout its various components. 
Also, now that I think of it, installing and unistalling individual indicators, desirable or not as it may be, still does not address customization of the default indicator lineup.
It's odd that a screen basically designed to display only active software comes with an unmodifiable indicator panel.

jackn

---

### Post by johnnyredshirt on 2011-05-03
By 'creating a launcher', do you mean adding it to the launcher?

Umm... sorry but it was very late, for me, last night and I was a bit drunk ;}. I think I started it with the command, then it appeared under startup applications. I clicked on it in there to add to startup and it worked... I think.

---

### Post by kid1000002000 on 2011-05-03
There is a way to whitelist the indicator applet to accept all indicators you throw at it.

[http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/)
is one way to do it.  Just know that you will be fighting bug 
[https://bugs.launchpad.net/unity/+bug/761409](https://bugs.launchpad.net/unity/+bug/761409)
if you follow the omgubuntu instructions.  The more people who subscribe to the bug list the better, though, so don't be bashful!

---

### Post by stinkeye on 2011-05-03
> **jackn said:**
> What I personally needed to realize here, Stinkeye, is that indicators needed to be installed and removed as independent pieces of software.

This is by no means obvious. I even think it's odd and inconvenient.

I'd expect indicators to be an independent feature of a piece of software. Thus, displaying the indicator would be independent of the function of that software. 
For example, Google Desktop search could be desired or not, per se, for its search function. 
Once installed and running, its indicator could be placed on the panel or not.
Indeed, I have exactly this issue. 
I have a Google Desktop search indicator on my panel. I don't want it. I could uninstall the whole software, which would remove the indicator, I think. 
I do want the search, however, and not the indicator... 
AFAIK, there's no independent software for this indicator which could be removed, while leaving Google Desktop search installed.

Likewise, I have a double sound indicator. I can't remove one of them.
I can't 'unistall sound'...

I think both of the above unwanted indicators landed on the panel through some unintended keyboard shortcut hits while I was using the dash.
In any case, I didn't mean to place them there.

It would be nice to be able to just drag and drop the indicators. Alternatively, a right-click option would do.
At this point, customizing the panel is an unwieldy process.
It's not the end of the world, but it would be nice to review it.

jackn

App Indicators are a fairly new project and I'm sure they will get better.
See here why they came about.
[**_[COLOR="DarkRed"]https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators[/COLOR]_**]("https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators")

From what I've read they were designed by Canonical and the StatusNotifier spec was presented to be included in gnome
but was rejected hence we are now seeing the unity panel as default.

Some people think gnome is hard to work with and get your own implementations accepted.
Some think Canonical just doesn't know how to work with gnome.
Me I got know idea and don't really care.
The bottom line is Unity will take a while to be more customizable and should
develop into a very unique desktop.

There are few things that irk me about Unity but like you said "it's not the
end of the world" and after all it is only the first release.

---

### Post by Mad-Halfling on 2011-05-08
I'm getting hit by a bug - I've enabled apps in the whitelist and they appeared.  Now, for some reason, they don't - I've even changed the whitelist to 'All' and this still doesn't work - in fact I've just found I can't even click on the sound, network, etc icons in the notification panel

---

### Post by stinkeye on 2011-05-08
> **Mad-Halfling said:**
> I'm getting hit by a bug - I've enabled apps in the whitelist and they appeared.  Now, for some reason, they don't - I've even changed the whitelist to 'All' and this still doesn't work - in fact I've just found I can't even click on the sound, network, etc icons in the notification panel
...exactly why for the time being there is a whitelist.

---

### Post by DoneRightI.T. on 2011-05-17
> **stinkeye said:**
> ...exactly why for the time being there is a whitelist.

I'm experiencing the same issue... and as a work-around for the time-being adding 'all' should allow everything.... so I'm not sure the point of the above?

Is there a reason changing this breaks the functionality of the "default" whitelisted icons?

---

### Post by stinkeye on 2011-05-17
From what I know app-indicators are a new spec and some applications that aren't written to this will cause problems and result in not being able to click on any of them. 
The indicators behave differently in that you only need to click on one  
indicator and the menus for the other indicators will open just by sliding your mouse accross, the same as the global menu.

---

