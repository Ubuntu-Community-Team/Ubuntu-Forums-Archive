---
title: "own live-cd"
date: 2008-01-31
forum: Desktop Environments
---

### Post by depele on 2008-01-31
hello, 

I have to make an own [SIZE="5"]live cd[/SIZE].

No gui.

install custom applications, like

apache
mysql
webgoat


We have to put some security holes in it like webgoat.

We also have to provide a script to start / open | stop / close the security holes.

 
Has anyone an idea?
Can somebody help me?
provide me some links?

Thanks a lot.

---

### Post by stalker145 on 2008-01-31
> **depele said:**
> hello, 

I have to make an own live cd.
No gui.
install custom applications, like
apache
mysql
webgoat
We have to put some security holes in it like webgoat.
We also have to provide a script to start / open | stop / close the security holes.
 
Has anyone an idea?
Can somebody help me?
provide me some links?

Thanks a lot.

Try setting up your system the way you like/need it and run [Remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys").

One of these days I'll get at and try it myself, but it looks like a promising project.

---

### Post by depele on 2008-01-31
I have also found in meanwhile uck.   (ubuntu customation kit).

Has anyone some idea's about the vurnabilities I can put in the live cd?

thanks

---

### Post by rconnely on 2008-01-31
I have used ubuntu customation kit and it worked ok, except for the Usplash.  For some reason it screwed up my gnome pannel.  Also, I agree with Stalker, Remastersys is a really good tool to use for this application.  If you are going to pre-build holes into your system you should build it the way you wont it to be and then run 

```
sudo remastersys backup
```

This will keep the holes in tact.  If you go with UCK, then it will use an image to build your awk directories or it will build it from an existing Live Distro.  Essentially, it will patch your holes for you :) And that seems as if it would defeat the purpose.  Good luck!

---

### Post by rconnely on 2008-01-31
One more thing... if you want a security hole for a LAMP server which may run something like Moodle (open education server) for example, you could always have the moodledata file inside your moodle directory.  If someone were to open a browser, they could navigate to that folder and delete al student data.  Also, if there is a wordpress site with php scripts enabled in the URL, then you could simply post some SQL injected statements into the URL to cause some havoc.  There are numerous holes that can be exploited if you dont have your IP tables locked down (ie shorewall, firestarter).  Also, you could keave the ssh connection port to 22 open, or FTP to 21 open.  Both of these default ports is a security risk as well.  I'll try and find you some cool docs that may help you leave some holes.

---

### Post by depele on 2008-02-01
Thanks a lot for the nice idea's..

If you have some more idea's?

I am wondering how I can implement **webgoat** in the live cd.

Thanks in advance

---

### Post by kostkon on 2008-02-01
Maybe you will find [*Reconstructor*]("http://reconstructor.aperantis.com/") useful.

---

### Post by depele on 2008-02-11
Thanks a lot for all the information.

If someone can give me some more idea's about security issues?

---

### Post by depele on 2008-02-13
Next problem: 

How to remove usplash from live cd?

---

### Post by az on 2008-02-13
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

That probably is a better way to start your project.

You can remove usplash by taking the work "splash" out of your boot line in your isolinux config

---

### Post by depele on 2008-02-14
Thanks a lot.

Now I am looking to change the default key map.

But no idea where to looK?

someone an idea?

---

### Post by depele on 2008-02-15
Ok, 

webgoat is running is chroot envirement.

but when I build the live cd It can't be started anymore, and it gives an nullpointer exception.


Is it actually possible to access a webgoat server from another computer.

[IMG]http://de-pele.my2gig.com/vm-livecd.bmp[/IMG]

---

### Post by depele on 2008-02-20
Ok finally foud the sollution, 
Or I add a gui so I can contact the webgoat from the livecd. 
Or I have to edit settings from the tomcat server.


Next question.


Please help me.

I installed apache on the livecd. I have installed a web-site on the live cd. but when I try to reach the webpage, it will not show me images. 

When I run it from within the chroot environnement, it does.


Thanks

---

### Post by depele on 2008-02-21
shameless bump   ******************

---

### Post by depele on 2008-02-23
sameless bump****************

---

