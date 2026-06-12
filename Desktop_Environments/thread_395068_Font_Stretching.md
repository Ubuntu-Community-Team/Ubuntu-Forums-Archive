---
title: "Font Stretching"
date: 2007-03-27
forum: Desktop Environments
---

### Post by Musicalmidget on 2007-03-27
Hello!

I do hope this is the right place to post.  I'm still getting my bearings here.

I've just installed Ubuntu 6.06 and have also installed the Microsoft TrueType fonts package.  However, when I'm viewing websites (Firefox 2.0.0.3), I notice that the fonts on every page seem to be a little unclear.  It's hard to describe in what way they look unclear, but it looks almost as if the fonts are being stretched vertically.

I've attached two screenshots of the same website below to try and illustrate the difference between viewing in Windows XP and viewing in Ubuntu with the stretching effect.  The font on the page is correct on both operating systems, but it's much more crisp and clear when viewed on Windows XP.

I should probably point out that I'm not totally sure whether fonts are stretching in other applications too, it's just that I only really notice the problem when viewing websites.

If anyone has any suggestions on how I might be able to clear up the fonts on my Ubuntu installation, I would be very greatful.

Thanks. :)

---

### Post by Crushyerbones on 2007-03-28
Have you tried smooth fonts here?

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_smooth_fonts](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_smooth_fonts)

It doesn't seem to do anything on my rig, maybe it'll fix yours

---

### Post by Musicalmidget on 2007-03-28
I've just tried enabling smooth fonts using the instructions at the link provided.  Unfortunately it appears to have had no effect.

---

### Post by Crushyerbones on 2007-03-28
Well... If you want Ubuntu to look like windows XP you can try this

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

By the way... Why did you install 6.06? 6.10 has been out of beta for a while and in april we'll get another version of Ubuntu... Go to System>About Ubuntu and check if it's really 6.06...

---

### Post by Musicalmidget on 2007-03-28
Hi, I've given those instructions a try and fonts still look to be stretched.  It's not that I particularly want Ubuntu to look like XP, I just want to stop the fonts from looking stretched, I'm sure it's not normal.

I've recently noticed another font problem in the Ubuntu Terminal.  I've attached a screenshot to this post.  See how some of the letters seem to overlap each other?  I'm not sure if this is related, or due to something else.

As for installing 6.06, it's because I only currently have an installation CD for 5.10.  I installed 5.10 the other day and just updated it to 6.06.  When time allows, I'll consider updating to 6.10 and getting a more upto date installation CD, but for the moment I'm planning on sticking with 6.06.

---

### Post by tho on 2007-03-28
It's a known fact that the microsoft truetype fonts don't display too well when antialiased/autohinted by the freetype font renderer.

Are you positive you can't live with the default bitstream vera fonts?

---

### Post by kerry_s on 2007-03-28
It looks to me like it's the font's your using.
Terminal is suppose to use monospace fonts, which corrects that squishing together problem. Check that the terminal font is set to something like "dejavu sans mono".

---

### Post by Musicalmidget on 2007-03-28
I can live with the stretched fonts if need be, I just wondered if there was a way to fix it.  I've also just fixed the terminal font, thanks for the pointer.

I've gone to System -> Preferences -> Font to reset all fonts (other than fixed width) back to Sans.  Unfortunately, I think I may have botched something else now, since the Sans font doesn't look the same as it used to (screenshot attached).  Similarly, I'm getting the following error in the terminal.

> Fontconfig error: Cannot load default config file

I've attempted to reinstall fontconfig but it appears to have no effect.
Anyone got any ideas?

Thanks for the help so far. :)

---

### Post by tho on 2007-03-29
> **Musicalmidget said:**
> I can live with the stretched fonts if need be, I just wondered if there was a way to fix it.  I've also just fixed the terminal font, thanks for the pointer.

I've gone to System -> Preferences -> Font to reset all fonts (other than fixed width) back to Sans.  Unfortunately, I think I may have botched something else now, since the Sans font doesn't look the same as it used to (screenshot attached).  Similarly, I'm getting the following error in the terminal.

I've attempted to reinstall fontconfig but it appears to have no effect.
Anyone got any ideas?

Thanks for the help so far. :)

Have you been messing around with the system-wide fontconfig configuration files?

To me it looks like 'Sans' have been aliased to something else than the default 'Bitstream Vera Sans'. Could you try to set the fonts in System -> Preferences -> Font to 'Bitstream Vera Sans/Serif/Mono' and see if you get the default ones back?

---

### Post by Musicalmidget on 2007-03-29
Thanks, I've got the default fonts back by selecting "Bitstream Vera Sans".

I'm not sure how I might have aliased the "Sans" font to something else, but it looks like that is indeed what I've somehow managed to do.  Is there some way to undo this?

Thanks again. :)

---

### Post by tho on 2007-03-29
> **Musicalmidget said:**
> Thanks, I've got the default fonts back by selecting "Bitstream Vera Sans".

I'm not sure how I might have aliased the "Sans" font to something else, but it looks like that is indeed what I've somehow managed to do.  Is there some way to undo this?

Thanks again. :)

Local changes to font aliases and rendering options are done in the file $HOME/.fonts.conf. If it's there, try renaming it to something like .fonts.conf.bak and see if you get your default aliases back ('sans', 'sans-serif', 'mono' or 'monospace').

If that doesn't fix your problem, chances are you've fiddled with the system-wide font configurations in /etc/fonts. Try reinstalling the package 'fontconfig-config' to re-populate /etc/fonts with the default files:

$ sudo dpkg --purge --force-all fontconfig-config
$ sudo apt-get install fontconfig-config

---

### Post by Musicalmidget on 2007-03-29
Thanks again, the default fonts are now back to normal.  Although, I did run into this error...

> E: Couldn't find package fontconfig-config

...when attempting to execute this command in the terminal...

```
sudo apt-get install fontconfig-config
```

Either way, the default fonts seem to be fixed now.  The only problem I seem to be having now, is that this error keeps appearing in the terminal...

> Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

I've taken a look at the fonts.conf file, and it seems to be blank.

---

### Post by tho on 2007-03-29
> **Musicalmidget said:**
> Thanks again, the default fonts are now back to normal.  Although, I did run into this error...



...when attempting to execute this command in the terminal...

```
sudo apt-get install fontconfig-config
```

Either way, the default fonts seem to be fixed now.  The only problem I seem to be having now, is that this error keeps appearing in the terminal...



I've taken a look at the fonts.conf file, and it seems to be blank.

Ah, just remembered you were on dapper still (!). You could try the commands I mentioned above with the package 'fontconfig' if you still think that the files in /etc/fonts are not the default ones.

As for ~/.fonts.conf, just delete it if it doesn't contain anything. The fontconfig parser is probably complaining because a blank file isn't valid XML. ;) The [gentoo wiki](http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts#.7E.2F.fonts.conf) has some good examples of options you can fiddle with in ~/.fonts.conf to improve font rendering.

---

### Post by Musicalmidget on 2007-03-29
Great!  All the errors seem now to be fixed.
Thanks very much for the help.  It's much appreciated.

Thanks also for the link.  I've just applied some of the customisations for LCD monitors and the fonts are looking a little better.

I'll try not to botch anything else up now. :)

---

