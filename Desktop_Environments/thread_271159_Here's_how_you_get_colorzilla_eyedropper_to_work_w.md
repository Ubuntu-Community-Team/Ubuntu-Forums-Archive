---
title: "Here's how you get colorzilla eyedropper to work with firefox 1.5.0.7/dapper"
date: 2006-10-04
forum: Desktop Environments
---

### Post by janroald on 2006-10-04
I finally got it working!
Was actually a quite easy solution.
It seems that when upgrading firefox, some files are **not** updated. More specifically the libxpcom* files (/usr/lib/firefox/)

So : 
* Uninstall colorzilla
* Download latest firefox binaries from getfirefox.com
* Unpack (tar -xvzf firefox.....tar.gz)
* cp firefox..../libxpcom* /usr/lib/firefox/
* Reinstall colorzilla 0.8.3.1 from [http://www.iosart.com/firefox/colorzilla/ColorZilla_0.8.3.1.xpi](http://www.iosart.com/firefox/colorzilla/ColorZilla_0.8.3.1.xpi)
or firefox extension library.
* Restart firefox and eyedropper should now work

---

### Post by got_nix on 2006-10-04
thats odd colorzilla always worked for me on dapper.. if it stopped working all of a suddent just check your extensions if they need updating (colorzilla specifically) and i'm sure it'll work after the update.. thats all i did.

---

### Post by janroald on 2006-10-04
I know from _lots_ of googling that lots of people has trouble with this.
Colorzilla works, but it's eyedropper functionality doesn't and all u get is a popup saying that your platform doesn't support this feature. I've personally had this problem with dapper since it's release, and through all firefox/colorzilla versions since.

Today i found this thread when _again_ trying to solve it:
[http://www.ubuntuforums.org/archive/index.php/t-205188.html](http://www.ubuntuforums.org/archive/index.php/t-205188.html)

I decided to check my libxpcom* -files (firefox 1.5.0.7) against the ones in the binary release, and the were not the same size.

My best guess is that these files dont get updated when one updates firefox through its own update-functionality.

Eyedropper now works when have replaced my libxpcom*-files with the newest and reinstalled colorzilla.

---

### Post by uber noob on 2006-10-08
Brilliant! Thanks for this tutorial. not having Colorzilla was really aggrevating.

---

### Post by page1ink. on 2007-01-23
works great! thank you!

---

### Post by chaoskaizer on 2007-04-14
Thanks for the note it does works

---

### Post by acl123 on 2007-08-26
I couldn't get Foxmarks to install with ColorZilla (Firefox wouldn't even open after Foxmarks was installed).

I uninstalled ColorZilla, then installed Foxmarks, then reinstalled ColorZilla using the instructions above and it all seems to work now.

---

### Post by marcuskoze on 2007-10-03
I'm here to confirm that the trick really worked and i'm more than happy, just need the Eyedropper like air !

just a thing, as for the 
```

cp firefox...../libxpcom* /usr/lib/firefox/ 
```

line, usually after you untar the downloaded tar.gz , the folder name is just "firefox", so simply type:

```
cp firefox/libxpcom* /usr/lib/firefox/
```

, because at first i attempted to say:
```
 cp firefox*[COLOR="DarkRed"]-version[/COLOR]*/libxpcom* /usr/lib/firefox/
```  
and got an error (i'm new into linux, so pardon me :) ). 

Otherwise i confirm that the trick works, and it works just fine. Thanks for the fix :)

---

### Post by davidwhthomas on 2007-10-14
Just to confirm the method in the first post worked for me on Firefox 2.0.0.7 and Ubuntu Feisty. Thanks! :-)

---

### Post by explemonk on 2007-10-24
This just worked for me on Firefox 2.0.0.8 and Kubuntu Gutsy.  Thank you!

---

### Post by kegie on 2007-10-29
Just thought i'd chime in and say that this did NOT work for me with firefox 2.0.0.8 and gutsy. It broke my firefox and I had to *apt-get --reinstall install firefox*. :/

**edit:** I got it to work! I followed the instructions on the official webpage ([http://www.iosart.com/firefox/colorzilla/](http://www.iosart.com/firefox/colorzilla/)) to first do this:
```
sudo apt-get install libstdc++5
```

After that, the steps in the first post did it. Thanks!

---

### Post by snaga on 2007-11-29
This worked for me as well with Ubuntu 7.10. The other odd thing is that I was also having trouble with firebug. It wouldn't work at all. As soon as Colorzilla worked, firebug did too.

---

### Post by Dred on 2008-02-16
What about for Firefox version 2.0.0.12, i can't get it to work....don't know where to extract the tar.gz or anything.

I'm new to Linux so excuse my ignorance. :lolflag:

---

### Post by Happibun on 2008-02-24
I'm a Noob, running gutsy, installed 2 days ago and still setting up my environment. 

I've just updated Firefox from 2.0.0.6 which came with my install to 2.0.0.12 to try and get Colorzilla working. I've tweaked my Synaptic Package Manager, and Software Sources so that important and recommended updates from Main, Universe, Restricted and Multiverse are up to date. Somewhere in all of that I downloaded and installed something called libstdc++5 as told by this [http://www.iosart.com/firefox/colorzilla/](http://www.iosart.com/firefox/colorzilla/) which I found by googling the problem.

I had uninstalled Colorzilla before I set about all that tweaking. I tried to install it again as a Firefox addon, and I got this message :- 

XML Parsing Error: not well-formed
Location: chrome://mozapps/content/xpinstall/xpinstallConfirm.xul
Line Number 1, Column 11: p dateType_" + update.type);
----------^

Oh dear. Have I broken it ?

<Update>

I switched it off and on again... That worked. :)) Firefox runs and I can install Colorzilla.

Who would have thought a trusty old Windoze solution would be the answer?

However, the eyedropper still does not work. Now I have to find out how I Unpack (tar -xvzf firefox.....tar.gz).

I'm going to ask on the absolute beginners forum, cos I guess that is where I belong... :(

---

### Post by benste on 2008-03-31
Is the same way for hardy?? 
eyedropper mode does not work for me with firefox3

---

