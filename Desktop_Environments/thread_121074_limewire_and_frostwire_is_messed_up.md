---
title: "limewire and frostwire is messed up"
date: 2006-01-24
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-24
Hi... problems problems etc.
Limewire and frostwire have worked fine for a long time.
Now they suddenly locks. I think they are still downloading because of netload,
but the programs is all gray.

I suspect its a java error but I cant understand that.
Ive installed java trough automatix...

chris@chris:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

---

### Post by syklitengutt on 2006-01-24
let me ask you then...
Shouldnt 768 MB ram be enough to run limewire or frostwire....
Why is limewire so much more memory and cpu consuming on ubuntu than in windows. 

Do any of you have problems using limewire?

---

### Post by PuNGS on 2006-01-24
I'm getting an error like that, and I found no solution. Just minimize and maximize the window and everything should be back to normal, temporally.

---

### Post by syklitengutt on 2006-01-24
nope minimize and maximize it turn everything grey.
what it starts with is that the downloads freeze in stats (showing me the down speed and time remainig.

---

### Post by syklitengutt on 2006-01-25
bump

---

### Post by syklitengutt on 2006-01-25
ok... let me explain this a little bit more.
Limewire and frostwire have worked fine all allong. now its stopped working...
anyone with some bright ideas?

---

### Post by syklitengutt on 2006-01-26
hump

---

### Post by syklitengutt on 2006-01-26
if I start Limewire trough terminal this error is going over and over again until it freezes!!!
any ideas?

> [Fatal Error] :336:1: Content is not allowed in trailing section.
[Fatal Error] :336:1: Content is not allowed in trailing section.
CyberGarage warning : java.io.FileNotFoundException: /WANIPConnection.xml (No such file or directory)
org.cybergarage.xml.ParserException: java.io.FileNotFoundException: /WANIPConnection.xml (No such file or directory)
        at org.cybergarage.xml.Parser.parse(Parser.java:100)
        at org.cybergarage.upnp.Service.getSCPDNode(Service.java:292)
        at org.cybergarage.upnp.Service.getSCPDNode(Service.java:330)
        at org.cybergarage.upnp.Service.getActionList(Service.java:351)
        at org.cybergarage.upnp.Service.getAction(Service.java:371)
        at com.limegroup.gnutella.UPnPManager.addMapping(UPnPManager.java:365)
        at com.limegroup.gnutella.UPnPManager.mapPort(UPnPManager.java:300)
        at com.limegroup.gnutella.Acceptor.init(Acceptor.java:250)
        at com.limegroup.gnutella.RouterService$Initializer.run(RouterService.java:300)
        at java.lang.Thread.run(Unknown Source)
        at com.limegroup.gnutella.util.ManagedThread.managedRun(ManagedThread.java:60)
        at com.limegroup.gnutella.util.ManagedThread.run(ManagedThread.java:49)
Caused by: java.io.FileNotFoundException: /WANIPConnection.xml (No such file or directory)
        at java.io.FileInputStream.open(Native Method)
        at java.io.FileInputStream.<init>(Unknown Source)
        at org.cybergarage.xml.Parser.parse(Parser.java:91)
        ... 11 more


---

### Post by syklitengutt on 2006-01-27
is it really noone who can help me?

---

### Post by arnieboy on 2006-01-27
these are known java related bugs in frostwire and have been reported on their forums though no one has any solution yet. they are all waiting for the next bugfix version of frostwire which u shd wait for as well.

---

### Post by syklitengutt on 2006-01-27
thats boring...
but why it suddernly happened I really dont know.
But arnieboy... trough automatix I got LW 4.9 and the latest version on their page says 4.10....

---

### Post by arnieboy on 2006-01-27
[QUOTE=syklitengutt]thats boring...
but why it suddernly happened I really dont know.
But arnieboy... trough automatix I got LW 4.9 and the latest version on their page says 4.10....[/QUOTE]
the latest version of automatix installs 4.10

---

### Post by syklitengutt on 2006-01-27
hmmm.... do I have to uninstall first, or just install over?

---

### Post by arnieboy on 2006-01-27
[QUOTE=syklitengutt]hmmm.... do I have to uninstall first, or just install over?[/QUOTE]
uninstall first.
4.10 seemingly gives the same error in certain circumstances.. as in urs.

---

