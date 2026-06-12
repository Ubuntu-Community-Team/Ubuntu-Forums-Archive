---
title: "Ubuntu 11.04 - Notebook LCD color management"
date: 2011-10-30
forum: Desktop Environments
---

### Post by andrey_ on 2011-10-30
Hello there!

I've just changed the LCD panel of my Acer Aspire notebook 5738Z, but the problem is that the screen is yellowish. 

 My VGA is Intel 4500M, please let me know if it's possible to adjust colors  in Ubuntu 11.04?

Thanks

---

### Post by mcduck on 2011-10-30
Sure. There's the conveniently named "Color" tool available in System Settings. Although you'll need to acquire a proper color profile file for your display to use it. It does support some color profiling tools, but doesn't have any basic GUI-based calibration utility (like Adobe Gamma) you could use without a hardware calibration tool.

Apart from that, I believe it might be possible to adjust the color temperature with some options in xorg.conf, but that probably depends on your graphics card.

---

### Post by andrey_ on 2011-10-30
> **mcduck said:**
> Sure. There's the conveniently named "Color" tool available in System Settings. Although you'll need to acquire a proper color profile file for your display to use it. It does support some color profiling tools, but doesn't have any basic GUI-based calibration utility (like Adobe Gamma) you could use without a hardware calibration tool.

Apart from that, I believe it might be possible to adjust the color temperature with some options in xorg.conf, but that probably depends on your graphics card.

Thank you for your reply.

I can change  brightness, contrast and gamma but could not manage to changes colors temperature.

My VGA is : Intel GMA  4500M , any suggestion on how to go about it (in steps) ? it's really frustrating and I've searched the web with no clear solution  :(

---

### Post by andrey_ on 2011-10-30
> **andrey_ said:**
> Thank you for your reply.

I can change  brightness, contrast and gamma but could not manage to changes colors temperature.

My VGA is : Intel GMA  4500M , any suggestion on how to go about it (in steps) ? it's really frustrating and I've searched the web with no clear solution  :(

I found the solution, all you need is to install Displaycalibration which is a front-end to 
Xgamma.
You can use Xgamma from the command line as well. Here is the link for more details:
[https://linuxtidbits.wordpress.com/2008/03/10/linux-design-calibrate-the-display/](https://linuxtidbits.wordpress.com/2008/03/10/linux-design-calibrate-the-display/)

---

### Post by mcduck on 2011-10-31
That's interesting, would you happen to have a link for the Displaycalibration tool you mentioned? (it's way too generic combination of words for Google to find...)

It would be useful to have such program available when I can't get my hands on a hardware calibration tool.

---

### Post by andrey_ on 2011-10-31
> **mcduck said:**
> That's interesting, would you happen to have a link for the Displaycalibration tool you mentioned? (it's way too generic combination of words for Google to find...)

It would be useful to have such program available when I can't get my hands on a hardware calibration tool.

My fault, it's "Displaycalibrator" and it's available for installation in Ubuntu Software Center. You can use this link [http://www.lagom.nl/lcd-test/](http://www.lagom.nl/lcd-test/) 
to help you with your calibration, though it's not that accurate as hardware calibrator such as "Spyder 2" but 
 for me it served the purpose.

---

### Post by mcduck on 2011-10-31
That's strange, I can't find any such package from Ubuntu's repositories, not even when searching from packages.ubuntu.com. Are you sure you don't have some third-party repository where the package is coming from?

edit: Ok, I figured out why I can't find it... The package exists for 11.04 and older versions, but not for 11.10.

---

