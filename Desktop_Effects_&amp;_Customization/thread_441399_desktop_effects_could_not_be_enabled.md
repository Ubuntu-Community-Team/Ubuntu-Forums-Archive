---
title: "desktop effects could not be enabled"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by abduliounited on 2007-05-12
Hi to Everyone!!

is there someone who have a problem to enable the "Desktop effects"? 
 After I installed my Ubuntu to my laptop I had a problem with my ATI video adapter MOBILITY RADEON 7500: in few word I was able  to see only 70% of my screen. 
Then I fixed it  thanks to our forum. 
Then I went to enable the Desktop effect and I got the following error message: Desktop effects could not be enabled.
Do you know if I can fix it? 
Thanks

---

### Post by moonoverhaddath on 2007-05-12
i'm having the same issue except that i couldn't enable Desktop Effects at all to begin with. 

i am completely new to linux and ubuntu. i just recently learned that 'feisty' is 7.04 and 'beryl' is an equivalent to windows aero. 

i have a laptop with a radeon xpress 200 m video card, and i could not enable desktop effects to begin with. the message i received was 'The composite extension is not available.'

does anyone have a solution, because i've read the other posts and i have a feeling that what's going on with my laptop has nothing to do with it.

:confused:

---

### Post by MasonM on 2007-05-12
You need to install the ATI driver for your card in order to enable 3D.

---

### Post by izizzle on 2007-05-19
I have an ATI RAge 128 pro and i got this message when trying to enable desktop effects: "desktop effects could not be enabled". How do i fix this? How do I install the driver for it? please help!

---

### Post by Bohlio on 2007-05-19
for the "Composite Extention..." error You need to install XGL. I cant remember where a good guide for that is, but i just used it earlier today.

---

### Post by izizzle on 2007-05-20
sorry, but was your post directed to me? If so, what "composite extension" are you talking about?

---

### Post by Ub1476 on 2007-05-20
I guess you are running your session in Gnome, right? You can check by typing "beryl" in the terminal. You'll probably get an error message about Composite Extention, which means you need to download XGL. Also check this code: 

```
glxinfo | grep direct
```

direct rendering: yes, if not, you need to install drivers for your graphic card. Follow this guide: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29"), it install both XGL, graphic driver and Beryl. You need to scroll down to ..Alternate method: Using closed source FGLRX drivers from ATI.. and begin the guide from there.

Good luck:)

---

### Post by Bohlio on 2007-05-20
sorry Izizzle, The Composite extention problem was MoonOverHaddath's. I'm sorry but i cant help you with your problem. The only reason i knew the other one was because I did it yesterday :-). I hope you figure it out though!

---

### Post by izizzle on 2007-05-20
I'll try Ub1476's idea. Hope it works!

---

### Post by lenswipe on 2007-12-09
im having similar problems except im running Gutsy gibbon 7 but when i try and enable ANY of the visual effects ubuntu 7 even normal the ubuntu says "Desktop effects could not be enabled" as if i cant see this with my own two eyes...


i saw some posts saying something about graphics card drivers...


i dont have a graphics card in my machine :(


HELP!!!

thanks

---

### Post by it_fixxer on 2008-02-27
Lenswipe
I'm fairly new to *nix but this is what you have to have a graphics card of some type (possibly built into the mainboard). Try adding the following packages to your system. I went through and found the ones I use for gnome...

gnome-compiz-manager
libgnome-compiz-manager0
libgnome-compiz-manager0-d
xserver-xgl
compiz
compiz-core
compizconfig-settings-manager
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
libcompizconfig0
libcompizconfig-backend-gconf
libdecoration0
python-compizconfig

Happy hunting!

---

### Post by ajeetraj on 2008-02-27
ok I have answered the same question before somewhere on this forum but I just can't hold of it but anyway, I will tell you one way to fix this. 

I don't know what version of ubuntu you are using, but if you are running compiz-fusion then its a common problem for the latest (recent) video cards...which are blacklisted by the distro as they are not very stable and that's why when you try to enable the desktop effects you get that error saying that "desktop effects could not be enabled". 

Well, what you have to do is to edit your compiz file which can be accessed like this from the terminal: 
```
sudo gedit /usr/bin/compiz
```

In the line 61 or 64 (or somewhere around that line) you will see which graphic cards are listed. All you have to do is just disable it by adding "#" in front of the line. Just to give you an idea...the line should look something like this:  ```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
```

Hope this helps! It has worked for me always and it has worked on every other computer i know which had the same problem. if you have further questions then just let me know! 

good luck!

ps: I am assume that you know how to install your graphic card driver...if you are using gutsy/hardy then you are already shorted.

---

