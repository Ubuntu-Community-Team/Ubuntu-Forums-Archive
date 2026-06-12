---
title: "Java &amp; Nes Online Emulators"
date: 2011-04-08
forum: Gaming &amp; Leisure
---

### Post by inukaze on 2011-04-08
Hi there , thanks for all before nothing.

Well , i try to use 2 Sites , to Emulate "N.e.s" , Online , using some pages , is very common , see sites try to load 

1 - vNES.jar
2 - NESCafe

But i never cant play under ubuntu in versions superior of 8.04 UBuntu Hardy , the Applets dont load , never ever . well i try , by diferents ways , but nothings happened with this 2 Sites

1 - [http://www.virtualnes.com/list/index.html](http://www.virtualnes.com/list/index.html)
2 - [http://www.nescafeplay.com/play/](http://www.nescafeplay.com/play/)

Under Another Distros , i can use this sites , distros like

1 - ArchLinux , 2 - Debian 6.0 Squeeze Stable , 3 - OpenSUSE 11.4 , 4 - Slacware 13.1 , 5 - etc

But Under UBUNTU this DONT WORK , i try first using the Debian Method

Steps : 

1 - Open Synaptic and uninstall : default-jre , default-jdk , openjdk-jdk , openjdk-jre , icedtea6-plugin

2 - Now Select the follow packages for install : "sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-plugin"

3 - Click "Apply" and wait the installation

And now try , much people , say me , that fix that , with sites similars , but dont work for me.

I try follow this steps : 

1 - [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
2 - [http://www.guia-ubuntu.org/index.php?title=Java](http://www.guia-ubuntu.org/index.php?title=Java)

I Try with the "Repositories" , and manual methos , but nothings works for me, someone have an idea how i can fix this ???

---

### Post by Philsoki on 2011-04-09
What do you get from:
```
java -version
```Also, it wouldn't hurt to run the following:
```
sudo apt-get upgrade
``````
sudo apt-get autoremove
``````
sudo apt-get autoclean
```

---

### Post by Dread Knight on 2011-04-12
I have the same damn problem.

Really wanted to play some classic games like Battletoads or Rush'n'Attack... [http://nintendo8.com/game/669/rush'n_attack/](http://nintendo8.com/game/669/rush'n_attack/)

Bummer :(

---

### Post by Dread Knight on 2011-04-12
> dread@Freezing-Moon:~$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)


Using Chromium daily build from a ppa; Ubuntu Natty 64.

---

### Post by inukaze on 2011-07-20
Im actully under "Lubuntu Natty 11.04 AMD64"

inukaze@Inukaze:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

inukaze@Inukaze:~$ sudo apt-get upgrade && sudo apt-get autoremove && sudo apt-get clean

And i use "gtk-Orphan" for a Good Clean of System.

The Error its still Present.

I has use this version too much , i think this its the worse version of Ubuntu .

Boot Quickly , but its too slowpoke , consume too much Ram ( 768 MB ) & 2 Processors 95 % of Dual Core , AMD Athlon of 3.13 Ghz . with LXDE

When i can make a Backup , i go to "Porteus" ( Fork of Slackware 13.37 ) to have a Real Working Linux :=) , or i Back to ArchLinux.

I hate so much this Version of Ubuntu
I think the best version of Ubuntu its Ubuntu Hardy

---

### Post by John-B on 2011-07-20
inukaze, I just gave a try to the Lemmings game at NESCafe and with Ubuntu 11.04, firefox 5 and jre1.6.0_26 and the game works fine...

---

