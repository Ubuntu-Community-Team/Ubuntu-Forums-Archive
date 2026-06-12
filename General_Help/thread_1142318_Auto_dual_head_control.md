---
title: "Auto dual head control"
date: 2009-04-29
forum: General Help
---

### Post by s.kaniff on 2009-04-29
Hi,
I want to set up a king of auto dual head control on my laptop. Basically i would like to call 'xrandr --output VGA --left-of LVDS' when I plug in a cable to my VGA port and revert back to normal when I plug out the VGA cable.

Does anyone know where in I need to put my scripts for this? Would it be somewhere in /etc/acpi ?

---

### Post by netmask254 on 2009-04-29
Refer [http://snippets.dzone.com/posts/show/6386]("http://snippets.dzone.com/posts/show/6386")

I use following script for my laptop. Unfortunately I didn't find a good way to automatically load it during system up. Though I can added the script (located in ~/bin/) to startup session, it may result the icons on Gnome panel out of order.

[FONT="Courier New"]#!/bin/bash
XRANDR_OUT=`xrandr -q`
if echo "$XRANDR_OUT"|grep -q 'VGA connected'; then
  echo 'Detected VGA connected';
if [ `echo "$XRANDR_OUT"|grep '*'|wc -l` -gt 1 ];then
  echo 'Turning off VGA';
  xrandr --output VGA --off
else
echo 'Turning on VGA';
  # turn on external monitor
  xrandr --output VGA --auto
  # set the external to be outside
  xrandr --output VGA --right-of LVDS
  # align the laptop output to be in the 'middle' of the bigger LCD.
  xrandr --output LVDS --pos 0x62
  # get the panels back where they ought to be
  gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1
  gconftool --type int --set /apps/panel/toplevels/panel_0/monitor 1
fi
else
  echo 'No VGA connected!';
  #turning off just incase
  xrandr --output VGA --off
fi[/FONT]

---

