---
title: "Openbox and gnome-settings-daemon colliding backgrounds"
date: 2008-05-08
forum: Desktop Environments
---

### Post by yohan on 2008-05-08
Hi!

I just ran a apt-get upgrade yesterday and now when i started run gnome-settings-daemon under openbox, gnome changes my background even though ive disabled "draw background" with gconf-editor. 

So when I log in now, The desktop starts with the one ive specified with feh, then it changes to ubuntu's, then changes back...and then changes to ubuntu's again. I wonder why its doing this a multiply times.

Any ideas guys? 

thanks!

---

### Post by yohan on 2008-05-12
*bump*

---

### Post by urukrama on 2008-05-13
I have no idea how to solve your problem, as I haven't used gnome-settings-daemon in a while. When I did use it, however, I never encountered this.

Was it working well before you upgraded? Perhaps something changed in gnome-settings-daemon.

Alternatively, you could use xfce-mcs-settings (the Xfce settings manager), use something like LXappearance or gtk-theme-switcher, or do it all through they gtkrc files (see my Openbox guide if you need help with this; follow the link in my signature).

---

### Post by strungoutfan78 on 2009-09-21
Not to resurrect the dead here, but I just recently ran into this same problem.  I figured since it was gnome-setting-daemon causing the problem I would just comment out those lines of code in ~/.config/openbox/autostart.sh (lines 26-28 ):
```
# Make GTK apps look and behave how they were set up in the gnome config tools
if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
 [B][COLOR="Red"]# /usr/libexec/gnome-settings-daemon &
#elif which gnome-settings-daemon >/dev/null; then
 # gnome-settings-daemon &[/COLOR][/B]
```

Once I did this, however, and it forced openbox to use xfce settings, for some reason the changes and settings I was using in xfce were not being recognized in openbox.

to fix this I also commented out line 31:

```
#xfce-mcs-manager n &
```

and added on the very next line (line 32):

```
xfsettingsd &
```

and oila.  the reason for this is that xfce-mcs-manager is deprecated and xfce4-settings-manager has replaced it.  the autostart.sh script that ships with openbox does not reflect this.  I hope this helps someone. this was driving me absolutely crazy. :guitar:

**EDIT** This is assuming, of course, that you have xfce installed.

---

### Post by strungoutfan78 on 2009-09-22
I forgot to change one very important line.  On line 30:

```
elif which xfce-mcs-manager >/dev/null; then

```

needs to be either removed or commented out and xfce-mcs-manager needs to be changed to xfsettingsd.  The whole block as I have it should look like this:

```
# Make GTK apps look and behave how they were set up in the gnome config tools
if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
 # /usr/libexec/gnome-settings-daemon &
#elif which gnome-settings-daemon >/dev/null; then
 # gnome-settings-daemon &
 Make GTK apps look and behave how they were set up in the XFCE config tools
[COLOR="Red"]elif which xfsettingsd >/dev/null; then
	#which xfce-mcs-manager >/dev/null; then[/COLOR]
  #xfce-mcs-manager n &
  xfsettingsd &
fi
```

Again, only if you're interested in using xfce rather than gnome.  I find it less boggy personally.

---

### Post by mcduck on 2009-09-22
Gnome-settings-daemon doesn't draw the wallpaper, so I really can't see how it would interfere with whatever means you use to set your wallpaper.. Are you perhaps using Nautilus as your file manager? In that case you need to start it with "nautilus --no-desktop" (since Nautilus is the program responsible of Gnome's desktop and wallpaper).

---

### Post by strungoutfan78 on 2009-09-22
During my endeavor I never once did I use Nautilus, unless the gnome-settings-daemon is causing Nautilus to be called.  Any time I logged in to Openbox with gnome-settings-daemon loaded it would behave exactly as the OP described, only mine ended up half drawn and the only way to 'fix' it was to either run 'nitrogen --restore' (again), or to grab a window and swirl it around the screen.

As suggested I installed gconf-editor and unchecked the box next to desktop:gnome:draw background.  This did absolutely nothing.  I included a screenshot here to illustrate what I just described.  If you look at the description of the 'draw background' it states "Have **GNOME** draw the desktop background."  If it were Nautilus, which I agree with you on, why would it make this statement?

Not until I rid my setup of the gnome-settings-daemon did things get back to the way I wanted them.

[IMG]http://farm3.static.flickr.com/2584/3943739303_bef371a97c.jpg[/IMG]

---

### Post by mcduck on 2009-09-23
Then something must be starting Nautilus for you, since it *definitely* is the program responsible of Gnome's wallpaper.

I mean that this is not just a guess, I know it as a fact. And I'm using both Openbox and Gnome myself, starting Nautilus in OB (or any DE/WM) brings Gnome's wallpaper and desktop icons, no Nautilus, no Gnome's wallpaper.

(the setting for drawing the wallpaper is under "desktop/gnome" in gconf because Nautilus is a core component of Gnome.)

Of course it could be that the program you use would use the information specified i Gconf to use the same wallpaper that Nautilus would use, but you mentioned that you use Nitrogen (so do I) and it definitely doesn't do anything like that.

My suggestion is doublecheking if Nautilus is running or not when you get the Gnome wallpaper. Also note that if no program writes data to the rot window it will keep it's previous contents. So if you log into Gnome, Nautilus will draw the background. Then you log out, and into OpenBox, the background will still be there (although at this point only as leftover data, with no running application actively handling it) unless some other program overwrites it...

edit: I also have yo mention that I just ran "gnome-settings-daemon" inside OpenBox, and it did absolutely nothing to my wallpaper, set by Nitrogen. Also I still have the gnome-settings-daemon -related lines in my autostart.sh. And bacause I'm also using Gnome, I of course do have the wallpaper enabled in Gconf, I kind of like having one in Gnome as well.. :))

---

### Post by strungoutfan78 on 2009-10-05
That's strange. When I run gnome-settings-daemon inside OpenBox all my windows disappear and flicker while the background immediately changes.  Once i kill the process and run 'nitrogen --restore' everything is back to normal.  Same applies if I run gnome-appearance-properties.

Somehting I did notice when checking running processes was:
```
neil@neil-desktop:~$ ps ax | grep gconf
  395 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
  448 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
```

Now I don't believe anything should be calling gconfd, should it?  How do I tell what is calling gconfd-2?  Could this be caused by running a native gnome application?

---

### Post by strungoutfan78 on 2009-10-05
I found the culprit.  In my autostart.sh I have nm-applet and firestarter.  Both of these programs call gconfd-2.  I have yet to revert my GTK apps settings and see if it still acts dodgy.

---

