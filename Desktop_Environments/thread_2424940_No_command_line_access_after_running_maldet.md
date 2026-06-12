---
title: "No command line access after running maldet"
date: 2019-08-17
forum: Desktop Environments
---

### Post by OtagoHarbour on 2019-08-17
I am using Ubuntu 18 LTS with Unity desktop. I installed, and ran, maldet (Linux Malware Detect (LMD)) on the whole disk. When I came back to check the results, the terminal window was blank. 


I got maldet (LMD) using


```
wget [http://www.rfxn.com/downloads/maldetect-current.tar.gz](http://www.rfxn.com/downloads/maldetect-current.tar.gz)

```


I tried all the settings, including making the background white and the text black, but it is still blank and still does not respond to the keyboard. Sometimes the window does not even open. It flashes and disappears. When it does open, it is always blank with no keyboard response.


I installed MATE term. It also just flashes and goes away. xterm and uterm did not even open. I installed, and launched, TMX, but it returned


```
bash: /usr/bin/sudo: Permission denied
```
every time I tried a command with sudo in it. (It did not ask for my password.)


When I tried ctrl-alt-F3, I got a terminal but, as soon as I entered my user-name and password, it flashed and went back to asking for my username again.


I had the best luck with PowerShell. It allowed me to enter


 ```
sudo apt-get install --reinstall gnome-terminal
```


I get


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm7
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 32 not     upgraded.
Need to get 160 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64     gnome-terminal amd64 3.28.2-1ubuntu1~18.04.1 [160 kB]
Fetched 160 kB in 0s (1,242 kB/s)      
(Reading database ... 231629 files and directories currently     installed.)
Preparing to unpack .../gnome-terminal_3.28.2-    1ubuntu1~18.04.1_amd64.deb ...
Unpacking gnome-terminal (3.28.2-1ubuntu1~18.04.1) over (3.28.2-    1ubuntu1~18.04.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libglib2.0-0:amd64 (2.56.4-0ubuntu0.18.04.4)     ...
Setting up gnome-terminal (3.28.2-1ubuntu1~18.04.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...

```


I cannot get the computer to go to the command/restore mode when I reboot. I try holding down the shift key but it goes straight to desktop.


Everything else appears to work fine. It is just anything to do with a terminal where I have problems. I could just use PowerShell but it seems that something is seriously wrong with my terminal functions as a result of using maldet. Also, when I click on the terminal icon, I get the non-functional gnome terminal instead of PowerShell although PowerShell shows the terminal icons in favorites. I was hoping there would be a way to fix it.


I opened PowerShell and entered


```
cat /etc/shells

```


The results were


```
/bin/sh
/bin/bash
/bin/rbash
/bin/dash

```


So it appears that /bin/sh is the default shell for PowerShell.


Neither /etc/bashrc nor ~/.bash_profile existed so I created them as outlined at [http://www.linuxfromscratch.org/blfs/view/svn/postlfs/profile.html](http://www.linuxfromscratch.org/blfs/view/svn/postlfs/profile.html)


The Gnome terminal still starts up blank.


I then tried


```
 mkdir backup
 cp ~/.bashrc backup
 cp /etc/skel/.bashrc ~

```


but the Gnome terminal still opened blank

---

