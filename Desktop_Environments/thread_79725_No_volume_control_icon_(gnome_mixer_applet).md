---
title: "No volume control icon (gnome mixer applet)"
date: 2005-10-20
forum: Desktop Environments
---

### Post by jrblevin on 2005-10-20
The gnome volume control applet isn't working for me in Breezy.  I started running the preview release when it came out and the applet was working fine until a few days before the final release came out.  I can only assume that one of the updates caused the problem, but now the icon doesn't show up on the panel.

The mixer_applet2 process is running, and if I kill it, it immediately asks me if I'd like to restart it, but the icon never shows up on the panel.  If I kill the process, and then try to add the applet to the panel again from the beginning, it does the same thing...it never shows up.

The gnome-volume-control program works fine, I can adjust the mixer settings so there is no problem with my sound or anything, just the applet.  Any ideas about what the problem might be or how I could troubleshoot it?

Thanks,

Jason

---

### Post by Vermyndax on 2005-10-21
Same thing is happening here... weird... it was working for me initially in Breezy release, but now it's disappeared and won't come back...

---

### Post by Vermyndax on 2005-10-21
Just out of curiousity... did you change your icon theme?

I changed mine to eXperience and turns out, eXperience doesn't feature a volume control icon it would seem.  If I change my icon theme back, it comes back.

FYI.

---

### Post by jrblevin on 2005-10-21
[QUOTE=Vermyndax]
Just out of curiousity... did you change your icon theme?
[/QUOTE]

Thank you!  That was the problem!  The interesting thing is that I've been using this icon theme (Kreski Lines) for over a year and the volume control didn't disappear until about two weeks ago.

When I switched back to the default theme, there were actually two mixer applets running :)

Thanks again,

Jason

---

### Post by giopas on 2005-10-21
even with "nuvola" theme, I can't see the audio controller on systray... :(

enjoy, ;)
giopas

---

### Post by rykel on 2005-10-21
[QUOTE=Vermyndax]Just out of curiousity... did you change your icon theme?

I changed mine to eXperience and turns out, eXperience doesn't feature a volume control icon it would seem.  If I change my icon theme back, it comes back.

FYI.[/QUOTE]

Hey, that solved my problem too!!  Thanks a lot, coz I have been contemplating a fresh install over this irritating, "disappearing" volume control applet. never had this problem before!!

btw, this missing applet is definitely a BUG imho.

---

### Post by anando on 2005-10-21
I reported this some time ago - 
[http://ubuntuforums.org/showthread.php?t=71895](http://ubuntuforums.org/showthread.php?t=71895)

It works only for certain themes and not for others - does anyone know a work around ? One more reason to believe that Breezy was a case of packing too much too soon.

Anyways.
Anando.

---

### Post by jrblevin on 2005-10-27
In the case of the Kreski-Lines theme, I think the problem lies with the theme itself and not Breezy.  Open the file ~/.icons/Kreski-Lines/index.theme file and find the line following line:

```
#Inherits=industrial
```

This line is commented in the original version of the file. Remove the comment and change it so that it reads

```
Inherits=gnome
```

Then, any icons that are missing from the theme (including the volume control applet) will be replaced by those from the default Gnome theme.

---

### Post by jcaceres on 2006-03-01
I had the same problem and i resolve it ..
follow the instrunctions ..
You have to know the "icons theme name"  that is un use on your desktop. That you can do it with:

 ls -l $HOME/.icons 
or system --> Administration --> Theme --> Theme Details --> Icons

Then you  execute .. 

cd /usr/share/icons/gnome && tar -cvf $HOME/.icons/<ICON_THEME_NAME>/vol.tar `find ./ -type f -name "*vol*" -print `

Where ICON_THEME_NAME is the current "icons theme name".

then you execute .. 

cd $HOME/.icons/<ICON_THEME_NAME>&& tar -xvf vol.tar

and it's ready ... 

Please send a feedback to know if it works ...

---

