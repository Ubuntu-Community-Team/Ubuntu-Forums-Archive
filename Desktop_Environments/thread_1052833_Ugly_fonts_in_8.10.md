---
title: "Ugly fonts in 8.10"
date: 2009-01-28
forum: Desktop Environments
---

### Post by 4rtur on 2009-01-28
Hi,

I can't figure it out why on my laptop fonts look ugly while on the desktop they look smooth and nice.

Both machines are set up in same way.

Attached a screen shot of my config and example websites with ugly fonts.

---

### Post by blazemore on 2009-01-28
1. Turn on Subpixel Smoothing in the Fonts preferences
2. Install the package msttcorefonts

---

### Post by overdrank on 2009-01-28
> **4rtur said:**
> Hi,

I can't figure it out why on my laptop fonts look ugly while on the desktop they look smooth and nice.

Both machines are set up in same way.

Attached a screen shot of my config and example websites with ugly fonts.

Hi and I found the website and it does not appear that bad on my system. What is the model of the graphics card and have you installed any drivers for it?

---

### Post by 4rtur on 2009-01-28
> **blazemore said:**
> 1. Turn on Subpixel Smoothing in the Fonts preferences
2. Install the package msttcorefonts

1. Can you explain why ? I'm using LCD screen.
2. It's installed.

---

### Post by 4rtur on 2009-01-28
> **overdrank said:**
> Hi and I found the website and it does not appear that bad on my system. What is the model of the graphics card and have you installed any drivers for it?

Take a look at attached screen shot.

---

### Post by mcduck on 2009-01-28
> **4rtur said:**
> 1. Can you explain why ? I'm using LCD screen.
2. It's installed.

Because LCD screens are the very reason why subpixel smoothing is used. Each pixel you see on your screen is actually three small pixels, red, green and blue. Subpixel smoothing uses information about your screen's DPI and subpixel order to smooth the fonts using these smaller subpixels instead of relying on larger full pixels. This gives better looking fonts with less blurring than waht you's get with normal smoothing methods.

Anyway, check what is the correct DPI setting for your display (this depends on screen size and it's native resolution), and then try different subpixel orders to see which one works best for your screen.

---

### Post by 4rtur on 2009-01-28
> **mcduck said:**
> Because LCD screens are the very reason why subpixel smoothing is used. Each pixel you see on your screen is actually three small pixels, red, green and blue. Subpixel smoothing uses information about your screen's DPI and subpixel order to smooth the fonts using these smaller subpixels instead of relying on larger full pixels. This gives better looking fonts with less blurring than waht you's get with normal smoothing methods.

Anyway, check what is the correct DPI setting for your display (this depends on screen size and it's native resolution), and then try different subpixel orders to see which one works best for your screen.

Don't think this is the deal here.
Look at the attached screenshot, it shows two pages displayed on same screen. Some font missing ? It's only happens on few websites.

---

### Post by mcduck on 2009-01-28
> **4rtur said:**
> Don't think this is the deal here.
Look at the attached screenshot, it shows two pages displayed on same screen. Some font missing ? It's only happens on few websites.

Missing a font should not be a problem, at least if you define good looking default fonts in your browser's settings.

---

### Post by 4rtur on 2009-01-28
> **mcduck said:**
> Missing a font should not be a problem, at least if you define good looking default fonts in your browser's settings.

This is my FF settings, I can't compere it to my home PC now.

Anything wrong ?

---

### Post by mcduck on 2009-01-28
> **4rtur said:**
> This is my FF settings, I can't compere it to my home PC now.

Anything wrong ?

Try those fonts outside of Firefox, if they look good then they are fine, if not use some others.

Font definitions in web pages are simply suggestions, the page suggests a list of fonts, your browser tries first one, if you have that font it's used and if you don't have it your browser tries the next one. In the end, if none of the fonts suggested are found the default fonts you have configured in browser settings are used.

Because of this a missing font can't cause ugly fonts on web pages. On the other hand if the page defines some ugly font, and you have that font, it will be used. I haven't got half of the fonts that page lists in it's font definitions so I can't check if any of them could be your problem.

---

