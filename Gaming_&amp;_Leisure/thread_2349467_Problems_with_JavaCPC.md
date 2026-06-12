---
title: "Problems with JavaCPC"
date: 2017-01-15
forum: Gaming &amp; Leisure
---

### Post by Preston_Thomas on 2017-01-15
When I had my Windows system (I switched to Linux a while back) I used to use an Amstrad CPC emulator called JavaCPC.

As you can tell within the name it uses Java so it should work on Ubuntu with no problems.

I have downloaded it and extracted it into a folder and made the .jar file into an executable.

When running it I go into the terminal then into the right folders and type Java -jar JavaCPC.jar and the emulator runs.

Problem I am having is that the emulator runs at around 4FPS which i know is wrong and was wondering if anything can help in getting this wonderful app to run at the proper speed.

thanks for you time

---

### Post by sgian on 2017-01-20
Hi, there are a couple things to check for slow fps with java apps.  

One is using openjdk that comes with Ubuntu instead of installing Oracle Java.  I use the instructions at [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java) but have to manually update.  Or you could use the java ppa from web upd8 so that it will update whenever the ppa maintainer sets up the update...  [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)  Either way should work.

The next thing to check is whether any proprietary drivers are available and whether they are being used.  What graphics hardware do you have?  Also mention the CPU specs and RAM.

---

