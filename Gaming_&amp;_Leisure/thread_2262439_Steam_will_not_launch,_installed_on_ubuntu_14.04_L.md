---
title: "Steam will not launch, installed on ubuntu 14.04 LTS"
date: 2015-01-24
forum: Gaming &amp; Leisure
---

### Post by Mike_Lavender on 2015-01-24
I just installed Ubuntu 14.04 LTS on a machine I just built. I went to the software center and Downloaded Steam from there. The launcher appeared in the left hand app bar and another blue steam icon is in the dashboard. The launcher does nothing but flash. I can right click the blue steam icon and I get the Library, Community, Servers etc.. if I click on one, I get the little circle with the spinning stuff in it like it is trying to open but it does nothing. If I right click on the steam icon in the dashboard the dropdown menu says "Installed on: None". AT the bottom there are two buttons, Uninstall and Launch. launch does nothing.
I have uninstalled steam and reinstalled it from the Steam site as well, the result is the same. The only thing ihave done is enabled the canonical repository. It didn't work when it was disabled either. 

Any help is appreciated, thanks.

Mike

---

### Post by efflandt on 2015-01-27
What video card/chip and video drivers are you using? Do you get the login popup and actually login before seeing the Library, Community, etc. and does anything initially come up underneath that (usually the default is the Store with games).

Did you try launching **steam** from a terminal window to see if you get any meaningful error messages? Some can be ignored, like about a proxy if not using a proxy.

---

### Post by oldrocker99 on 2015-01-27
You might have better results if you go to [http://steampowered.com](http://steampowered.com) and select "Install Steam." You'll get a link from which you can download a file called **steam_latest.deb**. Install this with gdebi, or The Ubuntu Software Center, or (preferred) open a terminal and enter
```
sudo dpkg -i steam_latest.deb
```

If you get an error message (which is likely), enter
```
sudo apt-get -f install
```
This will install any uninstalled dependencies that Steam needs.

This is how I install Steam on a new installation of a distro, and it works fine for me. **Many** users have had problems installing Steam from the Software Center; you are not alone. If you continue to have problems, please post here.

---

