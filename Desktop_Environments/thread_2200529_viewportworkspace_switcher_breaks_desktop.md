---
title: "viewport/workspace switcher breaks desktop"
date: 2014-01-19
forum: Desktop Environments
---

### Post by Luxx on 2014-01-19
I have become accustomed to using 4 workspaces. I can have a design project open in one, research in one, website stuff in one, and one just for documentation. It's quite helpful when working on website design.

For some reason it suddenly no longer works. When I click on any of the 4 showing workspace icons other than the first one, the screen goes black and I have an arrow cursor, but can't do anything. I have to shut down the computer and turn it back on from the power button in order to get function back. I have tried everything I can think of to fix the problem, but nothing seems to work. 

Yesterday I reinstalled Nautilus because it hadn't been my default file manager for a while and there was a conflict with nautilus-dropbox. I have used the workspaces quite a bit since I resolved that, though, so I'm confused as to why it suddenly broke total functionality trying to go to another workspace when I had been doing that for hours. 

I noticed the icons had moved over on the bottom panel just a bit beyond the edge of the screen and I tried to reconfigure the preferences so I could see them. This happened in the middle of the workday while uploading web pages via FTP. Changing the workspace icons on the bottom panel and then putting them back the way they were seemed to work as far as putting them back inside the screen where I can see them, but now trying to use other workspaces is disaster.

Any help to get my workspace switcher working again would be greatly appreciated.

I have been using compiz, not metacity, if that helps.

(UNSOLVED -- After switching to Gnome 3 with Tweak Tools plugins I am getting sudden restarts. I think it is related. I am suspecting Xorg issue.)

---

### Post by Luxx on 2014-01-20
Very strange. Ok, so I forgot I had installed some kind of tweak tool to fix my clock so it would show the date in panel along with the time. I removed this and I got a different behavior, although things weren't fixed. Now after removing the teak tool the panels bahaved strangely. If I tried to click on anything in either the top or bottom panel it would switch windows. Apps would not launch, workspaces wouldn't switch, but a different window would come to the front whenever I clicked on anything in the panels.

I uninstalled & purged Compiz & installed Metacity. Same issues.

I finally fixed the problems and I don't know why this fixed it or why I thought of trying it. I opened Software Center and typed Unity in the search and found there were some lingering programs related to Unity that had been left installed after I uninstalled it. I'm using Gnome, gnome-session 3.9.90, according to terminal, but gnome-session-flashback 1:3.6.2-0ubuntu15 aka Window Manager in Software Center. So I uninstalled everything Unity and purged Untiy in terminal. Now everything is normal.

---

### Post by grahammechanical on 2014-01-20
Ubuntu + Unity does not have top and bottom panels. Please explain what you installed to get top and bottom panels? Gnome-session-flashback? How did you change the default from one workspace to 4?

I ask because it is relevant. I have installed gnome-session-flashback on Trusty Tahr as an experiment and I found that if we run Gnome Flashback (with Compiz) and then increase the number of workspaces by clicking the workspace icon on the bottom panel and selecting Preferences and increasing the number of workspaces from the dialog box that appears, then we lose both the top and bottom panels.

A better way to do it is to install Compiz Configuration Settings Manager (CCSM) and open General Options>Desktop Size and set the number of workspaces from the panel "Number of Workspaces." Make sure that the Horizontal Virtual Size is set to 1 and the Vertical Virtual Size is blank.

That should work also in 13.10

Regards.

---

### Post by Luxx on 2014-01-20
Yes, I uninstalled Unity and tried several configurations of desktop environments before I settled on Gnome with Window Manager (gnome-session-flashback 1:3.6.2-0ubuntu15). I was actually trying to move away from that, but it turned out to be the only thing aside from Unity that worked with my socket FM2 APU architecture without considerable tearing. Well, there was Fluxbox, but that's another story.

Compiz Configuration Settings Manager was already installed, and your "better way of doing it" didn't do anything at all. Of course I tried CCSM first. I have had this kind of issue before and used CCSM to fix it. This time it didn't fix it. The Viewport Switcher, under Desktop, was actually disabled. The Desktop Size settings in General, General Options never had a value in Number of Desktops. I don't think that setting has had any significance since Hardy.

I reinstalled Compiz just a little while ago after realizing I could no longer resize windows. It's working fine, and I'm thinking purging the last lingering bits of Unity allowed Compiz to work properly with gnome-session-flashback. 

As far as I am aware, default number of workspaces has always been 4 in Ubuntu, but should go up to 12. 
The Workspace Switcher Preferences settings (right-click on the workspace icons, click Preferences to open Workspace Switcher Preferences) are:
Show all workspaces in: 2 rows; Number of workspaces: 4 

I hope you figure out a working solution in Trusty Tahr. Compiz has always seemed to bring up little bugs, but I'm never sure if the bugs are actually in Compiz. There is often an alternate DE involved when they do.

The most likely culprits in my case seemed to be Tweak Tool and Unity leftovers.

---

### Post by stinkeye on 2014-01-20
My experience is the same as **grahammechanical's**.
Using the settings shown in pic is what works for me.
The number of workspaces shown in the panel should change dynamically as you change
the ccsm setting.

Are you sure your still running compiz?
Install wmctrl (80kb) to check your current window manager.
```
sudo apt-get install wmctrl
```

Verify your session and window manager with this terminal command...
```
echo $DESKTOP_SESSION && wmctrl -m | head -n1
```
eg...
```
[COLOR="#008000"]glen@Saucy:~$[/COLOR] **echo $DESKTOP_SESSION && wmctrl -m | head -n1**
gnome-fallback-compiz
Name: Compiz
```

---

### Post by Luxx on 2014-01-20
Wait... are you guys reading the first post? I had a normally working set-up and then it suddenly broke.
 
When I tried to switch workstations I got a black screen with a cursor arrow and NO DESKTOP. Keystrokes did not work. I couldn't do anything but reboot by the power button. I had not changed any settings in Compiz before it broke.

Are you saying your experience was the same, you got the black screen, and changing those settings fixed it?
Are you sure you are trying to fix the problem I posted? Interestingly, it was marked SOLVED before anybody else participated.
Since it wasn't a change in Compiz settings that caused the problem and CCSM didn't fix it, I looked for other possible causes. I had actually UNISTALLED & PURGED Compiz and things were normal, except I couldn't expand my windows. Then I reinstalled Compiz and CCSM.

As a side note, CCSM doesn't allow me to change any of the settings under General, General Settings, Desktop Size. They just revert to 1, blank, blank. I was under the impression that "Desktops" were replaced with "Workspaces" years ago and that setting in CCSM was defunct. If this is not normal behavior I was not aware of that and I wouldn't know how to enable it.

I wonder if that would have anything to do with things opening only in Workspace 1 regardless of which workspace I'm in. but it wasn't doing that before it broke and the settings were the same as they are now. Come to think of it, I didn't have that problem until I reinstalled Compiz.

When I marked the issue SOLVED it was premature. It is now UNSOLVED.

---

### Post by stinkeye on 2014-01-20
The reason I posted what I did was because if I set the panel workspace switcher preferences to more than 1 workspace,
when running compiz, clicking on the workspace switcher makes the panel disappear and I have no desktop 
and  keyboard shortcuts similar to what you described in one of your posts.

You can change the workspaces in ccsm but when you open ccsm again to 
General > General Settings > Desktop Size
They revert back to one virtual desktop.

Compiz is regarded as 1 desktop no matter how many virtual desktops you have.
eg the default in unity is 2 horizontal and 2 vertical **virtual** workspaces
The "**Number of Desktops**" setting should always remain at 1.
I am running the cube in gnome-fallback-compiz...
[LIST]
[*]Horizontal Virtual Size **4**
[*]Vertical Virtual Size **1**
[*]Number of Desktops **1**
[/LIST]

So briefly for me to use multiple workspaces, the panel applet must be set to 1 workspace
and then set the virtual workspaces in ccsm.  
It's all just info to help you solve... not disputing your own experience.

---

### Post by Luxx on 2014-01-21
Thanks for clarifying, stinkeye. I was really confused.

So... if Compiz is regarded as one desktop no matter how many  virtual desktops you have, that might explain why it's acting like one desktop now, but why was the behavior different up until yesterday? although I resolved the main issue, I still can't get the workspaces to behave quite the way they did before, although it is functional now, just not in a way that I can really work in.

Anybody know of a way to change the default behavior from opening everything on Workspace 1 to opening things on the current workspace? I can't have everything open on Workspace1. It clutters workspace 1 and everything I'm working on gets lost. It totally undermines the whole reason I use multiple workspaces. 

Since this solved to the point that I have my workspaces back, I'm opening a new thread concerning the new behavior.
[http://ubuntuforums.org/showthread.php?t=2200778](http://ubuntuforums.org/showthread.php?t=2200778)

---

### Post by Luxx on 2014-01-21
I have no idea why, but I'm back to square one. Suddenly my workspaces are doing it again. I click on a workspace and my screen goes black. All I have is a cursor arrow. This time I still have the panel at the top. If I didn't have app launchers in it I wouldn't be able to get back to Workspace1. I don't want that behavior though. I shouldn't be forced back to Workspace1 on opening a window.

Something has gone really wrong in the last couple of days. I am at a loss.

---

### Post by stinkeye on 2014-01-21
You could try to create a new account and test the fallback session there
or
Reinstall ubuntu-desktop as I'm not seeing the problem here and I didn't uninstall any unity packages.

You can simulate the install first to see the missing packages with..
```
sudo apt-get **-s** install ubuntu-desktop
```

---

### Post by Luxx on 2014-01-21
New account? How would I do that? 
---Sorry I have to ask, but I'm seriously frazzled. I have had my brain twisted around this thing for a couple of days and now I'm behind on a deadline and I really need a nap I can't afford to take right now.

I did uninstall Unity, although months ago. The gnome-session-flashback worked best with my AMD FM2 APU architecture.
I got mad tearing in other desktop environments.
I recently uninstalled unity-lens-photos and unity-scope-gdrive, which I wasn't using.
Wouldn't installing ubuntu-desktop reinstall Unity?

---

### Post by deadflowr on 2014-01-21
There should be a section in the system tools(or whatever it's called in fallback/flashback?)in the admin part shoud have a program called user accounts. You can make a new user there.

The -s in the command stinkeye posted means that the command will only run a simulation and not the actual command.Handy to see what would be brought in, dependency-wise, without having to actually install it.

---

### Post by Luxx on 2014-01-21
OK. Thanks deadflowr. Testing new account.

[New account is so austere.]("https://www.dropbox.com/s/9k9auj6h76f08ug/desktop.png")
[IMG]https://www.dropbox.com/s/9k9auj6h76f08ug/desktop.png[/IMG]
There is nothing there. 

Simulation of installing ubuntu-desktop shows, as expected, all the Unity packages, but how is that supposed to help fix a windows mananger problem in a different desktop environment (gnome-session-flashback) that is not dependent on Unity?

You know what's wierd? I think I could actually work with that bleak desktop. Opening apps in terminal and accessing files in the menu of that one little icon isn't a bad setup. Better than broken workspaces that act crazy. It was this simplicity that attracted me to Linux in the first place. 

Brilliant suggestion, stinkeye. Just looking at that and thinking about how to work in it put things in a different perspective and I'm not nearly as stressed out about it now. It's better to have a few things that work and endless possibilities than to have cool features that are broken and getting in the way of your work.

---

### Post by stinkeye on 2014-01-21
Yeah strange you have no gnome-panel in the new account if you are logging into the fallback session.
I could see where it may be blank if your logging into the Ubuntu session because you've removed unity.
If you can access a terminal, use the command I gave earlier to check session and window manager...
```
echo $DESKTOP_SESSION && wmctrl -m | head -n1
```

& also try to run gnome-panel to see how it behaves...noting you have to add workspaces with ccsm.

You could also try the fallback(no effects) session using Metacity which should have normal workspace behaviour.
If something gives me grief and I think a fresh install will fix, I just backup and re-install.
I'm up and running with all my favourite applications in less than 30 mins.

---

### Post by Luxx on 2014-01-21
I thought that was strange too, so I ran gnome-panel in terminal and I got two lovely gnome panels, top & bottom and the window decorations changed, but only as long as the terminal was open. I uninstalled gnome-session-flashback and installed gnome-shell with the same results. I can run it in terminal and it's great as long as I never close the terminal.

---

### Post by stinkeye on 2014-01-21
> **Luxx said:**
> I thought that was strange too, so I ran gnome-panel in terminal and I got two lovely gnome panels, top & bottom and the window decorations changed, but only as long as the terminal was open. I uninstalled gnome-session-flashback and installed gnome-shell with the same results. I can run it is terminal and it's great as long as I never close the terminal.

Run.... 
```
gnome-panel & disown
```

---

### Post by Luxx on 2014-01-21
Aw, thank you. Let me check this out for a few minutes.

OK. That seemed to be just the ticket in the new account, yet the old account is still acting a bit strange.

---

### Post by Luxx on 2014-01-22
OK. Testing new account.

---

### Post by Luxx on 2014-01-22
When I realized I'm having to fight to log in and out of these accounts I started thinking I am looking at the wrong issue, or focusing on the wrong part of it. Then I got an apport error:
> System problem detected
com.ubuntu.apport-gtk-root problem

My hunch is that apport is working, so it may be trying to report something else. So I started checking on the WMs.
```
me@unkown:~$ sudo gnome-panel apport start force_start=1
[sudo] password for me: 

(gnome-panel:2745): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion 'accelerator != NULL' failed

** (gnome-panel:2745): WARNING **: Unable to parse mouse modifier '(null)'

Object 'object-0-1' has an invalid iid ('OAFIID:GNOME_Panel_TrashApplet')

(gnome-panel:2745): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion 'accelerator != NULL' failed

** (gnome-panel:2745): WARNING **: Unable to parse mouse modifier '(null)'

*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug

*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug

*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug

*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug
```

I got the same thing with compiz.

---

### Post by slooksterpsv on 2014-01-22
If the new account is working fine, then there's something goofed with the settings saved in your old account. May need to just A) migrate to the new account or B) remove all configurations from old account and reinstall the default configuration.

---

### Post by Luxx on 2014-01-22
@ slooksterpsv: I was thinking along those lines, but wanted to make sure what seemed to be working was actually consistent. 

```
me@unknown:~$ gnome-shell --replace
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Gjs-Message: JS LOG: Failed to register AuthenticationAgent
Gjs-Message: JS LOG: GNOME Shell started at Tue Jan 21 2014 23:57:30 GMT-0700 (MST)
```

```
me@unknown:~$ compiz --replace
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
```
...the rest is really long, just compiz (core) loading plugins, except text failed.


I enabled text in CCSM, no more failed plugins, but compiz only works while running in terminal. I cannot coax it to stay. I can get it to look like it will, but when I close the terminal I get a blank vanilla desktop with the computer icon on it, just like when I first logged into the new account, only this one already has folders all over it. I can't launch applications except via terminal which has to be launched with Ctrl+Alt+T. This appears to be consistent with the other gnome classic varieties I tried, and in both accounts. Yet, Gnome-shell (Gnome 3) seems to be working normally in both accounts.

I believe the best course of action here would be to go with Gnome 3.

So what I have done is installed all the gnome-shell components (I'll list them later), including Gnome Tweak tools and I have my basic configuration back to normal. Instead of a classic shell, there are settings you can change in Tweak Tool to get close to a classic look and function. My workspaces work. I can log in and out smoothly and my windows open in my current window. The only things missing are adding app launchers to the top panel, but the Applications menu with the Activities overview kind of takes care of having things where I can find them, though less elegant imo. I can work now.

---

### Post by slooksterpsv on 2014-01-22
If you want to continue using a Gnome 2 like look, there's always the fork MATE. I believe that's what you were doing is using a gnome 2 style look and functionality.

---

### Post by Luxx on 2014-02-17
Mate was so extremely limited I couldn't use it. It's not a matter of aesthetics, like the devs seem to think. It's actually a matter of function. I've been customizing my computer to FUNCTION the way "I" want it to for 7 years and now I can't, except maybe I if go back to Fluxbox as my DE, which I might when I find the time to customize everything, but that's a big job.

---

