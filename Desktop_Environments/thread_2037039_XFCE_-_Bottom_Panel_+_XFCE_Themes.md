---
title: "XFCE - Bottom Panel + XFCE Themes"
date: 2012-08-03
forum: Desktop Environments
---

### Post by xfcegnome on 2012-08-03
Hi everyone. I'm new to Linux and new on this forum :).

I have Xubuntu 12.04, i was experimenting around and I accidently deleted the bottom panel (or is it a launcher). Now I want it back. 

Does anyone know how to bring back the bottom panel. I have searched and searched but nothing helps. Thank you!


Also, is there an easier way to download and install themes to Xubuntu? I have seen photos of beautiful xfce-looks but have not been able too make it look anything near that. 

For example like this one

[http://mmesantos1.deviantart.com/art/Grey-Mountain-Horizon-317295402?q=boost%3Apopular%20xubuntu%2012.04&qo=4](http://mmesantos1.deviantart.com/art/Grey-Mountain-Horizon-317295402?q=boost%3Apopular%20xubuntu%2012.04&qo=4)

Thanks in advance and sorry for my english. :).

---

### Post by LewisTM on 2012-08-03
The only way to get that panel back would be to wipe you panel config so that everything is reset to factory defaults.

First logout and switch to a virtual terminal (Ctrl-Alt-F1).
Login and delete your panel config directory and config file
```
rm -rf ~/.config/xfce4/panel
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
```
The switch back to the login manager (Ctrl-Alt-F7) and log back in.
You can also delete these files graphically if you have another DE installed, as long as you are not logged into Xfce.

Cheers!

---

### Post by black veils on 2012-08-03
you are in the right place to get the themes [http://xfce-look.org/index.php?xcontentmode=15x100x420](http://xfce-look.org/index.php?xcontentmode=15x100x420)

**themes** >> **xfce** = window decorations


for panel themes/backgrounds  [http://xfce-look.org/usermanager/search.php?username=blackveils&action=contents](http://xfce-look.org/usermanager/search.php?username=blackveils&action=contents)


as for the panel/launcher, you can either do the config reset, or create a new bottom panel/launcher. the panels are all the same thing, its just a case of tweaking it into a launcher.

>> right-click top panel 
>> **panel** 
>>** panel preferences** 
>> where it says** panel 1**, there is a plus sign, click it to add a new panel 
>> drag it to the bottom of the screen by grabbing the handle, and slide along until it clicks to the center 
>> continue using the **panel preferences**, go to **items** tab 
>>  click the plus sign to add a new item 
>> highlight **launcher**, click **add** button for howevere many you want, then **close** 
>> highlight a launcher in the **items** tab list, click the settings icon at the bottom
>> here you will add the desired app to launch, click the plus sign 
>> type your app name or scroll through the list, click **add** 
>> go to the **advanced** tab to change any other settings like tooltips 
>> click **close**, it will now show on the panel, do the same with the other launcher items listed.

for general panel settings, go to the **display** and **appearance** tabs. you can switch between panels at the top drop-down box for configuring each using those tabs.

---

### Post by Toz on 2012-08-03
> **black veils said:**
> 
**themes** >> **xfce** = window decorations


To clarify, themes in Xfce are composed of two parts:

1. GTK2/3 skins = Settings Manager -> Appearance (everything inside the window borders and title bar)
2. Xfwm skins = Settings Manager -> Window Manager (window borders, window title bar, maximize/minimize/close buttons, ...)

If the theme you download comes with both gtk2/3 and xfwm directories, you'll need to set it in both locations. Of course, you could mix and match...

---

