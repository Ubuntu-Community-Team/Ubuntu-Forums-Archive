---
title: "Menus &amp; NetBeans"
date: 2010-10-12
forum: Desktop Environments
---

### Post by micael3000 on 2010-10-12
@ Ubuntu 10.10.

Hello.

I am having some issues on NetBeans, just as some other softwares as well...
In some cases, my menu have a strange font configuration, there are a black font in a black background with some pieces of white on it (hard to see!)... I would like to know how to fix it.

Also, I installed NetBeans (sudo apt-get install netbeans), but it came without support to J2EE what is exactly what i need... I cant find Servers panel and i cant load Web projects.

If you can help me, please, i will be pleased.

---

### Post by micael3000 on 2010-10-12
Hello? Anyone?

---

### Post by micael3000 on 2010-10-12
Adding a screen shot showing the color issue.

[IMG]http://img685.imageshack.us/img685/732/screenshotwb.png[/IMG]

---

### Post by micael3000 on 2010-10-12
I Downloaded FULL NetBeans from their site, and it is working fine now.

The only issue that remains is the color of the menu.

---

### Post by sealtrip on 2011-03-05
Hi micael3000,

I have just moved from windows...Did you find a solution to this strange menu behaviour?

Please post a solution..thanks

---

### Post by phil.lxnet on 2011-05-04
@sealtrip
Hello, I know this is an old thread but since I found it I thought others might also, plus your comment is quite recent.  I have just been struggling with this one myself.

I found various postings advising that I add the following to the netbeans_default_options in the ~/netbeans-7.0/etc/netbeans.conf file.
-J-Dswing.aatext=true -J-Dawt.useSystemAAFontSettings=on
or
-J-Dswing.aatext=true -J-Dawt.useSystemAAFontSettings=lcd

However neither worked for me.

But a workaround suggested to me by my friend Ben did:-

Change your System theme to Radiance (I was on Ambiance)
System - Preferences - Appearance - Theme tab

Very work around as changes your entire gnome theme but have spend ages trying to find an alternative and failed thus far.

The result is that netbeans menues are at least are usable now.

Hope this helps others.

---

### Post by micael3000 on 2011-08-02
Thank you very much phil!

---

