---
title: "display preferences"
date: 2009-05-19
forum: General Help
---

### Post by luisridaocruz on 2009-05-19
I'm a newbie to Ubuntu.
I tried to change the display preferences. The resolution is so "flawed" (visible dektop at 100 metres distance) that I can't just work. I cannot even edit through System->Preferences->Display because of the size of the window (no even able to scroll up and down). I'm forced to work in the Windows OS to post this.
 
Can anyone help, please?

---

### Post by Legace on 2009-05-19
> **luisridaocruz said:**
> I'm a newbie to Ubuntu.
I tried to change the display preferences. The resolution is so "flawed" (visible dektop at 100 metres distance) that I can't just work. I cannot even edit through System->Preferences->Display because of the size of the window (no even able to scroll up and down). I'm forced to work in the Windows OS to post this.
 
Can anyone help, please?

Open the Display application and then make the GNOME panels auto-hide.
You can change resolution by up or down arrow buttons, and to apply you can presse ALT + A :)

---

### Post by luisridaocruz on 2009-05-19
Well,,,I said that I am a "newbie".
So to open "Display" aplication is no problem but "to make GNOME panels to auto hide"
sounds non-sense to me. What I need is "instructions" on "how to make GNOME panels to auto hide" ,,,,,,,,,,,

---

### Post by colau on 2009-05-19
> **luisridaocruz said:**
> Well,,,I said that I am a "newbie".
So to open "Display" aplication is no problem but "to make GNOME panels to auto hide"
sounds non-sense to me. What I need is "instructions" on "how to make GNOME panels to auto hide" ,,,,,,,,,,,
Right click on the panel.
Do you get any option from properties?

---

### Post by luisridaocruz on 2009-05-19
The only options I get are the regular useless ones:

resize
close
....
move to right workspace

but NO, nothing like "make GNOME panels aotu hide" or anything like that.
Didn't I say that I cannot even to scroll down that window?

---

### Post by Legace on 2009-05-19
By panel, I mean the area where is "Applications - Places - System". Right click on a BLANK area and select properties.

Alternatively, open Applications->Terminal, type in the following, and copy paste the info here (you can copy by SHIFT+CTRL+C).
```
xrandr
```

---

### Post by luisridaocruz on 2009-05-19
luisridaocruz@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 640 x 400, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 640x400+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       59.9 +
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1* 
   640x350        85.1  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

---

### Post by Legace on 2009-05-19
What resolution do you want?
I will use 1280x800 in the example below. USE YOUR **OWN** RESOLUTION INSTEAD!

```
xrandr --output LVDS --mode 1280x800
```

---

### Post by luisridaocruz on 2009-05-19
It seems that I have finally managed to change the screen resolution 

Thanks for your help!!

---

### Post by Legace on 2009-05-19
> **luisridaocruz said:**
> It seems that I have finally managed to change the screen resolution 

Thanks for your help!!
No prob. Enjoy.

---

