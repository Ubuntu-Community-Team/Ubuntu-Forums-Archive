---
title: "[SOLVED] Help with Fluxbox background/wallpaper"
date: 2007-10-10
forum: Desktop Environments
---

### Post by cknight on 2007-10-10
Hi folks,

I'm having a problem keeping my wallpaper in Fluxbox.  I've chosen a wallpaper and it works fine if I set it in the terminal using 'fbsetbg'.  My task now is to make this stick on startup.  I've edited my ~/.fluxbox/startup to include the following:

fbsetbg -f /home/cknight/pictures/wallpaper.jpg

When fluxbox starts I see the wallpaper I choose very briefly before its replaced by the background which came with the fluxbox install (a solid (?) baby blue background).  Any ideas why my ~/.fluxbox/startup isn't able to properly keep the wallpaper or who is overriding it?  There are only two commands in my startup file, one being the fbsetbg and the other the exec command at the end.  Thanks in advance for any help!

---

### Post by yabbadabbadont on 2007-10-10
All themes now include a "background" option that will replace what you set in the startup as the theme is applied afterwards.  Create a file in ~/.fluxbox called "overlay" that contains the following:
```
background: aspect
background.pixmap: /home/cknight/pictures/wallpaper.jpg
```

See the "fluxstyle" manpage for details, but here is the section on backgrounds:
```
BACKGROUND
       Every style must specify the background option. If you don’t want your style to change the user’s background, then
       use ‘background: none’. The options ‘centered’, ‘aspect’, ‘tiled’, and ‘fullscreen’ require the ‘background.pixmap’
       resource to contain a valid file name. The ‘random’ option requires ‘background.pixmap’ to contain a valid directory
       name. For these options, fluxbox(1) will call fbsetbg(1) to set the background. The options ‘gradient’, ‘solid’, and
       ‘mod’ all require ‘background.color’ to be set. ‘gradient’ and ‘mod’ both require ‘background.colorTo’. ‘mod’
       requires ‘background.modX’ and ‘background.modY’ to be set as well. These options will be passed to fbsetroot(1) to
       set the background.

           background: centered|aspect|tiled|fullscreen|random|solid|gradient <texture>|mod|none
           background.pixmap: <file or directory>
           background.color: <color>
           background.colorTo: <color>
           background.modX: <integer>
           background.modY: <integer>

```

---

### Post by kerry_s on 2007-10-10
you should read the docs.
[http://fluxbox.sourceforge.net/docbook/en/html/chap-bg.html](http://fluxbox.sourceforge.net/docbook/en/html/chap-bg.html)

---

### Post by yabbadabbadont on 2007-10-10
> **kerry_s said:**
> you should read the docs.
[http://fluxbox.sourceforge.net/docbook/en/html/chap-bg.html](http://fluxbox.sourceforge.net/docbook/en/html/chap-bg.html)

Na, na!  Too slow!  :D

---

### Post by kerry_s on 2007-10-10
> **yabbadabbadont said:**
> Na, na!  Too slow!  :D

What! it's only what 10, 11 lines. :lolflag:

---

### Post by yabbadabbadont on 2007-10-10
> **kerry_s said:**
> What! it's only what 10, 11 lines. :lolflag:

I meant that your post was too slow.  Besides, that document is obsolete.  In the SVN changelog (or the mailing list, or somewhere) there was talk of removing the rootCommand option from the init file.

---

### Post by TeaSwigger on 2007-10-10
> **cknight said:**
> Hi folks,

I'm having a problem keeping my wallpaper in Fluxbox.  I've chosen a wallpaper and it works fine if I set it in the terminal using 'fbsetbg'.  My task now is to make this stick on startup.  I've edited my ~/.fluxbox/startup to include the following:

fbsetbg -f /home/cknight/pictures/wallpaper.jpg

When fluxbox starts I see the wallpaper I choose very briefly before its replaced by the background which came with the fluxbox install (a solid (?) baby blue background).  Any ideas why my ~/.fluxbox/startup isn't able to properly keep the wallpaper or who is overriding it?  There are only two commands in my startup file, one being the fbsetbg and the other the exec command at the end.  Thanks in advance for any help!

Hello cknight. What I do for now is:

a) Have this line in ~/fluxbox/init

```
session.screen0.rootCommand:	fbsetbg -l
```

which automatically restores your last chosen wallpaper (as recorded in the file ~/fluxbox/lastwallpaper ).

b) Have the image I want to be used as, effectively, a splash screen, specified in ~/fluxbox/startup

```
fbsetbg -f ~/.fluxbox/backgrounds/fluKbuntu.png
```

which being as I log in from KDE's kdm log in screen, I made to match:

[ATTACH]45843[/ATTACH]

:)

Or sometimes when I can fool with it (going to take some getting used to I guess), I try ROX-Filer as file manager and use its icon and background setting features in Fluxbox, which effectively supersedes part a). :)

---

### Post by kerry_s on 2007-10-10
> **yabbadabbadont said:**
> I meant that your post was too slow.  Besides, that document is obsolete.  In the SVN changelog (or the mailing list, or somewhere) there was talk of removing the rootCommand option from the init file.

my bag, i don't keep up much any more. i'm pretty settled into jwm. :)

---

### Post by cknight on 2007-10-11
Thanks for the replies.  The overlay file did the trick and I liked TeaSwigger's splash page (especially as I'm running fluxbox on top of KDM from my original Kubuntu install).  And for the record I did read the docs, well the 'startup' file comments anyway!  Does that count? :)

It says "You can set your favourite wallpaper here...".  A bit misleading if you don't understand that the style is applied afterwards and will override whatever you choose in the startup file.

---

### Post by yabbadabbadont on 2007-10-11
Just goes to show what every programmer knows.  The code always gets updated.  The comments/docs sometimes do...  ;)

(The Changelog file from the Fluxbox SVN does, however, get updated regularly.  Just FYI.)

---

### Post by trash on 2007-10-28
I've tried every possible way from the fluxbox wiki to get a wallpaper and they all fail, even the above overlay method, doesn't. I've had errors saying no wallpaper has been set, and now with the overlay i am getting no error but no wallpaper either, can anybody  help clarify.

---

### Post by yabbadabbadont on 2007-10-28
Open a terminal and use fbsetbg to try to set your desired wallpaper.  That should show you if there are any errors that are preventing it from being displayed.

---

### Post by trash on 2007-10-28
> **yabbadabbadont said:**
> Open a terminal and use fbsetbg to try to set your desired wallpaper.  That should show you if there are any errors that are preventing it from being displayed.

fbsetroot is installed and i assumed it was configured in the init file but i guess i am still missing something...

Warning: Failed to open file(/usr/share/fluxbox/nls/en_CA.UTF-8/fluxbox.cat)
for translation, using default messages.
fbsetroot 2.3 : (c) 2003-2006 Fluxbox Development Team
fbsetroot 2.1 : (c) 2002 Claes Nasten
fbsetroot 2.0 : (c) 1997-2000 Brad Hughes

  -display <string>        display connection
  -mod <x> <y>             modula pattern
  -foreground, -fg <color> modula foreground color
  -background, -bg <color> modula background color

  -gradient <texture>      gradient texture
  -from <color>            gradient start color
  -to <color>              gradient end color

  -solid <color>           solid color

  -help                    print this help text and exit

---

### Post by yabbadabbadont on 2007-10-28
fbsetroot can only set solid colors and gradients.  You have to use fbsetbg, which is just a shell script that calls an external program to set the root window wallpaper using an image file.  In a terminal window, run: ```
fbsetbg -a /path/to/wallpaper/directory/wallpapername
``` and see if it works.  If not, post the output and I'll see if I can help you.

---

### Post by trash on 2007-10-28
> **yabbadabbadont said:**
> fbsetroot can only set solid colors and gradients.  You have to use fbsetbg, which is just a shell script that calls an external program to set the root window wallpaper using an image file.  In a terminal window, run: ```
fbsetbg -a /path/to/wallpaper/directory/wallpapername
``` and see if it works.  If not, post the output and I'll see if I can help you.

fbsetbg was what I used before when i got that error message, and i got the same message using the code you gave me... I was mistaken though I have installed esetroot, so not sure where fbsetroot is coming from.

---

### Post by yabbadabbadont on 2007-10-28
Please post the **exact** command that you used when you ran fbsetbg in a terminal window.

---

### Post by trash on 2007-10-28
i've run all of em LOL, from here [http://fluxbox-wiki.org/index.php/Background](http://fluxbox-wiki.org/index.php/Background) and from this thread and the last one was the one you gave me.

---

### Post by D-EJ915 on 2007-10-28
> **trash said:**
> i've run all of em LOL, from here [http://fluxbox-wiki.org/index.php/Background](http://fluxbox-wiki.org/index.php/Background) and from this thread and the last one was the one you gave me.
why not just use Esetroot directly?

---

### Post by trash on 2007-10-28
I kept seeing fbsetroot in the lastwallpaper file so i changed that to esetroot, restarted and there was my background. WAY complicated way to get a background wow.

Thanks for the help, I still have no clue why fbsetroot was being used since I started the whole process with esetroot but oh well i gues i'll figure it out eventually:)

---

