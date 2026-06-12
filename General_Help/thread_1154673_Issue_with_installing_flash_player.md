---
title: "Issue with installing flash player"
date: 2009-05-10
forum: General Help
---

### Post by c10273 on 2009-05-10
I am installing ubuntu on my mothers computer and I can't get flash player to install. It says "Error: Dependency is not satisfiable: libcurl3". I am not sure what that means. She has XP on her laptop and I would like her to use this os. Hopefully someone can give me a clue to what I am doing wrong. I am new to this os system and I am very impressed with it so far. I am so impressed that I am also talking my sister-in-law to put it on her machine. I have tried it out on three different machines and this fourth one is the only one that has I could't get flash to download. Thanks in advance!

---

### Post by alwayshere on 2009-05-10
copy paste these in terminal one at a time  after that try doin ya flash again

sudo apt-get install libcurl3

sudo apt-get install libcurl3-gnutls

---

### Post by collinp on 2009-05-10
Running "sudo apt-get install flashplugin-nonfree libcurl3" should both solve the problem with the dependency /and/ install Flash for you. Double win!

---

### Post by c10273 on 2009-05-10
Thank you so much. I think I got everything on her computer that she needs, except her address book. I had it on there and then noticed with dual boot there was not much for that partition. wiped out her entire hard-drive and installed just ubuntu. As I was doing that I lost her address book. She said it wasn't a big deal (not much on there anyway). I think she will be very happy with not having a sloooow computer and running a way easier OS. Thanks again.

---

