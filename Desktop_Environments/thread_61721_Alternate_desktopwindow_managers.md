---
title: "Alternate desktop/window managers"
date: 2005-09-01
forum: Desktop Environments
---

### Post by dahli.llama on 2005-09-01
OK, I'm currently using the default Ubuntu Gnome desktop settings with Nautilus creating my desktop and gnome-panel for menus.  I do have fbpanel installed and I'm using that for the taskbar.

I want to try out some different options for guis and would love some suggestions.  I tried enlightenment, but it seemed to cause problems with Cedega and some games and in the end I got rid of it.

I really like the simplicity of Gnome, so I'd prefer to keep that.  I also hate desktop icons and much prefer launchers.

Another thing I want to know of is different terminal tricks.  I had the eterm as part of my desktop thing, but I didn't like having to minimize my windows to see it.  Are there any other cool things like that for Eterm of any of the other terminals?

Thanks in advance.

Andy

---

### Post by xmastree on 2005-09-01
Try [ICEWM]("http://icewm.org"), it's much lighter than gnome, so if you don't like all the fancy stuff it should be ok, and depending on your system if might improve the speed.

It's available in synaptic.

---

### Post by plb on 2005-09-01
[QUOTE=][/QUOTE]
 I always just used fluxbox and before fluxbox came out blackbox mmmm minimal ;]

---

### Post by zgoda on 2005-09-02
IceWM can be used as window manager for Gnome instead of dog-slow metacity, it just replaces window decorations and few other things, but it makes running Gnome reasonably faster.

---

### Post by dahli.llama on 2005-09-02
I guess maybe another question I should ask, is what exactly does Gnome give me?

If I have gnome installed, but I'm not actually using it as a WM I can still run Gnome dependant programs correct?

The main thing I like about the default setup is the easy to use menus.  I was a windows user for a long time and the GUI menus just make the transition easier.  I don't mind config files if I can find them though.  Could I run IceWM or Fluxbox and run gnome-panel and have fully functioning menus?

Also, where do I find the file to change what programs startup when I start my Wm?  If I want gdesklets and gnome-panel to startup with Fluxbox, what do I need to edit?

Thank you from a Linux semi-newb that is loving Ubuntu.

---

### Post by jpkotta on 2005-09-02
I use [fvwm](http://www.fvwm.org).  I also like IceWM; definately try it out.  But this solution should work for any wm.  Add whatever you want to ~/.xsession:
```
if [[ -z `ps -ef | grep $USER | grep '[g]nome-panel'` ]] ; then
    exec gnome-panel &
fi
``` 
The if statement prevents gnome-panel from starting twice, which it was doing for me for an unknown reason.  Unfortunately, a few things in the menus won't work, like log out.  I use my wm's log out function; for hibernating my laptop, I added a menu item that runs 'gnome-sudo /etc/acpi/hibernate.sh'.

If you don't want to have a desktop with icons, use the --no-desktop option when starting nautilus.  You can use xkill to get rid of it if it accidentally comes up.  There are many programs to set the root window (wallpaper).  I use Esetroot.  

It sounds like you had a large terminal taking up your entire desktop.  I tried this a while ago, but like you said, it's annoying to minimize windows to get to the term.  The solution I came up with is to have two terminals (but it could really be any number) that are hidden (in my case via window shading) and binding a key combo for showing them and giving them focus.  I really like the concept.  I'm not particularly proud of my implementation, because I feel it's too complicated, but I can put it up if you like. It is fvwm specific.  Many people have terminals that drop down like the console in Quake, I think there's a special fvwm in the Hoary repositories that has this built in somehow, but I've never tried it.

---

### Post by dahli.llama on 2005-09-04
That is pretty cool idea with the terminals.

I decided on Fluxbox for now and am really liking it.  I managed to get gnome-panel and gdesklets to startup after login and I have a little dropdown terminal that seems to work alright.

Thank you for all of the assistance.

---

### Post by Joeb on 2005-09-04
[QUOTE=dahli.llama]That is pretty cool idea with the terminals.

I decided on Fluxbox for now and am really liking it.  I managed to get gnome-panel and gdesklets to startup after login and I have a little dropdown terminal that seems to work alright.

Thank you for all of the assistance.[/QUOTE]

I'm suprised that nobody mentioned XFCE ([www.xfce.org)](www.xfce.org)).  It is ligthweight (although probably not as much as fluxbox) and sounds like it has features along the lines of what you are looking for.  It is very compatable with gnome applications and uses it's own WM instead of Metacity.

---

### Post by smeager on 2005-09-05
[QUOTE=Joeb]I'm suprised that nobody mentioned XFCE ([www.xfce.org)](www.xfce.org)).  It is ligthweight (although probably not as much as fluxbox) and sounds like it has features along the lines of what you are looking for.  It is very compatable with gnome applications and uses it's own WM instead of Metacity.[/QUOTE]

I'm glad somebody else mentioned it. I use it, runs great and is faster then Gnome or KDE. Click on the image below for a bigger screenshot.

[[IMG]http://img.photobucket.com/albums/v486/smeager/xfcesnapshotthumb.png[/IMG]](http://img.photobucket.com/albums/v486/smeager/xfcesnapshot.png)

---

