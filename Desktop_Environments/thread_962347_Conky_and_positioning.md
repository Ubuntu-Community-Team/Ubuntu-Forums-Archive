---
title: "Conky and positioning"
date: 2008-10-29
forum: Desktop Environments
---

### Post by Belgatom on 2008-10-29
I followed this guide ([http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)) to install Conky. Initially because I wanted to have a groovy digital clock on my desktop. In my windowsdays I used to fiddle around with Samurize, so I know the possibilities. Conky goes a lot further than that so really it's a new toy. 
Now when I implemented the conky guide mentioned above, I found that the Conky Window was positioned top right on my desktop. What I wanted, was that it appeared bottom right. So, I opened .conkyrc and changed alignement from top_right to bottom_right. But it's still floating in the middle of the right side. Also, the clock (same as you can see on the screenshot) is aligned at the right because when time goes from xx:01 to xx:02 my whole window moves as 01 takes up less space than 02. How do I go about positioning everything the way I would like? Seeing all the possibilities that the software has, I was kind of suprised I couldn't find that.

---

### Post by Belgatom on 2008-10-30
Bump!

Anyone?

---

### Post by m_duck on 2008-10-30
As far as the alignment of the clock goes, where the original script says:
```

 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}
```Remove the spaces on the left of both lines, then prefix both lines with "${alignc}":
```

${alignc}${font Radio Space:size=14}${time %A %d %Y}
${alignc}${font Radio Space:size=55}${time %H:%M}
```This should then keep the clock centered within conky's width regardless of the time.

As you have said, setting "alignment" to "bottom_right" should solve your positioning problem, however if it hasn't, check for blank lines at the bottom of the .conkyrc file, as conky will see these and put them on screen, effectively, shifting your conky config upwards.

If this doesn't solve it, post your ~/.conkyrc here and I'm sure someone will be able to help...
Also, check [conky screenshot thread]("http://ubuntuforums.org/showthread.php?t=281865") for loads of conky info.

---

