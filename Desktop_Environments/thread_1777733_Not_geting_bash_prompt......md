---
title: "Not geting bash prompt....."
date: 2011-06-08
forum: Desktop Environments
---

### Post by parag.nehete on 2011-06-08
Hi Friends,
I create one user by the following command....

#sudo useradd -d /home/parag.n -m parag.n
#sudo passwd parag.n

After creating user, when i logged in with that user, i am not able to get bash promt. When i start terminal i get only ( $ ), where generally we get ( username@localhost# ).

Please help me out from this......

Thank You,
Parag Nehete.

---

### Post by nothingspecial on 2011-06-08
Do this

```
cp /etc/skel/.bashrc /home/parag.n/ && . ~/.bashrc
```

And use adduser rather than useradd next time.

Congratulations by the way, you are the recipient of my 5000th post :popcorn:

---

### Post by parag.nehete on 2011-06-09
Hey, i run the command which you give me but it is not working. Do u have any other solution on this? And thank you so much for the information. I tried with "**useradd**" command & get prompt also. But need it for my exist user.

---

