---
title: "Logitech Trackman Marble FX"
date: 2006-07-10
forum: Desktop Environments
---

### Post by abbaZaba on 2006-07-10
I have the PS/2 mouse TRackman Marble FX but the two extra buttons do not function in Ubuntu 6.06. I've looked through the mouse config walkthroughs and such but none seem to work. 
[here]("http://csown.dhs.org/misc/tmmarblefx_b.jpg") is a picture of the mouse. those two small buttons near the leftclick button won't work. I'm a brand new Linux user but so far I've been pretty good with getting stuff working/figured out. can anyone shed some light on this?

---

### Post by luxor on 2008-04-13
Hi, I use the following version of the xserver in Gutsy:  xserver-xorg                               1:7.2-5ubuntu13                      the X.Org X server

You need to edit your /etc/X11/xorg.conf file to comment out the mouse0 InputDevice section and add the following to get the Trackman Marble FX to work in Gutsy

#Section "InputDevice"
    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Device"      "/dev/input/mice"
        Option          "Name" "TrackMan Marble FX"
        Option          "Vendor" "Logitech"
        Option          "Protocol" "explorerps/2"
        Option          "AngleOffset" "10"
        Option          "Buttons" "5"
        Option          "EmulateWheel" "true"
        Option          "EmulateWheelButton" "8"
        Option          "YAxisMapping" "4 5"
        Option          "EmulateWheelInertia" "8"
EndSection

---

### Post by Pelo1968 on 2008-04-20
I tried this in Hardy and it messed up my keyboard and monitor,  I have no idea why it would do that, I didn't get to test if the trackball worked properly. 
I'm hoping this is an issue with the xserver in hardy and that another tweak will become available, cause when I finaly got around to checking for this and found this I was extatic, and now I'm just annoyed. 

thanks anyway


I'm an idiot forget what I said I found my error , apparently I'm not allowed to comment out the stuff about wacom,  even if I don'T have any .

BUT I would love to know how I could set my little red button to work like it did with "Mouseware",  click scroll on,  click scroll off . Right now i need to hold it.

---

