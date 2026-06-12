---
title: "Linux not a fan of my hardware?"
date: 2006-01-11
forum: General Help
---

### Post by foulplay on 2006-01-11
[http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PAGE_TYPE=US&PRODUCT_ID=3669&SITE=NA](http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PAGE_TYPE=US&PRODUCT_ID=3669&SITE=NA)

That is the motherboard I use.

I have it in single graphics card mode, using a single x800xt platinum.

I also have a SATA HDD, which I assumed might be the problem but it installs fine, then just throws me to the command line (the first time, after that nothing just a black screen)

---

### Post by 23meg on 2006-01-11
Try changing the "Driver" line in the "Device" section of your /etc/X11/xorg.conf file to "vesa" and see if X starts. You should be able to do this if you boot in recovery mode.

---

### Post by foulplay on 2006-01-12
:confused: I'm sorry for my basic knowledge being so limited, but I'm really just trying to get into linux (avoiding Vista at all costs) so I'm not familiar with alot of this stuff... How would I go about doing that within the command line?

---

### Post by vruum on 2006-01-12
after logging in, type:
```
sudo nano /etc/X11/xorg.conf
```
notice that the X in X11 is capitalized
then find the line that says :
```
Section "Device" 
```
just below that, there should be a line saying 
```
Driver            "$SOMETHING"
```
replace the $Something with vesa, press F2, it will ask if you want to save the file, pres "y" pres enter, and it will save the file file and drop you back to the command line, type either:
```
startx
```
then it might start, or it will at least give you some error message, that you can post here.

---

### Post by foulplay on 2006-01-12
[QUOTE=vruum]after logging in, type:
```
sudo nano /etc/X11/xorg.conf
```
notice that the X in X11 is capitalized
then find the line that says :
```
Section "Device" 
```
just below that, there should be a line saying 
```
Driver            "$SOMETHING"
```
replace the $Something with vesa, press F2, it will ask if you want to save the file, pres "y" pres enter, and it will save the file file and drop you back to the command line, type either:
```
startx
```
then it might start, or it will at least give you some error message, that you can post here.[/QUOTE]
AWESOME, I'll try it out first thing tomorrow.  Thanks for the detailed step by step.

---

### Post by foulplay on 2006-01-19
I'd just like to thank everyone, I finally got around to trying it and it worked!

THANK YOU ALL!

---

