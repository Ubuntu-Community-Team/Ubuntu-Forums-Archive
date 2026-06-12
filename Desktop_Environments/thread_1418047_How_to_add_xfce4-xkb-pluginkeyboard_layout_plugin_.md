---
title: "How to add xfce4-xkb-plugin/keyboard layout plugin at startup?"
date: 2010-02-28
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-28
Hi,
i have this-for me huge problem- xfce4-xkb-plugin won´t save my keyboard setup and it won´t show after startup in xfce4 panel (xubuntu 9.10):
 
I did this:

1) i added in /etc/default/console-setup needed keyboard layouts (de,hr,rs)-because i know that after restart xfce4-xkb-plugin will not memorize my layouts.
> XKBMODEL="pc105"
XKBLAYOUT="de,hr,rs"
XKBVARIANT=""
XKBOPTIONS=""

2) i added at startup:
```
/usr/lib/xfce4-xkb-plugin/xfce4/panel-plugins/xfce4-xkb-plugin
```

That is where i found that plugin.

But after logout-nothing

So-is there any way to make keyboard applet to show up with proper Layouts?

Thanks

---

### Post by vickoxy on 2010-03-17
Bump!
No one uses keyboard applet in xubuntu? 

I keep losing that applet every one-two days- and have to add it in panel manually. 

Some sort of bug?

This is tastatur.desktop file in home/.config/autostart/

```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Tastatur
Comment=
Exec=/usr/lib/xfce4-xkb-plugin/xfce4/panel-plugins/xfce4-xkb-plugin
StartupNotify=false
Terminal=false
Hidden=false

```

---

### Post by 3Miro on 2010-03-17
The plugin is odd. I never lose it from the panel, once added it stayed there for me; however, every time I log out and back in, the settings have hanged. Everything is reset back to standard English and the keyboard shortcut is disabled. I have to manually add layouts again and again.

---

### Post by vickoxy on 2010-03-17
> **3Miro said:**
> The plugin is odd. I never lose it from the panel, once added it stayed there for me; however, every time I log out and back in, the settings have hanged. Everything is reset back to standard English and the keyboard shortcut is disabled. I have to manually add layouts again and again.

Ok- i think you should add your keyboard layouts here (before there was xorg.conf file where you could add this):
```
/etc/default/console-setup
```

At the end you have these lines:
```
XKBMODEL="pc105"
XKBLAYOUT="de,hr,rs"
XKBVARIANT=""
XKBOPTIONS=""
```

So, change/add manually in XBLAYOUT your keyboard layouts (i have "de,hr,rs").

So, after logout/reboot, your setup should be memorized. But still, i think you will lose your applet after few days continuous working.

---

### Post by 3Miro on 2010-03-17
> **vickoxy said:**
> 
So, after logout/reboot, your setup should be memorized. But still, i think you will lose your applet after few days continuous working.

Thanks I will try the advice, however, I have never lost the applet. I have both a laptop and a desktop and neither one has ever lost it. This is some sort of a bug probably.

---

### Post by vickoxy on 2010-03-17
> **3Miro said:**
> Thanks I will try the advice, however, I have never lost the applet. I have both a laptop and a desktop and neither one has ever lost it. This is some sort of a bug probably.

One question-do you use gnome (ubuntu) or xfce (xubuntu)? Because-this disappearing issue i didn´t have in gnome (ubuntu).

---

### Post by 3Miro on 2010-03-17
> **vickoxy said:**
> One question-do you use gnome (ubuntu) or xfce (xubuntu)? Because-this disappearing issue i didn´t have in gnome (ubuntu).

Ubuntu + spt-get install xfce4.

So I guess you can report this as an Xubuntu bug.

---

### Post by lunatico on 2010-12-09
> **3Miro said:**
> The plugin is odd. I never lose it from the panel, once added it stayed there for me; however, every time I log out and back in, the settings have hanged. Everything is reset back to standard English and the keyboard shortcut is disabled. I have to manually add layouts again and again.

Hey I know this is old but did you ever found a workaround?

At the moment after every logout it won't save my shortcut to change layout.

Thanks!

---

### Post by vangop on 2011-02-06
Also need help. How to make this stupid applet startup??

---

### Post by vickoxy on 2011-02-06
I don´t use xfce any more, so i am not from any help here... Sorry...

---

### Post by deskman on 2011-05-06
How about this video? Works wonders! [http://www.youtube.com/watch?v=gzYqREENVVY:guitar:](http://www.youtube.com/watch?v=gzYqREENVVY:guitar:)

---

### Post by ydamyanov on 2011-08-09
What worked for me on Xubuntu 11.04:

0. Added my alternate layouts using "Settings Manager | Keyboard | Layout | Keyboard Layout". 

1. Installed xfce4-xkb-plugin:
```
$ sudo apt-get install xfce4-xkb-plugin
```

2. Added the plugin to my bottom panel:
* Right-click on the panel; "Panel | Add New Items..."
* Choose "Keyboard Layouts"; click "Add", close.

3. Configured the xfce4-xkb-plugin to switch my kbd layouts using <Alt-Shift>:
* Right-click on the US flag shown by default; "Properties"
* Set up all fields as appropriate; close.

As I remember having the above mentioned issues with the plugin forgetting its configuration, I opened **$HOME/.config/xfce4/panel/xkb-plugin-29.rc** and tried to change **never_modify_config** to *true* but later saw it was put back to *false* and the plugin still worked fine.

[**EDIT**:] Sadly, I was wrong thinking that the plugin settings are rpeserved across reboots. They seem to be across logout-login, but not reboot. For now, I cannot find a way to make that config persistent. chown-ing the file to belong to root:root and chmod 444 also did not help; I find it later owned by me again, with mode 644. Anyone who knows a fix, please share it.

Yassen

---

### Post by detronator on 2011-10-09
Here are a possible way of switching between keyboard layouts in **xubuntu**:

[COLOR=DimGray]=== *This** method will assign a shortcut (in my  case ALT+SHIFT) that will switch between your preferred layouts (in my  case english, french and bulgarian phonetic)*[/COLOR]

1) Go to Start Menu > Settings > Settings manager > Session and Startup > Application Autostart (tab)
2) Click on the add button
3) Type anything you want for name and description (for exam: KBD_LAYOUT_SWITCHING)
4) In the Command field, you have to insert this:
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,fr,bg"(phonetic)"

[COLOR=DarkGreen]--Note: This command is an example and sets the  shortcut combination ALT+SHIFT to switch between english, french and  bulgarian phonetic layouts, but feel free to use anything you want.
  
  [COLOR=Black]5) Click OK[/COLOR][/COLOR] and that's it, but if you also need an icon in the tray read below[COLOR=DimGray]*: *[/COLOR][I]

[/I] [COLOR=Red]***[/COLOR]Since this method just adds the functionality to switch between layouts  and it doesn't show an icon in the tray, indicating the current  language, here is a good way to do this:

1) Open terminal and type: sudo apt-get install xfce4-xkb-plugin
[COLOR=DarkGreen]Note: In theory this is the perfect solution for  layout switching, but it has this weird problem of not remembering the  shortcut combination for kbd layout switching after reboot, therefore we  need to use both previous methods as well.. I hope this will change in  future. We will use this plug-in only to indicate in tray which layout  is currently used.[/COLOR]
2) Right click any panel and choose Panel > Add new items
3) Search for **Keyboard Layouts** (this is our new xfce plugin) and add it to the panel
4) By right-clicking on the plugin icon and choosing **properties**  you can set different cool things like using text instead of a flag icon  and Manage layout:globally. Most important is to add your preferred kbd  layouts(if needed).
5) That's it, now you have an indication of the current layout in your panel.

[COLOR=DarkGreen][COLOR=DimGray]==========[/COLOR]
Note: This method continues to work after reboot. [/COLOR]

---

### Post by vangop on 2011-11-09
The only problem is that you'll have a global system layout, but I'd like to have per-window layout.
Otherwise I don't need the stupid xkb-applet, just add "grp_led:caps" option (or other LED) so that the led will show if an alternative layout is on (works best for 2 layout though.)

---

### Post by LewisTM on 2011-11-29
The xkb-plugin is [buggy]("https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/548631?comments=all"), it crashes and then forgets on logout/reboot.

A solution (more like a hack) was just posted that allows persistent settings while keeping the usefulness of the plugin.
> 
If we want to still use the plugin (to switch, see the flag, etc) we cannot use a setxkbmap command on startup because the settings get overwritten by xkb-plugin (with blank ones).

Complicated temporary automated solution:
1. Set the desired options in the plugin
2. Copy the ~/.config/xfce4/panel/xkb-plugin-##.rc to some other file e.g. ~/.config/xfce4/panel/goodxkb.rc
3. Add this command to a startup job:

     sh -c "sleep 10 && cp ~/.config/xfce4/panel/goodxkb.rc ~/.config/xfce4/panel/xkb-plugin-##.rc && pkill xkb"
    (change the ## to your number)

The pkill part is crucial to reload the plugin and its config.

Works for me. Any change in the options will only affect the current session. The goodxkb file would need to be modified or recreated for the changes to persist.

---

### Post by vangop on 2011-11-30
Not really working for me.
Upon restart the settings in the plugin are reset, although the conf file is "good". Then after some time the plugin just rewrites the "good" conf to match its reset settings.

---

### Post by LewisTM on 2011-11-30
> **vangop said:**
> Not really working for me.
Upon restart the settings in the plugin are reset, although the conf file is "good". Then after some time the plugin just rewrites the "good" conf to match its reset settings.
I've tested the method on 4 different machines and it always works, so something must have gone wrong along the way.

What happens when you enter the cp...pkill command in a terminal?
Ideally you shouldn't get any error, the keyboard indicator should blink and respawn with the right configuration.

---

### Post by vangop on 2011-11-30
The xkb applet restarts, the rc file is not changed. But the applet is not responding to the settings in the rc. After some seconds the applet just overwrites the rc with the default settings.
Anyway I doubt the plugin is useful since I want more options than it offers, like grp_led or replace caps_lock with control.

---

### Post by LewisTM on 2011-11-30
The only thing I can think of is that the applet doesn't like what's in the rc file so it discards it. Did you modify it by hand?
Try creating a new one with fresh settings straight from the applet, then back it up to goodxkb.rc 
Change the settings again to something different, copy goodxkb.rc back to the xkb-plugin-##.rc file and pkill xkb. This should restore the fresh settings. If not, then I am at a loss.

---

### Post by superG on 2012-01-03
Got same problem too.
Found out, that xfce4-xkb-plugin settings are overwritten with global xfce configuration (Settings Manager/Keyboard/Layout).
No matter, what you have in xkb-plugin-##.rc file, it would be overridden with global settings, if they are set.
Here is how I am configuring this:
1. Set "Use system defaults" checkbox in Settings Manager/Keyboard/Layout;
2. Reboot xfce session;
3. Configure your layout and switch layout shortcut entirely in plugin configuration.

---

### Post by cipricus on 2012-02-27
I think I got a solution -  - which works after many reboots!

I posted it in my message to a similar thread - [here]("http://ubuntuforums.org/showthread.php?p=11722803#post11722803").

---

### Post by LewisTM on 2012-02-27
> **cipricus said:**
> I think I got a solution -  - which works after many reboots!

I posted it in my message to a similar thread - [here]("http://ubuntuforums.org/showthread.php?p=11722803#post11722803").
OR just set the global Xfce configuration (Settings Manager/Keyboard/Layout) to use system defaults, so there will be no conflict between configs. It seems to be the [consensus]("https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/548631") now to deal with this bug.
I still experienced some random but very, very rare events where the plugin ate the config file. Mostly when I had to kill the X server.

To prevent even that from happening I essentially locked my .rc file with command:
```
sudo chattr +i ~/.config/xfce4/panel/xkb*
```
And when needed I reload the plugin with a [FONT="Courier New"]pkill xkb[/FONT].

Cheers!

---

