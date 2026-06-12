---
title: "gnome trouble with aqua themes"
date: 2007-01-21
forum: Desktop Environments
---

### Post by dennis1200 on 2007-01-21
I have some aqua themes installed, specifically this one (among others) [here]("http://gnome-look.org/content/show.php?content=28686"). The problem is, scrollbars and buttons don't get skinned (though it certainly seems that other users are meeting with success. I just did a new install of Edgy, up from Dapper, and am very happy with the shift. The scrollbar/button problem is with all of the mac-aqua themes, so I suspect something amiss with my GUI (though mac-theme extensions for firefox and thunderbird work right). Any ideas?

---

### Post by aysiu on 2007-01-21
You don't happen to also have KDE installed, do you? Sometimes KDE messes with the Aqua Gnome themes.

---

### Post by jem7v on 2007-01-21
Make sure you have gtk2-engines-pixbuf installed. I think it was standard in a 6.06 install, but it doesn't seem to be in 6.10.

---

### Post by dennis1200 on 2007-01-22
the gtk2 pixbuf engine did the trick - thanks a bunch! everything looks ultra aqua, except for synaptic, which looks like the older grey block interfaces you see on earlier mozilla-based stuff (and plenty of other places, I'm sure). I prefer command-line aptitude anyways (but if you know what that problem might be, let me know).

---

### Post by mcduck on 2007-01-22
> **dennis1200 said:**
> the gtk2 pixbuf engine did the trick - thanks a bunch! everything looks ultra aqua, except for synaptic, which looks like the older grey block interfaces you see on earlier mozilla-based stuff (and plenty of other places, I'm sure). I prefer command-line aptitude anyways (but if you know what that problem might be, let me know).

That's because admin applications use root's themes and settings, not your normal user's. But there's a simple way to make root always have same theme that you are using (replace <username> with your own):

```
sudo ln -s /home/<username>/.themes /root/.themes
sudo ln -s /home/<username>/.icons /root/.icons
```

---

### Post by dennis1200 on 2007-01-22
great! now everything looks nice and together. gonna try out gdesklets as the next (and final) step.

---

### Post by jem7v on 2007-01-22
Cool trick, mcduck! I didn't know that!

---

