---
title: "Ubuntu 9.10 Java has not been found?"
date: 2010-02-24
forum: Desktop Environments
---

### Post by thehourman on 2010-02-24
Hey guys,
I am still new to Ubuntu, and want to learn more.
So far I am enjoying it, but my problem is I can't use my application which is .exe.
I installed wine and Java and when I right clicked on the .exe app and chose Wine, I got an error saying "Java has not been found on your computer. Do you want to download it?"
I opened the terminal and typed in Java -version and what I got is:
version "1.6.0_0"
Open Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)

I don't really know what to do now. any help would be appreciated.

Thanks

---

### Post by mthalis on 2010-02-24
Refer this, it shows how to configure Java in Ubuntu [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by thehourman on 2010-02-24
> **mthalis said:**
> Refer this, it shows how to configure Java in Ubuntu [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
I have tried it, but no luck. It keep saying no Java.

---

### Post by NefariousNobo on 2010-02-25
Yes... So if I'm reading this right, it's PE32 Windows Executable (*.exe) that requires Java? If I am correct, continue.

The issue is probably that the Wine Emulation used on the EXE doesn't have a JVM. The Linux system having a JVM is irrelevant, as Wine does not use the Linux system's JVM, it uses the Windows one (if it's installed). First thing I would recommend is that you go to the developer's web site and see if they offer a native Linux version (if it's written in Java, you'd think they'd have a Linux version). If they don't, then I recommend you download the Windows version of Java and install it with Wine.

Hope this helps...

---

### Post by thehourman on 2010-02-25
> **NefariousNobo said:**
> Yes... So if I'm reading this right, it's PE32 Windows Executable (*.exe) that requires Java? If I am correct, continue.

The issue is probably that the Wine Emulation used on the EXE doesn't have a JVM. The Linux system having a JVM is irrelevant, as Wine does not use the Linux system's JVM, it uses the Windows one (if it's installed). First thing I would recommend is that you go to the developer's web site and see if they offer a native Linux version (if it's written in Java, you'd think they'd have a Linux version). If they don't, then I recommend you download the Windows version of Java and install it with Wine.

Hope this helps...
How am I going to install it?
I would assume that this is the Windows version of Wine [http://www.pbidir.com/bt/pbi/11](http://www.pbidir.com/bt/pbi/11)
I have no idea how to install it. Also, there are two Wines, which are v7.x and v8.x, I don't know which one download.

I have Ubuntu 9.10 32bit on my Asus 1005HA netbook.
The Wine That I have is from the terminal "sudo apt-get wine", and the wine from Ubuntu Software Center did not work either.

---

### Post by Kakers on 2010-02-25
The problem you have is Wine is an emulator, like a mini OS add on inside your Ubuntu, so it will only use what is installed through wine and will not use the Java installed on Ubuntu.

So you need to install Windows Java on Wine to be able to run it, you can find the windows java from here:
[http://javadl.sun.com/webapps/download/AutoDL?BundleId=37717](http://javadl.sun.com/webapps/download/AutoDL?BundleId=37717)

Download that and then run the .exe. through wine.

---

### Post by Hero of Time on 2010-02-25
> **Kakers said:**
> The problem you have is Wine is an emulator, like a mini OS add on inside your Ubuntu, so it will only use what is installed through wine and will not use the Java installed on Ubuntu.

So you need to install Windows Java on Wine to be able to run it, you can find the windows java from here:
[http://javadl.sun.com/webapps/download/AutoDL?BundleId=37717](http://javadl.sun.com/webapps/download/AutoDL?BundleId=37717)

Download that and then run the .exe. through wine.

Wine stands for Wine Is Not an Emulator, so calling Wine an emulator wrong. It doesn't 'emulate' anything, it's a wrapper for API calls. It translates the MS calls from programs to that of Linux.

As for Java in Wine, keep in mind that it might not work at all. Best thing you can do is ask the dev to make a Linux build. It's all Java, it's cross platform and should not be any different to run on Linux as it is on Windows. Heck, it should even run on Mac OS and whatever system you have that has Java VM available.
According to [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1372](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1372), Java Runtime Environment should work in Wine, so your program should work. It might be very slow though.

---

### Post by Kakers on 2010-02-25
I stand corrected :P

---

### Post by thehourman on 2010-02-25
> **Kakers said:**
> The problem you have is Wine is an emulator, like a mini OS add on inside your Ubuntu, so it will only use what is installed through wine and will not use the Java installed on Ubuntu.

So you need to install Windows Java on Wine to be able to run it, you can find the windows java from here:
[http://javadl.sun.com/webapps/download/AutoDL?BundleId=37717](http://javadl.sun.com/webapps/download/AutoDL?BundleId=37717)

Download that and then run the .exe. through wine.
How do I install that Java into Wine?
Can you guide me to the command prompt if there 's a command for it?

---

### Post by Hero of Time on 2010-02-26
> **thehourman said:**
> How do I install that Java into Wine?
Can you guide me to the command prompt if there 's a command for it?

Read my reply and the link to the Wine AppDB. It's described there. What's so hard to download the JRE from java.sun.com, start the installer in wine and follow the onscreen directions?

---

### Post by thehourman on 2010-02-26
> **Hero of Time said:**
> Read my reply and the link to the Wine AppDB. It's described there. What's so hard to download the JRE from java.sun.com, start the installer in wine and follow the onscreen directions?
Ok, now I fixed it. What I did I went to Java website and downloaded the Windows version and use wine to execute it.

Thanks everyone I really do appreciate all the help

---

### Post by trimmer on 2010-02-26
In the future, you may want to consider NOT "installing java into wine". You'll probably experience performance decreases.

Instead, realize that IcedTea is the jre of choice for web browsers and not a true jre.

I recently removed IcedTea because I realized that my apps, locally, ran choppy and I could run fewer apps at a time.

I removed IcedTea and reinstalled sun-java6-jre and sun-java6-bin. In your case, you do not have either of them installed so what I would do if I were you would be as follows:

Uninstall java from wine
sudo apt-get remove IcedTea
sudo apt-get autoremove
sudo apt-get install sun-java6-jre

sun-java6-bin will auto install with the jre and then you will have native access to java jre and access to the jre from within wine natively too.

If this doesn't work, you can always easily get back to where you are with your current installation by removing the 2 files I suggested and then reinstalling the IcedTea app and all dependancies followed by "installing java into wine".

Good Luck

---

