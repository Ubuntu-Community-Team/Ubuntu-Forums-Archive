---
title: "itouch and linux (after the crack)"
date: 2009-03-01
forum: General Help
---

### Post by linux newb on 2009-03-01
hi again, as some of you have already read i was tryin to find a way to crack my ipod touch 2nd gen. well thanks to woosyrmomma, introducing me to the cywood tethered hack, i got my itouch out of jail, wworked extremely well and i really apreciated that woosyrmomma. but i tried to follow this tutorial [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone), sure that it was going to work but when i added the repository that it told me to add which was deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main, but i substituted gutsy for intrepid because for one i tried gutsy main at first, just to see, and when it started downloading all the new packages, all of the ones from the repository failed, just to make sure ads well i searched for ipod-convenience after the download was complete, and couldnt find it. for two it made more sense that i substituted intrepid because im using kubuntu 8.10. when i used intrepid instead, the same thing, the packages from the new third party repository failed to download, and i couldnt find my ipod-convenience. tried to manually install it butim not sure i was doing it right ( was following tutorial, but im not sure i understood it properly). downloaded the ipod-convenience tar.gz file directly from the source site, and unzipped it into my /home/ron folder and not sure what to really do from there. can anybody help me out? id really like to be able to transfer my music and converted movies onto my jailbroken ipod touch 2nd gen wirelesly via mounting it as a network drive, that would be the most extremely convenient setup ever, and ive found out you can do it i just need a tutorial or something for kubuntu 8.10, or does it matter? please im really desperate to get this working.

---

### Post by JECHO on 2009-03-01
> **linux newb said:**
> hi again, as some of you have already read i was tryin to find a way to crack my ipod touch 2nd gen. well thanks to woosyrmomma, introducing me to the cywood tethered hack, i got my itouch out of jail, wworked extremely well and i really apreciated that woosyrmomma. but i tried to follow this tutorial [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone), sure that it was going to work but when i added the repository that it told me to add which was deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main, but i substituted gutsy for intrepid because for one i tried gutsy main at first, just to see, and when it started downloading all the new packages, all of the ones from the repository failed, just to make sure ads well i searched for ipod-convenience after the download was complete, and couldnt find it. for two it made more sense that i substituted intrepid because im using kubuntu 8.10. when i used intrepid instead, the same thing, the packages from the new third party repository failed to download, and i couldnt find my ipod-convenience. tried to manually install it butim not sure i was doing it right ( was following tutorial, but im not sure i understood it properly). downloaded the ipod-convenience tar.gz file directly from the source site, and unzipped it into my /home/ron folder and not sure what to really do from there. can anybody help me out? id really like to be able to transfer my music and converted movies onto my jailbroken ipod touch 2nd gen wirelesly via mounting it as a network drive, that would be the most extremely convenient setup ever, and ive found out you can do it i just need a tutorial or something for kubuntu 8.10, or does it matter? please im really desperate to get this working.



you probably have to compile it from the source... cd into the ipod convenience directory and run 

```
./configure
```

once that goes good run:

```
make
```

then run 

```
make install
```



hopefully that works for you.

---

### Post by linux newb on 2009-03-02
thanks man ill try this tonight

---

### Post by Drellir on 2009-03-17
> **linux newb said:**
> hi again, as some of you have already read i was tryin to find a way to crack my ipod touch 2nd gen. well thanks to woosyrmomma, introducing me to the cywood tethered hack, i got my itouch out of jail, wworked extremely well and i really apreciated that woosyrmomma. but i tried to follow this tutorial [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone), sure that it was going to work but when i added the repository that it told me to add which was deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main, but i substituted gutsy for intrepid because for one i tried gutsy main at first, just to see, and when it started downloading all the new packages, all of the ones from the repository failed, just to make sure ads well i searched for ipod-convenience after the download was complete, and couldnt find it. for two it made more sense that i substituted intrepid because im using kubuntu 8.10. when i used intrepid instead, the same thing, the packages from the new third party repository failed to download, and i couldnt find my ipod-convenience. tried to manually install it butim not sure i was doing it right ( was following tutorial, but im not sure i understood it properly). downloaded the ipod-convenience tar.gz file directly from the source site, and unzipped it into my /home/ron folder and not sure what to really do from there. can anybody help me out? id really like to be able to transfer my music and converted movies onto my jailbroken ipod touch 2nd gen wirelesly via mounting it as a network drive, that would be the most extremely convenient setup ever, and ive found out you can do it i just need a tutorial or something for kubuntu 8.10, or does it matter? please im really desperate to get this working.

Hi where would I read your first thread? I'm interested in cracking my Ipod Classic.

Drellir

---

