---
title: "Lucida fonts"
date: 2009-06-03
forum: General Help
---

### Post by amirage on 2009-06-03
Dear all

I have installed Jaunty in my Dell laptop. Initially, I could not see any wordpress articles as firefox did not display the fonts properly. Then, I realised that I needed to install mac fonts into the fonts trutype folder. I did that, yet no respite. In the fonts tab under Appearance, Lucida and other mac fonts are previewed as squares.

Can someone explain to me why this is the case and how can I resolve this?

Awaiting your comments.

---

### Post by utnubuuser on 2009-06-03
have you googled: msttcorefonts ubuntu?

When you install new fonts you have to refresh the font cache> $sudo fc-cache -fv though I really couldn't say if that's the prob in your case.

---

### Post by amirage on 2009-06-03
Hey thx for the info. I did do all the steps u've mentioned. Still the same...

Pls help

---

### Post by Legace on 2009-06-03
1) Download the font from: [http://www.tcmagazine.info/forums/index.php?showtopic=175](http://www.tcmagazine.info/forums/index.php?showtopic=175)

2) Unzip

3) Open Terminal and type in the following:
```
gksudo nautilus /usr/share/fonts
```

4) Copy the fonts you downloaded into the new window that opened after you entered that code above. Now restart, and it should look better.

---

### Post by amirage on 2009-06-03
Hi 

I tried doing what you suggested before I made this post. It's still the same.

Thanks for the help. Any other suggestions. It's just that I can't sit through another reinstallation of 9.04

Pls help

---

