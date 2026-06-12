---
title: "VERY small text in kubuntu"
date: 2005-03-29
forum: Desktop Environments
---

### Post by arnoct on 2005-03-29
Hey, I just recently installed kubuntu-base from the repositories. I've had a few small issues with KDE, but the main problem I'm having is text size. Much of my text is WAAAAAAY too small! See the attached image. I've tried fiddling with font settings in the CP, but it seems to do nothing. Only KDE programs work normally. Someone suggested I install a certain library that was SUPPOSED to make GTK work with qt, but it didn't work. 

Any ideas? The text is fine in all other WMs.

---

### Post by arnoct on 2005-03-29
I fixed it, sort of. If I run gnome-font-properties, it seems to fix the fonts. Still, it's very inconvenient :\

---

### Post by odrop on 2005-03-30
Is this a problem with KDE/QT apps? or Gnome/GTK apps?

Either way, you have to use the respective configuration tools for each type of app (KDE or Gnome apps).  Its inconvient, yeah, but thats about the only way around it. 

The only other advice I could offer is that app you've already tried (I believe its called gtk2-engines-gtk-qt.)  If that is the one.

---

### Post by arnoct on 2005-03-31
I fixed the problem a bit better; instead of autoloading gnome-font-properties (which opens a window) I just autoload gnome-settings-daemon and it works fine.

---

### Post by Frustration on 2005-04-01
Hmm. I've just installed (and played about for a while) with kubuntu. So far - so good, nearly.

I've now got the same problem with very very small fonts - I have to set them to 16pt just to be able to read them even at 1024x768  :shock: 

I tried running gnome-font-properties - but I don't have it  :-k 

Arrrrgh!  ](*,)

---

### Post by fdoving on 2005-04-01
It could help to change to, or make sure, you're running X at 100dpi.

For KDM:
take a look at: /etc/kde3/kdm/Xservers
```

:0 local@tty1 /usr/X11R6/bin/X -nolisten tcp -dpi 100

```
Make sure you got the '-dpi 100' part..


For GDM:
Edit /etc/gdm/gdm.conf, find "server-Standard", and check that you've got the '-dpi 100' part.
```

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -dpi 100 -audit 0
flexible=true

```


Hope this helps..

---

### Post by Frustration on 2005-04-02
> ...Hope this helps..
 Thanks for that.  I actually got totally lost and the system started crashing (too much mucking about without knowing what I'm doing). So I reinstalled ubuntu and added in kde. 

That seems to of sorted things out :)

---

### Post by aramazan on 2005-04-02
[QUOTE=fdoving]```
:0 local@tty1 /usr/X11R6/bin/X -nolisten tcp -dpi 100
```Make sure you got the '-dpi 100' part..[/QUOTE]Actually this is addressing a root problem: X being just too clever than it really should.

Monitor's X,Y resolutions are automatically derived from DDC info of length in millimeters of X,Y viewable area from the monitor itself, and from the actual resolution selected. With this "calculated" DPI at hand, xfs scales the fonts while serving. See /var/log/Xorg.0.log and look for the string "DPI set to". The intended benefit is that, no matter which size of monitor and which resolution you use, a given 14 point font is always presented with the same physical size. This is my understanding. Correct me if I'm wrong.

Now the cons:
1. IMHO preserving the physical font size is *not* always a good thing, even if everything works as expected. General user tendency is that, users make a compromise between font and screen sizes. If one has a small screen, one doesn't keep the fonts at the same physical size. He uses smaller fonts (but not directly proportional to his screen size) so that while he keeps readability, he also attains some text coverage with his small screen. The opposite is also true for big screens. If a user has big screen, he again doesn't keep the same physical font sizes. He enlarges them a bit (but not directly proportional to his screen size) so that he both gains more coverage due to his big screen, and also he attains more comfortable reading. But this over-clever behavior of X tries to keep the physical font size exactly the same.

2. Sometimes DDC reading of the monitor doesn't work for some intermittent reason, and then X defaults to 75,75 resolution. So, sometimes you have 105,117 resolution with font sizes more appropriate for a preschool child, and other times you get 75,75 resolution with miniature fonts. I remember restarting X several times with Ctrl+Alt+Backspace in order to have it get the DDC values from the monitor. Now, I have a Samsung SyncMaster 793s monitor, which is a reasonable one. So I cannot blame the monitor for DDC read failures.

3. Many old monitors are not DDC capable. With these monitors, X always defaults to 75,75 resolution, regardless of viewable monitor area and the resolution set. IOW, sometimes working too dumb, sometimes too clever.

4. There are ready-made 75 dpi and 100 dpi fonts. If xfs is given a working DPI setting which exactly matches one of them, then xfs won't have to do font scaling and it will considerably add to X performance.

All considered, the approach below seems most convenient to me:

i) Auto DDC reading and DPI setting is disabled by default (only enabled by an explicit parameter or xorg.conf entry).
ii) On the fly setting of xfs DPI is made very easy, so that a simple GUI utility (maybe a panel applet, or a button at kdm) can be used to switch from 75,75 dpi to 100,100 and vice versa.
iii) X always starts at the last selected DPI as default.

Now, a user can only choose between 75 and 100 dpi. Sorry, no 89,95 dpi available. But this is scarcely an inconvenience, because either 75 or 100 dpi would be really comfortable for most people. Also, since xfs will always work in ready-made font sizes, it will never have to do on the fly font scaling. So, both CPU resources will not be wasted, and fonts will look crisp even without anti-aliasing (CPU economy again). Also, the user would have the ultimate say in his font resolutions. Also there will be no more intermittent behavioral weirdness of X, and no more inconsistent behavior between DDC capable and non-capable monitors.

Adjusting the fonts in kcontrol doesn't help, because other apps who get their fonts directly from X will still display miniature (or gigantic) fonts. The problem is rooted at X and xfs, and it should be addressed there.

Currently, when the too clever behavior of X doesn't fit me, I manually specify the DPI (to either 75 or 100) as you've suggested. But a new user, or the average of grand masses (which Kubuntu is presumably addressing) feels helpless when X presents him unacceptable font sizes and there's no immediately visible remedy to solve this. And this situation is occuring more frequently then many would guess.

---

### Post by Frustration on 2005-04-02
[QUOTE=fdoving]It could help to change to, or make sure, you're running X at 100dpi.

For KDM:
take a look at: /etc/kde3/kdm/Xservers
```

:0 local@tty1 /usr/X11R6/bin/X -nolisten tcp -dpi 100

```
Make sure you got the '-dpi 100' part..
[/QUOTE]

For some reason that file isn't there.  
 :-(

---

### Post by aramazan on 2005-04-02
[QUOTE=Frustration]For some reason that file isn't there.  
 :-([/QUOTE]It's now in /etc/kde3/kdm/kdmrc file. Edit it, find the line that says```
ServerArgsLocal=-nolisten tcp
```to```
ServerArgsLocal=-nolisten tcp -dpi 100
```HTH

---

### Post by aramazan on 2005-04-03
Here's a setup tool for DPI setting. Copy-paste it into a file called "setxdpi" and then,```

sudo cp setxdpi /usr/bin/X11
sudo chmod a+x /usr/bin/X11/setxdpi
sudo chown root:root /usr/bin/X11/setxdpi
```Now run "kmenuedit" (right clicking the K button couldn't run it on Kubuntu-RC). There create a new entry under System -> Additional Applications ::

Name: setxdpi
Icon: Select any that pleases you
Comment: Global Font Size
Command: sudo /usr/bin/X11/setxdpi
[x] Run in terminal session (enabled) 
[ ] Run as a different user (disabled)

That's it. When you click on "K -> System -> Additional Applications -> setxdpi" a new konsole session opens, asks for your password, and then asks for the DPI value to be set. The script is quite talkative and hopefully newbie friendly. Yes, it is a CLI facility afterall, but better than nothing. Here is the script to paste:
```

#!/bin/bash
# This script should be run as root. It sets X DPI value permanently so that a
# user can adjust the font sizes arbitrarily.
# When asked for DPI value, the user should either enter a value between 25-300
# to set DPI statically, or 0 (zero) to let X calculate DPI value dynamically,
# according to the DDC value read from the monitor regarding viewable area size
# in millimeters, and the selected (supplied or defaulted) screen resolution.

[ `id -u` -eq 0 ] || {
 echo "You must run this script as root."
 exit 1
}

until
  cat << EOMSJ

Please enter the DPI value for desired font scaling effect.
You may either enter 0 (zero) for dynamic DPI setting at each X run, or enter
a value between 25-300. If you leave it to dynamic setting, then your fonts
will always have the same physical size regardless of your monitor size and
resolution, provided that your monitor supports DDC. If your monitor doesn't
support DDC, then dynamic setting will always give you 75 dpi (small fonts).

Please first try either 75 (small fonts) or 100 (big fonts) for best viewing
with minimum CPU consumption, and only if neither of them is acceptable for
you, then select another value.

If you select lower than 50, fonts may be too small to read. You may not
select a value less than 25.

If you select higher than 150, fonts may be too big for practical use. You
may not select a value higher than 300.
EOMSJ
  echo -en "\n\nPlease enter a DPI value between 25-300 [default=0 (auto)] : "
  read -e DPI
  [ -z "$DPI" ] && DPI=0
  # Note: -a has precedence over -o so no parenthesis grouping required.
  [ $DPI -eq 0 -o $DPI -ge 25 -a $DPI -le 300 ]
do
  echo -e "\n\n\n\n\n\nSORRY. YOU FAILED TO ENTER A VALUE OF 0 OR BETWEEN 25-300. PLEASE RETRY."
done

# Backup the pristine original as *.orj
[ -f /etc/kde3/kdm/kdmrc.orj ] || cp -a /etc/kde3/kdm/kdmrc /etc/kde3/kdm/kdmrc.orj

# Backup the previous version as *.old.YYMMDD
TARIH=`date +%y%m%d-%H%M`
cp -af /etc/kde3/kdm/kdmrc /etc/kde3/kdm/kdmrc.old.$TARIH

if [ $DPI = 0 ] ; then
  DPIVAL=""
else
  DPIVAL=" -dpi $DPI"
fi

sed "s/^ServerArgsLocal=.*$/ServerArgsLocal=-nolisten tcp$DPIVAL/" /etc/kde3/kdm/kdmrc.old.$TARIH > /etc/kde3/kdm/kdmrc

echo -e "\n\n\nYour screen DPI is set to $DPI\n\nPlease either reboot, or logout and get to the login screen and there\npress [Ctrl+Alt]+Backspace keys at once for the new DPI to take effect.\n\nNow press any key to continue."
read -n 1

```

Note: Menu entry names etc. might not be exact. I'm working in Turkish KDE env, and translating the translated KDE options back into English. So they are appoximate.

---

### Post by hachre on 2005-04-03
I have a strange problem with fonts too.
I made gnome-settings-daemon autostart but every time I do it seems to change the fonts of the menu's in programs to make em bigger...

I have all fonts in KDE set to size 12 but some fonts appear as 14...

I'll attach a few screenshots to show this issue...
When I set the font of "menus" to 12, the context menus of programs appears at 14 while the context menu of the panel appears correctly.
When I set it to 10 the context menus of programs is 12 and the context menu of the panel is 10...

Why?!

---

### Post by aramazan on 2005-04-03
[QUOTE=hachre]I have a strange problem with fonts too.
I made gnome-settings-daemon autostart but every time I do it seems to change the fonts of the menu's in programs to make em bigger...

I have all fonts in KDE set to size 12 but some fonts appear as 14...

I'll attach a few screenshots to show this issue...
When I set the font of "menus" to 12, the context menus of programs appears at 14 while the context menu of the panel appears correctly.
When I set it to 10 the context menus of programs is 12 and the context menu of the panel is 10...

Why?![/QUOTE]
The first screenshot seems OK to me except the taskbar fonts: they don't seem to match other 12 size fonts.
Second screenshot is strange, because K menu fonts are smaller than what they should be.
Third and fourth screenshots are OK, because there you got what you asked for: 10 point menu fonts.

BTW, there are a couple of more font related places:
Konq setup -> Appearance -> Font size (for fonts shown in file manager)
Konq setup -> Fonts -> Minimum and Normal font sizes (for fonts while browsing the web)

So, the small Konq fonts (in background) in the first screenshot is OK. But I can't explain the other discrepancies in 1st and 2nd images. I would suggest disabling gnome-settings-daemon and see if it makes any difference. If you want matching font sizes between Gnome and KDE apps, you could change DPI parameter of X.

---

### Post by meldroc on 2005-04-03
The way I get my fonts to behave is to put the following line into my /etc/X11/xorg.conf, in the Monitor Section:

DisplaySize     325 244

where the two numbers are the horizontal and vertical dimensions of the screen in millimeters.  Once you have that set correctly, font sizes should be a bit more sane.

---

### Post by wh0rd on 2005-08-09
It looks like **aramazan**'s post seemed to have worked, but i'm not sure if that's the only solution. If you have any other solutions to this issue please post.

---

