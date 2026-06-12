---
title: "No desktop effects."
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by rhc on 2008-01-08
When i want to choose normal or extra from visual effects,it says "composite extension is not avaliable".
Then i tried from terminal

"compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity "

this message.

I read forums and find that i should whitelist my grapic card by 
"gksu gedit /usr/bin/compiz"
but i couldn't find exactly the name of my card.
I have ati in restricted drivers.

> # For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"


# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T 

This is the the whitelist blacklist thing from 
"gksu gedit /usr/bin/compiz"

---

### Post by Joeb454 on 2008-01-08
So you have the restricted drivers enabled?

Also you have an ATi card? Am I right in thinking?

---

### Post by Fixman on 2008-01-08
What is your vidoe card? What do you have in the Restricted drivers manager?

---

### Post by rhc on 2008-01-08
> **Joeb454 said:**
> So you have the restricted drivers enabled?

Also you have an ATi card? Am I right in thinking?

Yes.
is it wrong?
Shouldn't do it?

---

### Post by Dngrsone on 2008-01-08
Do 

```
sudo lspci
```

and see what it says for video card.

---

### Post by Kedster on 2008-01-08
This is what I did:

From command line make xorg.conf backup:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Open xorg.conf in text editor:
sudo nano -w /etc/X11/xorg.conf

Change:
Option "Composite" "0"
to:
Option "Composite" "1"

Save changes and exit editor.

From command line:
sudo apt-get install xserver-xgl

Restart X-server (Ctrl+Alt+Backspace -- I assume this works although I actually rebooted)

Go to System > Preferences > Appearance > Visual Effects and enable some of the most shameless eye candy yet seen
__________________

---

