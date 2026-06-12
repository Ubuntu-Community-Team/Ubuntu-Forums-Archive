---
title: "My experiences running Lubuntu 11.10 on a Toshiba Portege r835 ST6N02"
date: 2012-02-24
forum: Desktop Environments
---

### Post by Andrew York on 2012-02-24
A month ago, I wanted a light (~3 lb), long-battery-life (>5 hrs) Linux laptop with a good keyboard (full size, including pageup/pagedown keys). My previous machine (Lenovo x120) fit the bill, but frequently crashed running Ubuntu [(link)]("http://superuser.com/questions/386112/is-there-a-linux-distribution-that-almost-never-crashes-on-a-lenovo-x120e").

I just bought a Toshiba Portege r835 (ST6N02), and I've had a great experience with Lubuntu 11.10, so I figured I'd make the thread I wish I'd found last month when I was shopping.

Bottom line: it doesn't seem to crash ever, it boots in under 15 seconds, and the interface is simple and fast.

I've been nerding out on making small tweaks to get the machine just how I like it. The story so far:

[INDENT]Tried Linux Mint 12. Installer gave error messages, then hung after formatting disk. Abort.

Tried Ubuntu 11.10. Installer was smooth and flawless. Unity pisses me off, installing Chrome fails, and Synaptic's gone. Abort.

Tried Lubuntu. Install is smooth, Chromium's installed by default.

Added keyboard shortcut for Chromium by editing .config/openbox/lubuntu-rc.xml and running openbox --reconfigure
Also changed the shortcut that happens when you click "print screen" to something that doesn't involve "scrot" (mtpaint -s)

I don't use the 'menu' key on the keyboard, but I do like to do ctrl-alt-arrow right-handed to change desktops. This would be easier if 'menu' were 'alt', so let's learn how to remap a key. 
Following this advice:
[http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys)
Changed keymapping for the menu key using xev and xmodmap; this is temporary. Added an executable .xinitrc to $HOME, but googling suggests this is getting either ignored, or overruled by a later execution of setxkbmap. Sooo.... 
Hahaha I just add a sleep 10 && xmodmap .Xmodmap to .xinitrc and everything's cool? Ridiculous.
Nope, that didn't work either. Seems the real problem here is I don't know how to get scripts to run at startup in Lubuntu. This worked though: create this file:
/home/user/.config/lxsession/Lubuntu/autostart
containing this:
@/usr/bin/xmodmap /home/user/.Xmodmap
where I made the .Xmodmap file by piping modmap -pke to a file, and edited it to change the keys I wanted.
and add lines starting with @ to the file. For example, @lxterminal would launch the terminal. Woo lubuntu!

I don't like tap-to-click, so I followed this advice:
[http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)
to disable tap-to-click:
press> alt+f2
type> gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart
add your " @synclient MaxTapTime=0 "
Or:
gpointing-device-settings is a nicer way to do this. I initially thought I had to learn how to mess with .desktop files to add that to a menu, though! Add the package through Synaptic, but to get it to show up in a menu, make a shortcut, copy the shortcut to /usr/share/applications, then change the 'categories' part so it shows up in 'preferences'. wheee!
Turns out, haha, gpointing-device-settings actually MAKES a .desktop file in the right place (/usr/share/applications), but it's set to gnome-only. Edit the file, delete that line, **** works perfect!
EEEExcept the changes from gpointing-device-settings don't seem to get reapplied on restart. So the autostart @synclient method really is the way to go.
also added @synclient VertEdgeScroll=0 to disable scrolling.

Alt-f2 opens without focus. Hit it twice, and everything's cool. This fix:
[https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/889414](https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/889414)
 seems to solve things too. Other keyboard shortcuts don't open with focus though. For example, ctrl-alt-d still doesn't open home directory elegantly, and ctrl-alt-t often opens a terminal behind the current window. Still want to fix this.

Following this advice:
[http://www.linlap.com/wiki/toshiba+portege+z830-10f](http://www.linlap.com/wiki/toshiba+portege+z830-10f)
for a similar laptop, I changed /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor pcie_aspm=force i915.i915_enable_rc6=1 i915.lvds_downclock=1"
This is supposed to fix the brightness-on-resume problem (works for me), and supposed to increase battery life (haven't checked, not sure if this has any effect on battery life).

Task bar icons move around. ([http://ubuntuforums.org/showthread.php?t=1869357](http://ubuntuforums.org/showthread.php?t=1869357))
Fix:
add a file to /etc/pm/sleep.d that's basically a copy of restore_brightness, called reset_panel:
```
#!/bin/bash
case "$1" in
   suspend|hibernate)
      #do nothing
   ;;
   resume|thaw)
      export DISPLAY=:0 #What does this do? Are there side effects?
      sleep 5 && lxpanelctl restart & #Delayed so the battery icon can finish wrecking shop.
   ;;
   *)
      exit 1
   ;;
esac
exit 0

```
You gotta add the 'sleep' part, cause the icon movement happens after this script executes.

Existing problems:
Rapid opening/closing the laptop doesn't always result in the sleep/wake state you'd expect.
Power button does nothing when the computer is on/awake.[/INDENT]
More ramblings to follow if I find anything else to tweak. Thanks to whoever made Lubuntu, it's exactly what I wanted.

---

### Post by Rodney9 on 2012-02-24
Terrific Post, Well Done !

[http://lubuntu.net/about](http://lubuntu.net/about)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by idelosestados on 2012-03-18
> **Andrew York said:**
> Added keyboard shortcut for Chromium by editing .config/openbox/lubuntu-rc.xml and running openbox --reconfigure

Care to specify? :)

---

