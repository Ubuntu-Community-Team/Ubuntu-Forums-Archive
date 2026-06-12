---
title: "Troubles with Java"
date: 2009-06-14
forum: General Help
---

### Post by Oodi on 2009-06-14
I'm having some difficulty installing JRE 6.0... I downloaded the self-extracting file that goes along with the instructions to install here [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting). I moved the .bin file to /usr and then followed the instructions to install. Everything went well and according to the instructions. The only problem after that is when I went to use Java applications, they didn't work. 

I went the site to verify my version of Java to see if that worked properly, and firefox informed me that I didn't have the plugins to view that page. I installed the plugins that were suggested, and in the process some errors occured and it told me to input something into the terminal; I don't remember the specifics. After that was completed, I went back to verify my version of Java and it told me that I was using version 1.6... 

Unless it is in the information I've provided, I have no idea what the problem might be. I will answer all the questions necessary to get this working to the best of my ability. Thanks in advance.

---

### Post by QIII on 2009-06-14
The latest JRE is 6 Update 14.

Go to this site and ignore the BIG BLUE BUTTON!

Just below that button are the words "Do I have Java?"

Click that button to see if you have it installed properly.

If not, there is an easier way to get it.

JRE 6 Update 13 is available in the Ubuntu repositories (It's in Multiverse, so you may have to check your Software Sources).  It is not the "latest and greatest", but it will work for anything you are likely to want to use.

Go to System -> Administration -> Synaptic Package Manager.

Type "JRE" in the search box.

Select sun-java6-jre, sun-java6-bin and sun-java6-plugin

The Apply button should now be enabled.  Click it, and accept the changes to install.

---

### Post by Amilo1718 on 2009-06-14
or you might install the open JDK Java :KS

---

### Post by bogdan.veringioiu on 2009-06-14
Hi.

I suggest you to install sun java 6 jre from ubuntu repositories.
By installing the package, you will have the proper PATH settings in the system.

Try:
sudo apt-get install sun-java6-jre

After the installation, open a new terminal, and type:

java -version
You should get an output similar like this:

java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

This means that you have properly installed sun java, and you can run you java apps. Also you can try with firefox the sun plugin test page.

Bogdan

---

### Post by Oodi on 2009-06-14
[FONT=Arial][SIZE=2]QIII, all the names you gave were marked already in the Synaptic Package Manager.

When I use sudo apt-get install sun-java6-jre the output is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

When I use java [/SIZE][/FONT][FONT=Arial][SIZE=2]-version the output is: 
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)

When I go to verify my java version, it says:

[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Verifying Java Version [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Oops! You don't have the recommended Java installed.[/COLOR]

[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer.                                      [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation. 
[/COLOR]


[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]I'm still unable to run java applications properly. If I missed something, please point it out.
[/COLOR][/SIZE][/FONT]

---

### Post by QIII on 2009-06-14
> **Oodi said:**
> [FONT=Arial][SIZE=2]QIII, all the names you gave were marked already in the Synaptic Package Manager.

When I use sudo apt-get install sun-java6-jre the output is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

When I use java [/SIZE][/FONT][FONT=Arial][SIZE=2]-version the output is: 
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)

When I go to verify my java version, it says:

[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Verifying Java Version [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Oops! You don't have the recommended Java installed.[/COLOR]

[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer.                                      [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation. 
[/COLOR]


[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]I'm still unable to run java applications properly. If I missed something, please point it out.
[/COLOR][/SIZE][/FONT]

Seems that you still don't have the latest available in Ubuntu's repositories.  Make sure you have the Multiverse repository and go to terminal.

sudo apt-get install --reinstall sun-java6-jre

Remember, the Ubuntu repository has update 13, not 14, so you may get a message that you don't have the latest if you go back to Sun's site.


Here's the output of my java -version

java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)

I also just noticed you seem to have OpenJDK...which means that if you have both you may be running into conflicts.

---

### Post by bogdan.veringioiu on 2009-06-14
Hi.

Can you try this?

sudo update-alternatives --config java

This might help configure the default java executable in the system (choose jun java).

Let me know what are the results.

Bogdan

---

### Post by Oodi on 2009-06-14
sudo apt-get install --reinstall sun-java6-jre returns:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6.jre

sudo update-alternatives --config java returns:

There are 2 alternatives which provide `java'.

sudo update-alternatives --config java

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default
[*], or type selection number:

I don't see a "jun java".

---

### Post by bogdan.veringioiu on 2009-06-14
Hi.

Sorry, it was a typo (I meant sun java). :)

You can choose 2, to set sun java as default java executable in the system.

Bogdan

---

### Post by QIII on 2009-06-14
Are you sure you have Multiverse in your Software Sources?

And I still wonder if OpenJDK and and Sun are butting heads.

---

### Post by Oodi on 2009-06-14
Okay, thank you. I don't entirely understand what was done there, but it works now.

---

### Post by bogdan.veringioiu on 2009-06-14
Hello.

Basically, the theory behind this is simple.
The java executable in the system (/usr/bin/java, which is a symlink) was pointing to your OpenJDK installation.
update-alternatives is a tool to manage multiple installations of the same program (in your case java). What the tool did, was updating /usr/bin/java symlink to point to sun java installation.

Cheers

Bogdan

---

