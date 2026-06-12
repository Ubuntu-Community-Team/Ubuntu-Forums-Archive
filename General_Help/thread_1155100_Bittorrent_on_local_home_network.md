---
title: "Bittorrent on local home network?"
date: 2009-05-10
forum: General Help
---

### Post by blastus on 2009-05-10
Is it possible, with say two Gigabit network interfaces on each end, to use Bittorrent to transfer huge files between the computers at a much higher speed than a single network interface? I'm looking for something like an NFS-like server and client that can use Bittorrent.

---

### Post by danwood76 on 2009-05-10
To use two net interfaces you would need to create a network bridge but in doing so you would loose one interface due to the way TCP works.
It always finds the quickest route so would only use one cable at a time I think.

How fast do you need to transfer the files anyway?
Gigabit ethernet is faster than most hard disks read speed let alone the write speed which whill be slightly slower.

If you are looking for real speed then you should look into 10Gb ethenret :)

---

### Post by blastus on 2009-05-10
I don't really need faster speeds, but it's just a thought. You'd have to have some kind of service that controls the transfer in pieces in addition to a client that assembles the file together again. If it could work seamlessly with the file system like NFS does it would be simple to use. This could be used for wireless also to increase bandwidth.

In theory, I think this should be possible. :)

---

### Post by danwood76 on 2009-05-10
Well if you know much about how TCP/IP works then its a lot more diffucult than you think.
Although I do remember in the days of ISDN I had an ISDN2 which was effectivly 2 ISDN conenctions in parrallel down the same line, but this will have had a clever bridge at the end pulling the lines together and would work on the physical and data link layers of the TCP model whereas anything you do in software is at the top, application, layer so it makes things less easy.

(thinking aloud ;))

If you had enough time and programming experiance I'm sure you could create a proxy server which allows for a virtual IP and effectively switches data down the two lines but it would be very large and complex to work efficiently.

---

