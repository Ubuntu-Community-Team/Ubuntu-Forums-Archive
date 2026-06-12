---
title: "unable to open MP3 files"
date: 2005-05-06
forum: Desktop Environments
---

### Post by ashokmani on 2005-05-06
Hi,
Please guide to play a mp3 file. i am a newbie.
Whenever i open a mp3 file, ubuntu says "unable to open the file". do i have install some mp3 players or multimedia codecs to recognize mp3 ?

I also need help in installing new packages. kindly help.

Thanks

---

### Post by bored2k on 2005-05-06
Yes you need codecs.
Warty: [http://ubuntuguide.org/4.10/index.html#codecs](http://ubuntuguide.org/4.10/index.html#codecs)
Hoary: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

**If** you have Hoary, suggest you solve **all** your problems by typing this inside a terminal window:
```
wget http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh && sudo sh ubuntusetup.sh
``` [http://ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script](http://ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script) For more info)

---
Installing packages (for GNOME -- KDE users use Kynaptic)
1) Ubuntu panel (for GNOME) > System > Administration > Synaptic > Search > right click > Install > Apply > Ok


2) .deb
```
sudo dpkg -i filename.deb
```

3) .rpm
```
sudo alien -d filename.rpm && sudo dpkg -i newfilename.deb
```

4) .tgz
```
tar xzf filename .tgz
``` Then read the README or INSTALL file.

5) .bz2
```
tar xjf filename.bz2
``` Then do the same as above

---

### Post by ashokmani on 2005-05-06
bored2k, i am using warty.
i dont have my internet setup in linux. I am not too sure if the changes suggest in the link to install codecs will work, as that would require internet access.

wat i can do is, download the packages from the site using windows and transfer to linux partition using a CD. 

can u give me the exact path for the codec download.
and the steps to install it.

i am sorry for such basic questions. kindly bare with me. i am new to linux.

thanks

---

### Post by ashokmani on 2005-05-06
i found these files for gstreamer in the internet :

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/)
gstreamer0.8-plugins_0.8.5-1ubuntu3_i386.deb 

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins/)
gstreamer-alsa_0.6.4-5_i386.deb 

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-player/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-player/)
gstreamer-player_0.6.0-1_i386.deb 

but unable to find a file for w32codecs.

kindly help me.

---

