---
title: "I hate having my window buttons on the left, how can i put them back on the right cor"
date: 2010-12-04
forum: Desktop Environments
---

### Post by malarie on 2010-12-04
How can we fix this?

I am using Ubuntu Lucid, and maverick in a couple of minutes, once the upgrade is completed.

Thanks.

---

### Post by 3Miro on 2010-12-04
The technically correct way is to go to System -> Prefs -> Appearance and choose a theme with buttons on the right (like Clearlooks for example). 

You can also customize the theme to pick different window decorations, you can install additional themes from the Software Center or Synaptic Package manager as well as gtk-engine-something packages. You can also find themes at [http://gnome-look.org/](http://gnome-look.org/)

If you want to use the default theme with buttons on the right, open Apps -> Accessories -> Terminal and type:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by akand074 on 2010-12-04
What I did back in Lucid was exactly what the poster above said. But an alternative is to download [Ubuntu-Tweak]("http://ubuntu-tweak.com/"). Under window manager settings you could always switch it back and forth easily.

---

### Post by malarie on 2010-12-04
Thanks guys.

---

### Post by AlanR8 on 2010-12-04
I run the theme Mac4Lin out of choice. So I have the buttons on the left.

NO PROBLEMS.

Where I find problems is when I have to work on the corporate XP machines.

Nothing's logical....

---

### Post by bvc on 2010-12-04
[http://www.google.com/search?q=ubuntu+move+metacity+buttuns&hl=en&num=10&lr=&ft=i&cr=&safe=images](http://www.google.com/search?q=ubuntu+move+metacity+buttuns&hl=en&num=10&lr=&ft=i&cr=&safe=images)

[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

[http://www.netmoose.org/linux/move-ubuntu-10-04-metacity-buttons/](http://www.netmoose.org/linux/move-ubuntu-10-04-metacity-buttons/)

---

### Post by madjr on 2010-12-04
is better not to "hate" on the buttons on the left and start getting used to them slowly, since it might be necessary for 11.04

---

### Post by bvc on 2010-12-04
necessary? What makes you think it will ever be necessary?

---

### Post by madjr on 2010-12-05
unity

---

### Post by 3Miro on 2010-12-05
> **madjr said:**
> unity

I got the 11.04 alpha and it used the same Compiz/Metacity themes. You can get Clearlooks easily. You don't have to get used to the buttons on either side.

---

### Post by arjunlalb on 2010-12-05
right click on desktop,select background,go to themes tab,click on customize,rearrange the controls...

---

