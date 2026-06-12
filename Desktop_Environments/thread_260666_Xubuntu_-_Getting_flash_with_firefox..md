---
title: "Xubuntu - Getting flash with firefox."
date: 2006-09-19
forum: Desktop Environments
---

### Post by singedwings on 2006-09-19
I have found that getting most programs working in Xubuntu is simply a case of following the instructions pertinent to Ubuntu. However I have found that this does not hold true when trying to install Macromedia Flash support for Firefox.

Here is how I was succesful:

1. Ensure that the **flashplugin-nonfree** is not installed in the synaptic package manager. You may have installed this if you have tried the Ubuntu instructions to get flash.

2. Go to [http://http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")
click the download now button and save the **install_flash_player_7_linux.tar.gz** file to your home folder.

3. Left click on the file you downloaded and extract the files to your home folder. This will create a folder called **install_flash_player_7_linux**.

4. Open a terminal and enter:

```
cd install_flash_player_7_linux/
```
```
sudo ./flashplayer-installer
```

5. Follow the on screen instructions. When asked for the path to your browser enter **/usr/lib/mozilla-firefox**.

6. When the installer has finished flash should work when you next start firefox.


Hope this helps as it is my first attempt at a guide.

---

### Post by libertyblues on 2006-10-28
Thanks a lot. I had already tried to install flash several different ways, including trying Gnash, a substitute, but to no avail.

I ended up reinstalling firefox, following your guide, and now am happily watching youtube.

Thanks again.

---

