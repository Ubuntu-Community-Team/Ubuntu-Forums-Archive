---
title: "thunderbird, alltray and dropdown menu"
date: 2005-08-09
forum: Desktop Environments
---

### Post by jasplund on 2005-08-09
I'm using thunderbird with alltray which I think is great. It'd be even better if I could rightclick on the icon to write new mail or check for new mail. Would this be possible with the -m option? how?

From "man alltray"
> -m --menu
              Add entry "menu text:command" to popdown menu.


Thanks
Johan

---

### Post by jasplund on 2005-08-11
anyone?

---

### Post by Zyberdog on 2005-08-11
I haven't tested it, but it sounds like you need to start alltray with something like:

revision1;
> -m Compose:/path/to/thunderbird -compose

revision2;
> -m "Compose:/path/to/thunderbird -compose"

revision3(final);
> alltray mozilla-thunderbird -menu "Compose:mozilla-thunderbird -compose"

---

### Post by jasplund on 2005-08-11
Thanks but then I get the Thunderbird - Choose User Profile


Johan

---

### Post by jasplund on 2005-08-11
I tried with this

> alltray mozilla-thunderbird -m "Compose:mozilla-thunderbird -remote "mailto()""

But I got this

> bash: syntax error near unexpected token `('

---

### Post by Zyberdog on 2005-08-11
[QUOTE=jasplund]I tried with this



But I got this[/QUOTE]
 have a few other ideas.. but will test them myself instead of making you do all the work :)

---

### Post by Zyberdog on 2005-08-11
Ok .. finally found a working solution :)
```
alltray mozilla-thunderbird -m "Compose:mozilla-thunderbird -remote \"xfeDoCommand(composeMessage)\""
```
It might not work if you use multiple profiles, don't know if you are.

---

### Post by jasplund on 2005-08-11
Yes it works!


thanks a lot

---

### Post by KrIaXPaTaLa on 2006-06-04
It would be very nice to have a remote command for fetching new messages :P

Let's wait and see if mozilla delivers.

Regards.

KrIaX, Portugal

---

### Post by spiral out on 2006-06-24
[QUOTE=KrIaXPaTaLa]It would be very nice to have a remote command for fetching new messages :P

Let's wait and see if mozilla delivers.
[/QUOTE]

In 'minimize to tray' ([http://minimizetotray.mozdev.org/](http://minimizetotray.mozdev.org/)) they have the option.... (and 'minimize to tray' is only for windows :(  )

[IMG]http://minimizetotray.mozdev.org/images/earlyThunderbirdmenuSmall.png[/IMG]

---

### Post by Smoothas on 2008-02-13
Hello,
I'm a "gusty" newbie, and was after some help with Alltray and thunderbird. I've looked thought the fourms, but I cannot find what I'm looking for.

I've install alltray, and got Thunderbird to sitting nicely in my tray, I've also added a menu option to compose a new email, however, I was also trying to add to that would get Thunderbird to check for new mail ( similar to the Ctrl-shift -T option ).
I've tried the -k switch, but ( and hands up here ) I must be doing something wrong as the menu command either displays the -k options ( and therefore dosn't work ), or thunderbird will not load to the tray.

I was wondering if any one with more alltray / thunderbird / Ubuntu knowledge than me ( which is not hard at the moment :) ) could help an eager to learn Noob out ?

Thanks in advance
Gerald

---

