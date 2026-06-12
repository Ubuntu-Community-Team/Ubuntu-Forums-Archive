---
title: "howto change icon size? System load indicator."
date: 2011-05-15
forum: Desktop Environments
---

### Post by Azyx on 2011-05-15
About Unity on 11.04
1. How do i change the size of the icons in the left panel (Laucher)? I only get 9 button-icones on my little screen.

2. Is it possible to see system load and so on, as 'System monitor'-applet in gnome?

3. Is it possible to hide the upper panel to save space? Let it show when hovering with the mouse cursor, when you already should be in the upper area?

---

### Post by Azyx on 2011-05-15
Answer my self on no 1. Resize launcher icon size.
Install Compizconfig settings manager.  ```
sudo apt-get install compizconfig-settings-manager
``` 
after install, search after compiz and open Compizconfig setting manager. Then under Desktop there are an 'Ubuntu Unity Plugin' open it and select 'Experimental' tab and there you may change Launcher icon size between 32-62. 48 is default

---

### Post by Frogs Hair on 2011-05-15
You can view your load average from the processes tab on the system monitor . I added this horizontal Conky which appears at the bottom of my 1280 x 1024 screen without a conflict with maximized windows or the Unity launcher. [http://gnome-look.org/content/show.php/Horizontal+conky?content=140243](http://gnome-look.org/content/show.php/Horizontal+conky?content=140243)

---

### Post by Azyx on 2011-05-15
> **Frogs Hair said:**
> You can view your load average from the processes tab on the system monitor . I added this horizontal Conky which appears at the bottom of my 1280 x 1024 screen without a conflict with maximized windows or the Unity launcher. [http://gnome-look.org/content/show.php/Horizontal+conky?content=140243](http://gnome-look.org/content/show.php/Horizontal+conky?content=140243)

Please, can you tell me what I will do with the .conkyrc file?

/Cheers

---

### Post by Frogs Hair on 2011-05-15
There is a Conky tutorial an the second post of this thread . You will need to install lm-sensors and the conky-all packages .[http://ubuntuforums.org/showthread.php?t=1757540](http://ubuntuforums.org/showthread.php?t=1757540)

---

### Post by Frogs Hair on 2011-05-15
This is the method I used.
```
 sudo apt-get install lm-sensors 
``````
sudo sensors-detect
```Answer yes to all questions
```
sudo apt-get install conky-all
```Copy and paste the the Conky rc from the download page to the text editor save to home as ```
.conkyrc
```Press Alt + F2  and erter conky. There is a tutorial on the thread for an autostart script.

---

### Post by steinerd on 2011-05-15
For part 2 to your question..

I had some of the same questions with the panel-apps from gnome.  They call them "indicators" and I have gathered a few of them [here on my home page]("http://deep-sea.realservers.info/ubuntu/unity-launcher/unity-panel-indicators/").  Hopefully this helps you out.

[http://deep-sea.realservers.info/ubuntu/unity-launcher/unity-panel-indicators/](http://deep-sea.realservers.info/ubuntu/unity-launcher/unity-panel-indicators/)

---

### Post by Azyx on 2011-05-15
> **steinerd said:**
> For part 2 to your question..

I had some of the same questions with the panel-apps from gnome.  They call them "indicators" and I have gathered a few of them [here on my home page]("http://deep-sea.realservers.info/ubuntu/unity-launcher/unity-panel-indicators/").  Hopefully this helps you out.

[http://deep-sea.realservers.info/ubuntu/unity-launcher/unity-panel-indicators/](http://deep-sea.realservers.info/ubuntu/unity-launcher/unity-panel-indicators/)

Thanx look good. I have installed indicator-multiload but it does not appear :( How do i activate it?

---

### Post by Frogs Hair on 2011-05-15
> **Azyx said:**
> Thanx look good. I have installed indicator-multiload but it does not appear :( How do i activate it?

Type the name into dash and select it or restart , I had to do this with the weather indicator when I installed it .

---

### Post by Azyx on 2011-05-15
> **Frogs Hair said:**
> Type the name into dash and select it or restart , I had to do this with the weather indicator when I installed it .

Thanx it work fine :)

---

