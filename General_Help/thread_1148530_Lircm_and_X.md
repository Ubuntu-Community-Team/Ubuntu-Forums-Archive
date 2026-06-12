---
title: "Lircm and X"
date: 2009-05-04
forum: General Help
---

### Post by Grenage on 2009-05-04
Greetings!

I'm posting for some input after exhausting just about every angle I can come up with.  I'm using Lirc to use my remote in mplayer etc, and this is working perfectly.  The problem I am having here is using the lircm extension to control the mouse cursor with the remote control.

The device output is /dev/lircm (standard) and running cat /dev/lircm does generate output using the correct remote keys.  I have to assume that this means Lirc(m) is running just fine, and that the problem is my xorg.conf (God only knows how).  The relevant parts of my current config are:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "LIRC-Mouse"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "LIRC-Mouse"
    Driver         "mouse"
    Option         "Device" "/dev/lircm"
    Option         "Protocol" "IntelliMouse"
    Option         "SendCoreEvents"
    Option         "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
```


I believe my lircmd.conf is fine, but I'll post it anyway:

```
#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian
# 
# lircmd config file
# 
PROTOCOL IntelliMouse
# ACCELERATOR start max multiplier

ACCELERATOR 2 30 5
TOGGLE_ACTIVATE * Green

MOVE_N  * Two
MOVE_NE * Three
MOVE_E  * Six
MOVE_SE * Nine
MOVE_S  * Eight
MOVE_SW * Seven
MOVE_W  * Four
MOVE_NW * One

BUTTON1_TOGGLE * Five
BUTTON2_TOGGLE * Down

BUTTON1_CLICK * Five
BUTTON2_CLICK * Star
BUTTON3_CLICK * Hash
```


If anyone's got any ideas about where I'm going wrong, I'd be really grateful :)

Grenage.

---

### Post by Grenage on 2009-05-05
Shameless one-off bump.

---

### Post by Blackie_Chan on 2009-05-15
I have the same problem. Have you gotten lircmd to work?

---

### Post by Grenage on 2009-05-16
Alas no, I never managed to get it working.

---

### Post by Blackie_Chan on 2009-06-11
I fixed the problem for me. All I had to do was add the following to my ServerLayout section:

```
Option "AutoAddDevices" "off"
```

Prior to adding the above line, I noticed that my Lirc-mouse was disabled because AllowEmptyInput is on (according to /var/log/Xorg.0.log). When I turned AllowEmptyInput off, my lirc mouse was working but pressing a key on my keyboard caused the key to be repeated 3 times on the screen.

Cheers.

---

### Post by omarino on 2009-07-03
Blackie_Chans solution works, but it dissables HAL which is used for auto mouse and keyboard config since 8.10.
The more elegant solution is leaving AutoAddDevices enabled and configuring lirc mouse in hal and not in xorg.conf:
see: [https://bugzilla.redhat.com/show_bug.cgi?id=498580](https://bugzilla.redhat.com/show_bug.cgi?id=498580)

---

### Post by Grenage on 2009-07-03
Greetings, and thank you for the additions.

I've dabbled with various configs and did get it to work using **Blackie_Chan**'s advice (thank you so much).  I didn't have much luck with **omarino**'s link, unfortunately; HAL doesn't appear to get on with any of my configs.

Anyhow; it's an excellent result!

---

### Post by omarino on 2009-07-26
Disabling auto-add devices messes up my other configuration + it messes up my lirc mouse every time i reconfigure X.
Thats why i decidede to do things tje HAL way - instead of editing xorg.conf, i created a custom hal fdi config file:

> sudo gedit /usr/share/hal/fdi/policy/30user/10-lirc_mouse.fdi

with the following content:
> <?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.udi" string="/org/freedesktop/Hal/devices/lirc_mouse">
        <merge key="info.category" type="string">input</merge>
        <merge key="info.capabilities" type="strlist">input</merge>
        <append key="info.capabilities" type="strlist">input.mouse</append>
        <merge key="input.device" type="string">/dev/lircm</merge>
        <merge key="linux.device_file" type="string">/dev/lircm</merge>
        <merge key="linux.x11_options.Device" type="string">/dev/lircm</merge>
        <merge key="input.x11_driver" type="string">mouse</merge>
        <merge key="input.x11_options.Protocol" type="string">IntelliMouse</merge>
        <merge key="input.x11_options.Buttons" type="string">5</merge>
        <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
        <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
     </match>
  </device>
</deviceinfo>

After that i restarted hal
> /etc/init.d/hal restart
and the mousie works.

---

### Post by Grenage on 2009-07-26
Cheers for the update on how you got it working in the end; this should be a useful post for those with the same problem.

---

### Post by QkEterror on 2009-08-12
> **omarino said:**
> Disabling auto-add devices messes up my other configuration + it messes up my lirc mouse every time i reconfigure X.
Thats why i decidede to do things tje HAL way - instead of editing xorg.conf, i created a custom hal fdi config file:



with the following content:


After that i restarted hal

and the mousie works.

Omario. Can you help me. I did what you wrote. There was no 30user directory, so I created that. Furthermore I did exactly the same. The lircmd.conf has the IntelliMouse configured. The device (a remote wonder) has only 2 buttons, but it doesn't make a difference if I configure it with 2. If I cat /dev/lircm I get output, but there is no cursor movement in Kubuntu.

Is there a possibility to debug the hal to see what goes wrong or do you have any suggestions?

---

### Post by P4man on 2009-08-12
Thanks for posting guys, i got a remote that works fine in xmbc and the like,  and I kinda wondered how to use it as mouse replacement.

I guess this is how :)
I have to try this now :)

---

### Post by Krister Hallergard on 2009-09-06
Have installed 10-lirc_mouse.fdi as per omarino above.  The lircd deamon works fine but not the lircmd deamon.  Message that it cannot connect to socket /dev/lircm
Help please!

---

### Post by Grenage on 2009-09-07
Check that the point exists.  I never got that method to work, but I was able to get it to work with **Blackie_Chan**'s method.

---

### Post by Krister Hallergard on 2009-09-07
No I cannot get it to work with Option "AutoAddDevices" "off".  Well it looks ok in the Xorg.0.log, but it does not work

---

### Post by Krister Hallergard on 2009-09-08
Thanks, what did you mean "Check that the point exists" - might be something I have missed?

---

### Post by Grenage on 2009-09-08
Hi again, does /dev/lircm definitely exist, can you see it in /dev?

---

### Post by Krister Hallergard on 2009-09-08
Hi there, No I cannot see /dev/lircm, and believe that that is my problem.  How is lircm created??

---

### Post by Grenage on 2009-09-09
It sounds like the lircm daemon isn't running; if you manually start lircm, does it appear?

---

### Post by Krister Hallergard on 2009-09-09
Here it is:
> root@DESKTOP:~# /etc/init.d/lirc stop
 * Stopping remote control mouse daemon: LIRCMD                                                             [fail]
 * Stopping remote control daemon(s): LIRC                                                               [ OK ]
root@DESKTOP:~# /etc/init.d/lirc start
 * Starting remote control daemon(s) : LIRC                                                               [fail]
 * Starting remote control mouse daemon : 
LIRCMD
lircmd: could not connect to socket
lircmd: Connection refused  
                                                                   [fail]
root@DESKTOP:~#


---

### Post by Grenage on 2009-09-09
Ok, that looks like lirc itself is having some issues.  Take a look at the following link, especially the links referred to within it:

[http://www.murga-linux.com/puppy/viewtopic.php?t=3228](http://www.murga-linux.com/puppy/viewtopic.php?t=3228)

If you still have issues, post back and I'll do what I can to help.

---

### Post by Krister Hallergard on 2009-09-09
Thank you Grenage!  Will purge lirc an attempt a fresh install.
Will be back

---

### Post by Krister Hallergard on 2009-11-26
Am back after having installed Kubuntu 9.10.  Lirc is functioning beautyfully and now got a bit further with lircmd:  the lircmd deamon is running and I can see /var/run/lirc/lircm.

1.  I don't have any sign of the LIRC_mouse in Xorg.0.log.  Is this a "hal" problem?  Have used the 10-lirc_mouse.fdi mentioned above, and also the same edited with /dev/lircm replaced by /usr/run/lirc/lircm - no difference that I could detect.

2.  When the lircmd daemon start this message is give:> lircmd: unknown protocol IntelliMouse^M 

Any suggestion would be very much appreciated

---

### Post by Krister Hallergard on 2009-12-20
From the lirc mailing-list I learned that I was having Dos line endings (^M) instead of Unix line endings.  I had been using Windows to edit lircmd.conf.  Fixing that I now have a well functioning LIRC-mouse on the Mandriva partition.

On the Kbuntu partition I still have the problem that /var/log/Xorg.0.log does not recognize the LIRC-mouse, i.e. the HAL proceedure is not functioning.  Am using nVidia 173xx drivers - kernel problem??  Any suggestions?

---

### Post by Krister Hallergard on 2009-12-21
Not a kernel problem.  Found the answer here, posts 7-9:
[http://ubuntuforums.org/showthread.php?t=1329662](http://ubuntuforums.org/showthread.php?t=1329662)

---

### Post by Krister Hallergard on 2009-12-21
Just learnt an even easier way from jarajm: to use the new command lircmd --uinput. Very easy!

---

