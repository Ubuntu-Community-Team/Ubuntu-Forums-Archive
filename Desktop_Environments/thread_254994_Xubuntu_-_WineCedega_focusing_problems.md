---
title: "Xubuntu - Wine/Cedega focusing problems"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Wind_Sp00n on 2006-09-10
I'm having problems with wine/cedega focusing on my full screen games. When I load the game, I can use the mouse fine, but when I try to use the keyboard in the game for movement, It doesn't respond to the input I give it. Sometimes though If I run the game with thunar in the background, thunar is the program that gets the keyboard input instead of the game. I have tried to run Cedega in a windowed mode, and I was able to make it accept keyboard input.

I have looked into the XFCE control panel, but I have not found anything that would help in my problem, so I am rather clueless as to how I could fix this.

So any help would be appreciated. and thanks in advance.

---

### Post by Wind_Sp00n on 2006-09-16
Ok, I have found a solution (sorta)
Instead of using XFCE, Im now using wmii, and Cedega completely works, while wine doesn't work.

For example, If I use the command wine app.exe, the keyboard still focuses on the terminal instead of the application (mind you, this is only with fullscreen apps)

And a new question arises, Have you had that problem with Ubuntu? And if not, is there a way to convert my system to Ubuntu while removing XFCE?

Thanks in advance.

---

### Post by phoenix49 on 2006-09-16
sudo apt-get install ubuntu-desktop

---

### Post by Wind_Sp00n on 2006-09-18
I went ahead and tried ubuntu on vmware with wine, and found that it seems to focus correctly. an interesting thing I found though, is that when I used the sidenet config utility for wine on ubuntu, instead of going fullscreen like it used to, it took up a corner of the screen. Perhaps the sidenet configs are the cause of the problem. I deleted the .wine folder in my home directory, typed in winecfg in the terminal, and it made a new configuration. Still no luck though, I tried to run the program but the same problems still occurred.

Edit: I should also mention that installing gnome didnt do anything...

---

### Post by Wind_Sp00n on 2006-11-16
Now that 6.1 has been released, I went ahead and burnt a xubuntu cd and booted it up and tested wine on the cd, and I still have the same focusing problem. Im still curious if there has been a fix that I haven't found out yet. Before making this post, I did try searching, but I found nothing.

---

### Post by Wind_Sp00n on 2006-11-24
<_< I really feel like I shouldn't be doing this, but since I found a solution, I feel that this may be necessary 

Instead of using wine 9.22, I used wine 9.5 from wine hq, which can be acquired by...

```
wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

I pulled this from a how to guide because I believed that my wine was configured incorrectly.

[http://doc.gwos.org/index.php/HowToWine#Method_1_-_Winetools](http://doc.gwos.org/index.php/HowToWine#Method_1_-_Winetools)

I'm not sure if this is a bug of sorts due to that version of wine or whatever, but there have been some complaints about problems that I have been experiencing. I didn't think about searching for "wine keyboard," but I found some problems with steam based games that had problems like this.

well, problem solved (as far as I know)

---

