---
title: "Turning on secondary display logs out xfce"
date: 2013-01-06
forum: Desktop Environments
---

### Post by telewizor on 2013-01-06
Hi all,

I am trying to set up dual displays on xubuntu 12.10, using desktop computer with an additional video card. The main display is connected to an external card and works perfectly. The secondary display is the VGA monitor and is connected to an onboard VGA. I go to the 'Display' section and I have: 

for the main display (which works fine):
[IMG]http://i.imgur.com/4q3h0.png[/IMG]

for the secondary display (which does not work): 
[IMG]http://i.imgur.com/Kbj6l.png[/IMG]

When I tick 'use this output', xubuntu logs off, and it's impossible to log back. You can see this here as a movie:
[https://www.dropbox.com/s/0ggovzk37hjmwn9/VID_20130106_191146.mp4](https://www.dropbox.com/s/0ggovzk37hjmwn9/VID_20130106_191146.mp4)

To fix logging in issue, I am switching to the console, then editing displays.xml, to turn off the vga monitor.
I am changing:
    <property name="VGA1" type="string" value="Monitor">
      <property name="Active" type="bool" value="true"/>

to 'false'. 

Then I can log in again. But still, only the primary display is in use. The secondary display (the VGA one) shows 'green' light on its activity led and seems to be recognized, but it's blank all the time. 

Here are: 
My displays.xml: [http://pastebin.com/1u1aSryY](http://pastebin.com/1u1aSryY)
My xrandr output: [http://pastebin.com/WSWqvW35](http://pastebin.com/WSWqvW35)
My Xorg.log - just for the 'tick' event: [http://pastebin.com/q6tiqmy9](http://pastebin.com/q6tiqmy9)

Hardware details:
motherboard: gigabyte z77x-d3h
pci-ex video card: gigabyte hd-7950
xubuntu 12.10

the non-working display is connected to motherboard vga output. 

I will be very grateful for any help and advice. Thank you!

---

### Post by telewizor on 2013-02-25
I will reply to myself about the problem resolution. It's actually a workaround. Secondary VGA monitor works when it's connected to the gigabyte card (so both displays are connected to the same card). As the monitor has only vga connector, I have used the mini-displayport to vga adapter. The following command enables secondary display (I have placed that in rc.local)

xrandr --output DVI-0 --auto --output DisplayPort-1 --right-of DVI-0 --auto

---

