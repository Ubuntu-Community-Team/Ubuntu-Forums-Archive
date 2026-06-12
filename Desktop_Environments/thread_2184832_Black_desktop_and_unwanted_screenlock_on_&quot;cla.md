---
title: "Black desktop and unwanted screenlock on &quot;classic/no effects&quot;"
date: 2013-10-30
forum: Desktop Environments
---

### Post by gunter-bohles on 2013-10-30
Hello all

I ran an update a couple of days ago, and after re-starting, there are now a few weird things:
1. The desktop background is black
2. the screen locks after 5 minutes, and requires password to get back to my session
3. When I boot the PC, Ubuntu defaults to Cinnamon instead of the last used desktop (I don't usually use Cinnamon, I installed it ages ago out of curiosity)

The usual fix for 1 and 2 is to go to System Settings, choosing Appearance for the background (the preview window changes with my selection, be that one of the pre-fab wallpapers or one of my jpegs, but not the real thing), and Brightness and Lock, which show what I want (lock off and no password required) but is not effective.

On my last "no effects" log-in, I noticed that my usual background jpeg loaded for a fraction of a second, and then went to Henry Ford (any colour you want, as long as it's black).

Ideas, suggestions?

---

### Post by ibjsb4 on 2013-10-30
> I don't usually use Cinnamon, I installed it ages ago out of curiosity

Makes me wonder if you have other third party software laying around.  Maybe need to do some house cleaning.

Just a possibility :)

---

### Post by gunter-bohles on 2013-10-31
Maybe, like what? Thing is, this installation was working just dandy for over a year, and only hicked up after the last update.  BTW, I'm running 12.04

---

### Post by ibjsb4 on 2013-10-31
In terminal (one line at a time):

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
```

Take note of what autoremove wants to remove and post any errors (not warnings).

Do any good?

---

### Post by gunter-bohles on 2013-11-03
In terminal (one line at a time):

sudo apt-get clean
sudo apt-get autoremove

[COLOR=#ff0000]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-unique-3.0
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 68.6 kB disk space will be freed.
Do you want to continue [Y/n]? [/COLOR]

[COLOR=#ff0000]Removing gir1.2-unique-3.0 ...[/COLOR]

sudo apt-get update

Take note of what autoremove wants to remove and post any errors (not warnings).

[COLOR=#00ff00]No warnings or errors. [/COLOR]
[COLOR=#00ff00]I did some other digging, and found that at about the same time as the update, I fiddled with a setting that upset the background (metacity compositing), which I reversed, and now have my background back (that's why it's called a BACKground, right?)   :)

As for Cinnamon loading as default, and not the last used DM, I seem to remember that there is a setting somewhere for that (which I didn't change from "last used"), but can't recall where. Bummer.[/COLOR]

Do any good?

[COLOR=#00ff00]Doesn't look like it. Screen still locks, requiring password. So I set the screen to never turn off - the timing of the screen lock function still works. Weird.[/COLOR]

---

