---
title: "Suspend in Fluxbox"
date: 2009-05-09
forum: Desktop Environments
---

### Post by Uzi304 on 2009-05-09
Is there any way I make Fluxbox suspend when I close the laptop lid? If that isn't possible, how do I make it suspend at all? I've get everything else configured how I want. Thanks in advance

---

### Post by kerry_s on 2009-05-09
you could use "sudo pm-suspend" in a menu launcher.
you'll have to add a nopassword option in visudo for pm-suspend.

better test first see if suspend even works, in a terminal> sudo pm-suspend

are you installed on top of gnome? if so you might try using the gnome logout program instead, that should a suspend as a choice.

---

### Post by Uzi304 on 2009-05-09
sudo pm-suspend only brings me to the login screen. And yes I did install Fluxbox on top of Gnome. How would I bring up the gnome logout program? So I assume that's a no-go on the laptop lid suspension?

---

### Post by kerry_s on 2009-05-10
> **Uzi304 said:**
> sudo pm-suspend only brings me to the login screen. And yes I did install Fluxbox on top of Gnome. How would I bring up the gnome logout program? So I assume that's a no-go on the laptop lid suspension?

does it even suspend under gnome?

the command is> **gnome-panel-logout**
if it's slow or doesn't work you might need to run> **gnome-power-manager &**
in your ~/.fluxbox/startup.

i think thats all you need, no guarantees. :P
let me know what happens. 

the laptop lid, i think the default is to blank the screen, but if you put the "**gnome-power-manager &**" in your ~/.fluxbox/startup you can use that, the command is> **gnome-power-preferences**
or
if you want you can call> **gnome-control-center**
to access all those gnome settings.

hey, can you tell me how much memory your fluxbox is using right now and after you add the gnome parts, i would like to know the difference.
i choose to just cut down gnome instead of using a window manager, i've got it pretty bare bones i'm using around 98mb ram, it go's up and down.

---

### Post by Uzi304 on 2009-05-10
Thanks that's perfect! As for the mem usage, I'll post the results straight from top.

Fluxbox: Mem:   1016560k total,   562388k used,   454172k free,    41832k buffers

Gnome: Mem:   1016560k total,   634792k used,   381768k free,    45364k buffers

---

### Post by kerry_s on 2009-05-10
> **Uzi304 said:**
> Thanks that's perfect! As for the mem usage, I'll post the results straight from top.

Fluxbox: Mem:   1016560k total,   562388k used,   454172k free,    41832k buffers

Gnome: Mem:   1016560k total,   634792k used,   381768k free,    45364k buffers

thanks, that's not bad only a extra 7mb, i actually thought it would be a lot more.

---

### Post by samden on 2009-05-11
Thanks heaps kerry_s, "gnome-power-manager &" lets me set the computer to suspend when the lid is closed. It would be nice if there was a more fluxboxy way to do this easily, but this works.

However gnome-panel-logout returns "command not found", even with gnome-power-manager running. Are you sure that is the correct command to get the gnome logout screen?

---

### Post by kerry_s on 2009-05-11
it was on mine. i'm not running gnome any more, switched to xfce4 a couple of hours ago.
if you can give me the output of>** ls /usr/bin | grep gnome**
i can tell you what to try. :)

---

### Post by samden on 2009-05-12
```
gnome-about
gnome-about-me
gnome-appearance-properties
gnome-app-install
gnome-at-mobility
gnome-at-properties
gnome-at-visual
gnome-audio-profiles-properties
gnome-calculator
gnome-character-map
gnome-codec-install
gnome-control-center
gnome-default-applications-properties
gnome-desktop-item-edit
gnome-dictionary
gnome-display-properties
gnome-doc-prepare
gnome-doc-tool
gnome-eject
gnome-font-viewer
gnome-help
gnome-keybinding-properties
gnome-keyboard-properties
gnome-keyring
gnome-keyring-daemon
gnome-language-selector
gnome-mount
gnome-mouse-properties
gnome-nettool
gnome-network-properties
gnome-open
gnome-panel
gnome-panel-screenshot
gnome-power-cmd
gnome-power-manager
gnome-power-manager-inhibit
gnome-power-preferences
gnome-power-statistics
gnome-screensaver
gnome-screensaver-command
gnome-screensaver-preferences
gnome-screenshot
gnome-search-tool
gnome-session
gnome-session-properties
gnome-session-save
gnome-settings-daemon
gnome-sound-properties
gnome-sound-recorder
gnomesword2
gnome-system-log
gnome-system-monitor
gnome-terminal
gnome-terminal.wrapper
gnome-text-editor
gnome-thumbnail-font
gnome-typing-monitor
gnome-umount
gnomevfs-cat
gnomevfs-copy
gnomevfs-df
gnomevfs-info
gnomevfs-ls
gnomevfs-mkdir
gnomevfs-monitor
gnomevfs-mv
gnomevfs-rm
gnome-video-thumbnailer
gnome-volume-control
gnome-window-properties
gnome-wm
polkit-gnome-authorization

```
I can't see anything in there that looks obvious unfortunately.

---

### Post by kerry_s on 2009-05-12
i think i know what happened, there's a move towards using hal and policykit to control shutdown, reboot, etc...
i see a similar thing on my xfce4 setup, took me a while to work around it.

anyways you might have to do it the old fashion way. first step is to modify the sudo to allow you to do it with out a password.

in a terminal:
**sudo visudo**

add this:
[B]%users ALL=ALL NOPASSWD: /sbin/reboot, /sbin/halt, /usr/sbin/pm-suspend
[/B]

now you should be able to use "sudo reboot, sudo halt, sudo pm-suspend" with out it asking for a password in your menu.

or

if you want to go with a script:

```
#!/bin/sh
XMESSAGE=$(which gxmessage) || XMESSAGE=xmessage

$XMESSAGE " Logout Selections " -center -buttons "Cancel":1,"Suspend":2,"Reboot":3,"Shutdown":4  
case $? in
1) exit 0 ;;
2) sudo pm-suspend ;;
3) sudo reboot ;;
4) sudo halt ;;
esac

```

than can just call the script.

i have both methods in my setup, i use the script in the main menu and i have a icon menu with each command.

---

### Post by haiyun211 on 2009-05-26
Hi guys Im new to ubuntu and am trying to use fluxbox and dont know where to ask this question?  If you could either help or direct me to where I can get help that would be appriciated?  I am trying to edit the fluxbox startup but it keeps saying permission denied.  Any answers?

---

### Post by samden on 2009-05-26
How are you trying to edit it? Are you just typing something like:
```
nano ~/.fluxbox/startup
```
in the terminal? You may be entering that code wrong and trying to open a file that does not exist. The startup file is in your user folder so you shouldn't need any special permissions to edit it.

Please explain exactly what you are doing.

---

### Post by haiyun211 on 2009-05-26
I forgot nano in the terminal command thanks a bunch no one else wrote about the nano they just put ~/.fluxbox/startup so thanks again.

---

### Post by samden on 2009-05-26
No worries! If you don't like nano you can use any text editor, if you prefer gedit for example you'd just type:
```
gedit ~/.fluxbox/startup
```
Enjoy fluxbox!

---

### Post by haiyun211 on 2009-05-26
Thanks man you guys have been a big help.

---

### Post by samden on 2009-05-26
No worries, these forums are how I learnt about Ubuntu in the first place too, and I'm sure you'll be a great help to the next load of newbies in a few months! :)

---

### Post by haiyun211 on 2009-05-26
Do you know how to make it so I can use my flash drive on fluxbox?

---

### Post by samden on 2009-05-26
The simplest way is to just use Nautilus (the file management software from Gnome). You have to start it without allowing it to take over your desktop (otherwise you can't right-click on your desktop so lose your menu - very frustrating!). Start nautilus using the command:
```
nautilus --no-desktop --browser
```
Once nautilus is opened you should be able to use flash drives just as usual.
For convenience, add it to your menu by adding:
```
[exec] (Nautilus) {nautilus --no-desktop --browser}
```
to your ~/.fluxbox/menu file (before the [end] line).

---

### Post by haiyun211 on 2009-05-26
it said ( Could not parse arguments: Unknown option --nodesktop)

---

### Post by samden on 2009-05-26
My bad, typo sorry. Should read --no-desktop. Will correct above.

---

### Post by haiyun211 on 2009-05-26
that worked great thanks a bunch.

---

### Post by haiyun211 on 2009-05-28
Does any one know how to make my menus transparent and border-less in fluxbox?

---

