---
title: "random Awesome/DWM/WMII chatter"
date: 2008-02-06
forum: Desktop Environments
---

### Post by shearn89 on 2008-02-06
I'm not sure this thread as already been started, if it has, mods - feel free to merge.

I just thought that all the tiling WM users could do with their own version of the "random openbox chatter" thread, given that there's often a lot of code and chat that gets posted on the screenies thread...


Also, as a starting point, i've been looking at conky-cli, and using it in my awesome statusbar, but why bother? Surely you just take up all the space in the statusbar, and its easier just to have it in the background, on the desktop? I have mine running at the bottom of my screen, kind of like its own statusbar, and for my tiling layout "term" tag, there's a border to stop terms going over it.

Just wondering...

---

### Post by Gigamo on 2008-02-06
How do you get that border on the bottom to stop terms going over it?

Meanwhile I'm also trying to figure out how to display percentage of CPU being used in awesome statusbar (no conky). If anyone knows that be great.

---

### Post by shearn89 on 2008-02-06
one of the settings in the .awesomerc file is called "padding", i have this:
```

padding
    {
        bottom = 18
    }

```
For terms, its a bit messed up, as 18 pixels is perfect for maximised layout, but a bit too much in any other...
Works well enough though.

---

### Post by Gigamo on 2008-02-06
> **shearn89 said:**
> one of the settings in the .awesomerc file is called "padding", i have this:
```

padding
    {
        bottom = 18
    }

```
For terms, its a bit messed up, as 18 pixels is perfect for maximised layout, but a bit too much in any other...
Works well enough though.
Yep found that one out just now. My Trayer is moving up along with it though :(

---

### Post by Nythain on 2008-02-06
figure this is as good a place as any to start askin questions so i've got a few..
First... going from flux to awesome, what should i expect to gain/lose... so far all i've really noticed is an increase in customization/scripting of the "panel" and a loss of my beloved "root menu"...

Then, how does this "tiling" work anyways... like lets say i open a terminal... can i decide its geometry and just let the window manager handle the placement, or is i gonna try to handle the geometry also... i notice a bunch of screenies where there will be one big terminal thats like half the screen on one side of the screen with irssi or something, then a few others tiled on the right side of the screen in varying sizes

lastly at the moment... im still not quite understanding out these "tags" in the, usually, upper left go... are they like drop down menus i can put apps in that will launch the app in a certain "tiling mode" such as spiral, floating, etc... i mean, so far, thats what i've gathered, but havent really seen anything to illustrate one way or another...

hopefully you all can shed some light on at least some of this, because i keep getting very distracted from fluxbox every time i visit the forums and see what you all have managed to do next/now with Awesome... in fact, when i get home, i will be setting up a dual boot system on my "windows box" just so i can screw with flux/awesome more without disrupting my "server box" with reboots, crashes, and other assorted "problems"

ps, thanks for the awesomerc's and various scripts in the other threads, so far i've been piecing together what i can and want and expect before i get this dual boot goin :)

---

### Post by Gigamo on 2008-02-07
Indeed you will lose your root menu, there is no rightclick menu in awesome. However, when you get used to it and play with it for a few days, you can get stuff done so much faster since you can bind simply everything to key combinations.

As for tiling, yes that handles geometry. Let's say you open a terminal on an empty workspace (which is called "tag" in awesome), it will be maximized. When you open a second one, both will take half the screen. Open a third and one will take half the screen, the other two will share the rest, etc.

---

### Post by shearn89 on 2008-02-07
> **Nythain said:**
> figure this is as good a place as any to start askin questions so i've got a few..
First... going from flux to awesome, what should i expect to gain/lose... so far all i've really noticed is an increase in customization/scripting of the "panel" and a loss of my beloved "root menu"...

Then, how does this "tiling" work anyways... like lets say i open a terminal... can i decide its geometry and just let the window manager handle the placement, or is i gonna try to handle the geometry also... i notice a bunch of screenies where there will be one big terminal thats like half the screen on one side of the screen with irssi or something, then a few others tiled on the right side of the screen in varying sizes

lastly at the moment... im still not quite understanding out these "tags" in the, usually, upper left go... are they like drop down menus i can put apps in that will launch the app in a certain "tiling mode" such as spiral, floating, etc... i mean, so far, thats what i've gathered, but havent really seen anything to illustrate one way or another...

hopefully you all can shed some light on at least some of this, because i keep getting very distracted from fluxbox every time i visit the forums and see what you all have managed to do next/now with Awesome... in fact, when i get home, i will be setting up a dual boot system on my "windows box" just so i can screw with flux/awesome more without disrupting my "server box" with reboots, crashes, and other assorted "problems"

ps, thanks for the awesomerc's and various scripts in the other threads, so far i've been piecing together what i can and want and expect before i get this dual boot goin :)

There's no menu in awesome by default, but you can add one. Check their wiki.

As Gigamo said, tiling works by taking the first thing and making it take up the whole desk, then you open another and they share (1/2 each), then another, and one will be half, and the other two take a quarter. A third, and the first will still be half, and the other three share. There are a few variations on this theme.

Tags are like workspaces - you tag programs in the awesome config file, and then when they open, they open on that "workspace". You can set different tags to have different layouts as well. They're not like menus, and clicking on them just shows the "workspace" (tag).

Also, if you're interested in trying some of these on windows i recommend getting **virtualbox**. Its entirely free, and allows you to run a virtual instance of whatever on windows. I use it for testing .iso's and new distros to see whether i like them.

---

### Post by Nythain on 2008-02-07
Ok, so thats how it works... that made much more sense than anything else i read...
Im not really installing inside windows... i just decided to make my windows machine a dual boot... there's other things i want to play around with also, and got tired of my server randomly crashing or needing to reboot.

thanks much, ill probably end up asking a billion more questions before im done (poor yabba and red squirrel had to put up with the same thing back when i was learning flux)

---

### Post by shearn89 on 2008-02-08
Hahaha... The good thing about this forum is that people are always willing to help - i remember when I started on Arch I tried to get help in the Arch forums, and people where supremely unhelpful.

---

### Post by rjmdomingo2003 on 2008-02-09
Been trying to put icons into the statbar (ala Gigamo's) by adding the appropriate iconbox for each textbox in my awesomerc. However, upon restart, the statbar doesn't show anything.

Do I need to add something on the awesome-monitor? awesome.sh?

---

### Post by Gigamo on 2008-02-09
> **rjmdomingo2003 said:**
> Been trying to put icons into the statbar (ala Gigamo's) by adding the appropriate iconbox for each textbox in my awesomerc. However, upon restart, the statbar doesn't show anything.

Do I need to add something on the awesome-monitor? awesome.sh?

Normally not, no. Just make sure the icon is in .png format, and then it should show up.

Here is my textbox/iconbox section again in case you have a wrong syntax (which I doubt), but anyway:

```
        iconbox mpd_icon { 
		image = "/home/gig/.bitmaps/mpd2.png" 
         	mouse { 
                button = "1" 
                command = "spawn" 
                arg = "exec mpc toggle" 
            }
	}
        textbox mpd
        {
            fg = "#bbbbbb"
        }
        textbox separator0 { text = "·" 
                             fg = "#dddddd" }
        textbox cpu
        {
            fg = "#bbbbbb"
        }
        textbox separator1 { text = "·" 
                             fg = "#dddddd" }
        textbox mem
        {
            fg = "#bbbbbb"
        }
        textbox separator2 { text = "·" 
                             fg = "#dddddd" }
        textbox battery
        {
            fg = "#bbbbbb"
        }
        textbox separator3 { text = "· " 
                             fg = "#dddddd" }
        iconbox mail_icon { image = "/home/gig/.bitmaps/mail2.png" }
        textbox mail
        {
            fg = "#bbbbbb"
        }
        textbox separator4 { text = "·" 
                             fg = "#dddddd" }
        textbox date
        {
            fg = "#bbbbbb"
        }
        textbox time
        {
            fg = "#99ccff"
        }
```

---

### Post by shearn89 on 2008-02-09
yeah - the awesomerc is read in the order that you want stuff to appear (if you see what i mean), so wherever you put them is where they'll show (eg, after the tasklist, or after the tags). Make sure that the { } are there.

Maybe check the console for errors?

---

### Post by rjmdomingo2003 on 2008-02-10
Thanks, shearn & gigs! I think I have the wrong syntax!

Guess I didn't add:

```
_icon
```

to each iconbox line.

I'll check it out later and let you guys know.

---

### Post by shearn89 on 2008-02-10
that might make a difference - if they have the same name it might get confused!

---

### Post by rjmdomingo2003 on 2008-02-11
> **Gigamo said:**
> Normally not, no. Just make sure the icon is in .png format, and then it should show up.

Got the icons to appear, yay! Thanks, Gig!

Is your mail script for gmail? Can I use your script to get inbox alerts from Yahoo!?

Thanks!

---

### Post by Gigamo on 2008-02-11
> **rjmdomingo2003 said:**
> Got the icons to appear, yay! Thanks, Gig!

Is your mail script for gmail? Can I use your script to get inbox alerts from Yahoo!?

Thanks!

I have no idea about Yahoo, but yes it's for gmail.

It's here if you want to try:

```
#!/bin/bash

gmail_login="username(without @)"  
gmail_password="password" 

dane="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

if [ -z "$dane" ]; then
echo "!"
else
echo "$dane"
fi
```

---

### Post by Gigamo on 2008-02-15
Check this out guys:

[http://xs.to/xs.php?h=xs224&d=08075&f=2008-02-15951.png](http://xs.to/xs.php?h=xs224&d=08075&f=2008-02-15951.png)

Someone over at the arch forums's desk. Gotta find all this graphs and stuff out :D

---

### Post by rjmdomingo2003 on 2008-02-15
> **Gigamo said:**
> Check this out guys:

[http://xs.to/xs.php?h=xs224&d=08075&f=2008-02-15951.png](http://xs.to/xs.php?h=xs224&d=08075&f=2008-02-15951.png)

Someone over at the arch forums's desk. Gotta find all this graphs and stuff out :D
Ooh, sweet! When you find them, please share..:popcorn:

---

### Post by Gigamo on 2008-02-15
His configs are here: [ftp://sen.homelinux.org/config/](ftp://sen.homelinux.org/config/)

I have no time to fiddle around with it though.

---

### Post by corin.gs on 2008-02-21
So this may be just a dumb question, but I'll ask anyway. My current setup is with awesomewm and xcompmgr...and I wanted to know if there is a way that I can get xcompmgr to make all of my windows transparent, not just the unfocused ones? There is probably a simple solution, but I couldn't find it.

And, is there a way to make my main statusbar be toggled off by default?

---

### Post by miggys on 2008-02-27
I don't really know much about xcompmgr.

For statusbar off, if you do startx, you can put 

```

sleep 1 && echo 0 statusbar_toggle statusbar_identifier | awesome-client &

```

in your xinitrc before exec awesome.  If it doesn't work, try making your sleep longer.

Additionally, you could just run a script from here that does any start up thing you want.

If you use a gui login manager I'm sure you can do something similar but I'm not familiar with them.

---

### Post by fuscia on 2008-03-07
> **Gigamo said:**
> Check this out guys:

[http://xs.to/xs.php?h=xs224&d=08075&f=2008-02-15951.png](http://xs.to/xs.php?h=xs224&d=08075&f=2008-02-15951.png)

Someone over at the arch forums's desk. Gotta find all this graphs and stuff out :D

holy poop! that's impressive.

---

### Post by shearn89 on 2008-03-10
i've got the graphs and stuff working - you need lm_sensors installed (the arch name, not sure about the ubuntu repos version). Does anyone know how to align all the boxes to the right? at the mo, i just have a massive spacer... not so good.

---

### Post by emmerp on 2008-03-13
Currently trying out dwm and awesome. 
I notice that in dwm as well as in awesome my GTK looks 'old', like the old grey GTK1 stuff in stead of the bright light grey I have in Ubuntu. Are more people having this and is there a way to overcome this?

Here's a link with a firefox which shows what I mean (not my desktop though...): [http://www.xs4all.nl/~hustinxp/screenshots/bolan/bolan.full.png](http://www.xs4all.nl/~hustinxp/screenshots/bolan/bolan.full.png)

---

### Post by shearn89 on 2008-03-13
you probs don't have the gnome-settings daemon running. Either specify the gtk2 theme in your .gtkrc.mine file (i think its called that), or add gnome-settings-daemon to your autostart.

---

### Post by emmerp on 2008-03-18
Another thing... I ran into the problem that network things are woven into gnome which makes using dwm a bit hard. For example, I removed NetworkManager since this wasn't bringing my wireless up when I didn't logged into gnome but into dwm. My wireless works now (just by running dhclient3 in rc.local). But, I have a VPN connection setup in NetworkManager, which I cannot enable now. I could try to add this connection manually in /etc/ppp but last time I tried this it did not work, I'm happy it finally works with this easy to manage GUI setup (also regarding enabling/disabling VPN). So basicly, is there a way to get NetworkManager running in dwm? Or how did you guys configured your network without the NetworkManager?

---

### Post by shearn89 on 2008-03-19
You can run NetworkManager - although, i'm not sure that dwm has a tray. You may have to run something like visibility. 
NetworkManager is actually just a front-end for all the text files anyway, so if you have the time i'd just mess around with scripting etc. Check the forums for links about vpn via /etc/ppp, and see if you can work through it. My wireless setup is all scripted now, so I'm not sure about a GUI for network in dwm...

---

### Post by chucky chuckaluck on 2008-03-21
i've pretty much given up all other wm's for wmii. my only real problem with it comes when i use my laptop after mrs. chuckaluck has gotten a hold of it. she doesn't care about this stuff and the concept of a tiling window manager is completely unknown to her. when she gets done using it, my screen looks like a psychotic five year old has been messing with it. i'd teach her about it, but she works hard and has enough on her mind.

---

### Post by emmerp on 2008-03-24
> **shearn89 said:**
> You can run NetworkManager - although, i'm not sure that dwm has a tray. You may have to run something like visibility. 
NetworkManager is actually just a front-end for all the text files anyway, so if you have the time i'd just mess around with scripting etc. Check the forums for links about vpn via /etc/ppp, and see if you can work through it. My wireless setup is all scripted now, so I'm not sure about a GUI for network in dwm...

With tray software 'trayer' and NetworkManager installed I got it working now. trayer starts at tags[8] so only when I need to start VPN or do some other settings, I've a nice GUI which takes care of this, which doesn't get in the way when I don't need it.

---

### Post by Mateo on 2008-04-01
bumping up this thread dedicated to 3 awesome (pun intended) windows managers.

i love wmii with the exception of 1 thing; the tendancy for it to crash.  anyone else have this experience?

---

### Post by shearn89 on 2008-04-11
I'm an awesome user - hasn't crashed on me yet! it does have a tendency not to warn you about syntax error in the rc file, which leaves you with the default config....*shudder*

---

### Post by shearn89 on 2008-04-29
Just been setting up the hotkeys on my laptop and found [this post]("http://wiki.archlinux.org/index.php/Hotkeys#Running_applications_in_X") over at the Arch Wiki. Could be useful for anyone setting up?

---

### Post by adlaiff6 on 2008-05-09
Has anyone got any idea when they will put one of the later versions (2.2, 2.3, dare I suggest 3.0?) in the repos?

Alternatively, if anyone has a good link describing the differences between 2.0 and 2.3 configs (or a page with good 2.0 configs), that would also be appreciated.

---

### Post by emmerp on 2008-05-21
Anyone experience with running java gui programs in dwm?
I try to run squirrel, but I only get a large blank screen, without menu or other gui options. In gnome it works fine, so it's related to the layout dwm sets...starting it in floating layout does not solve the problem, is there another way to start it?

---

### Post by mali2297 on 2008-05-21
> **adlaiff6 said:**
> Has anyone got any idea when they will put one of the later versions (2.2, 2.3, dare I suggest 3.0?) in the repos?

There won't be any updates until the next release of Ubuntu in October.

> 
Alternatively, if anyone has a good link describing the differences between 2.0 and 2.3 configs (or a page with good 2.0 configs), that would also be appreciated.

Don't know. There is an example file included in the package. Copy and extract **/usr/share/doc/awesome/examples/awesomerc.gz** to your home directory.

---

### Post by emmerp on 2008-05-27
Added to my previous post: with running Eclipse, the 'Open Resource' dialog window (Ctrl-Shift-R) gets maximized, while I just want it to be floating, as the Eclipse Find dialog is. I just tried ion, awesome, wmii, different versions of dwm, but they all have the same problem. It does not matter which layout mode I'm in (tiled, monocle, etc..)
I know java programs are a known issue, but has anyone a solution for this?

---

### Post by emmerp on 2008-05-28
Shame on me....:S Turns out the window I thougth dwm was maximizing was just that big because I resized it once... found this out when in gnome it was the same size ](*,)

---

### Post by Nythain on 2008-06-09
does awesome 3 git still accept the old style awesomerc by chance, because i dotn know if ill ever get this whole lua thing down pat, and i really cant figure out why wicked and eminent are causing me wicked issues

---

### Post by shearn89 on 2008-06-09
> **Nythain said:**
> does awesome 3 git still accept the old style awesomerc by chance, because i dotn know if ill ever get this whole lua thing down pat, and i really cant figure out why wicked and eminent are causing me wicked issues

Given the way that the awesomerc breaks every time they update it, i wouldn't think so. However, i've been travelling for 5 weeks without my laptop, and i'll get home on wednesday morning (about 9 GMT), so i'll check then.
Lua? Wicked? Eminent?

---

### Post by Thanoulis on 2008-06-10
I use a custom made patched version of dwm, based on 4.9 version with Grid+Fibonacci layout support, different border colors in floating/tiled windows, push options and anything else i could find and work with it.
So, here you are:

---

### Post by kaiju on 2008-06-11
> **Nythain said:**
> does awesome 3 git still accept the old style awesomerc?

nope.
after a few days of getting used to and tweaking awesome 2.3.1, i tried awesome 3 from git yesterday. while imho it looks, feels & behaves much much better, and it seems to have tons of features added, it also totally kicked the rc file syntax, as it now uses lua. you can read up on all that on [jd's blog]("http://julien.danjou.info/blog/index.php/post/2008/05/20/awesome-3%3A-Lua-integration").

---

### Post by shearn89 on 2008-06-11
dammit. What's the likelihood of it sticking after 3 though? If they've moved to a whole scripting language, its likely to make sure that the syntax stays the same for future versions right?

---

### Post by Nythain on 2008-06-11
yeah, thats what i was affraid of... on one hand, im pleased at the decision to implement lua, it unlocks a near infinate amount of possibilities... but on the other hand, im not a programmer, and between xmonad and now awesome, im getting tired of the requirement to be a damn programmer just to get a window manager to work... hopefully when i get around to reformatting i can still find 2.1 on the web, as i really dont even have a desire to try out 2.3.1 and im definately never switchign completely over to 3

---

### Post by shearn89 on 2008-06-11
Or switch back to something like wmii or dwm - i'm sure you could get virtually the same functionality without the need for the ridiculous rc changes everytime...

---

### Post by kaiju on 2008-06-11
speaking of dwm and wmii...

the recompile-to-set-up approach of dwm seems too big a chunk of hackerdom for me. besides, from my googling around it doesn't seem to be overly extensible.

wmii sure smells like genius, so much so that i got intimidated by it the couple times i tried to test it. and here too, it seems one needs to know 'foreign languages' for the setup...

awesome 2.3.1 was not overly awesome, but version 3 sure is. too bad i won't have time for lua anytime soon.

...so unless i find a very detailed how-to for any of the above, i guess i'm just sticking with good old evilwm (+xbindkeys +dmenu) for a while :)

---

### Post by Nythain on 2008-06-11
yeah, the recompile to configure approach really turned me off of dwm, and its sad to hear ill need a same level of language knowledge to customize wmii, that was my next step :(

---

### Post by kaiju on 2008-06-12
> **Nythain said:**
> [...]its sad to hear ill need a same level of language knowledge to customize wmii, that was my next step :(

it seems though that you can use many different languages to tweak wmii. ruby is what i've seen, but i'd guess there are much more options. then again, that might not be overly exciting if, like me, you have zero knowledge of programming languages :p

---

### Post by shearn89 on 2008-06-16
does anyone know which deps I need for awesome (from the git repo)? my makepkg keeps sticking at cairo-xcb...

---

### Post by kaiju on 2008-06-16
> **shearn89 said:**
> does anyone know which deps I need for awesome (from the git repo)? my makepkg keeps sticking at cairo-xcb...

the arch pkgbuild file for awesome git lists the following dependencies:
lua dbus cairo-xcb gtk2 asciidoc xmlto docbook-xsl git autoconf automake pkgconfig

cairo-xcb might be conflicting with cairo, which in turn is needed by many apps. on arch, i had to compile that one from source, too, as it wasn't in the repos.

---

### Post by shearn89 on 2008-06-17
ahhh... thats probs it. I'll check the AUR for cairo-xcb.

---

### Post by kaiju on 2008-06-18
> **shearn89 said:**
> ahhh... thats probs it. I'll check the AUR for cairo-xcb.

on arch, you could use yaourt. it gets dependencies from the aur too. you can get it from the archlinux.fr repo or build it from the aur.

---

### Post by Nythain on 2008-06-24
so, being totally new to awesome still, are there any good guides on key names, like at the immediate moment im wanting to set up mod 4 + prtscr to execute a screenshot script i have, but i dont what prtscr would be called... took me eternity to figure out F2 needed to be F2 and not f2 to begin with

---

### Post by mali2297 on 2008-06-24
> **Nythain said:**
> so, being totally new to awesome still, are there any good guides on key names, like at the immediate moment im wanting to set up mod 4 + prtscr to execute a screenshot script i have, but i dont what prtscr would be called... took me eternity to figure out F2 needed to be F2 and not f2 to begin with

Use **xev**. 

If I press PrtSc, I see
```

KeyPress event, serial 34, synthetic NO, window 0x1e00001,
    root 0x60, subw 0x1e00002, time 130408002, (41,48), root:(382,290),
    state 0x0, keycode 111 (keysym 0xff61, [color=red]Print[/color]), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
Hence, the key name is *Print*.

---

### Post by Nythain on 2008-06-24
thanks, wasnt sure if awesome used the xev keyname or if it had its own names for the keys... guess ill give it a whirl

---

### Post by urukrama on 2008-07-06
I just installed awesome 2.3 (from source on a Hardy system). The statusbar is hardly visible, though, and is only about 1 pixel high. I tried changing the font (both type and size), but that didn't have any effect. I don't see any settings for height in the config file either.

My awesomerc is [here]("http://pastebin.com/md17bdce") (it is only slightly modified from the [default]("http://awesome.naquadah.org/wiki/index.php/Default_2.3_Theme")):

A screenshot is attached.

I used similar settings in the repos version (2.0), where the statusbar showed properly.

**EDIT:** Solved it. Apparently you can no longer set the font as "Fixed-8" but you need to use "Fixed 8" now.

---

### Post by shearn89 on 2008-07-06
yeah - its configured to use all fonts, so things like handelgotdlig work now. I haven't managed to build awesome 3 yet though, i kept running across errors when compiling. Although given the fact that the config file has completely changed, i'll stick with 2.3 for a while.

---

### Post by urukrama on 2008-07-06
**@ shearn**: I hope the developers will settle on a configuration file syntax soon!

Is there a way to remove the icons from the task list? Some applications display icons there before the window's name (like gedit), but others don't (Opera, urxvt).

---

### Post by mali2297 on 2008-07-06
> **urukrama said:**
> 
Is there a way to remove the icons from the task list? Some applications display icons there before the window's name (like gedit), but others don't (Opera, urxvt).

Yes, use the option *show_icons* in the tasklist section.
```

tasklist mytasklist {
 show_icons = false
 ...
}

```

---

### Post by urukrama on 2008-07-06
Thank you.

---

### Post by rjmdomingo2003 on 2008-07-06
@uru - About putting Remind in the statusbar, here's the relevant part of my awesome monitor (and a screenshot). Am still on Awesome v 2.1.

```
echo 0 widget_tell clock "`date   '+%a  %b %d %Y  %H:%M'`     `remind '-kecho %s'`      " | /usr/local/bin/awesome-client
```

---

### Post by urukrama on 2008-07-07
> **rjmdomingo2003 said:**
> @uru - About putting Remind in the statusbar, here's the relevant part of my awesome monitor (and a screenshot). Am still on Awesome v 2.1.

```
echo 0 widget_tell clock "`date   '+%a  %b %d %Y  %H:%M'`     `remind '-kecho %s'`      " | /usr/local/bin/awesome-client
```

Thank you. I ended up using a slightly different method, though (or so I think). I posted the result in [the Desktop thread]("http://ubuntuforums.org/showthread.php?p=5331801#post5331801"). Since I posted that screenshot, I've made some minor adjustments, but I'm rather happy the way it looks.

Awesome is pretty good, I admit. I'm having fun with it, and am starting to learn how to work with it (rather than just play with it) :-)

---

### Post by rjmdomingo2003 on 2008-07-07
> **urukrama said:**
> Thank you. I ended up using a slightly different method, though (or so I think). I posted the result in [the Desktop thread]("http://ubuntuforums.org/showthread.php?p=5331801#post5331801"). Since I posted that screenshot, I've made some minor adjustments, but I'm rather happy the way it looks.

Awesome is pretty good, I admit. I'm having fun with it, and am starting to learn how to work with it (rather than just play with it) :-)
Nice setup! And yeah, Awesome rocks! Been using it for 6 months now (after recovering from my fluxbox addiction).

I like it the way it can incorporate system stats into the.. erm.. statbar, making for a desktop less cluttered. Still strugling with dzen though.

Looking forward to your blog on Awesome. Cheers!

---

### Post by urukrama on 2008-07-07
I created a dzen script to show the reminders for the coming 4 weeks when I click on the remind in my statusbar (with today's reminder(s) highlighted). See the attached screenshot.

I'm very happy with it :D I'll post it on my blog soon.

---

### Post by rjmdomingo2003 on 2008-07-08
> **urukrama said:**
> I created a dzen script to show the reminders for the coming 4 weeks when I click on the remind in my statusbar (with today's reminder(s) highlighted). See the attached screenshot.

I'm very happy with it :D I'll post it on my blog soon.
Nice! :KS

You should post the script in the dzen website.

---

### Post by urukrama on 2008-07-08
> **rjmdomingo2003 said:**
> You should post the script in the dzen website.

I will, but I had problems registering to the wiki. I contacted the admin, so hopefully it will work out.

Is it possible to assign two or more tags to an application in the rules section, so that it is show in both tags? I assumed it was, since the option is plural ("tags"), but haven't been able to do so.

I tried adding more than one tag name (as tags = "one,two" and as tags = { "one", "two" }), as well as to add an additional rule with the second tag I want it to appear, but it either didn't work or broke my configuration file syntax.

---

### Post by rjmdomingo2003 on 2008-07-09
> **urukrama said:**
> I will, but I had problems registering to the wiki. I contacted the admin, so hopefully it will work out.

Is it possible to assign two or more tags to an application in the rules section, so that it is show in both tags? I assumed it was, since the option is plural ("tags"), but haven't been able to do so.

I tried adding more than one tag name (as tags = "one,two" and as tags = { "one", "two" }), as well as to add an additional rule with the second tag I want it to appear, but it either didn't work or broke my configuration file syntax.
Dunno. I haven't tried that yet. Maybe it's as simple as a syntax thing. 

You can check with Gigamo, he's an expert with Awesome.

---

### Post by urukrama on 2008-07-09
> **urukrama said:**
> Is it possible to assign two or more tags to an application in the rules section, so that it is show in both tags? I assumed it was, since the option is plural ("tags"), but haven't been able to do so.

I found the solution on Awesome's IRC channel. You need the following syntax:

```
rule { name = "thunar"		tags = "one|five"	float = "true" }
```

---

### Post by shearn89 on 2008-07-09
thats going to be damn useful when i eventually get round to buying a second monitor. Although i'm not sure if you can assign something to always open on one particular screen...

---

### Post by urukrama on 2008-07-09
> **shearn89 said:**
> thats going to be damn useful when i eventually get round to buying a second monitor. Although i'm not sure if you can assign something to always open on one particular screen...

Since the "tags" are part of the "screen" configuration, but the "rules" are not, I suppose you should be able to create tags unique to that screen, and use rules to make certain apps to show in them.

---

### Post by rjmdomingo2003 on 2008-07-10
> **urukrama said:**
> I found the solution on Awesome's IRC channel. You need the following syntax:

```
rule { name = "thunar"		tags = "one|five"	float = "true" }
```
As simple as that?! Nice!

I was thinking "why put a rule for an app?" You can forego assigning a rule (for tags) and go to each tag launching an instance of the app. Was that clear? Though it would be tedious to do.

But hey, thanks for this heads-up!

---

### Post by rjmdomingo2003 on 2008-07-10
> **urukrama said:**
> I found the solution on Awesome's IRC channel. You need the following syntax:

```
rule { name = "thunar"		tags = "one|five"	float = "true" }
```
That simple?! Wow, that's nice! Thanks! :KS

---

### Post by urukrama on 2008-07-10
> **rjmdomingo2003 said:**
> I was thinking "why put a rule for an app?" You can forego assigning a rule (for tags) and go to each tag launching an instance of the app. Was that clear? Though it would be tedious to do.

I've assigned rules for a number of apps, and I'm starting to see the great benefit from it (as well as some of its downsides). I find it handy for apps like thunar to appear on different tags, so I don't need to launch more than one instance of it or move the window around tags all the time.

If I want to move an app to a different tag, I've configured it such that if I middle click on a tag name, the currently selected window will be moved to that tag. Pretty handy. 

(You can also use the tag_view action to view all the running applications in a single tag; click on a tag name, and all is back to normal)

BTW, the method I posted earlier can also be used if you want to perform more than one action with one keybinding. Thus I have the following to change the song in mpd and display "Next" with osdctl:

```
key { modkey = {"Mod1", "Control"}  key = "Next"  command = "spawn"  arg = "exec mpc next|osdctl -s 'next'" }
```

---

### Post by urukrama on 2008-07-10
> **rjmdomingo2003 said:**
> Looking forward to your blog on Awesome. Cheers!

I was planning to post only my dzen remind script, but now [see what you made me do]("http://urukrama.wordpress.com/2008/07/10/first-steps-with-awesome-window-manager/")! :p

I've posted the remind script on the [dzen wiki]("http://dzen.geekmode.org/dwiki/doku.php?id=dzen:remind"). 

I'm very happy with this script. Unfortunately, though, dzen automatically scrolls down to the bottom, so if you have a lot of reminders, you'll have to scroll back up to see the today's ones. Perhaps that could be remedied if you tell it to display only one week instead of four (replace *remind -s+4* with *remind -s+1* in the script). I couldn't find any dzen option that prevents it from scrolling down automatically to display the last line of text (which kind of makes sense, I suppose).

---

### Post by shearn89 on 2008-07-11
nice guide! thanks for the shout out as well. I should really update my guide, as i've seen it posted on a couple of other blogs as well. I'll try and do some over the weekend...

I plan to try and get awesome 3 compiled and sorted sometime over the summer as well, so i may write a guide for that as well.

---

### Post by gotmor on 2008-07-11
Hi.

> **urukrama said:**
> 
I'm very happy with this script. Unfortunately, though, dzen automatically scrolls down to the bottom, so if you have a lot of reminders, you'll have to scroll back up to see the today's ones. Perhaps that could be remedied if you tell it to display only one week instead of four (replace *remind -s+4* with *remind -s+1* in the script). I couldn't find any dzen option that prevents it from scrolling down automatically to display the last line of text (which kind of makes sense, I suppose).

There is an action called "scrollhome" that will simply scroll to the beginning of the input.

You could use it like:

dzen2 -e 'onstart=scrollhome;OTHER_EVENTS_AND_ACTIONS'

or bind it to a key or something...

See [here]("http://dzen.geekmode.org/dwiki/doku.php?id=dzen:option-e") for further details.

Bye, Rob.

---

### Post by urukrama on 2008-07-11
> **shearn89 said:**
> nice guide! thanks for the shout out as well. I should really update my guide, as i've seen it posted on a couple of other blogs as well. I'll try and do some over the weekend...

What helped me there was not so much the technical info on how to fill in the syntax file, but more the general overview you wrote of Awesome's different components (tags, etc.).

> **gotmor said:**
> There is an action called "scrollhome" that will simply scroll to the beginning of the input.

Thank you very much! I read that page you linked to while I wrote the script, but I missed that action somehow.

---

### Post by rjmdomingo2003 on 2008-07-12
> **urukrama said:**
> I was planning to post only my dzen remind script, but now [see what you made me do]("http://urukrama.wordpress.com/2008/07/10/first-steps-with-awesome-window-manager/")! :p

I've posted the remind script on the [dzen wiki]("http://dzen.geekmode.org/dwiki/doku.php?id=dzen:remind"). 


I knew you couldn't resist adding this to your blog.;)

I've actually thought of ideas which are variations of your ideas. I'll post them on the monthly desktop threads as soon as I finish.

EDIT: Got my Remind widget to show the current time & calendar after clicking. Also got my right-click menu! Yay!!

On my calendar:

1. How do you align the numbers? They seem to align to the center.
2. Do the artwiz fonts only apply? How do I use the other fonts?

Thanks, mighty uru!

---

### Post by rjmdomingo2003 on 2008-07-12
> **shearn89 said:**
> nice guide! thanks for the shout out as well. I should really update my guide, as i've seen it posted on a couple of other blogs as well. I'll try and do some over the weekend...

I plan to try and get awesome 3 compiled and sorted sometime over the summer as well, so i may write a guide for that as well.
Man, I'm looking forward to this. Still on Awesome 2.1.

---

### Post by shearn89 on 2008-07-12
yeah, i've been getting epic compiling issues with awesome-git. Once i've finally worked through them, i'll get working on understanding lua, and then onto a guide. I think it may end up as a basic "how to write an awesome3 rc file", but that should still prove useful...

---

### Post by shearn89 on 2008-07-15
I found a thread on the arch forums where someone posted a repo with arch pkgs for awesome-git and the dependencies, so i have it up and running! Configuration is somewhat tricky - i have my tags set up, but atm I can't get my quicklaunch keyboard shortcuts to work... Once i've worked it all out, i'll post a bit here on writing the config file, and then maybe redo the howto with 2 sections - awesome 2.3, and awesome 3.

---

