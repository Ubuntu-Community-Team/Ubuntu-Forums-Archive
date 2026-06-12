---
title: "KDE Plasma Install"
date: 2018-03-31
forum: Desktop Environments
---

### Post by Mel_Blakey on 2018-03-31
I tried to install KDE Plasma using:
```
sudo add-apt-repository ppa:kubuntu-ppa/backports

sudo apt update

sudo apt install kubuntu-desktop
```

At the end of the installation I got the following error in terminal:
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Plasma is not available at the login screen :sad: So, I ran:
```
sudo apt update
```
again.
But, it has not worked.

I've done a search on here and tried the fix in this post [https://ubuntuforums.org/showthread.php?t=2374270&highlight=KDE+Plasma+Install](https://ubuntuforums.org/showthread.php?t=2374270&highlight=KDE+Plasma+Install) . It returned this error:
```
mel@mel-Lenovo-ideapad-100-15IBY:~$ sudo dpkg -r account-plugin-google
[sudo] password for mel: 
dpkg: dependency problems prevent removal of account-plugin-google:
 unity-scope-gdrive depends on account-plugin-google.

dpkg: error processing package account-plugin-google (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 account-plugin-google
```

Has anyone got any thoughts?
I have been getting system error warnings (pop-ups) for several months now. Maybe this is connected.
Either way I'm not averse to wiping my Ubuntu install and starting afresh with Kubuntu. As long as I can retain my data!

TIA

---

### Post by sudodus on 2018-03-31
What is (was) your original operating system, into which you try to install KDE Plasma? Which version of Ubuntu?

Maybe the following link can help you,

[Installing KDE on Ubuntu ...](https://askubuntu.com/questions/1020222/installing-kde-on-ubuntu-fails-to-fetch-files-because-of-versions-mismatches/1020381#1020381)

Please scroll down and read about the alternatives too (at the end of the answer).

---

### Post by Mel_Blakey on 2018-03-31
Hi
Thanks for the reply.

I'm running: Ubuntu 16.04 (64bit)

I have just tried to run sudo apt update and it returned this:
```
mel@mel-Lenovo-ideapad-100-15IBY:~$ sudo apt update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:3 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:5 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease         
Hit:6 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease     
Hit:7 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu xenial InRelease     
Hit:8 http://ppa.launchpad.net/claydoh/kmymoney2-kde4/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Hit:10 http://ppa.launchpad.net/kubuntu-ppa/backports-landing/ubuntu xenial InRelease
Hit:11 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu xenial InRelease
Ign:12 http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu xenial InRelease 
Hit:13 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease
Ign:15 http://ppa.launchpad.net/varlesh-l/indicator-kdeconnect/ubuntu xenial InRelease
Hit:16 http://ppa.launchpad.net/vikoadi/ppa/ubuntu xenial InRelease           
Hit:17 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease
Err:18 http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu xenial Release     
  404  Not Found
Get:14 http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu xenial InRelease [23.8 kB]
Err:19 http://ppa.launchpad.net/varlesh-l/indicator-kdeconnect/ubuntu xenial Release
  403  Forbidden
Err:14 http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu xenial InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
Reading package lists... Done 
E: The repository 'http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/varlesh-l/indicator-kdeconnect/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
E: The repository 'http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Additional Info:
Whilst I **can't** switch to Plasma after logging out, the system now shows the Kubuntu Logo at startup and shutdown.
If I type KDE into the dash, it shows 10 Plasma specific apps. ie 'KDE Partition Manager, Kate, KDE System settings, KWalletManager and I can open these up into Ubuntu Desktop!

If is a major issue, I can wipe the Ubuntu partition and install Kubuntu instead. It just seemed so easy when I read about adding another (Plasma) desktop and thought that it would tide me over until the new LTS comes out in April.

Thanks for your help!

---

### Post by sudodus on 2018-04-01
Installing a fresh operating system (or two) is probably the easiest and fastest way to get what you want. So I suggest that you install Kubuntu starting from an iso file, or if you wish, a dual boot system with two operating systems alongside each other, standard Ubuntu and Kubuntu.

---

### Post by Mel_Blakey on 2018-04-02
> **sudodus said:**
> Installing a fresh operating system (or two) is probably the easiest and fastest way to get what you want. [COLOR=#000080]**So I suggest that you install Kubuntu starting from an iso file**[/COLOR], or if you wish, a dual boot system with two operating systems alongside each other, standard Ubuntu and Kubuntu.

That's exactly what I'm going to do.

Thanks!

---

