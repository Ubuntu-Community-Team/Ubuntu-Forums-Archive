---
title: "ubuntu hardware issues?"
date: 2005-05-20
forum: Desktop Environments
---

### Post by newsman on 2005-05-20
The ubuntu installation went great,,, 


ran into a pickle for a tiny bit when grub refused to install cos i didn't want it in mbr and couldn't make out the correct drive ref for root partition

which i thought later was pretty odd that i had to specify for grub but when i selected lilo instead it remembered the boot partition (and i didn't have to input it manually just select the option to install it in boot partition)...

never mind...

When it first loaded up it seams like pretty sound distro except it has genome... and i rather just stick with it for now

i wanted to install speedtouch and also nvidia 6600 drivers.

now i searched through some threads previously and found there is good info on speedtouch,,, however the threads i read about nvidia point to some crashing problems

i still want a stable system.. so what is the opinion of experienced users and their nvidia graphics hardware.. what should i proceed with and is it stable enough to proceed bearing in mind that stability is my ultimate criteria..

---

### Post by nad on 2005-05-20
Use debian woody. This distro is based on debian testing with some unstable and experimental. We are all guinea pigs.

If you insist on using ubuntu, stick with the nv graphics driver. The closed source driver has additional features and capabilities, however, it will not run across kernels and an automatic kernel upgrade is a heart in throat experience.

---

### Post by newsman on 2005-05-20
I am a linux newbie.. don't feel comfortable with debian just yet

where can i read up about automatic kernel upgrade?

the reason i chose ubuntu is because you can select the language before you login... and i have an interest in learning other languages..... but before i try add languages and start using ubuntu as it should be and as alternative to windows i wanna make sure all the hardware issues are resolved.

---

### Post by poofyhairguy on 2005-05-20
[QUOTE=nad]Use debian woody. This distro is based on debian testing with some unstable and experimental. We are all guinea pigs.

If you insist on using ubuntu, stick with the nv graphics driver. The closed source driver has additional features and capabilities, however, it will not run across kernels and an automatic kernel upgrade is a heart in throat experience.[/QUOTE]


nad is trolling pretty hardcore, please don't get scared off. Ubuntu puts out a stable product based on Sid (unstable Debian- not Sarge or testing) that is stablized by months of hard work. If Ubuntu is any sort of "guinea pig," its for people that with use Etch (the release after Sarge) AFTER Sarge is released. For example, Debian will get Xorg because Ubuntu hammered it out. But at that level, ANY CUTTING EDGE DISTRO is a "guinea pig" so if you want a modern desktop OS don't worry about it.

Also please don't think that the Nvidia driver is unstable. I USE IT EVERYDAY and it only gets unstable if I run unstable programs (such as compositing) that most users won't use (because they aren't installed by default). If you follow the Ubuntuguide, the only problems you should have with the Nvidia drivers is if you want to hibernate on your laptop (that won't work). Otherwise its pretty stable for many people.

Sorry I moved this thread, but the original forum is for Linux beginners and anyone that knows what lilo is is not one of those. Take it as a complement,. the community loves when new knowledgable users come around!!!

---

### Post by newsman on 2005-05-21
thanks... i will take that as a complement...

---

