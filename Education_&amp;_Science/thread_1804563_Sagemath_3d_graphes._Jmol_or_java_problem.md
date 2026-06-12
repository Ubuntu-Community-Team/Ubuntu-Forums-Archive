---
title: "Sagemath 3d graphes. Jmol or java problem?"
date: 2011-07-14
forum: Education &amp; Science
---

### Post by jotacebusta on 2011-07-14
Hi all,
I've recently updated to 11.04. Il also installed sage 4.7, downloaded form sagemath site.

When I run sage from the console everithing works fine, 3d graphics are shown in a separate window of jmol.

But when I try to do the same thing using te notebook() interface, no graph is shown. Everything else works fine, so far. My default browser is firefox, but I've also tried with chromium, and chrome, and it does not work. 

Before I upgraded to 11.04 I had the same problem on firefox 3.6, but things were fine with chrome.

I've posted this problem in the sage forums, without any result.

Thanks a lot,

JC

---

### Post by PC_load_letter on 2011-07-16
I had this same problem way back (probably a year ago) and if you read about it on the Sage Google Group you'd learn that the OpenJDK that comes installed by default on Ubuntu has a bug resulting in the error you got. So, just uninstall it, and install the Sun Java instead.

---

### Post by jotacebusta on 2011-07-18
Thank you very much.
I didn't found the corresponding post in the sage users forum.

I've tried to remove openjdk and install SunJava instead, but it didn't work. Among other things, uninstalling OpenJDK created problems with JabRef, and GeoGebra as well. I guess that I can somehow tell my computer to use SunJava to tun these programs, but I do not know how to do it.

On the pther hand, I do not know how to tell firefox to use SunJava to run the applets.

Thanks a lot,

JC

---

### Post by PC_load_letter on 2011-07-18
Do a search (google) on how to install sun java and/or make it default. It's easy, I have done it many times but I do not recall the step by step procedure. How about this, launch synaptic, install Sun Java first, then uninstall OpenJDK. Now close synaptic and open a terminal, then type: 
```
$ java -version
```

You should then get something like this: 
```
$ java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

```

The post I was referring to was on the Sage developer group IIRC.

---

### Post by jotacebusta on 2011-07-18
Thanks again,

I manged to set sun-java as the default java stuff, using 
sudo update-alternatives --config java

But the applets still do not work. I think it's really a firefox problem, since when I go to jmol page, at sourceforge, I can't see the applets there.

Thanks

JC

---

### Post by PC_load_letter on 2011-07-19
One second, is JMOL working now from within SAGE, or not? JMOL has nothing to do with FF.
I'm not sure why FF is having a problem, according to this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
It should just works with Sun Java. Try reinstalling FF and see what happens, or start it from terminal and report the error messages when you start a non-working java page.

**EDIT:** To test your FF w/ java, go to:[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)
and see what the page will report about your java setup. For JMOL, why don't you install Chromium/Chrome, make it default, and see if JMOL will work with them.

---

### Post by PC_load_letter on 2011-07-19
I tested SAGE on my son's Natty install and everything worked fine, I plotted a 3D surface and it worked. Here is what I think where you may have a problem:
1- when you installed Sun Java, did you agree to the EULA? If you use Synaptic, you'll have to check a box to acknowledge that.

2- If you tried testing your browser (FF, or Chrome) at the link I gave earlier and got a "missing plugin" message then you need to install the Sun java browser plugin, from Synaptic or open a terminal and type:
```
sudo apt-get install sun-java6-plugin
```

Let's know how it turns out.

---

### Post by jotacebusta on 2011-07-19
Thanks again,

When I installed sun-java, using synaptic, I didn't got any checkbox in the process. I just tried to reinstall it and no checkbox appeared.

When I tested my java instalation at  [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp) things went fine.

At that moment, when I use chromium, I can obtain my 3D surfaces in the right way. This is not the case for Firefox.

At the jmol's page, in [http://jmol.sourceforge.net/index.nl.html](http://jmol.sourceforge.net/index.nl.html) the result is the same: chromium shows right, firefox does not.

Jmol works fine, when I use sage from the terminal, there is no problem for my surfaces.

I do have the sun-java-plugin installed, by the way.

Thakns again,

JC

---

### Post by PC_load_letter on 2011-07-20
In my previous post, I did my testing w/ Chrome, so I haven't tested it with FF. It might be a FF problem then. Given the rapid rate of version updating of FF, it may be a bug. I'll confirm in the morning.

---

