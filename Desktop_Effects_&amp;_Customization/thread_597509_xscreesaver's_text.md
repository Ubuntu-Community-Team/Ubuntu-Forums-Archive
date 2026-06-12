---
title: "xscreesaver's text"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by gcbzzzz on 2007-10-30
all screesavers uses the same input for text (and images, etc)
it's the output of /usr/bin/xscreensaver-text

The default is a lame ubuntu newsletter.... 
Makes most screensavers boring and useles.
change to:
```

#!/bin/sh
fortune -a

```

and you have a much better option.

If you like phosphorous, use:
```

#!/bin/sh
echo
echo
echo
echo
# remove forced line breaks, even with dash
# compress white space
# make it pretty for 26columns, when it's not the signature
# the last one does not seems to work... was supposed to make Q: A: look better...
#/usr/games/fortune |sed -e 's/-\?\n/ /g'|sed -e 's/  */ /g'|
/usr/games/fortune -a fortunes          |\
sed -e 's/-\?\n/ /g'                    |\
sed -e 's/  */ /g'              |\
sed -e 's/.\{24\} /&\n/g'  |\
sed -e 's/^/ /'         |\
sed -e 's/\t+/\t/'
sleep 30
exit 0

```

newbie note: to edit the file, use:
gksudo gedit /usr/bin/xscreesaver-text

cheers,

---

### Post by K.Mandla on 2007-10-31
Moved to Desktop Effects and Customization.

---

