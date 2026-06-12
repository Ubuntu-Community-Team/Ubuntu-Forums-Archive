---
title: "TabletPC (Wacom) and Jaunty"
date: 2009-04-25
forum: General Help
---

### Post by fr34k4d3113 on 2009-04-25
Hi,

I'm using Jaunty and I want to use my tablet-display. So far it already works but when I use my stylus it writes as soon as the Stylus is recognized by the tablet, not only when it touches it. When I used Windows it only wrote when I touched the display with the stylus.
How can I get this behavior under Linux?

I tried to add 
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```
to a new created /etc/hal/fdi/policy/wacom.fdi because I thought setting TPCButton to on will fix this issue.

thx

---

### Post by Favux on 2009-04-25
Hi fr34k4d3113,

I think you forgot the stylus line:
```
        <merge key="input.x11_options.Type" type="string">stylus</merge>
```
I don't think you need "TPCButton" on because that should be default for a tablet pc.  I think what you may be looking for is Button1 (the stylus tip) 1, a left mouse click?  But that should also be default.

Anyway it should probably look something like this:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <append key="wacom.types" type="strlist">eraser</append>
      </match>
    </match>
  </device>

</deviceinfo>
```
Being no .fdi guru I'm not sure if you can put the stylus options under stylus before you append eraser, it may be the other way around.  With stylus and then append eraser and then options, but I think it will work.  So I put stylus back in, added the stylus button as a right mouse click and added an eraser.  I realize you might not have some of these features.

I hope this is helpful.

---

### Post by fr34k4d3113 on 2009-04-26
Hi,

I tried it but unfortunately it makes no difference to my setup. 
With wacdump I can see that the touch with pen or eraser is recognized (only when I touch the display), but the display treats hovering over the display (recognized hovering pen, but neither touch down of eraser or pen in wacdump) also as a touch down. 
The problem is that I can't write anything because it doesen't write only while pushing the display but as soon as the stylus is nearby the display.

---

### Post by Favux on 2009-04-26
Hi fr34k4d3113,

That sounds frustrating.  What model tablet pc do you have?  Are you using the "default" linuxwacom 0.8.2-2 drivers and wacom-tools that came with Jaunty?

I forgot a line in the .fdi.  If you append eraser you need the HAL callout:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
      </match>
    </match>
  </device>


```
which is this line.
```
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
```
Is your tablet pc usb or serial?  If usb it looks like instead of the "info.capabilities" line you want:
```
    <match key="info.category" contains="input">
```
And a serial tablet pc would need some additional lines.

---

### Post by fr34k4d3113 on 2009-04-26
I tried your suggested modifications, but there's still no change. 
What I'm wondering about is, when I'm deleting the /usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi  and the /etc/hal/policy/tablet.fdi there is no change, too. I mean It is still working as when this files are existing. 

I have a USB-Tablet (Asus R1E, worst laptop I ever had so far..) and I'm using a self compiled version of the current wacom-drivers from sourceforge because the jaunty-shipped doesn't work (errorcode -113 while loading them, if I remember correctly)

---

### Post by Favux on 2009-04-26
Hi fr34k4d3113,

OK, I think I'm getting a handle on your situation.  If you compiled 0.8.3-2 from the LWP site you can probably use xorg.conf like before.  This is the first linuxwacom version that works with the new Xserver 1.6 in Jaunty. 

With the "native" Jaunty 0.8.2-2 drivers we've discovered that you need to replace the wacom.ko kernel driver (for usb) with the 0.8.3-2 wacom.ko and then 0.8.2-2 in Jaunty works.  These Jaunty drivers were specially patched by Timo Aaltonen to work with Xserver 1.6 and HAL.

But even with the new wacom.ko it still has problems.  Basically the callout from the .fdi file returns HAL names that linuxwacom doesn't recognize.  So rec came up with a script that translates them which you start before Xserver starts.

Please see the Jaunty Users section (near the top) on this thread:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  for more explanations, options, and HOW TO's.

---

### Post by fr34k4d3113 on 2009-04-28
Thanks Favux, now it works nearly perfect. One last question to perfection ;) When I rotate my display the resolution (and rotation) changes automatically, what can I do that xsetwacom set stylus rotate cw (same for cursor and eraser) is invoked automatically?

---

### Post by Favux on 2009-04-28
Hi fr34k4d3113,

Great!

You want a rotation script.  You can set it up in a launcher or bind it to a key(s).  Methods 1 or 3 here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  should work for you, with luck.

---

### Post by fr34k4d3113 on 2009-04-28
Ah, perfect. I modified the script and put it into gnomes 'startup applications' to automatically change the wacom-rotation when I rotate the display. Quick and dirty, but it works ;-) 
```
#!/bin/sh 

while [ 1 ]
 do
  sleep 2
  rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

  case "$rotation" in 
    normal) 
### rotate to the normal ###
    if [ `cat /home/user/.rotate/rotatestatus` = "right" ]; then
      compiz &
      xsetwacom set stylus rotate NONE 
      xsetwacom set eraser rotate NONE
      echo "normal" > /home/user/.rotate/rotatestatus
    fi
    ;; 
    right) 
### rotate to right ###
    if [ `cat /home/user/.rotate/rotatestatus` = "normal" ]; then
      xsetwacom set stylus rotate CW 
      xsetwacom set eraser rotate CW
      echo "right" > /home/user/.rotate/rotatestatus
    fi
    ;; 
  esac
 done

```

---

### Post by Favux on 2009-04-28
Hi again fr34k4d3113,

Nice!  So you have the advantage of Tom Jaeger's method without having the wacomrotate daemon in residence.  Would you mind if I added it to the thread?

Ah, right.  Are you using the gnome display applet to rotate?

---

### Post by fr34k4d3113 on 2009-04-29
Hi, 
My Tablet is rotating automatically as soon as I physically rotate the display, that worked out of the box. According to this I only needed the possibility to rotate the tablet input functionality, too.

---

### Post by Favux on 2009-04-29
You lucky dawg,

You mean to say your tablet works with the rotatescreen.sh in /etc/acpi?  I didn't know that actually worked for anyone!  Whatever signal my swivel hinge sends is seemingly not detected by anything.  So no automagic rotation for me.

---

### Post by fr34k4d3113 on 2009-04-29
Nice, didn't know this file. I'm going to add xsetwacom to this script. I think that solution is quick, but not dirty anymore ;-)

---

### Post by Favux on 2009-04-29
Sweet!  Does it work?

---

### Post by fr34k4d3113 on 2009-04-29
It works! ;-) The only problem is, that I can only use compiz in normal mode, since I have a black bar in the lower third of the screen. While using metacity I can use the whole screen. 

```
#!/bin/sh

user="yourusername"

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/scredrittelen-rotation`
fi

case "$ROTATION" in
        right)
        NEW_ROTATION="normal"
        ;;
        *)
        NEW_ROTATION="right"
        ;;
esac
echo $NEW_ROTATION

for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXconsole;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum.0"
        fi
        /usr/bin/xrandr -o $NEW_ROTATION
        echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation

        if [ $NEW_ROTATION = "normal" ]; then
            xsetwacom set stylus rotate none
            xsetwacom set eraser rotate none
            su $user -c "compiz &"
        fi
        if [ $NEW_ROTATION = "right" ]; then
            xsetwacom set stylus rotate CW
            xsetwacom set eraser rotate CW
            su $user -c "metacity --replace &"
        fi
done

```

---

### Post by Favux on 2009-04-29
Hi fr34k4d3113,

Thanks for sharing the final product!

Rotation and Compiz don't seem to get along well.  But I though Xserver 1.6 was suppose to have some fixes, including fixing the resizing bugs in 1.4 and 1.5?  Oh well.

---

