---
title: "Minecraft on Ubuntu (netbook)"
date: 2013-04-18
forum: Gaming &amp; Leisure
---

### Post by carolin3 on 2013-04-18
Hello 

I have an eeepc X101CH its running on Ubuntu 12.04 LTS
It has the following specs:

Memory 991.2Mib
Processor Intel Atom CPU N2600@ 1.60GHz x 4
Graphics "unknown"
OS type 32-bit
Disk 314 GB

When I run minecraft it runs on 2-3 fps , I want it to be able to run atleast at 25 fps. I have Oracle's Java 7

//Caroline

---

### Post by myromance123 on 2013-04-18
I can't guarantee this will make a large boost, but hopefully you will see a slight increase in fps with this method.

Right now, you are using the Unity + Compiz interface correct? Instead of using that, try using the MATE interface by doing the following (it will install it for you):
```
sudo add-apt-repository “deb http://packages.mate-desktop.org/repo/ubuntu precise main” 
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update && sudo apt-get install mate-core mate-desktop-environment
```

Do these commands in a new Terminal. Type the first line and hit Enter. Do the second line and hit Enter, and so on and so forth. After it's all done, restart your system. Now on the log in screen, click the circular Ubuntu icon and you can select between the default Unity or MATE interface. Click MATE and login. Now your interface will be different, but less taxing on your system resources. Try running Minecraft, and you should hopefully see a boost in fps. I can't say how much of a boost, but I hope it'll be worthwhile.

---

### Post by carolin3 on 2013-04-18
Yes I will try that, but the repository command didn't work?

---

### Post by myromance123 on 2013-04-18
What error did it return? I installed MATE on Ubuntu 13.04 on my laptop this way and it did work. You are using Ubuntu 12.04 Precise Pangolin right? Not Ubuntu 12.10?

---

### Post by carolin3 on 2013-04-18
it said 
xxx@xxx-X101CH:~$ sudo add-apt-repository &#8220;deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main&#8221; [sudo] password for xxx: 
Error: need a repository as argument
On this computer im using 12.04 lts 32bit

---

### Post by myromance123 on 2013-04-18
```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu precise main" && sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update && sudo apt-get install mate-core mate-desktop-environment
```

Alright, try this instead. I think the quotes were wrong. Strange why it pasted something else, but this should work. Let me know if it still doesn't.

---

### Post by carolin3 on 2013-04-18
Yes thanks , now it works :)

---

### Post by Nytram on 2013-04-19
I tried running Minecraft on my netbook and also got a very poor fps. I tried it using Windows XP which I have on another partition, and I doubt that Linux will be any faster. Sorry to say it, but I doubt a netbook is capable of running Minecraft (unless there's something I'm doing very wrong...)

---

### Post by efflandt on 2013-04-19
You may be able to speed up minecraft by adjusting some options in minecraft to shift it to performance with a shorter view and disabling some effects. Or it may help to increase your RAM to 2 GB. I am not familiar with mate, but according to glmark2, gl graphics in Lubuntu are about 1/3rd faster than Ubuntu running Unity.

I can run minecraft on an Acer W500P tablet PC with AMD C-50 cpu (1 GHz 2 core) 2 GB RAM w/ATI HD 6250 video @ 1280x800 booting Ubuntu or Lubuntu (w/common /home) from SD card. Speed slows down when loading chunks, but can be 15-20 fps at times when chunk loading settles down. I normally only use that computer when out of town.

Although, I have not tried most recent minecraft version, because since just before Steam was released for Linux, I have been playing Team Fortress 2 (and bought Half-Life and Counterstrike when on sale) on my desktop PC.

---

### Post by carolin3 on 2013-04-19
ok, thx.

Is it possible to increase the RAM on a netbook? :o

---

### Post by carolin3 on 2013-04-19
Btw now when I start minecraft it just becomes a black screen after login (where the mojang intro should be) and I can't do anything :(

---

### Post by Horbo on 2013-04-22
> **carolin3 said:**
> Btw now when I start minecraft it just becomes a black screen after login (where the mojang intro should be) and I can't do anything :(

This is a Java problem.  MC doesn't like Oracle Java 7, install Oracle Java 6 and run MC with that instead.

```
[COLOR=#000000]sudo add-apt-repository ppa:webupd8team/java [/COLOR]
[COLOR=#000000]sudo apt-get update && sudo apt-get install oracle-java6-installer[/COLOR]
```

---

### Post by carolin3 on 2013-04-22
Thanks :D

---

