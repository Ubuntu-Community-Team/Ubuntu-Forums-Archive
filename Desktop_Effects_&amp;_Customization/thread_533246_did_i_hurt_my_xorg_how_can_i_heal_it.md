---
title: "did i hurt my xorg? how can i heal it?"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by Maxster on 2007-08-23
ok sooo,

i got bored and tryed to get dual display working with nvidia settings.
I did it, it worked, but i preffered it wen i hade gl desktop.

so i got everthing back the way it was, but wen running the gl desktop effects i loose window boarder and title bar. and the terminal is blank, but i cant see what im writting... :-S

so how can i bring back the good ol window boarders and title bar?

thanks!
maxd

edit: and in the gl desktop gui the video card section says videocard0 instead of nvidia je-ne-sais-quoi

---

### Post by w4ett on 2007-08-25
> **Maxster said:**
> ok sooo,

i got bored and tryed to get dual display working with nvidia settings.
I did it, it worked, but i preffered it wen i hade gl desktop.

so i got everthing back the way it was, but wen running the gl desktop effects i loose window boarder and title bar. and the terminal is blank, but i cant see what im writting... :-S

so how can i bring back the good ol window boarders and title bar?

thanks!
maxd

edit: and in the gl desktop gui the video card section says videocard0 instead of nvidia je-ne-sais-quoi

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

### Post by Maxster on 2007-08-25
Thanks!
this should do it!

---

