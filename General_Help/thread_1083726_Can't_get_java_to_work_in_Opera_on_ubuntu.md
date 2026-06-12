---
title: "Can't get java to work in Opera on ubuntu"
date: 2009-03-01
forum: General Help
---

### Post by 3pinner on 2009-03-01
Hello,
I am trying to get Java to run in Opera. my setup is as follows:
	Os: Ubuntu 8.10 (Intrepid)
	using Debian (gnome) desktop
Opera version: 9.63

Version of java installed: java-6-sun-1.6.0.10

Path to the folder where java is installed: /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386

Java common files package is installed.
 and all other dependencies that come with the Ubuntu java 6 package are installed

I followed the instructions for installing Java on Ubuntu, verified that it is installed, and selected as the default version,
 then opened opera,>Tools>Advanced>content  and enabled java, pointed opera to the above folder. 
When I click on Validate Java Path, I get :
	The Java path seems to specify a valid directory.

So according to all the instructions, everything is loaded as it should be, and Opera is pointed to the correct folder . But  when I go to the test applet either on the Opera or java web sites, java is not detected.
Yes I did close opera and restart it before trying to test it.

What did I miss, or do wrong?

Thanks!

---

### Post by taurus on 2009-03-01
Are you talking about the plugin?  The default is in /usr/lib/mozilla/plugins.

```
ls -la /usr/lib/mozilla/plugins
```

---

### Post by 3pinner on 2009-03-01
> **taurus said:**
> Are you talking about the plugin?  The default is in /usr/lib/mozilla/plugins.

```
ls -la /usr/lib/mozilla/plugins
```

I installed the Jre package, and am trying to get that to work in Opera.

I installed java andthe plugin for Firefox, and it works, just can't seem to get it to run in Opera.
I also tried copying the Java folder and using Nautilus to paste it into the /usr/lib/opera/plugins folder, and pointing opera there, but that didn't work either.

---

### Post by .nedberg on 2009-03-01
Have you enabled Java?

F12 -> Use Java

Also, my java path in Opera is

/usr/lib/jvm/java-6-sun/jre/lib/i386

That is slightly different from yours...

---

### Post by 3pinner on 2009-03-01
> **.nedberg said:**
> Have you enabled Java?

F12 -> Use Java

Also, my java path in Opera is

/usr/lib/jvm/java-6-sun/jre/lib/i386

That is slightly different from yours...

Yours is the correct path, and I corrected mine. Still no luck.
as for enabling Java, I think so, but hitting F12 did nothing.
What should I enter into terminal to get enable Java?
Thanks!

---

### Post by taurus on 2009-03-01
What's the output of this command to see which java you have installed on your machine?

```
java -version
```

---

### Post by 3pinner on 2009-03-01
> **taurus said:**
> What's the output of this command to see which java you have installed on your machine?

```
java -version
```

Output:

java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

---

### Post by taurus on 2009-03-01
Have you tried to reboot?

---

### Post by .nedberg on 2009-03-01
> **3pinner said:**
> Yours is the correct path, and I corrected mine. Still no luck.
as for enabling Java, I think so, but hitting F12 did nothing.
What should I enter into terminal to get enable Java?
Thanks!

Go to Tools->Settings->Advanced->Content, enable java (I don't have English language in Opera so wording might be different).

It is the same place as where you select the java path.

Also try to run opera from a terminal, it might throw some errors that can lead to an answer. Try starting it with
```

opera -debugjava

```
and/or
```

opera -debugplugin

```

also running it with
```

opera -pd /home/<username>/tempOpera

```
will start opera for "the first time", and let you see if it is your settings that are wrong.

---

### Post by 3pinner on 2009-03-01
> **taurus said:**
> Have you tried to reboot?

Yes I have, and got the same results.

Some further information.
I googled "java test" just for the heck of it, and found two sites that would test what version I have.
the one at javatest.org tested fine, with Opera identifying itself as Opera.
The java website java.com/en/download/help/testvm.xml failed the test, until I went into Tools>Quick preferences and set the identity as Firefox; then it tested fine.

So evidently java is working both with Ubuntu and in Opera, it was the java web site that was being fussy about which browser I am using. 
Therefore, when I have problems with a particular site,I'll just switch the browser identity.

I steadfastly refuse to give up Opera just because of a site that won't cooperate!

THANKS FOR THE HELP!

---

### Post by .nedberg on 2009-03-01
java.com/en/download/help/testvm.xml works fine in my opera...

Glad it turned out right for you! I love Opera too, but you do have to work a bit more with it on some sites. But it is worth it!

---

