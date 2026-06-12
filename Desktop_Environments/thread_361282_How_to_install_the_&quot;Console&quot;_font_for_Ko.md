---
title: "How to install the &quot;Console&quot; font for Konsole?"
date: 2007-02-14
forum: Desktop Environments
---

### Post by xnd on 2007-02-14
Hello!

Please, I'm begging you, that font was keeping my eyes alive. I work a lot from the Konsole and I really need that font. Please, if anyone knows how can I get it back.. it will be VERY much appreciated!

I'm running Kubuntu Edgy. 

THANK YOU!

---

### Post by xnd on 2007-02-14
without this font, I really can't work so i see no other alternative than going back to fedora. Ubuntu is WAY better than fedora but I NEED THAT FONT!

I AM  BEGGING YOU!!!! 

If anyone knows how to set the console font so it will show up in the font chooser for Konsole, i will be forever appreciating.

The font i'm looking for is located here:
/usr/share/apps/konsole/fonts/console8x16.pcf.gz

how do i use it with Konsole ?! PLEASE!

---

### Post by highneko on 2007-02-14
What's in the [COLOR="Red"]/usr/share/apps/konsole/fonts/console8x16.pcf.gz[/COLOR] file? If it's a true type font then maybe you could try copying it to your [COLOR="Red"]~/.fonts [/COLOR]directory. You would have to make the directory first; [COLOR="Red"]mkdir ~/.fonts[/COLOR]. This is just a guess. Might be worth a try. Good luck, have fun.

---

### Post by polomint on 2007-03-30
you might need to turn on bitmap font rendering if not enabled already. 

to to do this open a terminal and enter:

```
sudo dpkg-reconfigure fontconfig-config
```

select native rendering, automatic AA, and answer yes when asked to enable bitmap fonts. 

then update font cache with:

```
fc-cache -f -v ~/.fonts
```

assuming the fonts have been copied to ~/.fonts

finally log out, hit <ctrl>+<alt>+<backspace> to restart X.  log back in and you should be able to select the font in the standard way.

hope this helps...

---

### Post by gijsbrecht on 2007-04-11
> **polomint said:**
> you might need to turn on bitmap font rendering if not enabled already. 
(...)
finally log out, hit <ctrl>+<alt>+<backspace> to restart X.  log back in and you should be able to select the font in the standard way.

hope this helps...
This worked for me

---

### Post by haizaar on 2008-05-13
The much cleaner solution is here:
[https://wiki.kubuntu.org/console8x16](https://wiki.kubuntu.org/console8x16)

---

