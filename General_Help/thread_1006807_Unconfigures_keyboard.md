---
title: "Unconfigures keyboard"
date: 2008-12-09
forum: General Help
---

### Post by Fernanddo Saenz on 2008-12-09
Hello! The keyboardd of my laptop (Dell Vostro 1000, Hardy 8.04) suddenly lost its config. I have a Latin American layout and the Preferences set up such that I can compose foreign characters like vowels with grave accent, circumflex or tilde, and the At sign, using the Right Alt key as "3rd level selector".

The Prefs are still as always -nothing is changed- but now they don't work anymore! The accented vowels work with "dead keys": For example, for Acute accents (like this: á, é - these work) I hit the accent key first -nothing is seen- and then the vowel key. Only the accents which require the "3rd level selector" lost their functionality.

Any suggestions?

---

### Post by SM666AT on 2009-01-31
I have the same problem with a Dell Vostro 1000 with 8.10 (after upgrade from 8.04). I had the same problem in hardy, then added the option nodeadkeys in xkb-section of xorg.conf and had no problem any more, but now this section is commented out saying "this is handled by HAL".

can anyone help...?

thanx

Mario

---

### Post by Nepherte on 2009-01-31
Create or open /etc/hal/fdi/policy/10-keymap.fdi:
```
gksudo gedit /etc/hal/fdi/policy/10-keymap.fdi
```
and make it look like this:
```
<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.keymap">
      <append key="info.callouts.add" type="strlist">hal-setup-keymap</append>
    </match>

    <match key="info.capabilities" contains="input.keys">
      <merge key="input.xkb.rules" type="string">base</merge>

      <!-- If we're using Linux, we use evdev by default (falling back to
           keyboard otherwise). -->
      <merge key="input.xkb.model" type="string">keyboard</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name"
             string="Linux">
        <merge key="input.xkb.model" type="string">evdev</merge>
      </match>

      **<merge key="input.xkb.layout" type="string">be</merge>**
      <merge key="input.xkb.variant" type="string" />
    </match>
  </device>
</deviceinfo>
```
The bolded part is to set the language layout. Change the value to your country iso code. Any option you would have added below Section "InputDevice" in /etc/X11/xorg.conf for the keyboard can be put here in a similar way like layout, model and variant are done here. so it should look like this:
```
<merge key="input.xkb.someoption" type="string">somevalue</merge>
```
After you saved the file, you need to restart hal for the changes to have effect.
```
sudo /etc/init.d/hal restart
```

In gnome, you might have to set the keyboard to "Managed by evdev" as well.

---

### Post by SM666AT on 2009-01-31
SO, now I fixed it in 8.10: you have to specify the ISO_Level3_Shift - Key by using something like
sudo xmodmap -e "keycode 0x9c = ISO_Level3_Shift"
And then by using
xmodmap -pke > .Xmodmap
in you home directory (i.e. /home/username) you make it permanent. at the next login you are asked if you want to use these settings, and that's it.

for me it is working perfectly fine now.

best and good luck

Mario

---

