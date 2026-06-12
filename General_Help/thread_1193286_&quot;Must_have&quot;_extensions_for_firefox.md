---
title: "&quot;Must have&quot; extensions for firefox"
date: 2009-06-21
forum: General Help
---

### Post by mbreezy on 2009-06-21
Okay, so I put Ubuntu on my wife's laptop and she loves it so far...  She's computer illiterate, but Ubuntu is so easy even the most inexperienced can use it.  Anywho...  She plays flash-based games on Facebook and noticed there's some faults with the flash.  Example, on one of her games a scroll bar is missing but it was there when she used FF on Windows.

So this leads me to the title of this thread...  What are some "must have" extensions for firefox on Ubuntu?  What extensions are necessary to get it back to working like a Windows machine.  I have Shockwave Flash 10.0 on here, but didn't see anything newer.  What else do I need to get this browser rockin?

---

### Post by blueridgedog on 2009-06-21
Essential to me is adblock plus.

---

### Post by SuperSonic4 on 2009-06-21
> **blueridgedog said:**
> Essential to me is adblock plus.

And to me.

Adblock Plus
Flashblock (noscript is good but whitelisting gets annoying)
British English Spell Checker
Video Downloadhelper

---

### Post by tubbygweilo on 2009-06-21
I would like to add NoScript, Flashblock, MediaPlayerConnectivity & CopyPlainText.

---

### Post by paperplate9 on 2009-06-21
Flash has always sucked on linux (for me). Extensions won't fix that.

---

### Post by izizzle on 2009-06-21
I really like [Fasterfox]("https://addons.mozilla.org/en-US/firefox/addon/9148").

---

### Post by lovinglinux on 2009-06-21
> **mbreezy said:**
> So this leads me to the title of this thread...  What are some "must have" extensions for firefox on Ubuntu?  What extensions are necessary to get it back to working like a Windows machine.  I have Shockwave Flash 10.0 on here, but didn't see anything newer.  What else do I need to get this browser rockin?

Flash is not an extension is a plugin.

> From [http://en.wikipedia.org/wiki/Plugin#Plug-ins_and_extensions](http://en.wikipedia.org/wiki/Plugin#Plug-ins_and_extensions)

Plug-ins differ from extensions, which modify or add to existing functionality. Plug-ins rely on the host application's user interface and have a well-defined boundary to their possible set of actions[1]. Extensions have fewer restrictions on their actions, and may provide their own user-interfaces. Mozilla Firefox added support for extensions to help to decrease the size of the host application and to offer optional functions. Mozilla Firefox and related software products use the term "Add-on" as an inclusive category of augmentation modules that consists of plug-ins, themes, search engines and a well-developed system which aims to reduce the feature creep that plagued the Mozilla Application Suite.


Flash probably won't work like on Windows, because flash sucks on Ubuntu (specially 9.04) with every browser. If you are interested on improving Flash experience, then try [this](http://ubuntuforums.org/showthread.php?t=1146943) and [this](http://ubuntuforums.org/showthread.php?p=7394346) .

Additional threads about flash problems:

[flash jaunty](http://www.google.com/search?q=flash jaunty+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0), [flash 9.04](http://www.google.com/search?q=flash 9.04+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0), [flash performance](http://www.google.com/search?q=flash performance+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0), [flash chop](http://www.google.com/search?q=flash chop+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0), [flash stuttering](http://www.google.com/search?q=flash stuttering+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0), [flash issues](http://www.google.com/search?q=flash issues+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0), [flash video](http://www.google.com/search?q=flash video+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0)



If you are interested on extensions then check [this thread](http://ubuntuforums.org/showthread.php?t=1171450). Firefox is the most extension rich browser available. You can browse extensions on the [Mozilla addon site](https://addons.mozilla.org).

[My extension list. I'm currently using more than 40 extensions.](http://lovinglinux.megabyet.net/?p=36)

---

### Post by gettinoriginal on 2009-06-21
You can also try [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html), it really sped firefox up for me.  As for the other suggested extensions: +1  :P

---

### Post by lovinglinux on 2009-06-21
I forgot about this:

> **lovinglinux said:**
> You could also try to optimize Firefrox databases. There is a tutorial somewhere about this with an optimization script, but I can't find it. You can try my own script, which is not elegant. Follow instructions below:

1 ) install [sqlite3](apt:sqlite3)
2) create an empty file where you save your personal scripts (usually ~/bin) and name it *firefox-databases*, then right-click on it, select *Preferences*, then *Permissions* tab, then select the option "*Allow to execute as program*".
3) Create a new empty file in the same folder and name it *firefox-optimize*, then add the code below to it and save it. 

```

#!/bin/bash

killall firefox

echo "#!/bin/bash" > $HOME/bin/firefox-databases

echo "" >> $HOME/bin/firefox-databases

find $HOME/.mozilla -type f \( -name "*.sqlite" \) | sed 's/.*/sqlite3 &/g' | sed 's/.*/& "vacuum"/g' >> $HOME/bin/firefox-databases

$HOME/bin/firefox-databases
```

Then make it also executable and run it from the terminal.

```
firefox-optimize
```

The script above will basically search for all sqlite databases on the ~/.mozilla folder, create a new script to optimize these databases, save it as *firefox-databases* in your script directory and will execute it.



---

