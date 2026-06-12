---
title: "Azureus won't open."
date: 2005-05-19
forum: Desktop Environments
---

### Post by bdmp on 2005-05-19
Like I said, Azureus won't open. I see the bouncing icon and then "tah-da"... nothing.  I installed it from the directions in the "unofficial ubuntu starter guide" [http://ubuntuguide.org/](http://ubuntuguide.org/)  Any suggestions?

---

### Post by bored2k on 2005-05-19
[QUOTE=bdmp]Like I said, Azureus won't open. I see the bouncing icon and then "tah-da"... nothing.  I installed it from the directions in the "unofficial ubuntu starter guide" [http://ubuntuguide.org/](http://ubuntuguide.org/)  Any suggestions?[/QUOTE]
 Open up a terminal window, go to that directory and type sh azureus. What happens ?

---

### Post by bored2k on 2005-05-19
[QUOTE=bored2k]Open up a terminal window, go to that directory and type sh azureus. What happens ?[/QUOTE]
 You can also enable backports and install it there.

---

### Post by bdmp on 2005-05-20
[QUOTE=bored2k]Open up a terminal window, go to that directory and type sh azureus. What happens ?[/QUOTE]
By "that directory" what do you mean?

---

### Post by bored2k on 2005-05-20
[QUOTE=bdmp]By "that directory" what do you mean?[/QUOTE]
 Well how did you install azureus ?
If you download the backported version, hit
```
sh /usr/bin/azureus
```

If you downloaded the bz2 from azureus.sourceforge.net extract it , then point terminal to that direction [cd dirname] and type sh azureus

---

### Post by bdmp on 2005-05-20
[QUOTE=bored2k]Open up a terminal window, go to that directory and type sh azureus. What happens ?[/QUOTE]

I in stalled asureus and java from the faq on the link that I listed in the first post. When I did the sh azureus command I got

```
root@chibi:/opt/azureus # sh azureus
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
``` 

What should I do now?

---

### Post by bored2k on 2005-05-20
[QUOTE=bdmp]I in stalled asureus and java from the faq on the link that I listed in the first post. When I did the sh azureus command I got

```
root@chibi:/opt/azureus # sh azureus
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
``` 

What should I do now?[/QUOTE]
 Do you have java installed ? no? yes? doesn't matter.

Do this [http://ubuntuguide.org/#backportsrepositories](http://ubuntuguide.org/#backportsrepositories) (Add backports)
Install sun-j2re1.5 and azureus
[ sudo apt-get install azureus ]

That is it.[select from your menu].

---

### Post by bdmp on 2005-05-22
Worked thanks a lot.

---

### Post by oliwally on 2005-07-27
Howdy,

I have a similar problem. I installed azureus using synaptic. I also have sun-j2re1.5 installed.

When I hit the Azureus button I get the bouncing icon but then it disappears. At one stage I even got a screen up with the frog logo, but the program got hung there.

What do I need to do?

Is azureus worth the trouble or should I use amule, which works but won't download anything. From what I read I  need to fiddle with the iptables settings. Can that be done using Guarddog or Firestarter?

---

### Post by sinbad782 on 2005-07-27
That's a weird one. I have the usual archive and backports repositories set up and azureus works fine for me. I have the most up to date sun-j2re1.5 Java runtime environment package from backports installed. 

Something I did notice is that while Azureus DOES take around five minutes to start in Windows XP, while in Ubuntu it starts almost instantaneouly - go figure.

---

### Post by oliwally on 2005-07-28
I'll try installing the latest java thingo and see how it goes

---

### Post by oliwally on 2005-07-29
I've installed the latest version of the sun-java thingo, and have re-installed azureus, but no luck - it won't open. Does anyone have any wisdom to share?

---

### Post by oliwally on 2005-07-31
bump

---

### Post by bored2k on 2005-07-31
sudo apt-get install sun-j2re1.5 ?
What's the output if you run azureus from a terminal ? (sh azureus)

If all else fails, sudo apt-get install azureus

---

### Post by oliwally on 2005-08-09
this is the output of sh azureus


```
DEBUG::Tue Aug 09 22:28:32 GMT+10:00 2005
  java.lang.ClassNotFoundException: com.sun.net.ssl.internal.ssl.Provider not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/swt-gtk-3.1.jar], parent=gnu.gcj.runtime.VMClassLoader{urls=[core:/], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Unknown Source)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

DEBUG::Tue Aug 09 22:28:32 GMT+10:00 2005
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists(java.lang.String) (Unknown Source)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Unknown Source)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

DEBUG::Tue Aug 09 22:28:32 GMT+10:00 2005
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists(java.lang.String) (Unknown Source)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Unknown Source)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

DEBUG::Tue Aug 09 22:28:33 GMT+10:00 2005::com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector::start()::-1:
    IncomingSocketChannelManager::start()::-1,IncomingSocketChannelManager::IncomingSocketChannelManager()::-1,NetworkManager::NetworkManager()::-1,NetworkManager::<clinit>()::-1,Class::initializeClass()::-1,AzureusCoreImpl::AzureusCoreImpl()::-1,AzureusCoreImpl::create()::-1,AzureusCoreFactory::create()::-1,Main::Main(java.lang.String[])::-1,Main::main(java.lang.String[])::-1,MainThread::call_main()::-1,MainThread::run()::-1
java.net.BindException: Address already in use
   at gnu.java.net.PlainSocketImpl.bind(java.net.InetAddress, int) (/usr/lib/libgcj.so.6.0.0)
   at java.net.ServerSocket.bind(java.net.SocketAddress, int) (/usr/lib/libgcj.so.6.0.0)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.start() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.IncomingSocketChannelManager.start() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.IncomingSocketChannelManager.IncomingSocketChannelManager() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.NetworkManager.NetworkManager() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
StartSocket: passing startup args to already-running Azureus java process.
Aborted

```
The first time I did the sh azureus it just kept looping over and over with the azureous splashscreen displayed. The second time it spat the above out.

I also tried sudo apt-get install azureus, but same result.

---

### Post by oliwally on 2005-08-11
bumpity

---

### Post by bored2k on 2005-08-11
[QUOTE=oliwally]bumpity[/QUOTE]
 I wish I had an answer for your crying soul :( .. I've made myselfa  java deb package AND tried the UBackports JRE and they both work perfectly with azureus, I don't know what the deal with your box is.

---

### Post by webmassa on 2005-08-27
[QUOTE=bored2k]I wish I had an answer for your crying soul :( .. I've made myselfa  java deb package AND tried the UBackports JRE and they both work perfectly with azureus, I don't know what the deal with your box is.[/QUOTE]
 I've got the same problem since I installed some atmel drivers for my WLAN-Card.
I installed some libraries that were needed for making the pcmcia drivers and after that, azureus won't show up again.
If I start it, no window appears and after 10 Minutes the process exits with a java timeout.
Befor installation of some GTK and wxWidget (wx-config) Libraries everything went fine and azureus started within a view seconds but now I stuck.
Reinstalled everything, from java to azureus but can't get it to work again.

Regards...Webmassa

---

### Post by lithorus on 2005-09-08
[http://twoday.tuwien.ac.at/mindmedic/stories/7436/](http://twoday.tuwien.ac.at/mindmedic/stories/7436/)
In short, make sure that the loopback network interface is up and running.

---

### Post by barsanuphe on 2005-09-14
i have the exact same problem and that didnt work for me.

---

### Post by Rylan on 2006-05-26
I just stumbled into this thread from a  Google search.  The problem I had was that the JRE I was using was the default gcj, even after I installed the Sun 1.5 JRE.  

Some more googling and I found this: 

sudo update-alternatives --config java 

That let me switch to Sun's JRE, and now Azureus works fine.

---

### Post by bled on 2006-05-27
I had the same problem and your procedure with the "sudo update-alternatives --config java" etc was really  helpful, thx!

But before this worked for me, I had to add my jre installation to the alternatives with:
sudo ln -s /etc/alternatives/java /usr/local/bin/java 
sudo update-alternatives --install java java /usr/lib/jre1.5.0_07/bin/java 400

after this I could use
sudo update-alternatives --config java
to choose the newly added alternative. After this my Azures worked ^^

---

### Post by Ram Crammer on 2007-11-07
I had been using Deluge 0.5.0 but thought I'd try Asureus, since so many people are using it. After screwing around for half an hour, trying to get it to work, I found a link to install a fix for the Java Run Time Environment. I Installed that, but then the Ubuntu installer complained saying the older version of Asureus was better supported on Ubuntu. Well, I decided to try the newest version of Asureus, despite the dire warning. The latest Asureus wouldn't start, and gave the same Java Run Time error message in terminal. So, I installed the older version. Now Asureus runs, but I could never get the NAT errors to go away.

My router (a slick 2-Wire 700HG) does not support or require reassigning port IDs (the router does it automagically), so what the hell are you supposed to do then? But that was just one of many problems I encountered while trying to decipher the cluttered and illogical Asureus interface and overly complex configuration wizard and options. So, I decided to go back and download the very latest version of Deluge (v.0.5.6.2), and Man, does it rock!!! All the features I had wanted for months has now been implemented, and my downloads are now much faster. You can select the files for download in bunches, and tag the entire bunch at once, with various priorities, including "don't download this file". The Deluge interface is beautiful and logical. Deluge is sooo much easier to set up, and use than any other client I've seen. No fuss, no frustration. From download to up-n-running took all of about 2 minutes, and never a bit of trouble. To all you Asureus sufferers out there, wake up! Deluge blows Asureus out of the water.

So, the moral is, don't download the earlier version of Deluge from the repositories, and don't bother with Asureus. You can install and master Deluge v.0.5.6.2 in minutes. It does everything you need without having to take a Masters level course in bit-torrent technology. Get it here: [http://deluge-torrent.org/about](http://deluge-torrent.org/about) The Deb installer for the Ubuntu version worked flawlessly on my 32 bit machine. There is an installer for 64 bit systems also. You can buy me a bear next time we meet

---

