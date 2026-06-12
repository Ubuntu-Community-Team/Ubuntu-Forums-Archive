---
title: "Hp Jetdirect Setup And Vjava Http Request Setup"
date: 2005-10-29
forum: Desktop Environments
---

### Post by sorry_name_taken_already2 on 2005-10-29
HELLO ALL!

I am stilltrying to get my head around linux but Ubuntu makes it as easy as guessing in Windows!

I have a HP JetDirect EX plus which serves a Lanier 5245 MFC Copier or Ricoh. Can someone tell me how to set it up. I tried using the KDE print manager wizard! I tried using Network TCP/Remote CUPS/Network Printer. 
The config for the printer :
IP :             192.168.1.205
SUB:          255.255.255.0
Gateway:  192.168.1.254

And now what is the deal with Konqueror. Its a pain inthe bum mozilla/firefox rocks. It was a breeze when I was using Hoary Gnome 5.04! I am having problems Setting up JAVA HTTPS support for Applets!!

I cant find the mysterious $KDEDIRS/share/apps/kjava directory!

Getting HTTPS support for Applets 
 You can get applets to work over https with konqueror using Sun Microsystem's JSSE (Java Secure Sockets Extension classes). These are available at  [http://java.sun.com/products/jsse](http://java.sun.com/products/jsse). You will need to download JSSE version 1.0.3 (Sun requires a free registration to do so). You will get a zip file that will contain 3 jar files: jcert.jar, jnet.jar, and jsse.jar. Simply copy those to your $KDEDIRS/share/apps/kjava/ directory and KJAS will automatically use them. If you don't have write access to your $KDEDIRS directory, then copy the three jar files to your $KDEHOME/share/apps/kjava/ directory. Then copy the $KDEDIRS/share/apps/kjava/kjava.jar to $KDEHOME/share/apps/kjava/. Konqueror will then look here instead of the KDEDIRS directory. 
 Please Note that you do NOT need to edit your java.security file or do any of the steps outlined in the JSSE installation howto. Simply copy the jar files and KJAS will make use of them. 

HELP [email]a0wong@hotmail.com[/email]

---

### Post by sorry_name_taken_already2 on 2005-10-30
thanks.... so far no replies!

---

### Post by greatshape on 2005-10-31
[QUOTE=sorry_name_taken_already2]HELLO ALL!

I am stilltrying to get my head around linux but Ubuntu makes it as easy as guessing in Windows!

I have a HP JetDirect EX plus which serves a Lanier 5245 MFC Copier or Ricoh. Can someone tell me how to set it up. I tried using the KDE print manager wizard! I tried using Network TCP/Remote CUPS/Network Printer. 
The config for the printer :
IP :             192.168.1.205
SUB:          255.255.255.0
Gateway:  192.168.1.254
[/QUOTE]

Try this as printer adres ipp://192.168.1.205:631/ in your printer setup.

Good luck

---

