---
title: "Ubuntu hangs after login"
date: 2007-08-31
forum: Desktop Environments
---

### Post by mitkonanov on 2007-08-31
Hi im using Ubuntu Feisty Fawn and until two days ago everything worked just fine, im on IBM ThinkPAD z60m with ATI graphics card, i was working with Desktop Effects turned on. Two days ago i suddently noticed that the proccess Compiz.Real takes 80% of my cpu ( wasnt like that before ) and before i could do something the system totally stucked ( no mouse/keyboard crtl-alt-backspace also not working ).I forced a computer reboot and from than i cant login, if i login in XGL session it stucks as soon as i see my desktop background, if i log in with a normal GNOME session i have no window borders, the login window hangs on "Natalius" for about 5 mins in which i cant log into internet, and if i try to go to the window options i get a message ( Window Manager "Unknown" Could not be executed ) or something like that...
Have searched the forum for a solution couldnt find one, i think this occured after ubuntu has downloaded some new Compiz update ( used the original compiz that comes with ubuntu, havent experimented with fusion and so.. )...

thanks in advance..

---

### Post by bmorency on 2007-08-31
i was getting the same problem myself. every time i would login everything would freeze and   i would have to hit the power button to restart. but now it seems to be running a lot better for me since i have installed the compiz-fusion tray icon.

i found it  [here.]("http://ubuntuforums.org/showpost.php?p=3163821&postcount=8")

it hasn't froze on me since i started using it.

---

### Post by mitkonanov on 2007-08-31
i would try it right away and will report whats happening, thanks for the response...

---

### Post by mitkonanov on 2007-09-03
have tried no luck :(, afterwards came into some guide over ati video cards, uninstalled my closed ati driver, rebooted and now i cant get into the graphic interface at all :(
any suggestions before im reinstalling?

---

### Post by Note360 on 2007-09-03
ok, boot into failsafe terminal. from here navigate to the directory ~/.config/autostart
```
cd ~/config/autostart
```
Now, delete the compiz.desktop file or whichever one has to do with compiz. using the rm command. (use the ls command to get a list of files).
```
$ ls
$ rm file_that_is_nolongerwanted.desktop
```

---

### Post by OlympicSoftworks on 2007-09-03
I've got the same thing on an older machine with an Intel Chipset and integrated video.  Machine runs fine, has sound and pretty much everything...until you login.  Then the login music plays and the Gnome bars at the top and bottom flash on and off a few times and the desktop just hangs there.

I can get to the context menu and it works just fine, screenshot does too so the launcher is working.  There seems to just be a problem with some intel graphics displays and Gnome.

What is wierd is mine worked with the files straight off of the CD, after updating is when it fails.  And going back to the previous Kernel does nothing, it's not a kernel thing.

---

### Post by tipiglen on 2007-09-13
Hi, 
I've got a problem which sounds familiar.  On first boot from scratch install (from hard disk - cdrom useless!), everything worked fine, but on second and all sucessive boots, after login all I get is a nice dark maroon background and a movable mouse.  Keyboard useless, except to get to bailout terminal.  ctrl/alt/del starts shutdown, but that hangs at deconfiguring networks......

Xsesion errors:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ed"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/4548

I don't know if I've got x installed properly, but I can't do anything if I can't get to the desktop, because the bailout terminal's got no powers at all.

Any ideas??

ed

Middle-aged celeron with 512MB RAM, shared by video, formerly windoze ME (quite appropriate)

---

