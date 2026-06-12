---
title: "I can't reduce pointer speed enough"
date: 2012-08-02
forum: Desktop Environments
---

### Post by JohnTho on 2012-08-02
Hi, I'm setting up a new system with Ubuntu 12.04 as the only OS. Everything's going smoothly except that the mouse pointer sensitivity is too high and the controls in System Settings don't give me enough control to reduce it to a useable level. I've tried two different mice, one's an old Kensington Si300, the other is a new (budget) Trust 16951-04. They both seem to have similar sensitivity (ppi, I guess) which is still too high with the acceleration and sensitivity sliders at minimum.

Is there any way to further reduce the pointer speed?

---

### Post by NikTh on 2012-08-02
Hi , 
please open a terminal (ctrl+alt+t) and paste below command and give results here
```

 xset -q | grep accel
```
put results inside [code] tags , by highlighting the text and click # on top of message pane.

Thanks

---

### Post by JohnTho on 2012-08-02
Sorry, I don't understand what you're asking re: using code tags, but the command produces the following response. I hope this is what you were wanting:

acceleration:  1/1    threshold:  1

---

### Post by NikTh on 2012-08-02
> **JohnTho said:**
> Sorry, I don't understand what you're asking re: using code tags, 
Hi , 

When you click New Reply , first click # symbol on top of message pane , and then paste code between the brackets.
This is for future knowledge. When we post code here , we post it that way. 

> **JohnTho said:**
> acceleration:  1/1    threshold:  1

Now , try this command and tell me if meet your needs.
```
xset m 1/3
```
**EDIT:** Ok , I searched before but....
...I found it now. Here is the thread --> [http://ubuntuforums.org/showthread.php?p=12143902](http://ubuntuforums.org/showthread.php?p=12143902) , take a look and "play" with different values until find the most appropriate for you. 
Then you can either just write the command on a terminal each reboot or make a script and add it to startup applications. 
Thanks

---

### Post by JohnTho on 2012-08-02
Hi, thanks for the reply. I've tried that value but if it makes any difference it's barely perceptible. In fact that's also true of the GUI adjustment sliders - almost impossible to notice any difference from max to min. I've even tried other values than the one you suggested, up to 1/1024, and can't detect any difference. It seems to me that this value only adjusts acceleration and the threshold at which it starts to take effect rather than the ratio of mouse counts to screen pixels. Have I got that right? If so I think what I need is to divide down the mouse counts by a greater value. To give you some idea I'm using a standard mouse mat which is 24cm wide. From one side of my screen to the other the mouse moves 2cm. I don't want it to move the whole width but at the moment it's just too sensitive for comfort.

---

### Post by NikTh on 2012-08-02
Hi , 
you can adjust and fist value , as the second. 1/1024 ? no. 
I know for sure that xset can reduce your mouse speed. I did it myself . 

Try other values until achieved the expected. 
eg
```
xset m 4/10
``` 

Thanks

---

### Post by JohnTho on 2012-08-02
I don't think it's changing anything. I tried your new value 4/10 and moving the mouse really slowly to avoid the acceleration kicking in it measures 2.5cm side-to-side. I then used xset m with no parameters to reset to the default, checked with xset q this gives 2/1  1, then repeated the measurement and it was still 2.5cm.

---

### Post by NikTh on 2012-08-02
Hi , 
maybe you want to adjust threshold too ? 

```
xset m 5/2 4
``` 

Sorry but I don't know another way to reduce mouse-speed beyond the system-settings.

```
man xset | grep -A15 mouse
``` 

Thanks

---

### Post by JohnTho on 2012-08-02
Hi NikTh,

I've sorted it. It turned out I needed to use xinput set-prop to set the "Device Accel Constant Deceleration" quantity. Having found a value that gives the speed I want I then used the code you included in the thread you linked to create an executable script and add it to the startup applications.

Thanks for all your help, especially the info on creating and using the script.=D>

---

### Post by NikTh on 2012-08-02
Hi , 
glad I helped (even a little) 

Xinput indeed , can do a lot of things.

Thanks

---

