---
title: "How to install Brave browser"
date: 2020-05-03
forum: Desktop Environments
---

### Post by geovino on 2020-05-03
I've tried to install Brave Browser, but for some reason it won't install. Here's what I've ran...

```
davek@op780:~$ curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
[sudo] password for davek: 
OK
davek@op780:~$ sudo sh -c 'echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com `lsb_release -sc` main" >> /etc/apt/sources.list.d/brave.list'
davek@op780:~$ sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release         
Get:3 https://brave-browser-apt-release.s3.brave.com focal InRelease [2,820 B]
Hit:4 http://us.archive.ubuntu.com/ubuntu focal InRelease          
Hit:5 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:7 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease
Err:3 https://brave-browser-apt-release.s3.brave.com focal InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FE13824E3FFC656
Hit:8 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
W: GPG error: https://brave-browser-apt-release.s3.brave.com focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FE13824E3FFC656
E: The repository 'https://brave-browser-apt-release.s3.brave.com focal InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/brave.list:1 and /etc/apt/sources.list.d/brave.list:2
davek@op780:~$ sudo apt-get install brave-browser brave-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brave-browser
E: Unable to locate package brave-keyring
davek@op780:~$ 

```

How do I correct this?

Running Kubuntu 20.04

---

### Post by geovino on 2020-05-03
I've decided to used snap instead. It's installed now. 

[solved]

---

### Post by Frogs Hair on 2020-05-03
Try the following.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4FE13824E3FFC656
```
```
sudo apt update
```

---

