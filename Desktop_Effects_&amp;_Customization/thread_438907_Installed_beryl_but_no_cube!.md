---
title: "Installed beryl but no cube!"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by srt5 on 2007-05-10
I successfully installed Beryl on my Acer Aspire 5050 by following a tutorial posted on an external blog [here]("http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html"). It works really well, and I am able to use beryl-manager in order to use all of the effects. At the moment it looks very pretty.

However I don't seem to be able to get the cube to show up. The keyboard shortcut is set to <Control><Alt>Next  (which I presume is <Control><Alt>RightKey) but when I press this combination, nothing happens, the cube doesn't unfold.

Does anyone have any suggestions as to why I can't see the cube? I've read somewhere that some cards only support 2D acceleration with Beryl, could this be the case?

---

### Post by shadowboxer_k on 2007-05-10
maybe you could try this in terminal:

```
gconftool-2 &#8211;type int &#8211;set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 &#8211;type int &#8211;set /apps/compiz/general/screen0/options/number_of_desktops 1
```

oops, that's for compiz. sorry, i will look around for a solution for beryl.

---

### Post by srt5 on 2007-05-10
thanks for the reply :) any information that you can provide regarding this problem with beryl will be much appreciated. It's just a bit weird since all of the other effects seem to work fine.

---

### Post by flayofish on 2007-05-10
I have the effects and cube selected.  Effects work great, but no Cube.

---

### Post by kjelle392 on 2007-05-10
I have the same problem.

---

### Post by Hewure on 2007-05-10
Do you have a Mouse? Press the Scroll button down, move the Mouse & see if that works.

---

### Post by EXCiD3 on 2007-05-10
Hold Ctrl-Alt and then Click Mouse Button 1. This will zoom out of the current desktop and give you the cube. Move the mouse to change the camera view.

---

### Post by srt5 on 2007-05-10
Thanks for all of the replies guys. I'm somewhat glad to see that I'm not the only one who has this problem. I have tried all of the suggestions about using the mouse shortcuts, but unfortunately, still no joy - the cube does not display even though I have turned the setting on in beryl-manager.

I've done a bit of reading around and this is what I've found. Typing the following into a terminal

```
lspci | grep VGA
```

gives me this output > 01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

Reading [this page]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") under heading number 2, it suggests that for ATI cards which fall under the Xpress 200M category, Beryl will only be able to provide 2D acceleration. This is my best guess as to why other users and I are not able to see the 3D cube.

Would this explain the problem that we are experiencing?

---

### Post by kjelle392 on 2007-05-10
I think I have solved the problem! 

Check how many "viewports"/desktops you have. I had only one, and therefore no cube...

To change the number of "viewports" in beryl, go to beryl manager General Options --> General Options --> Main --> Horizontal Virtual Size and change it to what you want, the default is 4, which gives you a cube.

---

### Post by srt5 on 2007-05-10
> **kjelle392 said:**
> I think I have solved the problem! 

Check how many "viewports"/desktops you have. I had only one, and therefore no cube...

To change the number of "viewports" in beryl, go to beryl manager General Options --> General Options --> Main --> Horizontal Virtual Size and change it to what you want, the default is 4, which gives you a cube.

It worked! Thank you so much! I had already been through those settings and set the number of desktops to 4, but I missed that one!

Thanks again! I am one very happy Ubuntuer :)

---

### Post by epitaph123 on 2007-12-28
Hi, I saw your post on installing beryl successfully on acer aspire 5050, can you fix the broken link to your walk through?

---

