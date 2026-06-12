---
title: "Triple Monitor in Ubuntu. Help me help you!"
date: 2011-04-20
forum: Desktop Environments
---

### Post by MisteR2 on 2011-04-20
So... I've been playing around with a triple monitor system. Haven't found a way to get it work perfectly, but it's close. After bouncing around to different threads and seeing how people deal with different issues (portrait monitors, dual monitors with one being portrait, twinview and xrandr playing nicely, etc.).

Before I get started, I'm running two X screens on my server. 0 being my twinview setup and 1 being my portrait monitor.

Started with metacity controlling everything (starting it by terminal, didn't switch settings in gdm), then ran "compiz --replace --only-current-screen" which puts screen0 under compiz control while leaving screen1 under metacity control.

Although I need to walk that back a bit. I did add a line in /etc/gdm/Init/Default to have xrandr rotate screen1 on start.

As it stands it's possible to switch twinview between two and one monitors through nvidia-settings without it messing with the compiz/metacity combo. But if anything happens (such as effect detail changing) compiz takes over completely, which leads to screen1 being corrupted, since compiz appears to have issues with portrait monitors.

As much as I love my effects, that's not the reason I wanted compiz to be in control of screen1. Anyone that's played with triple monitors on nvidia chipsets notices that twinview display geometry gets nuked when there's more than one screen. 

Compiz provides a workaround under General options > Display settings > Outputs. Examine the modeline for your setup with twinview activated and place the monitors in there in that fashion. For example 1440x900+0+0 for my main and 1680x1050+0+900 for my secondary monitor (which sits below main) in my twinview screen. Compiz will now limit your windows (not your bars from what I've seen) to those monitors now.

:guitar:

So, anyone out there with triple monitors on an nvidia set may be able to use this. Whether it works for ATI, dunno. But it seems to be a nice workaround right now.

Here's where I'm getting hung up though. I'm considering just making a script that runs after login to switch everything to metacity and then lay compiz over screen0. Seems to be the easiest way of going about this. But what I'd love to do is the opposite of this so I don't have to worry about compiz not loading plugins (seems to not pull from gconf for plugins when started from the commandline). Or if there's even a cleaner way of doing this, post it! :P

Quick update:
Compiz has no problem in the portrait monitor when started similar to the twinview screen (--only-current-screen option). Had wobble effects and whatnot. Seems the issue begins when Compiz on screen 0 gets restarted and tries to take everything over. Then it distorts and freezes. Progress?

Another update:

It seems to work now. Added a quick script to the startup processes that waits for two seconds before running the command to switch screen0 to compiz. Which gives metacity enough time to get up on screen1. Here's the script. Enjoy!

> #!/bin/sh
sleep 2
exec compiz --replace --only-current-screen --sm-disable

---

### Post by MisteR2 on 2011-04-22
Looks like it's possible to have compiz on both screens at the same time with one being rotated portrait. I added sections to direct the starting of compiz at the individual screens instead of session-wide.

> #!/bin/sh
sleep 2
DISPLAY=:0.0 compiz --replace --only-current-screen --sm-disable &
DISPLAY=:0.1 compiz --replace --only-current-screen --sm-disable &


I still have metacity starting as default to prevent anything super funky going on. 

There is an issue with focus between the screens. Sometimes the cursor will get stuck on one screen. Even if you highlight a program window in the other screen, the cursor will stay there and typing focus will remain. The only way I've been able to break it semi-reliably is to open a gnome terminal window in screen0 and start typing in there to bring focus over.

---

### Post by Krytarik on 2011-04-22
> **MisteR2 said:**
> 
There is an issue with focus between the screens. Sometimes the cursor will get stuck on one screen. Even if you highlight a program window in the other screen, the cursor will stay there and typing focus will remain. The only way I've been able to break it semi-reliably is to open a gnome terminal window in screen0 and start typing in there to bring focus over.
That is really ugly! How about running it this way instead?:
```
#!/bin/sh
sleep 2
compiz --replace --display :0.0 --sm-disable &
compiz --replace --display :0.1 --sm-disable &
```And how about placing your script into "/usr/local/bin", for example, and set it as the window manager in Gconf, thus avoiding loading two window managers after each other at login? Then, of course, remove the "sleep" command in your script.
```
gconftool-2 /desktop/gnome/session/required_components/windowmanager --type string --set /usr/local/bin/compiz-custom
gconftool-2 /desktop/gnome/applications/window_manager/current --type string --set /usr/local/bin/compiz-custom
gconftool-2 /desktop/gnome/applications/window_manager/default --type string --set /usr/local/bin/compiz-custom
```The values for Metacity are "metacity" and "/usr/bin/metacity" respectively.

---

### Post by MisteR2 on 2011-04-22
Tried out your suggestions. Placing the script in /usr/local/bin makes things neater (less clutter in the home folder :P). Set the script to run from gconf-editor. Logged in and logged out, works fine. 

Only things I changed as far as the content of the script is to nuke the --sm-disable option from the both lines (without too much issue), and the removal of the sleep line. Defining the screen within the compiz command line options led to it still taking over both screens, leaving my portrait monitor garbled. 

On the upside, now I can double-click on the desktop I want to work in and it moves focus to that screen, not the greatest workaround, but better than it was earlier.

Thanks for your suggestions and help!

---

### Post by Krytarik on 2011-04-22
> **MisteR2 said:**
> 
On the upside, now I can double-click on the desktop I want to work in and it moves focus to that screen, not the greatest workaround, but better than it was earlier.
With the commands I suggested and the garbled portrait monitor?
Or with your earlier commands, minus "--sm-disable", and run through Gconf?

---

### Post by MisteR2 on 2011-04-22
Sorry for the confusion. The script looks like this now.

```
#!/bin/sh
DISPLAY=:0.0 compiz --replace --only-current-screen &
DISPLAY=:0.1 compiz --replace --only-current-screen &
```

When I tried your lines, which had the target screen defined in compiz's options it gave me a garbled portrait monitor. (possibly instances fighting again?) Defining the target screen outside of the compiz options leaves me with working screens with the "double click to focus" thing going on.

---

### Post by Krytarik on 2011-04-22
> **MisteR2 said:**
> Defining the target screen outside of the compiz options leaves me with working screens with the "double click to focus" thing going on.
Then that behaviour didn't change at all from before, only that you figured now how to better work around those issue?

---

### Post by MisteR2 on 2011-04-22
That's right. The --sm-disable option must have been playing havoc behind the scenes. And having both screens with the option doesn't fly. Not to say that double clicking on the desktop to focus flies well either, but I'm not having to open a terminal on each screen just to move focus. :)

I was looking at some of the command line options for compiz, and there was an option to give compiz a session management client ID. (--sm-client-id) I haven't tried playing with it yet because I haven't found or seen anything that lets you "link" instances of compiz together through that.

---

### Post by Krytarik on 2011-04-22
I just yet noticed that (at least) the manpage of 'compiz' for 10.10 is different from those for 10.04, which I have followed, the latter doesn't even mention the option "--only-current-screen".

So, following the manpage for 10.10, the previously suggested command structure would be rather like this:```

#!/bin/sh
compiz --replace --display :0.0 --only-current-screen &
compiz --replace --display :0.1 --only-current-screen &
```However, I don't expect that the result is different from what you have now.

After a quick web search, I didn't find anything really helpful about the option "--sm-client-id" so far.

---

### Post by MisteR2 on 2011-04-22
Yeah, no change in operation with those lines substituted. It didn't garble up the portrait monitor though. So it's something with one compiz instance running things on both screens. I've having to dig back into my memory now, but I've dealt with something similar to this with a HP TX2500Z tablet. 

Rotation wasn't working properly on it and I asked around for some help with getting it taken care of. As far as the physical switch issues, those were resolved, but if I remember correctly, whenever the tablet was switched (landscape -> portrait) compiz had to be shut down and metacity put in it's place. Maybe this is an extension of that issue where compiz doesn't like being rotated or managing two screens at the same time where one is rotated.

I didn't find anything on the --sm-client-id option either.

---

### Post by MisteR2 on 2011-04-23
Started using the triple monitor setup some more today (normally have 2 monitors off unless showing reference). Blender and The Gimp seem to get stuck within monitors in the twinview screen. Both were stuck on the 1680x1050 monitor and wouldn't move to the 1440x900 up top. Had to restart the program to allow it to move again, only to get locked in if I moved it a couple more times.

No workaround for that one yet. :P

---

### Post by MisteR2 on 2011-04-29
Recently upgraded to 11.04. Screen setup (sort of) nuked. Thanks to foyb over here > [http://ubuntuforums.org/showthread.php?t=1689514]("http://ubuntuforums.org/showthread.php?t=1689514") I've got my portrait monitor back in proper orientation. 

XRandR doesn't want to save the modelines I use for this. So for now I'm going to place the lines into a script and put it in /usr/local/bin until I get this sorted again.

---

### Post by Krytarik on 2011-04-29
> **MisteR2 said:**
> 
XRandR doesn't want to save the modelines I use for this. So for now I'm going to place the lines into a script and put it in /usr/local/bin until I get this sorted again.
Those are always ad-hoc commands, so you need to add them to GDM's startup script as well, just like you did with the rotate option before:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts)

---

### Post by MisteR2 on 2011-04-30
Thanks for the heads up on that. I have a line in the init script for gdm pointing to a script in /usr/local/bin. Seems better than mucking around in there and blowing something up. :P

As far as window management goes for the portrait monitor, mutter goes over there at boot to a certain extent. Can't place any launchers over there, they just shoot over to the main desktop for Unity. So I've got Avant Window Navigator running things on my portrait display and things seem to be stable right now.

---

### Post by Krytarik on 2011-04-30
You don't really mean Mutter, I guess, since Natty's Unity is handled by Compiz, too. What specifically are you meaning?

As for the launchers, it seems to be a common issue when running multiple xscreens/workspaces. No more focus issues then?

Yeah, I, too, am using AWN, with my single screen. It's a really great replacement for *all* panels/launchers. :D

---

### Post by MisteR2 on 2011-04-30
<badinfo> I need to dig the link back up, but from what I read windowing duties are handled by mutter. Mutter even shows up in the process list. :/ </badinfo>

Anyways, Unity and X-head still needs some love. Running the third monitor now (the twinview setup) and windows maximize after setting compiz up to ignore detected monitors and go with what I tell it to go with. 

Maximized windows on the lower screen still use the main panel for menu, so moving from lower screen to top screen for menu actions has to happen for now. Side panel stretches from top screen to bottom screen. Also the panel stretches into non-viewable area, so logout is now on the AWN panel. 

And the focus issue: Gone!

:popcorn:

---

### Post by MisteR2 on 2011-05-10
What?!? Five hundred some-odd views and nobody else has anything to say?? :P

Well, instead of just bumping this up, there is an issue I've run into. The wacom driver doesn't like negative values, which is necessary for me due to the vertical orientation of the twinview screen. It takes the values just fine from xsetwacom, but doesn't like it being set in 50-wacom.conf.

---

