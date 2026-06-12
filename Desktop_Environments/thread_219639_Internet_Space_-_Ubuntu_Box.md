---
title: "Internet Space - Ubuntu Box"
date: 2006-07-20
forum: Desktop Environments
---

### Post by bitoiu on 2006-07-20
Hi,

I'm in charge of some computers that provide internet to whoever likes it. It's a state program. Well the govermnent makes us use Windows but fortunatly one of the licences got lost ... that means UBUNTU :) :) :) 

I use Ubuntu for a long time at home, and my question is considering the security of the network.

I installed a fresh ubuntu and I have a user account. What should I install remove to make the box safer ou more productive in this enviroment?

Thanks!!!

---

### Post by Paerez on 2006-07-20
Well it's already nice and safe since all ports are closed by default. If you plan to open ports (if you want to make it a computer) then you should get a firewall. But you don't need a firewall for daily use.

As for productivity, ubuntu is already productive with its programs.. what do you mean?

---

### Post by bitoiu on 2006-07-20
Hi, the system is behind a fisic firewall, that manages all trafic to the building. My real question was about apps that by default could harm the other pc's in a network.

For example if dsniff was installed by default it would be bad for the other users. I'm asking if I should remove some programs that may for example track data down or access other pc's in the network.

I'm asking just to be sure, and I thank you very much for your anwser...

By the day, do you still suggest a firewall, like firestarter for example?

Thanks

---

### Post by Paerez on 2006-07-20
I would only suggest a firewall for a computer that has ports open to the WWW. Your computer is already behind a firewall and ubuntu closes all ports be default, so you are 2xOK :D

As for the applications, the only thing that I know of that will interact with the other windows boxes would be Samba. Just don't set Samba to be a WINS server (it is off be default) because that would mess up people's file sharing between their computers.

Regarding stuff like Dsniff, there aren't any of those genre of programs installed by default.

---

### Post by bitoiu on 2006-07-20
Thanks for all your help Paeres :) , I feel more relaxed now. 
Thank You Very Much!

---

