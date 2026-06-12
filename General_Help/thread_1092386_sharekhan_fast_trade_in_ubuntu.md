---
title: "sharekhan fast trade in ubuntu"
date: 2009-03-10
forum: General Help
---

### Post by krishmish on 2009-03-10
i am unable to work sharekhan fast trade terminal in ubuntu firefox.
pls suggest me a fix for that.

---

### Post by kellemes on 2009-03-10
> **krishmish said:**
> i am unable to work sharekhan fast trade terminal in ubuntu firefox.
pls suggest me a fix for that.

1- What is.. this fast trade thing?
2- How is it not working?

---

### Post by Joeb454 on 2009-03-10
Thread moved to  General Help :)

---

### Post by nickbuntu on 2009-03-10
It sounds like it's referring to this

[https://strade.sharekhan.com/rmmweb/applet/Login.jsp](https://strade.sharekhan.com/rmmweb/applet/Login.jsp)

So I guess the poster is having trouble using applets? :?

First go here to see if you have a Java plugin at all, and if it is the Sun one or one of the others:

[http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)

It may require the Sun version of Java, in which case you can install it either in the command line

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

or go to Add/Remove Programs and find "Sun Java 6.0 Plugin". In fact, if you visit the above link and you don't have a plugin Firefox may ask you there and then to pick a plugin to install, which is probably the easiest way.

You can then check what version Firefox is using by going to the about: plugins page (without a space)

After writing all this I'll probably find the problem was nothing to do with Java... :)

---

### Post by kellemes on 2009-03-10
> **nickbuntu said:**
> After writing all this I'll probably find the problem was nothing to do with Java... :)

Still a valuable post ;-)

---

### Post by cariboo on 2009-03-11
Have a look at [this]("http://www.sharekhan.com/downloads/help.html"), it tells you what the requirements are.

Edit: the link changes the size of Firefox for me and opens another instance of Firefox.

Jim

---

### Post by krishmish on 2009-04-07
actually, in windows while using internet explorer, it uses JVM which once can download from the sharekhan fast trade terminal window(from the computer settings link).then u have to install JVM so the applets of the terminal are visible when u login into it.
but the issue in ubuntu with firefox is that jre6 and the plugin doenst work with the fast trade terminal.
i already had a go before in the same manner but without success...
and im still waiting...
thanx...

---

