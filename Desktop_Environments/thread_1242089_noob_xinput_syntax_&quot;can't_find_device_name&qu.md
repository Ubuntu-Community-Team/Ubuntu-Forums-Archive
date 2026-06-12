---
title: "noob: xinput syntax? &quot;can't find device name&quot;"
date: 2009-08-16
forum: Desktop Environments
---

### Post by jorx on 2009-08-16
**EDIT**.

After placing the right lines into the 10-wacom.fdi file and rebooting the machine, my wacom now works as I wanted it to. (Intuos 3, and I wanted to swap buttons 2 & 3). 'wacomcpl' and 'xsetwacom list' still return nothing. (and xinput cannot find the device, with the only exception of 'xinput list 2' )

**/EDIT**


Hi everybody,

I'm trying to remap the two side buttons on my wacom pen.
So after following advice elsewhere, I was given the command;

```
xinput set-button-map 4 1 3 2
```But that just gives me a 
"unable to find device 4"

Yet when I run 

```
xinput list 4
```I do get a proper result;
```

"Wacom Intuos3 6x8"     id=4    [XKeyboard]                         
        Num_keys is 248                                             
        Min_keycode is 8                                            
        Max_keycode is 255                                          
        Num_buttons is 7                                            
        Num_axes is 6                                               
        Mode is Absolute                                            
        Motion_buffer is 256                                        
        Axis 0 :                                                    
                Min_value is 0                                      
                Max_value is 40640                                  
                Resolution is 5080                                  
        Axis 1 :                                                    
                Min_value is 0                                      
                Max_value is 30480    
```So how can I get it to find this device 4 ??? I just need to remap the buttons! :confused:

---

### Post by Favux on 2009-08-16
Hi jorx,

You should be able to use wacomcpl to calibrate and configure your tablet, including the stylus buttons.  Right now the names being returned aren't linuxwacom names.  To see this enter in a terminal:
```
xsetwacom list
```
You should get back stylus, eraser, pad etc. not a blank.

I assume you're in Jaunty (9.04).  This is because the 10-wacom.fdi isn't parsing the names correctly that HAL (xinput --list) is returning.  To get a .fdi that does parse the names correctly use the modified 10-wacom.fdi in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  Then to set up wacomcpl go to "Section 3: Calibrating your Tablet PC." here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Then you should be able to set up your stylus buttons.

Hope this helps.

PS:  Using wacomcpl assumes you have 'wacom-tools' installed through Synaptic Package Manager.

---

### Post by jorx on 2009-08-17
"xsetwacom list" and wacomcpl are installed- but both giving me total blanks- but I'll follow your steps.

I'm running kubuntu desktop on linux mint 7, (based on the latest ubuntu 9 I believe)

---

### Post by jorx on 2009-08-17
Ok, my system does not have a *wacom.fdi file, so after googling I made a new file:

/etc/hal/policy/mytabletrules.fdi

and copied and pasted someone else's very similar Intuos 3 configuration into that.  Then I rebooted xwindows.

And it failed! It rebooted many times, and came up with a large ASCII error that it was trying too many times.
So it was the limit of my knowledge to terminal into that folder and delete the custom fdi file.  

So where am I supposed to put it the fdi file? And what does it mean if xwindows/KDE can't load?

Thanks, I really appreciate the advice!

---

### Post by Favux on 2009-08-17
Hi jorx,

Well, you put a custom_wacom.fdi in the custom location.

The proper location  and .fdi is in the post #176 I linked you to above.  It should be "/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi".  I know it works for Mint too.  The command "gksudo gedit" etc. will create the file for you if it isn't there.

You're the first person I know who's managed to break X (Xserver-the windowing manager that runs your graphical environment) with a .fdi!  It's fairly common though with the xorg.conf.  I'm almost curious enough to ask to see the .fdi you tried.

If it's still not loading something is most likely borked in your xorg.conf.  Probably with the video sections.  Which I don't understand since you shouldn't have been doing anything to it.

---

### Post by jorx on 2009-08-17
Ok, so my 10-wacom.fdi (didn't turn up when I ran a search for *wacom.fdi ?) contains the following:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
      <match key="info.product" contains="WALTOP">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>

</deviceinfo>

```

So should I replace the entire file?

I'm running an Intuos3, where as the link you supplied me is for a graphire 4.  But for troubleshooting purposes I will try replacing the whole file and let you know what happens

---

### Post by jorx on 2009-08-17
Ak!! After hotplugging- it definitely changed- now it's in relative mode (prefer absolute) and none of the buttons work!
But editing the file to my own liking (changing flat from "Relative" to "Absolute", or deleting the entire line) does nothing! So it's unusable until we can fix this problem.
And still no show in wacomcpl.


'sudo wacdump /dev/input/event5' works fine: gives me this;

```
wacdump v0.8.2

MODEL=Wacom Intuos3 6x8                 ROM=1.0-2
CLS=USB  VNDR=Wacom  DEV=Intuos3  SUB=PTZ-630




TOOLTYPE=NONE                             SERIAL=0x00000000
 IN_PROX=out                              BUTTON=+00000 (+00000 .. +00000)
   POS_X=+00000 (+00000 .. +40640)         POS_Y=+00000 (+00000 .. +30480)
   ROT_Z=+00000 (-00900 .. +00899)      DISTANCE=+00000 (+00000 .. +00063)
PRESSURE=+00000 (+00000 .. +01023)        TILT_X=+00000 (+00000 .. +00127)
  TILT_Y=+00000 (+00000 .. +00127)      ABSWHEEL=+00000 (+00000 .. +01023)
RELWHEEL=+00000 (-00001 .. +00001)      THROTTLE=+00000 (-01023 .. +01023)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=
     BT8=                BT9=               BT10=               BT11=
    BT12=               BT13=               BT14=               BT15=
    BT16=               BT17=               BT18=               BT19=
    BT20=               BT21=               BT22=               BT23=




```





Original post below:

Ok, nothing happened;
I made a backup (renamed to 10-wacom.fdi.bak )
and replaced the entire contents of the file with the one in the link you gave me as root.  But still no change- after restarting KDE wacomcpl still reads empty and my buttons have not been swapped (as the commands in that fdi file?)

---

### Post by Favux on 2009-08-17
Hi jorx,

Ok, you've now replaced the .fdi with one that parses names correctly for usb tablets.  To see if it's working run in a terminal:
```
xsetwacom list
```
Now you should see the proper names like stylus, eraser, pad, etc. rather than it being blank.  You probably have not installed "wacom-tools".  Wacomcpl is in it.  In Synaptic Package Manager search "wacom" and make sure it's installed.

You can configure the buttons in the .fdi but it's easier to do with wacomcpl.

---

### Post by jorx on 2009-08-17
Ok, I tried other .fdi's (via google) until I could get it going back to absolute mode.
The new .fdi reads as follows;

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
    <match key="info.product" contains="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
</deviceinfo>
```

"xsetwacom list" still returns nothing at all, not even a newline. 'wacomcpl' as well.

Is it essential to have xsetwacom and wacomcpl finding the tablet? Or can I just simply swap the two buttons in the .fdi file like I've seen elsewhere?

---

### Post by Favux on 2009-08-17
Hi jorx,

Your Intuos3 is a USB Wacom tablet, correct?

You seem intent on making this difficult.  I've told you a couple of times now how to get it working, see post #2 above.

If you want to experiment and mess around, fine.  Have fun.  Otherwise reread what I've posted.

---

### Post by jorx on 2009-08-17
*SOLVED*!!! 


Although I was at odds as  to where exactly I should put;

```
       	<merge key="input.x11_options.Button2" type="string">3</merge>
       	<merge key="input.x11_options.Button3" type="string">2</merge>
```



I fit it into my fdi file, so that my final 10-wacom.fdi is as follows. (this is for my Intuos 3, with the purpose of swapping buttons 2 and 3)

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
    <match key="info.product" contains="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <merge key="input.x11_options.Button2" type="string">3</merge>
    <merge key="input.x11_options.Button3" type="string">2</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
</deviceinfo>
```

Wacomcpl and xsetwacom still do nothing, but that's ok for now.

Now all I have left to do is figure out how to absolute map it to screens 1 or 2 in a multi-screen environment, and preferably have a script or button that switches between the two monitors!

---

