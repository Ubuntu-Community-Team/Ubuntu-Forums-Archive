---
title: "myTunes/OurTunes"
date: 2005-11-04
forum: Desktop Environments
---

### Post by drguitarum2005 on 2005-11-04
Does anyone know any solutions for being able to use something like myTunes or OurTunes that runs in Windows? For those who don't know what im talking about, those 2 programs both do the same thing and allow you to browse the shared iTunes libraries on your network and play/grab the shared songs. Does anyone know how to go about doing this?I would assume Samba needs to be set up for it to work also....

---

### Post by mustang on 2005-11-05
I'm interested in this question as well. Also, has anyone tried running myTunes through WINE?

---

### Post by drguitarum2005 on 2005-11-05
yes, I tried it through WINE and while the app works, it obviously won't automatically connect to a windows network and due to the lack of configurability of myTunes, you can't point it through samba or anything...

---

### Post by shenki on 2005-11-06
I downloaded the ourTunes .jar file ([http://prdownloads.sourceforge.net/ourtunes/OT44src.jar?download)](http://prdownloads.sourceforge.net/ourtunes/OT44src.jar?download)), and ran it with
 
$ java -jar OT44src.jar

It loaded fine, and discovered iTunes music shares.

You may need to install something that will do the zeroconf backend stuff, such as avahi, but I'm not sure - give it a go without.

---

### Post by chele on 2005-11-29
I have RhythmBox & Avahi running and can see & play other peoples shared iTunes tunes. 

I believe the version of RhythmBox I have was specially prepared with Avahi support. Avahi was install via apt-get.

---

### Post by mjsoccer1 on 2006-02-08
I downloaded OT44.jar, ran it using java -jar OT44.jar, after installing libgcj6-awt (AWT peer runtime libraries) as well as the java engine.  I get the app to start to load, then it is immediately aborted, and the following is returned:
[I]I AM IN CSTC
lo
eth2
Interface eth2 seems to be InternetInterface. I'll take it...

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted[/I]

Anyone know how to fix this?  Any help is appreciated! Thanks!

---

### Post by mjsoccer1 on 2006-02-22
Anyone???  I'm at a loss as to why I can't get the program to work.  I have Rhythmbox 0.9.3 installed and it works using Avahi... but I would rather use OurTunes...

---

### Post by dude of wonders on 2006-02-22
dont know how to fix your problem, but theres a program coming out for linux soon called dtv democracy. it will work like itunes suppose to be better, its already out for mac and windows the linux version is still in beta. dont have the url , but just google dtv democracy. hope this helps:-D , until then i'm stuck using the windows.:-|

---

### Post by jjkrueger on 2006-02-22
DTV can be found at [http://www.getdemocracy.com](http://www.getdemocracy.com)

---

### Post by mjsoccer1 on 2006-08-21
I had OurTUnes working correctly on Breezy Badger... however now that I have Dapper Drake, I can get it to run, but I cannot connect to any other computers... and I know the other computers have connections available.  I have installed the avahi library as well as libgcj6-awt, but that did not seem to work. Here is the out put when I run OT44.jar:

[I] sudo java -jar OT44.jar
I AM IN CSTC
lo
eth1
Interface eth1 seems to be InternetInterface. I'll take it...
Exception in thread "Rendezvous.ServiceResolver" Exception in thread "Rendezvous.ServiceResolver" java.lang.ArrayIndexOutOfBoundsException
   at java.lang.String.init(libgcj.so.7)
   at java.lang.String.<init>(libgcj.so.7)
   at itunes.client.request.Request.readString(Request.java:125)
   at itunes.client.request.Request.processDataFields(Request.java:184)
   at itunes.client.request.Request.processDataFields(Request.java:203)
   at itunes.client.request.Request.Process(Request.java:177)
   at itunes.client.request.Request.<init>(Request.java:73)
   at itunes.client.request.ServerInfoRequest.<init>(ServerInfoRequest.java:39)
   at itunes.client.swing.One2OhMyGod.addHost(One2OhMyGod.java:369)
   at itunes.client.swing.One2OhMyGod.resolveService(One2OhMyGod.java:362)
   at com.strangeberry.rendezvous.Rendezvous$ServiceResolver.run(Rendezvous.java:775)
[/I]

Any ideas?

---

### Post by mjsoccer1 on 2006-09-13
Figured it out...

sudo update-alternatives --config java
select /usr/lilb/jvm/java-1.5.0-sun/jre/bin/java

I was using another Java environment (/usr/lib/jvm/java-gcj/jre/bin/java)

---

