---
title: "suspend on lid close works most of the time"
date: 2005-12-13
forum: Desktop Environments
---

### Post by pataphysician on 2005-12-13
i have a toshiba m35 laptop. usually when i close the lid it hibernates, and when i open the lid it pops back. about 20% of the time, however, it turns off the screen, but doesn't fully hibernate. i usually don't notice this until i sense a huge amount of heat coming out of my bag. sometimes the fan kicks on and i hear it, other times there's no fan and it just sits there and cooks itself. when i open the lid in these situations, the screen doesn't turn back on and the keyboard doesn't respond (num/caps lock don't work). i'm guessing resume isn't doing anything because the machine isn't fully hibernating?

i'd really like to figure out what's causing this. any recommendations as to what i should look at? i checked the acpi log file, but it looks the same whether hibernation works or fails:

[Tue Dec 13 17:45:27 2005] executing action "/etc/acpi/sleep.sh"
[Tue Dec 13 17:45:27 2005] BEGIN HANDLER MESSAGES

sleep.sh looks like this
```

#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXuser;

if [ x$ACPI_SLEEP != xtrue ]; then
  exit;
fi

# Generic preparation code
. /etc/acpi/prepare.sh

if [ x$LOCK_SCREEN = xtrue ]; then
  . /usr/share/acpi-support/screenblank
fi

if [ x$DISABLE_DMA = xtrue ]; then
  hdparm -d 0 /dev/hda
fi

echo -n $ACPI_SLEEP_MODE >/sys/power/state

if [ x$DISABLE_DMA = xtrue ]; then
  hdparm -d 1 /dev/hda
fi

# Generic wakeup code
. /etc/acpi/resume.sh

```

---

