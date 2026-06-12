---
title: "Nessus Install"
date: 2008-12-30
forum: General Help
---

### Post by danuk88 on 2008-12-30
I am using ubuntu 8.10, can someone please tell me how to install and run nessus?

Thank you

Dan

---

### Post by sPiN1 on 2008-12-30
first install the ia32-libs by typing this in the terminal: apt-get install ia32-libs
download the 32 bit library libssl0.9.7 from Debian repository
install the library with: dpkg -i --force-architecture
install Nessus with same command: dpkg -i -force-architecture

---

### Post by eder.apt-get on 2008-12-30
Download the file nessus-installer.sh from here: [http://www.nessus.org/posix.html]("http://www.nessus.org/posix.html")
Then, as root, I mean sudo :), do ```
./nessus-installer.sh
```
I think that will do it.

---

### Post by eder.apt-get on 2008-12-30
Or
Open a terminal window and type in:
sudo apt-get install nessus
sudo apt-get install nessusd
sudo nessus-adduser
sudo ln -fs /etc/init.d/nessusd /etc/rc2.d/S20nessusd
sudo /etc/init.d/nessusd start
sudo gedit /usr/share/applications/Nessus.desktop

Insert the following lines into the new file

[Desktop Entry]
Name=Nessus
Comment=Nessus
Exec=nessus
Icon=/usr/share/pixmaps/nessus.xpm
Terminal=false
Type=Application
Categories=Application;System;

After that you can find Nessus in the Gnome menu under Applications -> System Tools.

(Make sure we have multiverse and universe repositories in your source.lst)

---

### Post by danuk88 on 2008-12-30
Thank you, eder.apt-get

I have now got Nessus installed and running.

do I need to update the plugins are is this done automatic?

Thank you

Dan

---

### Post by cariboo on 2008-12-30
There is a mini-nessus and ntop howto [here]("http://ubuntuforums.org/showthread.php?t=207072").

Jim

---

### Post by danuk88 on 2008-12-30
I have got Nessus installed and running, but do I need to update the plugins?

Thanks

---

### Post by danuk88 on 2008-12-31
Ok,

So I have got nessus installed and running, But how can I up date the pluging's? 

If I run the command nessus-fetch --register XXXXXXXXXXXXXXXXXXXX

that all goses ok but when I run,, nessus-update-plugins when I restart my pc it hangs on boot.....

Any ideas??

Cheers

Dan

---

