---
title: "Logisim on Ubuntu 14.04 LTS gets java error"
date: 2014-05-02
forum: Education &amp; Science
---

### Post by jtmfam on 2014-05-02
Greetings.  I upgraded to Ubuntu 14.04 LTS from 13 today.  Logisim was deinstalled in the process (I'm guessing since its a third party application.) Logisim 2.7.1 installed without errors, but when I try to run it, I get java errors, if any one has any guesses at solutions or where error logs might be:
dad@compaq:~$ /usr/bin/logisim
Exception in thread "main" java.awt.HeadlessException
	at sun.awt.HeadlessToolkit.getMenuShortcutKeyMask(HeadlessToolkit.java:234)
	at com.cburch.logisim.gui.menu.MenuFile.<init>(MenuFile.java:37)
	at com.cburch.logisim.gui.menu.LogisimMenuBar.<init>(LogisimMenuBar.java:87)
	at com.cburch.logisim.gui.start.Startup.run(Startup.java:152)
	at com.cburch.logisim.Main.main(Main.java:36)
dad@compaq:~$ 

Thanks In Advance.

---

### Post by jtmfam on 2014-05-02
Clunky Solution:
I had java6 and 7 installed, so I tried removing the java7 installer.  It said it succeeded but dpkg still showed it.
sudo apt-get remove oracle-java7-set-default

dad@compaq:~$ java -version
java version "1.7.0_55"
OpenJDK Runtime Environment (IcedTea 2.4.7) (7u55-2.4.7-1ubuntu1)
OpenJDK 64-Bit Server VM (build 24.51-b03, mixed mode)


Logisim was deinstalled somewhere down the road
dad@compaq:~$ dpkg --get-selections | grep logisim
logisim						deinstall

I reinstalled Logisim and it came up.  
sudo apt-get install logisim

I noticed that the java7 packages were deinstalled.  The upgrade to Ubuntu 14 got rid of the third party sources, so I added those back.
[http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-jdk-6-7-8-or-jre](http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-jdk-6-7-8-or-jre)
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]get install python[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]software[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]properties
[/FONT][/COLOR]sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

I guess the moral of the story is to try reinstalling logisim and at worst remove and reinstall any third party packages.

---

