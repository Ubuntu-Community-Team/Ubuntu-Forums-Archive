---
title: "how to find the ideal resolution for a 11.6 screen?"
date: 2010-10-17
forum: Desktop Environments
---

### Post by abelito8 on 2010-10-17
Hi there, 

I have ubuntu installed on my Acer Aspire One 11.6 160GB and I cannot find a decent resolution. If I go to system>preferences>monitor it says "unknown" (that is the system does not recognize the size of the screen)

I had found a post helping to add a screen definition through the terminal but it did not help, I also checked what resolution I should use as standard but still

anyone with a computer of the same size having solved the issue?
thank you in advance

---

### Post by mister_playboy on 2010-10-17
The native resolution for that laptop appears to be 1366x768.

---

### Post by ankspo71 on 2010-10-17
Hi,
I used to have that "monitor = Unknown" problem when I was using my older CRT monitor for my desktop computer. 

So are you having trouble finding a resolution with the correct aspect ratio? 

Here is a perfectly shaped circle:
[www.steeldolphin.com/htmltuts/swoosh/step3_circle.gif](www.steeldolphin.com/htmltuts/swoosh/step3_circle.gif)
If it appears as an oval shape, then you aren't using the correct screen resolution for your monitor's aspect ratio, or you might need to adjust your monitor's settings (if available) to increase/decrease the height and width of your screen a lttle.

You can use this site to find the best resolution for surfing the web.
[http://www.infobyip.com/testwebsiteresolution.php](http://www.infobyip.com/testwebsiteresolution.php)
It is a simulated Kubuntu (or other KDE distro) desktop :P

Also, you can type 'xrandr' in the terminal to see what screen sizes and refresh rates are available for your monitor. It might be better than using the display configuration tool in the "system settings" There is also a graphical tool for this "KRandRTray". It is a KDE utility that runs in the system tray. It is located at Kmenu > Applications > System > KRandRTray. You can use it to preview some of the available screen sizes, and if you create a startup entry for it, it "should" remember your selected screen size, but if not it will run in the tray. It has been so long since I last used it with my older monitor though, so I'm not sure if it will keep your selected size. If that doesn't work, you can create a script to run xrandr to set a good screen size for you on startup.

---

### Post by ankspo71 on 2010-10-18
Hi Again,
Here is another link concerning xrandr:
[http://ubuntuforums.org/showthread.php?p=9989665](http://ubuntuforums.org/showthread.php?p=9989665)

For more info on xrandr, see:
[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Hope this helps.

---

### Post by kio_http on 2010-10-18
Your laptop has a 1366 X 768 WXGA LCD Flat panel

---

### Post by abelito8 on 2010-10-23
Thank you very much
now I have added the new resolution (1368 x 766 instead of 1366 x 766 but still...)
I tried and it gives me

xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        73.0  
   640x480        86.0  
  1368x768_60.00 (0x13a)   85.0MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.6KHz
        v: height  768 start  771 end  781 total  798           clock   59.7Hz


which means it can detect it...

the problem is how to make it default

if I type 
xrandr --addmode default 1368x768_60.00 (0x13a)   85.0MHz
bash: syntax error near unexpected token `('

the tutorial says 

You can direct xrandr to set a different resolution using the following command
 [INDENT]xrandr --output VGA --mode 1024×768 --rate 75


but I do not know what is output VGA  or LVDS

[/INDENT]

---

### Post by abelito8 on 2010-10-23
It also says 

If the mode already exists, but just isn't associated for the particular output, you can add it like this: 

  $ xrandr --addmode S-video 800x600

but what is the result of S-video?

---

### Post by abelito8 on 2010-10-23
I also tried

abelito@Ernestino:~$ xrandr --1024x768+0+0 0mm x 0mm --mode 1368x768_60.00

and it gives

usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query


etc...

---

### Post by ankspo71 on 2010-10-23
> **abelito8 said:**
> Thank you very much
now I have added the new resolution (1368 x 766 instead of 1366 x 766 but still...)
I tried and it gives me

xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
[COLOR="Red"]default[/COLOR] connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        73.0  
   640x480        86.0  
  1368x768_60.00 (0x13a)   85.0MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.6KHz
        v: height  768 start  771 end  781 total  798           clock   59.7Hz


which means it can detect it...

the problem is how to make it default

if I type 
xrandr --addmode default 1368x768_60.00 (0x13a)   85.0MHz
bash: syntax error near unexpected token `('

the tutorial says 

You can direct xrandr to set a different resolution using the following command
 [INDENT]xrandr --output VGA --mode 1024×768 --rate 75


but I do not know what is output VGA  or LVDS

[/INDENT]

Hi,
Your output is called default as seen highlighted in red in the above quote. My output is the same way. I have not had any luck adding my own custom resolution but the command you could use to try to see if it works would be like this:

xrandr --output default --mode 1368x768_60.00 

Hope this helps.

---

### Post by abelito8 on 2010-10-23
Something is moving...
it tries to configure, I see the screen lights up and down but then 


abelito@Ernestino:~$ xrandr --output default --mode 1368x768_60.00
xrandr: Configure crtc 0 failed

....

---

### Post by abelito8 on 2010-10-23
I have tried graphically and at least it shows 1368x768 in the list of possible configurations...

but also says it cannot be applied...

---

### Post by bruno9779 on 2010-10-24
have you checked if you have any proprietary drivers available to install?

Your computer should have an intel GMA 500 GPU, I don't know if any drivers are available for it.

I read it isn't a very well supported graphics card, but this should help:

[http://www.webupd8.org/2010/05/fix-intel-gma500-poulsbo-graphics-in.html](http://www.webupd8.org/2010/05/fix-intel-gma500-poulsbo-graphics-in.html)

or this

[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

---

### Post by abelito8 on 2010-10-24
I typed the two lines suggested by the post and it worked.....now I have the definition I needed on a 11.6

faraway...so close

thanks a million

---

