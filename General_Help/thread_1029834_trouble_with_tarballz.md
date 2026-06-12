---
title: "trouble with tarballz"
date: 2009-01-03
forum: General Help
---

### Post by Zaragon on 2009-01-03
I am a neophyte Ubuntu user and I just installed a new sound card.  Creative actually has a linux driver for it which I downloaded.  I was able to extract it XFiDrv_Linux_Public_US_1.00.tar.gz => folder on desktop named XFiDrv_Linux_Public_US_1.00  I am absolutely stuck on where to go from here though.  I would welcome any help y'all can give me on subsequent steps.  Thanks.   Zack

---

### Post by taurus on 2009-01-03
Is there a README or INSTALL that tells you what to do next?

What's the output of this command from a terminal?

```
ls -la ~/Desktop/XFiDrv_Linux_Public_US_1.00
```

---

### Post by Zaragon on 2009-01-03
There is a readme:  It just says "Go to source directery and use make install"  I don't know enough to find that useful however.

---

### Post by zenmatrix on 2009-01-03
Get the output but usually with installers theres somesort of perl script(file.pl) or just a file that says setup or installer. for example if you install vmware-server its vmware_install.pl but you have to go to a command line and get into the folder and type ./vmware_install.pl to get it to work

---

### Post by zenmatrix on 2009-01-03
for make install have to open the terminal and open the folder you extracted and type make let that finish then type install from wht you posted. you can try both at once by typing

***make&& install***

---

### Post by taurus on 2009-01-03
> **zenmatrix said:**
> for make install have to open the terminal and open the folder you extracted and type make let that finish then type install from wht you posted. you can try both at once by typing

***make&& install***
:confused:

I think you mean

```
sudo make install
```

---

### Post by Zaragon on 2009-01-03
Y'all are assuming a greater level of sophistication than I possess.  I think I should go study some terminal commands and then come back and ask my question again.  This should create less damage to both my forehead and my screen.  Thanks for the help though.

Zack

---

### Post by zenmatrix on 2009-01-03
sorry did forget the sudo its needed for to get the program to compile. If this seems too much try to find a .deb they are already compiled programs

---

