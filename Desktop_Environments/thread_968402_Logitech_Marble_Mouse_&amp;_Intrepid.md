---
title: "Logitech Marble Mouse &amp; Intrepid"
date: 2008-11-02
forum: Desktop Environments
---

### Post by jcphil on 2008-11-02
I finally understood how a mouse is supposed to be configured under the new X setup. I even found a configuration for my mouse here:

[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

But this has no effect on my mouse. The only effect I see is that left/right click no longer pastes what I highlighted earlier. Any other things I can try? :confused:

---

### Post by jcphil on 2008-11-03
Hmm! My latest update tonight incuded an update for evdev. Now the tiny buttons on my Marble Mouse work, but what they do is move me forward and backward in the history of my Web browsing. That's some progress. But how to get them to scroll?

---

### Post by mormegil on 2008-11-04
I'm having the same issue.  This problem is addressed in the community docs:
[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)
and is reported solved here:
[http://tennessee.ubuntuforums.com/showthread.php?t=938487&page=2](http://tennessee.ubuntuforums.com/showthread.php?t=938487&page=2)

These solutions seem to have no effect on my Logitech Marble mouse, still cannot scroll.

---

### Post by mormegil on 2008-11-04
Reboot and it works (logging off and on didn't seem to do it).  The wiki thread implies that rebooting isn't necessary.  Anyway, good to have scrolling again.  Hope the solution works for you.

---

### Post by xm4ss4cr3 on 2008-11-05
That was my initial problem too, but using the example mouse-wheel.fdi from [https://help.ubuntu.com/community/Logitech_Marblemouse_USB]("https://help.ubuntu.com/community/Logitech_Marblemouse_USB") I got the tiny left one to scroll.

To use the other button for scrolling just switch around some numbers on the ButtonMapping line.

I use the other button to close tabs in Firefox (ctrl+f4). To map keypresses to that little button use imwheel.

my imwheelrc:
```
".*"
None, Up, Control_L|F4

"(null)"
None, Up, Control_L|F4
```

The little left button is button 8, and the right one is button 9.
To start imwheel with the above configuration for button 9 start it like:
```
$ imwheel -k -b "9"
```

---

### Post by jcphil on 2008-11-08
To the poster above, I can only say that I have re-booted a good twenty or so times since I changed the policy in /etc/hal/fdi/policy. It hasn't made any difference. I tried the imwheel suggestion too. The current behavior is:

1. left tiny button goes back to the previous page in history
2. right tiny mouse button minimizes Firefox

Both of these things are a long way from scrolling. So, I'm damned if I know what works.

---

### Post by mageus on 2008-12-25
The fix listed in [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB) works . . . temporarily.

However, if you unplug the trackball, the functionality will be lost and you have to restart the x server.

I have my trackball and keyboard plugged into my monitor.  When I turn my monitor off (if I leave the computer), it cuts its USB port connections.  When I return, I've lost the scroll functionality.

Apparently, if you add:

Section "ServerFlags"
    Option "AutoAddDevices" "false"
EndSection

to your xorg.conf file, it uses the older xorg configuration.  I'm going to try this out.

---

### Post by dupsatOU on 2009-04-17
> Apparently, if you add:

Section "ServerFlags"
Option "AutoAddDevices" "false"
EndSection

to your xorg.conf file, it uses the older xorg configuration. I'm going to try this out. 

This worked for me!  I just upgraded from 8.04 to intrepid and my marble mouse stopped working the way it was supposed to and I discovered the hal/fdi stuff.  I couldn't get that to work apparently but I put the above suggestion in my old xorg.conf file and it worked just like it used to.  Little button scrolls and two big buttons together are my middle click.

My mouse section from my xorg.conf is below for those who are curious.

> Section "InputDevice"
        Identifier      "Logitech USB Mouse"
        Driver  "mouse"
        Option  "CorePointer"
        Option  "Device"        "/dev/input/mice"
        Option  "Protocol"      "ExplorerPS/2"
        Option  "Emulate3Buttons" "True"
        Option  "Buttons"       "9"
        Option  "EmulateWheel"  "1"
        Option  "EmulateWheelButton"    "8"
        Option  "YAxisMapping"  "4 5"
        Option  "XAxisMapping"  "6 7"
EndSection


---

### Post by kmoffat on 2009-04-17
Are you connected via USB or PS2

---

### Post by kmoffat on 2009-04-22
FYI:
In Ubuntu 9.04 I added the following file, /etc/hal/fdi/policy/mouse-wheel.fdi, and my Logitech Marble Mouse, plugged in to USB, has scroll wheel functionality, apparently both verticle and horizontal, at least in Firefox, while holding the small left button and moving the ball:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.Buttons" type="string">5</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 4 5 6 7 2 9</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.EmulateWheelTimeout" type="string">300</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>

---

### Post by jjarrettc on 2009-08-31
I also have the Logitech Marble Mouse, use Ubuntu 9.04, and it is fully up to date.

I added the /etc/hal/fdi/policy/mouse-wheel.fdi per kmoffat's post and still do not have scrolling capability.  The small 2nd, and 3rd buttons work as forward and back buttons in firefox.

Any ideas I might try?

Thanks,
John

---

### Post by cid egypt on 2010-10-27
Do you know about the Egyptian marble ? do you know   that the Egyptian marble is the best marble around the world, [COLOR=black] the Egyptian  Marble has a wide variety of types it can look sophisticated or simple, warm or cool, elegant or rustic due to its wide range of colors [/COLOR] such as : sunny, silvia ,topica rosa ,sinai pearl 

also  the Egyptian granite is one of the best granite over the world [COLOR=black]It resists wear, deterioration and weathering, while maintaining its natural beauty and finish indefinitely,
there are many types of the Egyptian granite such as :  gandona aswan , karnak gray , shabah Sinai , nero aswan  and another marvelous  types .

cid egypt can export any types of the Egyptian marble and granite to any place over the world [/COLOR]with affordable prices , cid Egypt also provide After-sales service 
 cid egypt have created unique and innovative designs with co-operation of Mr. Hazem Shoukry designs who are  the best natural stone designer in Egypt and middle
 east. 
with cid Egypt you can order delivery and installation  easily, do you know that cid Egypt recently made a deal with HSBC to protect your deposit until you receive your order!
  This means that your money is secure until you receive the goods you are paying for ultimately making you feel more secure and relaxed when dealing with us. 


   
  



contact us at : 


**Office No.: **                         002 22 62 63 97 
                                             0020 10 16 49 770



**English landline: **             0044 02030027894
 
**Address: **      17 El Shahid Ahmed Zaki St.,behind El-Ebour building,4th floor, Apartment 42. Box 11371


website:  [  ]("http://www.cidegypt.com")[marble import and export]("http://www.cidegypt.com")

E-maiL:            [EMAIL="info@cidegypt.com"]info@cidegypt.com[/EMAIL]
                         [EMAIL="marketing@cidegypt.com"]marketing@cidegypt.com[/EMAIL]

---

### Post by cid egypt on 2010-10-31
Do you know about the Egyptian marble ? do you know   that the Egyptian marble is the best marble around the world, [COLOR=black] the Egyptian  Marble has a wide variety of types it can look sophisticated or simple, warm or cool, elegant or rustic due to its wide range of colors [/COLOR] such as : sunny, silvia ,topica rosa ,sinai pearl 

also  the Egyptian granite is one of the best granite over the world [COLOR=black]It resists wear, deterioration and weathering, while maintaining its natural beauty and finish indefinitely,
there are many types of the Egyptian granite such as :  gandona aswan , karnak gray , shabah Sinai , nero aswan  and another marvelous  types .

cid egypt can export any types of the Egyptian marble and granite to any place over the world [/COLOR]with affordable prices , cid Egypt also provide After-sales service 
 cid egypt have created unique and innovative designs with co-operation of Mr. Hazem Shoukry designs who are  the best natural stone designer in Egypt and middle
 east. 
with cid Egypt you can order delivery and installation  easily, do you know that cid Egypt recently made a deal with HSBC to protect your deposit until you receive your order!
  This means that your money is secure until you receive the goods you are paying for ultimately making you feel more secure and relaxed when dealing with us. 


   
  



contact us at : 


**Office No.: **                         002 22 62 63 97 
                                             0020 10 16 49 770



**English landline: **             0044 02030027894
 
**Address: **      17 El Shahid Ahmed Zaki St.,behind El-Ebour building,4th floor, Apartment 42. Box 11371


website:    [    ]("http://www.cidegypt.com")[marble import and export]("http://www.cidegypt.com")[URL="http://www.cidegypt.com"]
[/URL] 
E-maiL:            [EMAIL="info@cidegypt.com"]info@cidegypt.com[/EMAIL]
                         [EMAIL="marketing@cidegypt.com"]marketing@cidegypt.com[/EMAIL]

---

