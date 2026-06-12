---
title: "Need help with tiny font bug workaround"
date: 2009-04-18
forum: General Help
---

### Post by CalSkeptic on 2009-04-18
I'm trying to make a workaround to a bug that causes 8.10 and 9.04 to boot Gnome with tiny system fonts. This can be fixed temporarily by clicking System/Preferences/Appearance, which causes the font size to return to normal.

So far, I've got the following shell script file:

#!/bin/sh
gnome-appearance-properties %F

This works, but I still need to make two improvements:

1. a statement that causes the Appearance/Preferences window to close. "Exit" doesn't work.

2. make the file execute when Gnome starts up.

Can someone help me with these two steps? Thanks!

---

### Post by joeyknuccione on 2009-04-18
> **CalSkeptic said:**
> I'm trying to make a workaround to a bug that causes 8.10 and 9.04 to boot Gnome with tiny system fonts. This can be fixed temporarily by clicking System/Preferences/Appearance, which causes the font size to return to normal.

So far, I've got the following shell script file:

#!/bin/sh
gnome-appearance-properties %F

This works, but I still need to make two improvements:

1. a statement that causes the Appearance/Preferences window to close. "Exit" doesn't work.

2. make the file execute when Gnome starts up.

Can someone help me with these two steps? Thanks!

Don't know if it'll help, but maybe try Ubuntu Tweak, just google for it.

---

### Post by codeseer on 2009-04-20
I made this bash script for you:

```

#!/bin/bash

for ((a=0; a <= 1; a++))
do

if [ $a != 0 ]
then
killall gnome-appearance-properties
else
gnome-appearance-properties %F
sleep 1
fi

done

exit 0

```

That will solve part 1, yes?

For part 2, you only need to add it to Sessions; System->Preferences->Sessions.

---

