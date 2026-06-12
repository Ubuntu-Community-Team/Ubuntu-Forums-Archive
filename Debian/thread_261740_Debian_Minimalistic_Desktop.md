---
title: "Debian Minimalistic Desktop"
date: 2006-09-20
forum: Debian
---

### Post by era86 on 2006-09-20
Hey yall! I want to run sarge on my home computer and I need it to run as minimal as possible. The comp is slow and I don't want to use much resources if I don't have to.

My question is... I want to use Openbox as my main desktop and I would like to be able to play multimedia as well. I have the multimedia down from the tutorials I've found and I think I can handle that myself. What files do I need to install openbox and have it functioning correctly?

In Ubuntu, it is easy to install.. just apt-get install it. But in sarge I know that you need to install some x stuff. That's what I need help on.

Thanks!

---

### Post by croak77 on 2006-09-20
It should be the same as in Ubuntu. Make sure you have xserver-xorg and x-window-system-core.

---

### Post by moore.bryan on 2006-09-20
*did you hit-up the ob website for the dependencies?*

---

### Post by croak77 on 2006-09-20
You don't have to 'hit-up' anything. Openbox is in the debian repo's. It's the same commands as Ubuntu. apt-get install openbox.

---

### Post by moore.bryan on 2006-09-20
> **croak77 said:**
> You don't have to 'hit-up' anything. Openbox is in the debian repo's. It's the same commands as Ubuntu. apt-get install openbox.
*thanks, croak... i didn't know debian had it in there repos too.*

---

### Post by era86 on 2006-09-20
well you need some of the x stuff.. that's what I had questions about.. i did a debian base install only.. thanks though croak! ill try that out

---

### Post by kerry_s on 2006-09-20
su
apt-get install x-window-system-core xterm gdm openbox obconf menu

that should get you bare bones, i recommend synaptic so you can see the installed stuff and trim it further by removing some of the base stuff you don't need, like the extra xorg drivers for cards you don't have, the raid stuff if you don't use that,...

Then just install light weight apps like rox-filer(file manager),firefox(if your system can handle),dillo(very fast web browser)gaim(for im and checks mail), leafpad(editor)...

after you finish installing you can delete /usr/share/doc and /usr/share/man if you want to get back some extra space(about 150+mb depending on what you install) don't forget to delete the temp files in synaptic(settings>preferences>files>delete cached package files).

I just installed openbox yesterday to see what it looks like(when you see the gray screen, that means it's loaded, there's no background) just right click and launch "terminal emulator" and do> update-menus <and that will give you a debian menu instead of just xterm.

I'm just fixin to do a server-install+openbox, right now i just added openbox to my wmaker install to see if it's worth trying. So far it's like a bare bones fluxbox, if you've used that before you should pick up pretty quick. Here's a shot of mine with a background and conky, it's so empty it's scary, but everything you need is in the right click. ;)

---

### Post by K.Mandla on 2006-09-21
Boy, that screenshot is veeeeery tempting. ... It's been a while since I did an openbox install. Maybe I need to brush up tomorrow. ... :biggrin:

---

### Post by kerry_s on 2006-09-21
Hey, I just got finish setting most of it up. I did the server+openbox install. I've been trying the different WM's for weeks now and i think openbox is one of those super fast ones, everything is so dang quick, there is a real difference how apps feel from wm to wm even though there the exact same apps. I'll run it for awhile and see if it grows on me. ;)

---

### Post by era86 on 2006-09-21
yea.. i ran openbox with ubuntu for awhile and I decided to explore what i can do with just a bare install of debian.. should be alot of fun to do! keep me posted on some new stuff and ill let you know how my install goes

---

### Post by era86 on 2006-09-22
I am having some issues with my x-window-system-core install. When it gets to the part where it is setting up xfonts-100dpi, it freezes up. Anyone know what this could be?

---

### Post by kerry_s on 2006-09-22
Maybe a bad archive? Try taking out the region part. Example->

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
to
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

Then do the> apt-get update <again then> apt-get install x-window-system-core

---

### Post by era86 on 2006-09-25
Thanks kerry_s that about did it.

---

### Post by kerry_s on 2006-09-25
I'm glad that worked for you. i'm just now installing straight openbox again. I was trying other wm's and decided i liked just plain old openbox best.lol. I just installed dillo 5 minutes ago so i can grab FF 2b2 on line.

---

### Post by era86 on 2006-09-25
Got the base debian system installed, openbox running, xdm, and dillo! My minimal system is complete! Now to mess around with all of this stuff. Thanks for all the help people!

era

---

### Post by era86 on 2006-09-26
I am curious.. will I be able to run nm-applet in debian?

---

### Post by tturrisi on 2006-09-26
> **era86 said:**
> I am curious.. will I be able to run nm-applet in debian?
yes!
network-manager-gnome is in the debian repositiries for testing (etch) & unstable (sid), thus if use stable (sarge) you will have to find a backport of the package.

---

### Post by era86 on 2006-09-27
so if i add the unstable stuff to my repositories, i should be able to do apt-get install nm-applet? because I cannot find the package.. or do I have to install by source?

---

### Post by era86 on 2006-10-02
Hey everyone.. I have been playing around with Debian Sarge on my desktop now and I have it working great.. I use openbox as my main environment.

I like the setup I have, but now I am trying to use debian on my laptop ( my primary comp ) and it needs more than just a gui desktop.

I was wondering what you girls or guys use to handle these tasks:
1. wireless internet with wpa
2. music player to play mp3s and such
3. video player to play any file format
4. internet browsing with multimedia
5. power management

If possible, I am trying not to fill up my laptop with gnome! Any feedback at all would help me out! Thanks.

era

---

### Post by kerry_s on 2006-10-02
1. don't know
2. mplayer and xmms (with w32codecs and libdvdcss2)
3. see 2
4. Firefox has the best support for plugins
5. don't know, i always leave my computer and just turn the screen off after about 5 min. of inactivty, i use xset.->
xset s off off 
xset +dpms 
xset dpms 0 0 300

---

### Post by skymt on 2006-10-02
2. Look into [mpd](http://www.musicpd.org/). I'm using Amarok at the moment, but that's too heavy for an Openbox desktop.

3. mplayer. I've never run into a valid, non-DRM file mplayer couldn't play.

4. If you need multimedia, you probably want Firefox. Konqueror also has good multimedia support with the kmplayer plugin, but that pulls in most of KDE. Some people have had success with Opera (my browser of choice) and mozplugger, but I haven't.

5. xset is surprisingly powerful. Read the man page.

---

### Post by era86 on 2006-10-03
> **skymt said:**
> 2. Look into [mpd](http://www.musicpd.org/). I'm using Amarok at the moment, but that's too heavy for an Openbox desktop.

3. mplayer. I've never run into a valid, non-DRM file mplayer couldn't play.

4. If you need multimedia, you probably want Firefox. Konqueror also has good multimedia support with the kmplayer plugin, but that pulls in most of KDE. Some people have had success with Opera (my browser of choice) and mozplugger, but I haven't.

5. xset is surprisingly powerful. Read the man page.

no one uses wireless internet here?! surprising.. my nm-applet isn't working.. it can't seem to find any of my networks!

---

### Post by skymt on 2006-10-03
> **era86 said:**
> no one uses wireless internet here?! surprising.. my nm-applet isn't working.. it can't seem to find any of my networks!

Most Wi-Fi users on Ubuntu seem to use the auto-magical GNOME Network Manager. When that doesn't work, it seems to be rough going.

---

### Post by era86 on 2006-10-03
Well.. I'm using openbox and it worked on that before. The only problem is, no networks show! I am so lost.. I am thinking I need to update the kernel to 2.6 from 2.4 and disable hotplug.. any ideas?

---

### Post by Rumor on 2006-10-03
Hmm, I don't use wireless, so I am clueless. Is this link helpful? [http://jkossen.nl/articles/2006/08/05/debian-etch-and-networkmanager](http://jkossen.nl/articles/2006/08/05/debian-etch-and-networkmanager)

---

### Post by era86 on 2006-10-04
That might just work. I will try that when I get my laptop at home! Thanks alot Rumor.

---

### Post by Anonii on 2006-10-04
Completely off-topic, but when I see such topics, I always feel sad for the 1000$ I wasted to buy my computer... When I could have used 450$ and be fine with that for a long time... I wont repeat the same mistake.

---

### Post by RAV TUX on 2006-10-04
> **era86 said:**
> Hey yall! I want to run sarge on my home computer and I need it to run as minimal as possible. The comp is slow and I don't want to use much resources if I don't have to.

My question is... I want to use Openbox as my main desktop and I would like to be able to play multimedia as well. I have the multimedia down from the tutorials I've found and I think I can handle that myself. What files do I need to install openbox and have it functioning correctly?

In Ubuntu, it is easy to install.. just apt-get install it. But in sarge I know that you need to install some x stuff. That's what I need help on.

Thanks!

Try Aquamorph, a simply beautiful XFCE distro. based on Morphix/Knoppix/Debian

---

### Post by tturrisi on 2006-10-05
yes, do a apt-get dist-upgrade to upgrade from sarge to etch.  Presently, sarge is dated and etch will become the new stable in 2 months.  The 2.6 kernel is better!

---

### Post by era86 on 2006-10-13
I am now running etch with pypanel and openbox. Here is a question that I've been pondering. I have the network-manager applet running in my tray. Is there a battery moniter and volume control moniter available for the system tray as well?

---

### Post by Xilon on 2006-11-10
I have just finished installing a similar barebones system... nothing but openbox :) I just wanted to see how it would work out and if I could even do it hehe.

I have a few questions though;
[LIST=1]
[*]I'm not sure if it's the gfx driver's fault, I will install the nvidia driver in a minute, but the resolution is really weird. There are "lines" of blurryness on the screen, it's kind of hard to explain. Anyone know how to fix this? :P And on a similar not any idea how to change the resolution? [FIXED: Changed vesa driver to nv]
[*]How do I change the GTK theme? I am getting the default (not clearlooks, the win95 type) theme and I would love to have it match the openbox theme [ANSWER FOUND: You need to create a .gtkrc-2.0 config, [link]("http://gentoo-wiki.com/HOWTO_Openbox")]
[*]Currently I am using xinitrc (ie. via startx) to startup openbox, is there any way to automatically log into the session? Or do I have to use XDM or something like it to have a GUI login (I just don't want it to start to the tty)?
[*]Anyone know of a minimalistic image viewer? Eog or gThumb were ok but I don't want to install all the gnome libraries this time :(
[*]Anyone know how to setup ivman or equivalent? (for USB automounting)
[/LIST]

---

### Post by tturrisi on 2006-11-11
4. xzgv is a good lightweight image viewer

from Synaptic description:

[SIZE="1"]Picture viewer for X with a thumbnail-based selector
xzgv is a picture viewer for X, with a thumbnail-based file selector.
It uses GTK+ and Imlib. Most file formats are supported, and the
thumbnails used are compatible with xv, zgv, and the Gimp. It can also
be used with `xzgv file(s)', to effectively bypass the file selector.
For more on how xzgv works and how to use it, do `info xzgv' or `man
xzgv' once it's installed.

xzgv differs from other picture viewers for X in that it uses one
window for both the file selector and viewer, it (unlike xv) allows
both scrolling and fit-to-window methods of viewing large pictures,
and it (unlike xv and some others) doesn't ever mangle the picture's
aspect ratio.

It also provides extensive keyboard support; if you prefer using the
keyboard, this is almost certainly the best viewer for you. But it
doesn't skimp on the mousey stuff, either.

Note that this program is written by the author of the svgalib-based
"zgv", and has similar features.[/SIZE]

---

