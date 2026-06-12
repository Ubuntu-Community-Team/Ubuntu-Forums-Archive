---
title: "[SOLVED] Fluxbox,shortcut keys and volume manager"
date: 2007-09-06
forum: Desktop Environments
---

### Post by mojoman on 2007-09-06
Hi,

I've been configuring Fluxbox to run on my desktop. I use Fluxbox on my laptop so I'm fairly familiar with it but as I don't use my laptop that much I haven't tweaked it as much before. Now I've run into some problems and could really use some help with the following.

First off, my shortcuts doesn't work, most of them at any rate. They work fine on my other machine and some of them work fine on this, specifically the 'extra' keys (shortcut for calculator, mail and Internet) and tab between windows work fine but all other are dead. I've tried grasping a couple of straws, such as removing the quotation marks on the ExecCommand or reconfiguring it using the configuration tool in the Fluxbox menu but it's no good. It's as if the keys aren't configured. The file is correctly named 'keys' and located in ~/.fluxbox and the contents follow below. Damn it, I need those shortcuts!

```
Control Tab :NextWindow
Control Shift Tab :PrevWindow
Control F1 :SendToWorkspace 1
Control F2 :SendToWorkspace 2
Control F3 :SendToWorkspace 3
Control F4 :SendToWorkspace 4
Control F5 :MaximizeWindow
Control F6 :MinimizeWindow
Control F12 :Close
Mod4 F1 :ExecCommand Terminal
Mod4 F2 :ExecCommand /usr/local/bin/firefox32
Mod4 F3 :ExecCommand mozilla-thunderbird
Mod4 F4 :ExecCommand thunar
Mod4 F5 :ExecCommand "gftp"
Mod4 F6 :ExecCommand "filezilla"
Mod4 F7 :ExecCommand "xchat"
Mod4 F8 :ExecCommand "gaim"
Mod4 F9 :ExecCommand "oowriter"
Mod4 F10 :ExecCommand "mousepad"
Mod4 F11 :ExecCommand "xmms"
Mod4 F12 :ExecCommand "xine"
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
None 161 :ExecCommand "xcalc"
None 111 :ExecCommand "scrot"
None 178 :ExecCommand "/usr/local/bin/firefox32"
None 236 :ExecCommand "mozilla-thunderbird"
Control Mod1 Shift 102 :MoveRight
Control Mod1 Shift 100 :MoveLeft
Control Mod1 Shift 98 :MoveUp
Control Mod1 Shift 104 :MoveDown
```

Second, I could really use a volume manager. Is there one available? I know that the one from Gnome works with fluxbox but who wants to install Gnome dependencies on a lean machine running on Fluxbox? Any other alternatives on this? Once the key shortcut works I intend to use the keyboard keys for volume up, down and mute but I still want a docked volume manager.

EDIT: I realized that *volume control* better describe what I need (sorry about that, I'm a 'furriner' you know...) and after I made another search I came up with an application called volume.app. It's in the repos and it gets the job done but, man, is it ugly! So, another alternative would still be very much appreciated.

There's probably lots of other minor issues that will pop up on the way but these are my major headaches at the moment. If anyone could help my I'd sure appreciate it.

Best regards
mojoman

---

### Post by mojoman on 2007-09-07
I've made some headway. Most of the shortcut keys work now. I robooted :oops: I thought logging out and restarting X would be enough for for Fluxbox to re-read all the configuration files but obviously it wasn't. I guess keys isn't part of X, which makes sense, once you think about it. Turned out that it doesn't matter if the ExecCommand is surronded by " " or not, it's read anyway. However, a few things don't work.

(1): Move windows. I've tried using "NudgeUp" etc and "MoveUp" etc but none of them works. So, have can I set a key combination to move an active window?

(2) My volume keys (i.e. Vol up, down and mute) don't work. They are simple dead, even though they work fine in Xfce. When I try mapping them in xev I get this output:
```

FocusOut event, serial 32, synthetic NO, window 0x1400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x1400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

Now, my guess was that they simply wasn't configured and that I would have to define them in .Xmodmap BUT I got nothing to configure. The output shows no key code! Now, before I have actually gotten an output so I do have key # for these keys (176, 174, 160) but I don't have the corresponding code (e.g. 0xff67) so I don't know if that is any help. However, if I get these keys active I can control volume be means of ExecCommand aumix -v +5/-5/0 and wouldn't really need a docked volume control. But how can I ressurect these dead keys?

Any help would be appreciated, I'm at my wits end here. 

Thanks
/mojoman

---

### Post by RedSquirrel on 2007-09-07
> **mojoman said:**
> I've made some headway. Most of the shortcut keys work now. I robooted :oops: I thought logging out and restarting X would be enough for for Fluxbox to re-read all the configuration files but obviously it wasn't. I guess keys isn't part of X, which makes sense, once you think about it.

I'm surprised you had to reboot. On my system (currently Fluxbox SVN 5056), all I have to do to get the keyboard shortcuts to work is select "Reload config" (AKA, Reconfigure). That should make Fluxbox reload everything. If that fails, the Fluxbox menu -> Restart usually does the trick (that only restarts Fluxbox, not the computer ;)).


> **mojoman said:**
>  However, a few things don't work.

(1): Move windows. I've tried using "NudgeUp" etc and "MoveUp" etc but none of them works. So, have can I set a key combination to move an active window?

You have to provide an argument, for example, "MoveUp 10".

Have a look at this:

[http://fluxbox-wiki.org/index.php/Keyboard_shortcuts](http://fluxbox-wiki.org/index.php/Keyboard_shortcuts)






> **mojoman said:**
>  (2) My volume keys (i.e. Vol up, down and mute) don't work. They are simple dead, even though they work fine in Xfce. When I try mapping them in xev I get this output:
```

FocusOut event, serial 32, synthetic NO, window 0x1400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x1400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```Now, my guess was that they simply wasn't configured and that I would have to define them in .Xmodmap BUT I got nothing to configure. The output shows no key code! Now, before I have actually gotten an output so I do have key # for these keys (176, 174, 160) but I don't have the corresponding code (e.g. 0xff67) so I don't know if that is any help. However, if I get these keys active I can control volume be means of ExecCommand aumix -v +5/-5/0 and wouldn't really need a docked volume control. But how can I ressurect these dead keys?

If you know the number, I think you can use them directly in the keys file. Here's an example from the link above:
```
Mod1 113 :exec xterm
```I haven't had to use this sort of trick myself because my keys all worked out in a very straightforward manner. 

I think you get the output you posted when the key has already been assigned to some action. For instance, I have assigned my Windows key to open the right-click menu. When I press my Windows key, I get the same output from xev that you have posted and the right-click menu opens. The same output is shown when I press my multimedia keys (which have been assigned to run different amixer commands).

---

### Post by mojoman on 2007-09-08
RedSquirrel:

Thanks for the help. Adding an argument sure did the trick for moving windows. (I have a TwinView dual monitor setup with a monitor and a projector. If windows are opened in the projector part of the screen when it's turned off that option is a lifesaver.) I had been looking at the fluxbox homepage at sourceforge but the wiki you sent had lots and lots of more useful information. Excellent resource!

Now, about the issue with the keys I've been reading up and thinking real hard. As usual, it got me nowhere but on the road to nowhere I came up with this:

1) Some keys are not supported by the kernel and this is, I've gathered, a fairly common problem with the keyboards that use lots of extra keys. However, as at least the volume keys work in Xfce and the play, stop, ff, rew keys are recognized using 'xev' that problem can at least be excluded.

2) The next thing that struck my feeble mind was that perhaps the keys weren't configured in xmodmap and I had a look, using 'xmodmap -pke'. Now, those keys didn't show up so a created the file ~.Xmodmap and added them. Now, they do show up with 'xmodmap -pke' but they still don't work. This makes sense, because the multimedia keys for browser, mail and calculator work perfectly well and they didn't show up with 'xmodmap -pke' either. Still, it was a straw that begged to be grasped.

At this point I got your reply and it turns out that you're right about xev output and assigned keys. I commented out the sound keys from .fluxbox/keys, reloaded the configuration and tried again and, sure enough, they show up. Also, it is possible to use the key number directly in .fluxbox/keys and that is in fact what I do for the browser/mail/calculator hotkeys and they work fine. Still, for some strange reason volume keys just don't work. So, grasping for some more straws I tried assigning functions that do work with other keys to the keys that apparently don't work. And that works fine! The damned keys are read by the system after all, I just can't get them to behave.

So, where I'm at now is that basically I can configure the sound keys or the play,stop,ff,rev keys to, say, open a browser or start a terminal but I can't seem to get it to raise or lower sound. Now, the command I've tried to get the sound keys to use is:
```

None 160 :ExecCommand "aumix -v 0"
None 174 :ExecCommand "aumix -v -5"
None 176 :ExecCommand "aumix -v +5"
```

The commands work fine in a terminal so that's not the problem. The keys are correctly stated so that's not it either. If I change the command to something else, like "thunar" it executes it alright so it's not the combination 'None 160' that don't work. I just don't get it...:confused:

Sorry if this was a bit long but I thought I'd share my train of thought for anyone having similar problems. Any more help on this is greatly appreciated.

Best regards
mojoman

ps: Your howto for setting up fluxbox menus is really good. I had been tweaking the one on my laptop quite a bit (that and the keys are what basically what I've been tweaking in fluxbox) so had some experience with it but still found lots of useful tips and tricks in it. ds.

---

### Post by RedSquirrel on 2007-09-08
> **mojoman said:**
> I had been looking at the fluxbox homepage at sourceforge but the wiki you sent had lots and lots of more useful information. Excellent resource!

Yes it is. I used to have a link to it in my signature. Maybe I'll put it back... :)


> **mojoman said:**
> Still, for some strange reason volume keys just don't work. So, grasping for some more straws I tried assigning functions that do work with other keys to the keys that apparently don't work. And that works fine! The damned keys are read by the system after all, I just can't get them to behave.

So, where I'm at now is that basically I can configure the sound keys or the play,stop,ff,rev keys to, say, open a browser or start a terminal but I can't seem to get it to raise or lower sound. Now, the command I've tried to get the sound keys to use is:
```

None 160 :ExecCommand "aumix -v 0"
None 174 :ExecCommand "aumix -v -5"
None 176 :ExecCommand "aumix -v +5"
```The commands work fine in a terminal so that's not the problem. The keys are correctly stated so that's not it either. If I change the command to something else, like "thunar" it executes it alright so it's not the combination 'None 160' that don't work. I just don't get it...:confused:

That's weird. I'm using amixer commands. Have you tried those?

```
XF86AudioMute :Exec amixer set PCM toggle > /dev/null 
XF86AudioLowerVolume :Exec amixer set PCM 1%- > /dev/null 
XF86AudioRaiseVolume :Exec amixer set PCM 1%+ > /dev/null 

```

**EDIT:**

I have never used quotation marks in the keys file syntax. I decided to test that out and when I put them around the *mute* command above, like this:

```
XF86AudioMute :Exec "amixer set PCM toggle > /dev/null"
```

it ceased to work. At least on my system, quotation marks are a bad idea. :grin:




> **mojoman said:**
> Sorry if this was a bit long but I thought I'd share my train of thought for anyone having similar problems. 

Great idea. 


> **mojoman said:**
> ps: Your howto for setting up fluxbox menus is really good. I had been tweaking the one on my laptop quite a bit (that and the keys are what basically what I've been tweaking in fluxbox) so had some experience with it but still found lots of useful tips and tricks in it. ds.

I'm glad it was helpful.

---

### Post by mojoman on 2007-09-08
RedSquirrel:

You know what? I tried the audio keys without the quotation marks. It's really grasping a straw since It works with the quotation marks for other keys and even works with the quotation marks for the audio keys when other commands are assigned, right? But I figure, why not try, it's for free? Well, now it works! For some reason, I can qoute the commands for other keys and I can even quote other commands for the audio keys and have them all work but the sound command, if assigned to the audio keys, must be without quotation marks. :confused:

Now, I'm not even going to try to figure out how this is wired, I'll just leave it without the quotation mark and be real happy about the fact that I got working volume keys! At last! Problem solved.

Thanks, I could have keept going with this forever without your help!
/mojoman

EDIT: Took me about a minute to set up the other media keys to control xmms. Works like a charm. Real sweet!

---

### Post by RedSquirrel on 2007-09-08
That's great news! Sometimes it's a challenge to configure the keyboard shortcuts but once they work it's pure joy... :)

---

