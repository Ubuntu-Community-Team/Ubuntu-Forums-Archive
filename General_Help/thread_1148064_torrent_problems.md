---
title: "torrent problems"
date: 2009-05-04
forum: General Help
---

### Post by rogerrabbitsclone on 2009-05-04
ok so my really good fast computer has ubuntu, my old slow next to no ram computer has windows. if i download my torrent programs made for windows on my ubuntu comp and just transfer them from system to system with a flash drive, will they work?

---

### Post by _Purple_ on 2009-05-04
If you are talking about the torrent installer file, yes you can download it in your ubuntu machine and transfer it to the windows machine. That is you have to download the .exe file and then install it in windows machine after transferring it.

---

### Post by zvacet on 2009-05-04
If you think of torrent client then no.You can find good torrent clients in synaptic (Transmission,Deluge,Ktorrent...).If you think of downloaded files then yes.

---

### Post by lovinglinux on 2009-05-04
If you are talking about downloading a Windows application with the torrent client on Ubuntu and then installing the downloaded application on Windows, then yes. Ubuntu won't modify your downloaded file, so you can transfer it using a flash drive and install it on Windows.

If you are talking about the torrent client, which means the software responsible for downloading the stuff, then no. Windows programs runs on Window, not Linux. Nevertheless, you can run some applications like uTorrent using Wine. [Wine](http://www.winehq.org/) is a compatibility layer software, that allows you to install some Windows programs on Linux. Additionally, there are some torrent clients with both Windows and Linux versions. I recommend Deluge, which is easy to configure, has a nice interface and all important features.

If you are talking about continuing to download your files on the Windows machine, then yes. You need to transfer the files currently being downloaded and the .torrent files (those that control the download of each file) from one machine to the other. You must save them on the corresponding folders in the Windows machine (this is setup on the torrent client). Then you need to load the .torrent files into the client running on Windows and do a "recheck". The client will compare the data in the .torrent file with the actual data already downloaded and start the download from were you stopped.

---

### Post by rogerrabbitsclone on 2009-05-04
thats exactly what i wanted to know. 

ive tried wine with a couple programs, but it always seemed to find a way to make my computer crash. and then it made it so when i went online, going "up" on my scroll wheel made me go back a page. i dont think it could handle sony vegas.

---

