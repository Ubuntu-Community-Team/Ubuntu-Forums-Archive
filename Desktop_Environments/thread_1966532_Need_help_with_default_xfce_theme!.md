---
title: "Need help with default xfce theme!"
date: 2012-04-27
forum: Desktop Environments
---

### Post by Owl94 on 2012-04-27
I installed Xubuntu 12.04, before I had Mint 9 Xfce. I didn't format my  home partition, so my settings were preserved. The problem is that now  my Xfce desktop doesn't look like it was in  a live cd environment. The  windows and their buttons look different, while it's supposed to be  simple grey like here [http://lh5.ggpht.com/_1QSDkzYY2vc/TT1LfLyDegI/AAAAAAAACwA/4rmROCrlqrA/xubuntu-graybird-theme.png](http://lh5.ggpht.com/_1QSDkzYY2vc/TT1LfLyDegI/AAAAAAAACwA/4rmROCrlqrA/xubuntu-graybird-theme.png)
but it looks similar to this [http://www.eioba.com/files/user2571/xfce_thunar2008_1.jpg](http://www.eioba.com/files/user2571/xfce_thunar2008_1.jpg)
It also happened when i upgraded from Mint 9 to 10 with the same home  partition. I believe this is because of that. I tried changing appearance settings but none of the themes gave the result. What  files  should i delete or modify to get back the default look? Maybe I could  copy config files from a fresh xubuntu install made on Virtualbox? I  really need some help. Also it would be good to know what Lxde cofig  files are.
 Thank you.

---

### Post by c2tarun on 2012-04-27
> **Owl94 said:**
> I installed Xubuntu 12.04, before I had Mint 9 Xfce. I didn't format my home partition, so my settings were preserved. The problem is that now my Xfce desktop doesn't look like it was in a live cd environment. The windows and their buttons look different, while it's supposed to be simple grey like here [http://lh5.ggpht.com/_1QSDkzYY2vc/TT1LfLyDegI/AAAAAAAACwA/4rmROCrlqrA/xubuntu-graybird-theme.png](http://lh5.ggpht.com/_1QSDkzYY2vc/TT1LfLyDegI/AAAAAAAACwA/4rmROCrlqrA/xubuntu-graybird-theme.png)
but it looks similar to this [http://www.eioba.com/files/user2571/xfce_thunar2008_1.jpg](http://www.eioba.com/files/user2571/xfce_thunar2008_1.jpg)
It also happened when i upgraded from Mint 9 to 10 with the same home partition. I believe this is because of that. I tried changing appearance settings but none of the themes gave the result. What files should i delete or modify to get back the default look? Maybe I could copy config files from a fresh xubuntu install made on Virtualbox? I really need some help. Also it would be good to know what Lxde cofig files are.
Thank you.
 
 
Well this might be a dirty suggestion, but it always works for me. Unmount home partition and open Xubuntu. Compare your default home folder with your HOME PARTITION, try to REPLACE (not copy/merge) all hidden folders and files from your default home to your HOME PARTITION and mount again and reboot.

---

### Post by Owl94 on 2012-04-27
Yeah, thats not bad, but i don't want to replace all folders, like the ones related with firefox and other apps.

---

### Post by c2tarun on 2012-04-27
> **Owl94 said:**
> Yeah, thats not bad, but i don't want to replace all folders, like the ones related with firefox and other apps.
 
 
You can obviously omit that :) I also keep some like
.mozilla
.gnupg
.ssh
 
I also save .bashrc, .vimrc :)

---

### Post by Toz on 2012-04-27
The default Xubuntu theme is Greybird. Make sure its selected in both the Appearance and Window Manager applets. The first image that you posted looks alot like the Bluebird theme (possibly modified if its from Mint). See: [http://shimmerproject.org/project/bluebird/]("http://shimmerproject.org/project/bluebird/").

If the theme that you want is from a Mint install, you might want to boot a Mint Live CD and copy the active theme directory from /usr/share/themes and import it back into your Xubuntu install.

---

### Post by Marzata on 2012-04-28
Another suggestion is just to create a new user in Xubuntu and compare your hidden files and folders with his, then just delete what is appropriate.

---

### Post by Owl94 on 2012-04-30
Thanks for the input. I wouldn't have thought of creating a new user. I made it and it was ok, but couldn't find the right config files. I just downloaded a Graybird theme, installed and now it works :] I have just learned how to manage window buttons in window manager, also the bottom panel has an option to control opacity only in the new user account, but not in mine...it needs compositing.

---

