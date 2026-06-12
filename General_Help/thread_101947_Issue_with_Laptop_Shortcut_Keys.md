---
title: "Issue with Laptop Shortcut Keys"
date: 2005-12-10
forum: General Help
---

### Post by Caligatio on 2005-12-10
I finally got both my headphones and speakers working with my ASUS Z71V

The issue that now I face is that volume up/down and mute shortcut keys affect the microphone channel and not the PCM channel.

I found out what gets executed when I hit the button... it's voldownbtn.sh

Contents:

```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXconsole
if [ x"$XAUTHORITY" != x"" ]; then
    acpi_fakekey 174
fi
```

I have no idea what the acpi_fakekey 174 does

---

### Post by larytet on 2007-01-26
in my case (Sony VAIO VGN-S460) this is 

#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_VOLUMEDOWN

I am using version 6.10

I tried to control ALSA mixer with amixer 

amixer set 'PCM' 100
does the trick - I wil post the script in a day or two
If you know bash a little bit try to copy and modify this one
/etc/acpi/sonybright.sh
this script does almost everything, just remove all BRIGHTNESS things and replace dimmer by amixer
you can keep a current value for the PCM in any file. For example /etc/acpi/pcm_volume


I had a moment to write the script

put the following in the /etc/acpi/voldownbth.sh
```

#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_VOLUMEDOWN

PCM_VOLUME=$(cat /etc/acpi/pcm_volume)
   if [ "$PCM_VOLUME" -gt 1 ]; then
      PCM_VOLUME=$(( $PCM_VOLUME - 32 ))
      echo $PCM_VOLUME > /etc/acpi/pcm_volume
      echo "PCM_VOLUME=$PCM_VOLUME"
      [ -x /usr/bin/amixer ] && /usr/bin/amixer sset 'PCM' $PCM_VOLUME > /dev/null
   fi

```

/etc/acpi/volupbth.sh
```

#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_VOLUMEUP

PCM_VOLUME=$(cat /etc/acpi/pcm_volume)
   if [ "$PCM_VOLUME" -lt 255 ]; then
      PCM_VOLUME=$(( $PCM_VOLUME + 32 ))
      echo $PCM_VOLUME > /etc/acpi/pcm_volume
      echo "PCM_VOLUME=$PCM_VOLUME"
      [ -x /usr/bin/amixer ] && /usr/bin/amixer sset 'PCM' $PCM_VOLUME  > /dev/null
   fi

```


you can choose any ALSA control, not necessary PCM, for the list of controls
sudo  amixer scontrols


Now if anyone would help me with NVIDIA dual screen support

---

