---
title: "Kubuntu Root Issues"
date: 2005-12-26
forum: Desktop Environments
---

### Post by evangelos on 2005-12-26
I've just installed the latest version of Kubuntu on my laptop and everything functions perfectly, everything except that it doesn't prompt me to set a root password, completely locking me out of the system. I've tried re-installing it several times, along with reformatting the partition it resides in several times, hoping for a clean start; however, these attempts have yet to yield administrative access.

Any ideas?

---

### Post by TudorB on 2005-12-26
You are requested to create an user with administration rights during the install. 
With this user you can execute commands as root with sudo and then typing your user password.
If you want to be able to login as root, type in a terminal
```
sudo passwd root
```
Enter your password and you will be prompted for the root password.

---

### Post by Freddy on 2005-12-26
You never login as root into your kubuntu and you will never have to login as root through a konsole either.
When using Kubuntu you will use the sudo command instead, so when doing a sytemupgrade with apt-get you will use.
```
sudo apt-get upgrade
```
instead of.
```
su
apt-get upgrade
```
If you need to browse your files in Konqueror (for example), you will have to open in with either sudo or kdesu, kdesu is better for grahpical kde apps and sudo for commands in a konsole.
When sudo asks for a password it will be the first user on that you created when installing your system.   /// Freddan

---

