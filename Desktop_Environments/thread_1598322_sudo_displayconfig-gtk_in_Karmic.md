---
title: "sudo displayconfig-gtk in Karmic???"
date: 2010-10-19
forum: Desktop Environments
---

### Post by Moozillaaa on 2010-10-19
edit:
The Wiki X/Config/Resolution page I think has at least one error, and perhaps another.

One error is solved at post #10. It applies only to 'per-session' fix. I am still working on making the fix permanent, since one of the 3 'fixes' on the Wiki page works only in part...

------------------------------------------------

Alright - start from scratch again here, noted so I can reverse failed steps...

[B][COLOR=DarkGreen]Existing modes:
[/COLOR][/B]
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$ 

**[COLOR=DarkGreen]Then check for ability to change modes [COLOR=Indigo]*and back*[/COLOR] - good[/COLOR]**:
[COLOR=DarkGreen](obviously 'VGA-0' is the correct name...)[/COLOR]

chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 --mode 640x480
chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 --mode 1360x768
chuckhtpc@chuckhtpc-desktop:~$ 

**[COLOR=DarkGreen]Now CREATE and ADD undetected resolution:[/COLOR]**

**[COLOR=DarkGreen]Create 'ModeLine with cvt utility[/COLOR]**:
chuckhtpc@chuckhtpc-desktop:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline **[COLOR=Red]"1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync[/COLOR]**
chuckhtpc@chuckhtpc-desktop:~$ 
[B][COLOR=DarkGreen]
Enter newmode:[/COLOR][/B]
chuckhtpc@chuckhtpc-desktop:~$ xrandr --newmode **[COLOR=Red]"1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync[/COLOR]**
chuckhtpc@chuckhtpc-desktop:~$ 

[COLOR=DarkGreen]**Addmode  **[/COLOR][B][COLOR=DarkSlateGray]
syntax = --addmode <output> <name>[/COLOR][/B]
chuckhtpc@chuckhtpc-desktop:~$ xrandr --addmode VGA-0 [SIZE=2]**???**[/SIZE]
What is the name for addmode syntax?
"1280x1024" ? 
"1280x1024_60" ?
[COLOR=Black]"1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync[/COLOR]?

With or withOUT parenthesis???


**[COLOR=DarkGreen]Taking a look at modelines now, BEFORE doing 'addmode', shows THIS???[/COLOR]** :confused:

chuckhtpc@chuckhtpc-desktop:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
  [B]1280x1024_60.00 (0x129)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz[/B]
chuckhtpc@chuckhtpc-desktop:~$ 

[B][COLOR=DarkGreen]Should another parameter been added to 'newmode'???



edit:
I just looked at 
[http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html](http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html)
and, although he denotes the <NAME> in addmode, his <output> syntax is different:
(one dash before 'addmode', and no dash in VGA[/COLOR][SIZE=3][COLOR=DarkGreen][COLOR=Red]-[/COLOR][/COLOR][/SIZE][/B][B][COLOR=DarkGreen]x
[/COLOR][/B]xrandr [SIZE=3]**[COLOR=Red]–[/COLOR]**[/SIZE]–addmode VGA1 “1680x1050_60.00&#8243;
[B][COLOR=DarkGreen]
[/COLOR][/B]

---

### Post by ankspo71 on 2010-10-20
Hi, I have tried doing this myself to see if it can be done, about 10 times already. I tried different sizes and refresh rates and none of them could be activated. They were all reasonable sizes too.

This type of result is given when we use an underscore in the mode name:
1280x1024_60.00 (0x129)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

As far as I can tell, the name requires quotes around it, but does not require an underscore.

I'm going to try recreating an existing working mode. I will try using the same size and refresh rate, except give it a different mode name to see if it works. I will try it with both specifications from gtf and cvt too. I'll be back to let you know if this works or not.

---

### Post by ankspo71 on 2010-10-20
Hi,
This link talks about getting modelines from xorg logs and from a Windows program called PowerStrip (which would be good if you dual-boot Windows and Linux). [http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)

---

### Post by ankspo71 on 2010-10-20
According to 'man xrandr' in the terminal (of Ubuntu 10.10):
> 
EXAMPLES:

Forces to use a 1024x768 mode on an output called VGA:
              xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
              xrandr --addmode VGA 1024x768
              xrandr --output VGA --mode 1024x768

I notice there are no quotes in the --addmode and --output lines, and the --newmode line is different too... it doesn't have the refresh rate - the one that was in the modeline name.

Here I go again: I already have a mode called 1600x900 so I will call it 1600x900-test*. My output is simply called default, and the output name works with pre-existing modes.

james@Kubuntu:~$ cvt 1600 900 51
# 1600x900 50.92 Hz (CVT) hsync: 47.35 kHz; pclk: 99.25 MHz
Modeline "1600x900_51.00"   99.25  1600 1688 1848 2096  900 903 908 930 -hsync +vsync

xrandr --newmode "1600x900-test2"   99.25  1600 1688 1848 2096  900 903 908 930 -hsync +vsync
xrandr --addmode default 1600x900-test2
xrandr --output default --mode 1600x900-test2

Nope: the new mode I created wouldn't apply:
james@Kubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   1600x900       50.0* 
   1440x900       51.0  
   1360x768       52.0     53.0  
   1280x720       54.0  
   1152x864       55.0     56.0     57.0     58.0  
   1024x768       59.0     60.0     61.0  
   960x600        62.0  
   960x540        63.0  
   840x525        64.0     65.0     66.0     67.0  
   832x624        68.0  
   800x600        69.0     70.0     71.0     72.0  
   720x450        73.0  
   700x525        74.0     75.0  
   680x384        76.0     77.0  
   640x480        78.0     79.0     80.0     81.0     82.0  
   512x384        83.0     84.0  
   400x300        85.0  
   320x240        86.0     87.0  
   1600x900-test   47.9  
   1600x900-test2   50.9  

I also tried recreating the working existing modes, but they didn't work either.
Nvidia Settings can properly detect my monitor in Ubuntu, but it is not detected in Ubuntu's own display settings tool. In Kubuntu it only says "default", in Ubuntu it says "unknown" (I think), but they both give me a generic set of working display modes to choose from.


[http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html](http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html)

---

### Post by Moozillaaa on 2010-10-20
You apparently are having identical problems, except for the one error - > xrandr: Failed to get size of gamma for output default So your syntax is good, but perhaps a parameter call is unanswered (or undefined, with no default).

There seems to be compatibility errors SOMEwhere ( I believe they involve compatibility with the distribution ), rather than end-user errors. I'm in Karmic.

AFTER you did '--newmode', and BEFORE you did '--addmode', did you check to see if it  appeared in xrandr return?

Note that I did do this, and the '--newmode' appeared in my HDMI modelist, NOT the VGA-0 modelist. This seems to indicate perhaps another parameter is necessary in the '--newmode' codestring. ???

If (since) the '--newmode' appears in xrandr return, BEFORE '--addmode' is executed, what's the purpose of '--addmode'???

I do dual boot, but have not tried to get data from the XP partition...

Your 1600x900-test mode didn't work... Does X need to be re-started?

Your re-created WORKING mode did not work (when called by re-created NAME, right)? Again, does X need to be re-started?

And yesterday, when I tried to '--delmode' (delete the mode that didn't work), why was 'mode not found'??? This was after '--newmode', and '--addmode' were executed....... 

???????

I've tried nothing past post 1 above; will re-try tomorrow here...

---

### Post by ankspo71 on 2010-10-20
Hi,
Yes, I just checked to see if my custom mode is listed in xrandr after using the first command with --newmode (and it shows it is listed), but if I try to test it without using --addmode, I get a result saying this: 
```

james@Kubuntu:~$ xrandr --output default --mode 1600x900-test5
xrandr: cannot find mode 1600x900-test5
```


It seems we need to use the --addmode after using --newmode. I think --newmode creates it and allows it to be viewed in xrandr, and --addmode adds it physically.


I have already tried rebooting after creating the custom modes, but the custom modes ends up getting removed automatically from the xrandr list each time I reboot like shown below.

```
james@Kubuntu:~$ xrandr --output default --mode 1600x900-test5
xrandr: cannot find mode 1600x900-test5
```

And here it shows it is gone:
```
james@Kubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   1600x900       50.0* 
   1440x900       51.0  
   1360x768       52.0     53.0  
   1280x720       54.0  
   1152x864       55.0     56.0     57.0     58.0  
   1024x768       59.0     60.0     61.0  
   960x600        62.0  
   960x540        63.0  
   840x525        64.0     65.0     66.0     67.0  
   832x624        68.0  
   800x600        69.0     70.0     71.0     72.0  
   720x450        73.0  
   700x525        74.0     75.0  
   680x384        76.0     77.0  
   640x480        78.0     79.0     80.0     81.0     82.0  
   512x384        83.0     84.0  
   400x300        85.0  
   320x240        86.0     87.0  
```

I'm not sure where to go from here.

---

### Post by ankspo71 on 2010-10-20
Hi,
I just found the out the --addmode command we use in the terminal is only temporary for testing purposes, so those custom modes will automatically be lost on reboot. Permanent changes can can be made in /etc/gdm/Init/Default by pasting the same commands in there as shown in the following link: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html) , and the original source article here: [http://ubuntuforums.org/showthread.php?p=8595940](http://ubuntuforums.org/showthread.php?p=8595940)

Have you noticed that cvt and gtf give different modeline values?

```
$ gtf 1600 900 50
# 1600x900 @ 50.00 Hz (GTF) hsync: 46.30 kHz; pclk: 97.04 MHz                                        
Modeline "1600x900_50.00"  97.04  1600 1680 1848 2096  900 901 904 926  -HSync +Vsync                

$ cvt 1600 900 50                                                                   
# 1600x900 49.94 Hz (CVT 1.44M9) hsync: 46.39 kHz; pclk: 96.50 MHz                                     
Modeline "1600x900_50.00"   96.50  1600 1680 1840 2080  900 903 908 929 -hsync +vsync
```

---

### Post by Moozillaaa on 2010-10-20
You had this return once:
> james@Kubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output defaultFrom xrandr usage:
[B]  --output <output>
      --...
      --...
      --...
     [COLOR=Red] --gamma <r>:<g>:<b>[/COLOR][/B]
Mean anything to you? Was yours asking for YOUR input? Or was your system supposed to supply the info?

-------------

Yep - after re-boot, the new / added modes should be gone. I now remember that the wiki page that you linked to said the modification was session-specific, and needed to be made permanent.

But we can't seem to get to that point.....
--------------
So today I booted up, and got reduced resolution. The display GUI showed resolution set at 1360x768. xrandr in the CLI said different; 640x480 - see screenpic.
(the Sony is a 32", and is the secondary output...)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=172942&d=1287598535[/IMG]

In the GUI, I clicked the resolution drop-down, not actually changing it, but keeping it on 1360x768, and 'Applied Settings'. It stayed at 640x480.

So xrandr takes precedence over the display GUI, and cannot be changed using GUI? That's not right...
--------------------
So I'm gonna' try some things sort of like you did here:

**[COLOR=DarkGreen]Re-designate an existing mode:[/COLOR]**
[COLOR=DarkGreen](Modeline from cvt utility)[/COLOR]
chuckhtpc@chuckhtpc-desktop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
chuckhtpc@chuckhtpc-desktop:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
chuckhtpc@chuckhtpc-desktop:~$ 
[B][COLOR=DarkGreen]
See how it now shows up, before '--addmode':[/COLOR][/B]
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
  [COLOR=Blue][B]1024x768_60.00 (0x129)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz[/B][/COLOR]
chuckhtpc@chuckhtpc-desktop:~$ 

**[COLOR=DarkGreen]Try to call it up BEFORE '--addmode', by different names, just to see if anything happens:[/COLOR]**

chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 --mode 1024x768_60.00
xrandr: cannot find mode 1024x768_60.00
chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 --mode 1024x768 60.00 (removed underscore)
usage:  [COLOR=Red](usage syntax)[/COLOR]
...
...
...
chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 --mode **[COLOR=Blue](0x129)[/COLOR]** [COLOR=DarkGreen]from '--newmode' entry in xrandr return[/COLOR]; [COLOR=DarkGreen]see above[/COLOR]
bash: syntax error near unexpected token `('
chuckhtpc@chuckhtpc-desktop:~$ 


[B][COLOR=DarkGreen]Ok - now do --addmode
--addmode <output> <name>
[/COLOR][/B][COLOR=black]chuckhtpc@chuckhtpc-desktop:~$ xrandr --addmode VGA-0 1024x768_60.00 **[COLOR=Blue](0x129)[/COLOR]**
bash: syntax error near unexpected token `('
chuckhtpc@chuckhtpc-desktop:~$ [/COLOR][COLOR=DarkGreen][COLOR=Black]xrandr --addmode VGA-0 1024x768_60.00
chuckhtpc@chuckhtpc-desktop:~$ [/COLOR][/COLOR][B][COLOR=DarkGreen]

Now see what shows in xrandr return, since it's 'added'...
[/COLOR][/B][COLOR=DarkGreen]
[COLOR=Black]chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  [B]
   [COLOR=Red]1024x768_60.00   59.9 [/COLOR][/B] 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$ [/COLOR][/COLOR][B][COLOR=DarkGreen]

It HAS added into the VGA-0 modes section



[/COLOR][/B]

---

### Post by Moozillaaa on 2010-10-20
**[COLOR=DarkGreen]Now try to pull it up by the CREATED output name[/COLOR]**:

chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 1024x768_60.00
usage: xrandr [options]
...
...
...
chuckhtpc@chuckhtpc-desktop:~$ 
[B][COLOR=DarkGreen]
Obviously it does not like  the 'created' name. And there's no other way to test for the '--added' mode, since it already exists by it's own name.[/COLOR][/B]
[B][COLOR=DarkGreen]
So we can only try again with the undetected resolution, which we've already tried...[/COLOR][/B]

---

### Post by Moozillaaa on 2010-10-20
[SIZE=3]**[COLOR=DarkGreen]We have some progress to report[/COLOR]**[/SIZE]:

[B][COLOR=DarkGreen]From the cvt utility, which gives the 'Modeline' info, is deleted the [COLOR=Red]screen refresh rate[/COLOR]:
800x600_60[/COLOR][/B]


chuckhtpc@chuckhtpc-desktop:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024[SIZE=2]**[COLOR=Red]_60.00[/COLOR]**[/SIZE]"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
chuckhtpc@chuckhtpc-desktop:~$ xrandr --newmode "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
chuckhtpc@chuckhtpc-desktop:~$ xrandr --addmode VGA-0 1280x1024
chuckhtpc@chuckhtpc-desktop:~$ ^C
chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 --mode 1280x1024
chuckhtpc@chuckhtpc-desktop:~$ 

[B][COLOR=DarkGreen]After the '--addmode' command, I was not returned to a prompt. I waited for a minute, then terminated the process <Ctrl + C> and the I was returned to the prompt, and the ^C text appeared at the prompt simultaneously. I don't know what this was about at all.

Now to make it permanent...
(still need help on this)

I then changed the output for VGA-0, and it changed the resolution as desired!!![/COLOR][/B]

---

### Post by ankspo71 on 2010-10-20
Hi,
I think I just stumbled onto something. I trashed my display in Kubuntu today, and I had a copy of PClinuxOS 2010.7 laying around, so I decided to boot into that. I couldn't add my own custom modes here either, and it seems to be worse because each mode I create cant be found when I try to apply it with xrandr. 

But, I looked at the /etc/X11/xorg.conf file, and it has information we might be able to use including some modelines. We might be able to use parts of (or the entire) xorg.conf too. The xrog.conf I was using in Ubuntu barely had anything in it, and it didn't have any modelines.

Here the xorg.conf says "modeline generated by gtf(1) [handled by XFdrake]". The thing I don't know about them is...I don't know if these modelines will work, or if they are currently in use. 

So if you have a copy of PClinuxOS 2010 laying around (or maybe another distribution not based on Ubuntu), boot into it and run the command:
cat /etc/X11/xorg.conf

In the live cd of pclinuxos, with the non-free Nvidia 195.36.71 graphics driver installed and working, cat /etc/X11/xorg.conf shows this:
```
[guest@localhost guest]$ cat /etc/X11/xorg.conf
# File generated by XFdrake (rev )

# **********************************************************************
# Refer to the xorg.conf man page for details about the format of
# this file.
# **********************************************************************

Section "ServerFlags"
    Option "DontZap" "False" # disable <Ctrl><Alt><BS> (server abort)
    #DontZoom # disable <Ctrl><Alt><KP_+>/<KP_-> (resolution switching)
    AllowMouseOpenFail # allows the server to start up even if the mouse does not work
EndSection

Section "Module"
    Disable "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "glx" # 3D layer
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Plug'n Play"
    ModelName "2036"
    HorizSync 30-83
    VertRefresh 55-75
    
    # Monitor preferred modeline (60.0 Hz vsync, 60.0 kHz hsync, ratio 16/9, 91 dpi)
    ModeLine "1600x900" 108 1600 1624 1704 1800 900 901 904 1000 +hsync +vsync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1600x900_120"  255.69  1600 1728 1904 2208  900 901 904 965  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1600x900_100"  208.90  1600 1720 1896 2192  900 901 904 953  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1600x900_85"  174.79  1600 1712 1888 2176  900 901 904 945  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1600x900_75"  152.28  1600 1704 1880 2160  900 901 904 940  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1600x900_60"  119.00  1600 1696 1864 2128  900 901 904 932  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1600x900_50"  97.04  1600 1680 1848 2096  900 901 904 926  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1368x768_120"  185.67  1368 1472 1624 1880  768 769 772 823  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1368x768_100"  151.73  1368 1464 1616 1864  768 769 772 814  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1368x768_85"  125.67  1368 1456 1600 1832  768 769 772 807  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1368x768_75"  110.19  1368 1456 1600 1832  768 769 772 802  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1368x768_60"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1368x768_50"  69.92  1368 1424 1568 1768  768 769 772 791  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x765_120"  182.63  1360 1456 1608 1856  765 766 769 820  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x765_100"  149.22  1360 1456 1600 1840  765 766 769 811  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x765_85"  124.65  1360 1448 1592 1824  765 766 769 804  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x765_75"  108.34  1360 1440 1584 1808  765 766 769 799  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x765_60"  84.40  1360 1424 1568 1776  765 766 769 792  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x765_50"  69.34  1360 1416 1560 1760  765 766 769 788  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x720_120"  161.56  1280 1376 1512 1744  720 721 724 772  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x720_100"  131.85  1280 1368 1504 1728  720 721 724 763  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x720_85"  110.01  1280 1360 1496 1712  720 721 724 756  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x720_75"  95.65  1280 1352 1488 1696  720 721 724 752  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x720_60"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
    
    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1280x720_50"  60.47  1280 1328 1456 1632  720 721 724 741  -HSync +Vsync
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia Corporation"
    BoardName "NVIDIA GeForce 6100 and later"
    Driver "nvidia"
    Option "DPMS" "false"
    Option "DynamicTwinView" "false"
    Option "AddARGBGLXVisuals"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Modes "1600x900" "1366x768" "1360x765" "1280x720"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1600x900" "1366x768" "1360x765" "1280x720"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1600x900" "1366x768" "1360x765" "1280x720"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1600x900" "1366x768" "1360x765" "1280x720"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    Screen "screen1"
EndSection

```

Good luck with that. I have to reinstall Kubuntu before I can try it, which will be later today.

> From xrandr usage:
  --output <output>
 --...
 --...
 --...
  --gamma <r>:<g>:<b>
 Mean anything to you? Was yours asking for YOUR input? Or was your system supposed to supply the info?

No, mine just kept metioning 'failed to get gamma' (or something like that). It didn't ask me for any gamma values, or any other additional input. This is a 20" widescreen LCD monitor, with a max resolution of 1600x900. It works great with the non-free drivers, but my eyesight doesn't work as good though, so I was hoping for more display options.

Hope this helps.

---

### Post by Moozillaaa on 2010-10-20
I think it's solved; see post 10.

I just sent a message to the Wiki/Launchpad pagemasters...


I wasted my display too, and copied my X11 folder in its entirety from a Karmic install on my laptop. I have PCLOS '07, but never boot it up. It wouldn't do Broadcom wireless. Aside from that, it was the fastest distro I ever used, by far...

---

### Post by Moozillaaa on 2010-10-20
Time to get bold, and create a startup script.

First, the new/added mode has to be made the default (preferred) selection;
This is done with '--auto'? '--preferred'? Help?

(be back on it later here)

---

### Post by Moozillaaa on 2010-10-20
[B][COLOR=DarkGreen]I got the xrandr script added to the gdm startup file, 
[/COLOR][/B]
> #!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi

[B][COLOR=Red]xrandr --newmode "1280x1024" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA-0 1280x1024

xrandr --output VGA-0 --mode 1280x1024[/COLOR][/B]

initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

(rest of file edited for length)

[B][COLOR=DarkGreen]and rebooted.

It came up with the login screen at 1280 x 1024 (I'm pretty sure), but the desktop was at 640 x 480 (note the asterisk):[/COLOR][/B]
> 
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9[SIZE=3]**[COLOR=Red]*[/COLOR]**[/SIZE] 
   1280x1024      59.9  
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$

[COLOR=DarkGreen][B]I think one of the command lines needs either '--auto', or '--preferred' added to the textline, for the default...

Anybody?[/B][/COLOR]

---

### Post by Moozillaaa on 2010-10-21
I don't know if anybody is following this or not, and so far I've found one syntax error on the Wiki page [here](https://wiki.ubuntu.com/X/Config/Resolution), and the second part of the page, which shows how to make adjustments permanent, is working only in part. I have not found the solution to that error yet.

The 'newmode' of resolution seems to be made permanent by addition of the xrandr commands to the file /etc/gdm/Init/Default, but only the login screen resolution takes the preferred setting. The desktop, in my case, opens at the lowest resolution, until I re-execute the xrandr command to change the mode.

---

### Post by COKEDUDE on 2010-10-27
> xrandr: cannot find mode 1024×768

I see a lot of people are having trouble with this. 

In Linux capitalization is VERY important. Here you guys did not capitalize your the "X" in your resolution. Once you capitalize your "X" you should be good. Here is an example of what worked for me. 

```
xrandr --output VGA1 --mode 1024x768 --rate 60
```

---

