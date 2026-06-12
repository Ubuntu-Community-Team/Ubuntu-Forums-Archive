---
title: "Root Access and Eagle USB"
date: 2005-04-26
forum: Desktop Environments
---

### Post by eltower on 2005-04-26
Hey.
I recently installed Kubuntu 5.04. It was amazing at first (most of my hardware recognised at first, even my USB Xbox gamepad!), but I was quick to run into problems.

For example, I have a Comtrend CT350 USB ADSL modem, and Kubuntu does not recognise it. I cannot therefore access the web. Then, by looking around in the CD, I found the Eagle USB packages in /pool/main/e, which I knew I needed to install. Kubuntu had not done this for me though. I tried reinstalling Kubuntu in expert mode, but I could not get a menu to select packages. 

I have the eagle USB .deb packages on my desktop, and i could use dpkg to install them, but whenever i try to open a new root shell, it just closes after I put in the password, and I cannot use the install feature of dpkg without superuser privileges. I also have other problems with root access. I would like to have available athe option o login as root, as whenever I try, i get -login failed-.

Help would be appreciated.
eltower

---

### Post by Firetech on 2005-04-26
1. The password you should enter in the root terminal is _your_own_ password, and you should rather run dpkg in a normal terminal, prefixed by "sudo " ("sudo dpkg -i ...")
2. Edit the file /etc/gdm.conf (with root privilegies (spelling?)) There should be some line that says AllowRootLogin or something like that... (I don't use GDM, so I don't know the exact name. I know that the setting is there though.)
3. The root login is disabled per default. To enable it, fire up a normal terminal and type "sudo passwd" and enter a password for root. (It will first ask you for your password, then the new root password twice.)

---

