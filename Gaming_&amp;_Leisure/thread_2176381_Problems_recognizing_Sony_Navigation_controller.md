---
title: "Problems recognizing Sony Navigation controller"
date: 2013-09-24
forum: Gaming &amp; Leisure
---

### Post by Pako Pako on 2013-09-24
Anyone else successfully use a [Playstation Move Navigation controller]("http://us.playstation.com/ps3/accessories/playstation-move-navigation-controller-ps3.html")? (Specifically in Natty/11.04, but I'll take advice for 12.04 or even Windows too.)

My goal is to use it via the USB cable, but I am getting mixed results. The Navigation controller works on an Android tablet (connected via USB), on a 12.04 laptop (connected via USB), but not on my 11.04 laptop (connected via USB).

I've installed **joystick** (which includes **jstest** driver version is 2.1.0); it recognizes as the **Sony Navigation Controller**, but all the Axis values (all 28 of them) and the buttons aren't responding. Nothing responds in Calibration, clicking Mapping causes the GUI to quit. Running jstest command-line on /dev/inout/js0 causes it to read everything as off and hang until I interrupt with CTRL+C. 

I've even installed **Rejoystick**, but I get no response from the program when I click buttons or rotate the joystick; some of the axis were always lit on the 12.04 machine (probably the motion-sensor). The controller behaves the same way in Windows XP; it gets read by name, but nothing clicks on testing. No games register the controller either.

I've tried installing **[COLOR=#333333][FONT=arial]qtsixa[/FONT][/COLOR]**[COLOR=#333333][FONT=arial] from the [/FONT][/COLOR][COLOR=#333333][FONT=arial]repository *ppa:falk-t-j/qtsixa*, even adding python-qt4, but it won't recognize the USB connection.[/FONT][/COLOR]

Is my 11.04 lacking something, and if so, can I do anything about it?

---

