---
title: "Graphics Stutter in Budgie"
date: 2018-05-30
forum: Desktop Environments
---

### Post by speartip on 2018-05-30
At present I find Budgie the best implementation of 18.04. However there is a problem for me that doesn't exist in the other 'Buntus.
About every 10 seconds the Graphics Stutter, Whether watching Video, playing Card Games, or moving windows. I ran the "glxgears" program, & there it was. The gears turned smoothly, but about every 10 seconds they stuttered & then carried on. Pretty basic setup here with Intel HD3000 integrated graphics. As I mentioned this is not an issue on Kubuntu or Xubuntu which I dual boot with.
Any Ideas?

---

### Post by #&amp;thj^% on 2018-05-30
Hello speartip do you have a "xorg.conf" file?
To see use:
```
cat /etc/X11/xorg.conf
```
I don't use Budgie so I'm not familiar with the compositor used. 
I had to add this for mine (xubuntu).
```
Section "Device"
    Identifier  "intel"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
    Option      "AccelMethod"  "sna"
    **#Option      "TearFree" "True"**
    #Option      "Tiling" "True"
    #Option      "SwapbuffersWait" "True"
EndSection


```
And by your use of "Stutter" do you mean Flicker?

---

### Post by speartip on 2018-05-30
I do use a xorg.conf file similar to yours, but with or without it the stutter is still there. This isn't just a flicker, it's as if the screen freezes for a split second then carries on.

---

### Post by #&amp;thj^% on 2018-05-30
> This isn't just a flicker, it's as if the screen freezes for a split second then carries on.
Thanks for that. :)
I'm going to have to defer to someone wiser on Budgie then, as you point out this is the "only effected DE"
Sorry and Good Luck

---

### Post by speartip on 2018-05-30
No Probs. Thanks. I'll keep trying a process of elimination.

---

### Post by kerry_s on 2018-05-30
for are intel graphics it helps to have "beignet" installed.

sudo apt install beignet

---

### Post by speartip on 2018-05-31
Hi kerry.. I checked out the "beignet" package in synaptic. However it says it's for Integrated GPUs of Ivy Bridge & later. My card is Intel Ironlake, which I think is before then.
Thanks anyway for the suggestion.

---

### Post by speartip on 2018-05-31
Finally managed to solve this.
The culprit was the Budgie Panel Applet "Window Previews".
Deleted that and now all is good.

---

