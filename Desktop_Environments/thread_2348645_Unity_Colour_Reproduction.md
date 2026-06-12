---
title: "Unity Colour Reproduction"
date: 2017-01-05
forum: Desktop Environments
---

### Post by inhumangeek on 2017-01-05
I have recently noticed a significant difference between the appearance of colours in Ubuntu compared to within my Windows 7 VM. (Ubuntu is washed out and de-saturated compared to the VM). See attached screenshot looking at the same image uploaded to Flickr (in Chrome) - Ubuntu host is on the left and Windows 7 VM on the right. I have noticed this before in Nautilus but this is the first time I have seen it affecting other applications, such as Chrome.

[https://dl.dropboxusercontent.com/s/avf75xz2a98xu5i/Screenshot%20from%202017-01-05%2022-42-13.jpg?raw=1](https://dl.dropboxusercontent.com/s/avf75xz2a98xu5i/Screenshot%20from%202017-01-05%2022-42-13.jpg?raw=1)

 I am into photography and use Lightroom in my VM, and I have calibrated my monitor (within Ubuntu) using dispcalgui, so I don't think it is calibration... and anyway wouldn't the calibration affect both the host as well as the VM equally? Anyway, I'm fairly sure it is Ubuntu that is out as I can look at Flickr from multiple devices as it always matches the Windows reproduction.

Any tips much appreciated.
Thank you!

---

### Post by wildmanne39 on 2017-01-05
Please use thumbnails or url's when posting images because not everyone have broadband or unlimited connections .
Thanks

---

### Post by inhumangeek on 2017-01-05
Apologies - I had downsized the image but will link in the future.

---

### Post by Keith_Helms on 2017-01-05
Are you positive the color profile that dispcalgui created is being loaded at startup?  When I login to my Xubuntu system, the colors look like they did before calibration for a second and then the calibrated profile loads and I can see the colors change.

---

### Post by inhumangeek on 2017-01-08
After a bit more playing I have found it is not calibration, it is to do with colour spaces / RGB... The way ubuntu is converting them I think?

---

