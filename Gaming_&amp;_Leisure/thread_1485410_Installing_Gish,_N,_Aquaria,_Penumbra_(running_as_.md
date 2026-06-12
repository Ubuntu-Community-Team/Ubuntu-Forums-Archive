---
title: "Installing: Gish, N, Aquaria, Penumbra (running as executing as program does not work"
date: 2010-05-16
forum: Gaming &amp; Leisure
---

### Post by kiddykoff on 2010-05-16
I've downloaded the Humble Indie Bundle and had things working fine in Karmic. (actually i had an issue with Gish not wanting to run from the Applications menu)

I've done a fresh install of Lucid and now for some reason when i try to run these installs they don't start. This goes for launching from Nautilus and Terminal

Did i miss something?

Just for clarification these games are.
aquaria-lnx-humble-bundle.mojo.run
darwinia-demo2-1.3.0.sh
et-linux-2.60.x86.run
gish153-1.tar.gz
lugaru-full-linux-x86-1.0c.bin
penumbra_overture_1.1.sh

I've tried running in sudo and got

```
kurtis@Turion:~$ dir
aquaria-lnx-humble-bundle.mojo.run  Downloads	      Pictures	 Ubuntu\ One
Desktop				    examples.desktop  Public	 Videos
Documents			    Music	      Templates
kurtis@Turion:~$ sudo aquaria-lnx-humble-bundle.mojo.run 
[sudo] password for kurtis: 
sudo: aquaria-lnx-humble-bundle.mojo.run: command not found
```

tldr: files not running as program

---

### Post by hikaricore on 2010-05-16
chmod +x program.sh
sudo ./program.sh

---

### Post by kiddykoff on 2010-05-16
> **hikaricore said:**
> chmod +x program.sh
sudo ./program.sh

Thanks Hikari. This worked on my penumbra program. I'm going to try this on the other files. I think i have forgotten to run with the ./

I'm trying the rest out.

---

### Post by kiddykoff on 2010-05-16
hmm.. it only seemed to work on Lugaru.I tried it on another .sh file darwinia, but that seems to give me another problem

```
Verifying archive integrity... All good.
Uncompressing Darwinia demo2 1.3.0.......................................................................
./setup.sh: 281: /home/kurtis/.setup15115: not found

```

I'm not too concerned tthough. It's only a demo and i didn't mean to list it.

---

### Post by kiddykoff on 2010-05-16
i'm going to try re downloading these at least the ones from the indie bundle.

---

### Post by ssj6akshat on 2010-05-17
I made a HOWTO

[http://ubuntuforums.org/showthread.php?t=1483236](http://ubuntuforums.org/showthread.php?t=1483236)

---

### Post by RainEverAfter on 2010-05-27
Hello, I hope you guys could help me installing Lugaru and Aquaria. I'm still trying to get use to Linux. I'm trying to install Aquaria and Lugaru on my Linux Mint 9 machine, can anyone help me?

Permission to allow the files to run as executable is ticked
Saved the files on my Downloads folder
Whenever I double-click the file, nothing happens
Downloaded the game from the website again.. and did the following steps:

 ~ $ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
 ~ $ cd Downloads
 ~/Downloads $ dir
aquaria-lnx-humble-bundle.mojo.run  lugaru-full-linux-x86-1.0c.bin
jre1.6.0_20                OxygenRefit2-green-version.tar.bz2
 ~/Downloads $ sudo aquaria-lnx-humble-bundle.mojo.run
sudo: aquaria-lnx-humble-bundle.mojo.run: command not found
 ~/Downloads $ chmod +x program.sh
chmod: cannot access `program.sh': No such file or directory
 ~/Downloads $ chmod +x aquaria-lnx-humble-bundle.mojo.run
 ~/Downloads $ sudo ./aquaria-lnx-humble-bundle.mojo.run
sudo: unable to execute ./aquaria-lnx-humble-bundle.mojo.run: No such file or directory
 ~/Downloads $ sudo lugaru-full-linux-x86-1.0c.bin
sudo: lugaru-full-linux-x86-1.0c.bin: command not found
 ~/Downloads $ chmod +x lugaru-full-linux-x86-1.0c.bin
 ~/Downloads $ sudo ./lugaru-full-linux-x86-1.0c.bin
sudo: unable to execute ./lugaru-full-linux-x86-1.0c.bin: No such file or directory
 ~/Downloads $ sudo aquaria-lnx-humble-bundle.mojo.run
sudo: aquaria-lnx-humble-bundle.mojo.run: command not found

Tried drag and drop:
 ~/Downloads $ '/home/mintyelvin/Downloads/aquaria-lnx-humble-bundle.mojo.run' 
bash: /home/mintyelvin/Downloads/aquaria-lnx-humble-bundle.mojo.run: No such file or directory

huhuhu...

---

### Post by ShadowMage on 2010-05-28
For .sh files in terminal, I believe the correct syntax should be
```
sh program.sh
```not sure if this will solve the problem or not tho.

---

### Post by kiddykoff on 2010-05-30
I totally forgot about this thread. I've actually got these games working now, but i'm sorry to say, i don't know how i did it.

I just tried running it again one day and it just worked.:confused:

---

### Post by RainEverAfter on 2010-06-04
awww.. still hasn't worked for me yet...

---

### Post by hikaricore on 2010-06-04
This is really very simple and you're likely doing something wrong.
Unless linux mint uses an entirely different bash configuration than normal it's a user error..
Please follow the instructions I posted before obviously substituting program.sh for the actual filename and it will work.

---

### Post by Kazade on 2010-06-04
If you are on 64bit: [http://kazade.livejournal.com/5358.html](http://kazade.livejournal.com/5358.html) ;)

---

### Post by RainEverAfter on 2010-06-04
Oh yeah, I'm on 64bit. Wow, it worked!!! I checked Kazade's link and ran ia32-libs package then followed hikaricore's instructions. Thank you very much guys for your patience going thru my posts!

---

