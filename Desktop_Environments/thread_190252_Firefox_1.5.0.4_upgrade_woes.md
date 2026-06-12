---
title: "Firefox 1.5.0.4 upgrade woes"
date: 2006-06-06
forum: Desktop Environments
---

### Post by ramcosca on 2006-06-06
So I was trying to do the update to the newer version of the browser, checked a couple threads here, downloadd studd, entered through root... nothing works. How can I get this thing to work, my friends? Is it even possible?
Thanks.

---

### Post by aysiu on 2006-06-06
If you have the Ubuntu version, it won't upgrade for another week.

If you have the Mozilla version, you should be able to update it if you close it and then run it as ```
gksudo firefox
```

---

### Post by bluevoodoo1 on 2006-06-06
How about this link?
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

EDIT: Beaten.

---

### Post by aysiu on 2006-06-06
[QUOTE=bluevoodoo1]How about this link?
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

EDIT: Beaten.[/QUOTE] Not beaten. I didn't link to that.

It's a very good script, by the way. Nanotube worked hard on that. If ramcosca already has it installed in /opt, though, I'm not sure if that script will work.

---

### Post by ramcosca on 2006-06-06
[QUOTE=aysiu]If you have the Ubuntu version, it won't upgrade for another week.[/quote]"Ubuntu version" as in "the one that came with the OS"?

[quote=aysiu]If you have the Mozilla version, you should be able to update it if you close it and then run it as ```
gksudo firefox
```[/QUOTE]:-k Mozilla is the one I download directly then, I presume. I downloaded it, opened the file, and clicked on 'firefox'. It opened the 1.5.0.4 version, but without the skin I had just previously installed in the 1.5.0.3. Closed. Clicked the Panel icon for Firefox and it opened with the skin... on 1.5.0.3. Again, the same happens with Applications > Internet > Firefox Web Browser... but it's logical, since the Panel one is just a link to this one.

How can I overwrite/change this for it to run the newer version?

[QUOTE=bluevoodoo1]How about this link?
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

EDIT: Beaten.[/QUOTE]
I had read in a previous thread that this linked to an older version?
[Edit] [Reference]("http://ubuntuforums.org/showthread.php?t=189450&highlight=firefox+1.5.0.4").

Thanks for the fast replies.


[Edit, again]
What's this mean: "installed in /opt"? I'm new to Linux!

---

### Post by ramcosca on 2006-06-06
I should've listened in the first place.

The gksudo one I had tried without positive results, but the nanotube one worked.

Thanks for the help.

---

