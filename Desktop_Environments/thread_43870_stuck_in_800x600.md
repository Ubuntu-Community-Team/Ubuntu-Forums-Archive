---
title: "stuck in 800x600"
date: 2005-06-23
forum: Desktop Environments
---

### Post by Diddy1 on 2005-06-23
I can't get my screen resolution to get any lower. My xp pro partition gives me a 1024x768 and others. But ubuntu won't. i have a Compaq fs7600 17-inch CRT flat screen monitor. And in the xorg.conf it's detected and listed right. I've tried removing the other screen resolutions from the xorg config but it worn't work. So anyone got a suggestion?

Thank You

---

### Post by rachii on 2005-06-23
in xorg.conf put in the screen resolutions you want (under section Screen and subsection Display), also put in the HorizSync and VertRefresh under the Monitor section

---

### Post by Diddy1 on 2005-06-23
[QUOTE=rachii]in xorg.conf put in the screen resolutions you want (under section Screen and subsection Display), also put in the HorizSync and VertRefresh under the Monitor section[/QUOTE]


Tried no responce. But however as i said i keep getting only the lowest 800x600.

---

### Post by Xian on 2005-06-23
Please post the 'Section "Monitor"' and 'Section "Screen"' portions of your xorg.conf file.

---

### Post by byen on 2005-06-23
Xian... a while ago ive seen a post from you with specs stating you had a compaq with a radeon 7500 graphic card.. if so what is the highest resolution you get...?  I have a 1024X726 at a measly 60hz (i did not install any drivers...it came default after installation . Is this the max i can get? i know fo sure i got more when i ran suse for a while (an hour). .... itd be kool if yu can help....

PS - diddy' sorry i popped into your thread. I have a similar Q so i thought i might chip in too.

---

### Post by Zeroedout on 2005-06-23
for one monitor i had, i had to put both the horizsync nad vertrefresh as well as DispSize with even one of those mising it would only show 640x480 so make sure you ahve all 3

---

### Post by crane on 2005-06-23
Be sure to restart X after the config file is changed and saved.

---

### Post by Xian on 2005-06-24
[QUOTE=byen]Xian... a while ago ive seen a post from you with specs stating you had a compaq with a radeon 7500 graphic card.. if so what is the highest resolution you get...?  [/QUOTE]
Nah, the monitor is a 7500 series. I use a nvidia card.
It runs at 1024x768 @85.

---

### Post by byen on 2005-06-24
[QUOTE=Xian]Nah, the monitor is a 7500 series. I use a nvidia card.
It runs at 1024x768 @85.[/QUOTE]
 duh! guess my desperation to get a higher resolution has made me delusional...sorry!

---

### Post by Diddy1 on 2005-06-24
i tried this 
[http://ubuntuforums.org/showthread.php?t=21984&highlight=resolution](http://ubuntuforums.org/showthread.php?t=21984&highlight=resolution)
but it still igves me the lowest. My screen is so big i can barely edit xorg.conf please help suggest anything and i'll try it. I really love ubuntu and want to use as my primary os.

---

### Post by virgule on 2005-06-24
First, [Is this your monitor?](http://www.peachdirect.com/product.tml?sku=CPQ%20FS7600&subCategory=3003&_UserReference=179AE833349B0C4441AAB09E) 
Second, does your xorg.conf file have a **Modeline** line in **Section "Monitor"**? If it does not, use **gtf** utility to generate an appropriate Modeline you will then insert in **Section "Monitor"**: But before you go edit, yet again, xorg.conf, lets make sure it already have the proper value for **VertRefresh** and **HorizSync**. According to the spec sheet I found, It should be like that:
```

Section "Monitor"
(snip...)
        HorizSync       30-70
        VertRefresh     50-140
(...snap)
EndSection

```

Now that we are sure we have the all the proper monitor specs in xorg.conf, lets make it actually work. I used **gtf** for you to generate the correct **Modeline** for 1024x768@85Hz:
```

 gtf 1024 768 85

  # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

```
If you want a bit more, Im confident you can safely raise the resulution a notch by sacrifying(spell?)  some refresh rates (75 instead of 85). Its up to you..
```

gtf 1152 864 75

  # 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
  Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync

```

Alright, insert one of these line in xorg.conf's **Section "Monitor"**:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-140
        # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
        Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
EndSection

 --OR--

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-140
        # 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
EndSection

```

Finally, the last step is **Section "Screen"** setup:
```

Section "Screen"
(...)
        SubSection "Display"
                Depth           1
                Modes           "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes            "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes            "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes            "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes            "1152x864" "1024x768"
SubSection "Display"
                Depth           24
                Modes            "1152x864" "1024x768"
        EndSubSection
EndSection

```
Keep two or leave one. If there is more than one, Xorg will auto-choose the first in line.

Restart Xorg and see the results. Let me know if its working or smoking.

-Andrew (aka: virgule)

---

### Post by Moezzie on 2005-11-30
made it exactly as u told, but it dident work...
had the same problem wen i used Suse but after some configurations in the devicemanager it worked just fine.

I think i changed something to VGA monitor or something like that.

---

### Post by teaker1s on 2005-11-30
sudo dpkg-reconfigure xserver-xorg to set it up easily

---

### Post by Moezzie on 2005-11-30
thanks for the tip man.
It worked just fine. But now my keyboard dosent work. But that probarbly my own fault.

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```
This is the easy way to edit xorg.

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.  (Number of MB * 1024)

Log out and ctrl-alt-backspace to restart xserver.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

