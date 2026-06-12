---
title: "Can not set resolution to 1280 * 1024"
date: 2012-02-20
forum: Desktop Environments
---

### Post by MIRAAN Baloch on 2012-02-20
Hi 

I have installed Ubuntu 11.10 I have facing some problems pl z help me

I want to set dispaly as 1280 by 1024

But in display there is 1280 by 1024 not present but there is 1024 768 and 800 600 present!


Plz Solve this problem 

thanks

---

### Post by youngunix on 2012-02-20
Does your monitor support 1280x1024?

---

### Post by MIRAAN Baloch on 2012-02-21
> **youngunix said:**
> Does your monitor support 1280x1024?


yes I have HPLP1965 LCD Moniter, 

plz chack this screen shot?
[ATTACH]213040[/ATTACH]

---

### Post by youngunix on 2012-02-21
> **MIRAAN Baloch said:**
> yes I have HPLP1965 LCD Moniter, 

plz chack this screen shot?
[ATTACH]213040[/ATTACH]

I have checked the specs of your monitor and it seems that 1280x1024 is the max resolution. 
I should have asked you about the graphics card as well, ma bad. 
Check if it supports that resolution.
Check if there are any drivers available in >>Settings>Additional Drivers.

*Just to  be sure; sometimes other resolutions are down/up, you just need to scroll to see them.

---

### Post by MIRAAN Baloch on 2012-02-22
**thanks**

---

### Post by JC Cheloven on 2012-02-22
> **MIRAAN Baloch said:**
> **thanks**
Not sure if that means you fixed your problem. 

If not, please, post bacck the output of this command on a terminal:
```
xrandr
```
and also ```
lspci |grep VGA
```

---

### Post by roelforg on 2012-02-22
Run and post output:
```

sudo cat /proc/cmdline

```

---

### Post by MIRAAN Baloch on 2012-02-22
> **JC Cheloven said:**
> Not sure if that means you fixed your problem. 

If not, please, post bacck the output of this command on a terminal:
```
xrandr
```and also ```
lspci |grep VGA
```



$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  


Maximum is 8192 x 8192 but i cant set 1280 x 1024

---

### Post by JC Cheloven on 2012-02-27
The state of the question so far is:

- Your monitor [DOES support]("http://www.google.es/url?sa=t&rct=j&q=hplp1965%20lcd&source=web&cd=2&sqi=2&ved=0CDYQFjAB&url=http%3A%2F%2Fh18000.www1.hp.com%2Fproducts%2Fquickspecs%2F12620_na%2F12620_na.PDF&ei=O9VLT5SOC6Of0QXNu5iZDg&usg=AFQjCNHm-KPtG2T6LJz-rv1Ew8Fp--az-A&sig2=XRK9HiFCqdP7EtJmEPYvQg&cad=rja") 1024x768

- The xrandr command does not offer 1024x768 as possible choice, which most likely indicates that the graphics card does not support that resolution. That's why I asked you for the output of lspci command.

The most sensible choice should be to use the maximum resolution of both the monitor and the graphics card. We could try to setup a new 1024x768 graphics mode using the xrandr command, but first we should know if that is supported both by monitor and graphics card.

---

