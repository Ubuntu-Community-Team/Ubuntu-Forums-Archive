---
title: "Java applets in Firefox 2.0"
date: 2006-11-23
forum: Desktop Environments
---

### Post by grav on 2006-11-23
I've upgraded from Dapper to Edgy and now java applets don't work in Firefox 2.0.

Java Runtime environment is installed and working (v1.5) and I've also tried installing the package 'java-gjc-compat-plugin'.

I've also tried 
```
sudo update-alternatives --config java
```
which gives me these alternatives:

```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

I've tried each and every one and restarted FF, but it didn't help.

about:plugins mentions nothing of java.

What to do?!

**Update:**
I did the following after searching some more:

* Exit ff
* $ sudo rm /usr/lib/firefox/plugins/libjava*
* $ sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
* start ff

... which solved it

Now I remember doing this with Dapper and FF 1.5 as well. Just wondering why this is at all necessary.

---

### Post by daddywifi on 2006-12-09
I am wondering how you got it to work in Dapper. I have done several searches and everything I have tried has not worked :( Can you offer any help? Thanks in advance

---

### Post by grav on 2006-12-09
> **daddywifi said:**
> I am wondering how you got it to work in Dapper. I have done several searches and everything I have tried has not worked :( Can you offer any help? Thanks in advance

Well, not really except from the above. Have you tried all the things I mention?

---

### Post by tankafrey on 2006-12-19
My java applets now work under Edgy.  I used synaptic and 
installed sun-java5-bin and sun-java5-jre (I believe java-common
was already installed).   This was fine, but applets didn't
work until I then installed sun-java5-plugin.  I rebooted
(perhaps overkill?) and things worked beautifully. 

Here's the description of the sun-java5-plugin package:
The Java(TM) Plug-in, Java SE 5.0
Java Plug-in enables applets written to the Java Platform 5.0
specification to be run in Mozilla and other web browsers.
Java Plug-in comes with the Java Runtime Environment (JRE).
This is a metapackage containing dependencies for running Java in
various browsers.

It may be that sun-java5-plugin or the equivalent is all you need. 

-tf

---

### Post by l1ltw1st on 2006-12-22
Can some direct me to where you are seeing sun-java* ?  In Edgy when I do

sudo apt-cache search sun-java

nothing is returned, I do a search for sun-java in synaptic, no results.  Am I missing a repository in sources.list or something? ](*,) 

This is killing me as I am trying to get Ubuntu installed on 51 laptops, this is the last piece I need to work to complete my proof of concept...  TIA

---

### Post by ThrobbingBrain66 on 2006-12-22
It looks like you're missing some repos.  Go to System > Administration > Software Sources > Ubuntu 6.10 tab and make sure that the 'multiverse' checkbox is ticked.  Then open synaptic and you'll have all the sun-java5-* packages

---

### Post by l1ltw1st on 2006-12-22
> **ThrobbingBrain66 said:**
> It looks like you're missing some repos.  make sure that the 'multiverse' checkbox is ticked.  Then open synaptic and you'll have all the sun-java5-* packages

You are absolutely correct, thank you so much !!!

---

### Post by bro on 2007-04-04
j2re1.4-mozilla-plugin might be what you need/want to install?

---

