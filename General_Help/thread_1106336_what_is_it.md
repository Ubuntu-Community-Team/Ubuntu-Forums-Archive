---
title: "what is it"
date: 2009-03-25
forum: General Help
---

### Post by drdob on 2009-03-25
dear all:P could you help me with this massage::
 'W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
' 
what does it mean :confused:??  
thank you dr dob

---

### Post by scottuss on 2009-03-25
It means you don't have the key installed for that repo. Basically, your computer cannot confirm that the packages are legit and haven't been tampered with. You can probably find the key via launchpad if you want to add it.

You should still be able to install software, ignoring the message.

---

### Post by evilaim on 2009-03-25
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

This should help. you have to add a PPA key.  This link should inform you of how to do it.

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/60630](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/60630) <-- this forum solves it.

---

### Post by kanikilu on 2009-03-25
It means you are using a repository for a PPA and don't have the gpg key yet.

Open a terminal (Applications > Accessories > Terminal), try the following:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 60D11217247D1CFF
sudo apt-get update
```

---

### Post by anjilslaire on 2009-03-25
I have success with
```

gpg &#8211;keyserver keyserver.ubuntu.com &#8211;recv 60D11217247D1CFF
gpg &#8211;export &#8211;armor 60D11217247D1CFF | sudo apt-key add 
sudo apt-get update

```

---

### Post by drdob on 2009-03-26
thank you for your help :P

 i used this link:
  [http://blog.launchpad.net/ppa/adding...-key-to-ubuntu](http://blog.launchpad.net/ppa/adding...-key-to-ubuntu)

This should help. you have to add a PPA key. This link should inform you of how to do it.

[https://answers.launchpad.net/ubuntu...question/60630](https://answers.launchpad.net/ubuntu...question/60630) <-- this forum solves it.
dr dob

---

