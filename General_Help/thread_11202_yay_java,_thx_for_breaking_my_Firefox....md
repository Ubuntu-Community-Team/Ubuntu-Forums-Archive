---
title: "yay java, thx for breaking my Firefox..."
date: 2005-01-14
forum: General Help
---

### Post by node on 2005-01-14
Well, I tried installing java on my notebook, now firefox won't start anymore.
Tried apt-get remove mozilla-firefox and re-install it afterwards, but the error I keep getting is : INTERNAL ERROR ON Browser End: Could not get plugin manager 
system error?:: Success.
Please help.

---

### Post by spartas on 2005-01-14
i've had the same problem pretty recently as well.  i removed Java, Mozilla, and Mozilla-Firefox (the latter using apt-get remove), then reinstalled them all in reverse order.  

When you installed java, did you follow the instructions at ubuntuguide.org, or using your own method.  One thing to be aware of is that you create the symbolic links correctly.  That's what messed up my last installation, however after I performed the steps above, firefox would work, but I was unable to access the Downloads panel in Edit->Preferences.  I gave up and reinstalled Warty from one of the official pressed CDs I have.

---

### Post by wallijonn on 2005-01-14
Maybe we ought to start a thread entitled, "Don't install this or you'' break your system". 

Besides Java I would include gDesklets and X.Org on Warty.

---

### Post by Sensebend on 2005-01-15
I and many others have experienced no problems with Java on Warty.

gDesklets and X.org should certainly be on that list though :)

---

### Post by node on 2005-01-16
Ok, obviously it was 1.5 which was the problem, 1.4 works :)

---

### Post by ixus_123 on 2005-01-16
gdesklets haven't given me any problems on Warty. I'm going to remove them though as I was underwhelmed with them.  I was expecting something similar to Konfabulater on the Mac

---

### Post by Siddhartha V. on 2005-03-07
I'm agree with node that the 1.5 version has a problem....... Even installed with the ubuntuguide's howto, firefox fails to start.

But with the 1.4, everything is fine. Just uninstall the 1.5 and use this direct link to the 1.4.2 that's work: [http://java.sun.com/webapps/download/AutoDL?BundleId=9718](http://java.sun.com/webapps/download/AutoDL?BundleId=9718)

And here is the marvelous guide for tweaking your Warty  ;) : [http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)

---

### Post by apriest on 2005-03-07
I installed the java 5 jre  in  usr/java. I created a link from my 
/home/uname/.moziilla/plugin directory to.  

ln -s /usr/java/j2re1.5.0/plugin/i386/ns7/libjavaplugin_oji.so

and it works. 

Don't use plugin/i386/ns7-gcc29/javaplugin_oji.so as this caused the same problem you described above.

---

### Post by WirelessMike on 2005-03-07
> *Posted by apriest:*
I installed the java 5 jre in usr/java. I created a link from my/home/uname/.moziilla/plugin directory... 

I think it may be worth mentioning that if you're using Firefox, you'll want to create this link in the .mozillafirefox/plugins directory, even though that should be pretty obvious.

---

