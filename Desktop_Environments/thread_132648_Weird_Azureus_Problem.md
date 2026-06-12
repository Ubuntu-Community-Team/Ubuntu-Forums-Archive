---
title: "Weird Azureus Problem"
date: 2006-02-18
forum: Desktop Environments
---

### Post by mssm on 2006-02-18
Recently I upgraded from Azureus 2.3.6 to 2.4.0 using azureus  auto-updater. After that I started having strange problem. First, the swt-gtk file could not be installed however hard I tried. Even I tried to install it by running azureus as root. Even then it didn't work. Next, I uninstalled azureus and again reinstalled its 2.3.6 version using automatix. I switched auto-updater in azureus. I still have those problems.

1. I use baghira theme in KDE. After running azureus for sometime, it makes the windows bar vanish.
2. The konsole becomes inactivated. Even if I click on it, it remains as a deactivated window.
3. The main problem is with superkaramba. I use it heavily. I never had any problem with it. But after running azureus for some time, it closes all those programs like liquid weather, sound-mania etc. one by one.

Finally I had no option left but to restart X. Moreover, azureus makes the computer and network extremely slow.

Has any one of you faced this problem?[COLOR="Red"][/COLOR]

---

### Post by Ocxic on 2006-02-18
I have the same problem with the file not getting installed, but none od the others you discribe. and it's obviouse why azureus will make your network slow, your downloading stuff and making tons of connections to other computers, this uses up your bandwidth, theres no getting around it, unless you download when your not on your comp.

---

### Post by nalmeth on 2006-02-18
I get the same error with swt-gtk, but no other performance problems

---

### Post by mandrakethepenguin on 2006-02-18
Automatix screws the installation of Azureus up.  I reccommend downloading and installing Azureus from their website manually.

---

### Post by kingsidy on 2006-02-19
i am having the same issue with swt-gtk when i upgraded from 2.3.0.6 to 2.4 does anybody know how to update it manually?

---

### Post by Perfect Storm on 2006-02-19
First uninstall the previous Azureus.
Then:

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.


```

cd /to/the/folder/where/you/saved/azureus 
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/ 
sudo chown -R root:root /opt/azureus/ 

```


For launcher:
Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png


> Finally I had no option left but to restart X. Moreover, azureus makes the computer and network extremely slow.

Azureus uses Java which why it's a power hungry hog, but I find v. 2.4.0.0 better when it comes to resources. There can be diffrent reseasons why you network gets slow, the mainly reason I can think off is when people are downloading from you (P2P you know) as you downloading stuff from them. Also check if you set your firewall to grant access for bittorrent usually port 6881

Moving the thread to KDE forum

---

### Post by noigeaR on 2006-02-19
installing the latest sun jre 1.5.0_06 might help too, as it fixes a few memory leaks over the last version (and also some security holes, so upgrading is recommended anyway). unfortunately ubuntu plf still has the old 1.5.0_05 packages, so you need to build the debs yourself. it's quite easy though. see the [ubuntu wiki]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca") for installation instructions

---

### Post by mssm on 2006-02-26
[QUOTE=Artificial Intelligence]First uninstall the previous Azureus.
Then:

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.


```

cd /to/the/folder/where/you/saved/azureus 
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/ 
sudo chown -R root:root /opt/azureus/ 

```


For launcher:
Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png




Azureus uses Java which why it's a power hungry hog, but I find v. 2.4.0.0 better when it comes to resources. There can be diffrent reseasons why you network gets slow, the mainly reason I can think off is when people are downloading from you (P2P you know) as you downloading stuff from them. Also check if you set your firewall to grant access for bittorrent usually port 6881

Moving the thread to KDE forum[/QUOTE]

Sorry for replying back so late. First, let me thank Artificial Intelligence for his post. I did exactly what he said. I waited for like a week to see any malfunction but the system is running smoothly without a hitch. Thank you evrybody for your quick response. I will not be able to upgrade azureus and actually I don't want to :). Who wants an unstable upgraded package than a stable relaible old package?

I hope this thread might help somebody facing this annoying problem.

---

