---
title: "Strange theme problem"
date: 2009-02-08
forum: General Help
---

### Post by O-pos on 2009-02-08
Hello,

I installed a new ubuntu theme from gnome-look.org and I have a strange problem with it: it works fine except every time I have to start an application which requires password. Let's say, If I have to start gedit in terminal, I type "gedit" and everything works fine, gedit is embedded in a nice theme. If I do "sudo gedit", then gedit is embedded in a very ugly theme (just gedit), the rest of the desktop is ok. What is the reason  and how can I extend the theme everywhere?

Thanks,

O-pos

---

### Post by overlord.gaurav on 2009-02-08
The sudo application (ie. root applications) use the root theme. If you want root theme to match your current user theme, run the following commands:
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

### Post by O-pos on 2009-02-09
Thanks, that worked well!

---

