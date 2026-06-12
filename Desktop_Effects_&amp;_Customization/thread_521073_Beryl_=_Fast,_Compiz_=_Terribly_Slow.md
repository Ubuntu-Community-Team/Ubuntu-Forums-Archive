---
title: "Beryl = Fast, Compiz = Terribly Slow"
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by neo65536 on 2007-08-09
I've been messing around with compiz on a Dell Optiplex 960.  It has an integrated Intel 82845G/GL graphics adapter and 1.5GB RAM.

Having switched from Beryl, I was extremely disappointed in the speed of compiz.  I have read many forums on how to optimize the i810 driver (using Intel's version,downloading the latest compiz, etc.) - nothing works.  I know it is just eye candy, but it's fun...

I have since completely removed compiz and reinstalled beryl from scratch.  It is blazing fast!!!  If the two projects have merged, they've certainly degraded the product.

Has anyone with an Intel 82845G/GL (Brookdale) been able to make compiz perform at any decent speed?

Thanks!

---

### Post by Alexander2007 on 2007-08-09
I know compiz is slow but somehow compiz-fusion is faster and less buggy. They fixed many bugs cause I hardly get crashes with it. Try it.

Open terminal window and type: 
```
sudo apt-get remove compiz-core desktop-effects compiz compiz-gnome 
```


Then type: ```
sudo gedit /etc/apt/sources.list
```

Add the following to the bottom:                                  
 ```
# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository    
 deb http://download.tuxfamily.org/3v1deb feisty eyecandy         
 deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy     

```

Save and close the file. 

 
Add Trevino's Key: 
SEE ATTACHMENT!
Open it and save it as Trevino Key (without the ".txt" extension)
Then go to "System > Administration > Software Sources"
Goto "Authentication" tab and import the key you saved. 

Download and install Compiz-Fusion: 
```

sudo aptitude -y update 
sudo aptitude install compiz compiz-gnome \ 
compizconfig-settings-manager compiz-fusion-plugins-extra \ 
compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf 
```



Then 
```
sudo aptitude upgrade 
```



To run Compiz-Fusion (ALT+F2): 
```
compiz --replace 
```



To replace Metacity (ALT+F2): 
```
metacity --replace 
```

---

### Post by neo65536 on 2007-08-09
Alexander,

Thanks!  I guess I should have been more specific, I did attempt to use compiz fusion and have completely removed all compiz packages using syncaptic.  Unfortunately, I have done all of this with no success.  I am hoping that someone will post something specific for my video adapter because that is what I think is the problem.  Simply dragging windows around on the desktop is choppy using compiz fusion.

Tom

---

### Post by xl_cheese on 2007-08-09
I agree.  Compiz Fuzion is stupid slow.

Maximizing and minimizing windows should not hesitate like they do.

---

### Post by bubba2120 on 2007-08-09
i have the same adapter, (well similar) its an instel 82865g integrated on my dell. i tried my nvidia geforce4  mx 4000, that didnt work at all. but back to the point. i have succesfully installed compiz fusion, everything is fine. im not sure what your problem could be. there is nothing choppy about mine at all, except every once in a while it gets choppy on transparent cube if im running a lot of apps. i used [This]("http://ubuntuforums.org/showthread.php?t=481314") tutorial if it helps

---

### Post by xl_cheese on 2007-08-09
I installed the same way.

I have a pretty fast system too.

---

