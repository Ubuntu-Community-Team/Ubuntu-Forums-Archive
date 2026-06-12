---
title: "Dell Inspiron 530N Desktop Video Card Driver?"
date: 2007-08-25
forum: Dell  Ubuntu Support
---

### Post by rcdegges on 2007-08-25
Hey. I bought the new Dell Inspiron 530N with ubuntu preloaded, and I formatted it with ubuntu again. I got everything working except for the video card driver. I followed the guides in this forum, but I couldn't find a driver for this nvidia card. If someone could help me I would 'really' appreciate it. I have a 24" monitor and I like watching tv shows and movies on it. And now (with no video card driver), watching movies suckssss. It has really crappy picture quality and everything looks choppy. Thanks!

The card I have is a:    	 128MB NVIDIA GeForce 8300GS

---

### Post by w4ett on 2007-08-26
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Good Luck

---

