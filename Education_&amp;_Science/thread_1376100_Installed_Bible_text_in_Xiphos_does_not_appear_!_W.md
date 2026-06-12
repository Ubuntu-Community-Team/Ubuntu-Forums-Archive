---
title: "Installed Bible text in Xiphos does not appear ?! What should I do ?"
date: 2010-01-08
forum: Education &amp; Science
---

### Post by jakenetch on 2010-01-08
My ubuntu is Wubi-installed Karmic Koala.
I'd installed Xiphos via Ubuntu Software Center and manually installed module from crosswire website.
Xiphos can detect package but only some topics did appeared.The whole text did not as you can see in attached picture.

I'd uninstalled both app & modules & involved directories, did it over and over. But result is the same.

What should I do ?

---

### Post by not_a_phd on 2010-01-08
have you tried installing the xiphos-data package? From the command line type:

```
sudo apt-get install xiphos-data
```

Or, find it in the Synaptic repo.

---

### Post by not_a_phd on 2010-01-08
Disregard last. xiphos-data is automatically bundled with xiphos.

I did notice from your screen shot that you are looking at a Thai KJV module. Have you tried installing a purely English module? If so, are you having similar problems?

When I installed xiphos (Karmic Koala also), I selected the English ASV biblical text through the crosswire ftp site and had no difficulties displaying. It came up Romans 8:28 just as yours is trying to do, but the text was displayed in the upper left corner.

---

### Post by jakenetch on 2010-01-08
> **not_a_phd said:**
> Disregard last. xiphos-data is automatically bundled with xiphos.

I did notice from your screen shot that you are looking at a Thai KJV module. Have you tried installing a purely English module? If so, are you having similar problems?

When I installed xiphos (Karmic Koala also), I selected the English ASV biblical text through the crosswire ftp site and had no difficulties displaying. It came up Romans 8:28 just as yours is trying to do, but the text was displayed in the upper left corner.

I did tried english version (but it's) of KJV.
My network was set to block ftp protocol so I have to install module via manual method.

Or ftp is the only way ?? :(

Anyway I'll try ASV ver. as you suggested and let you know the result ASAP. Thank you ;)

---

### Post by not_a_phd on 2010-01-08
Something else to investigate - make sure that you are configured to install your modules in your** /home/username/.sword** directory. 

To see how you are presently configured, click on the main menu **Edit|Module Manager** item (or just press F4).

Then, under the SWORD tree item, click on **Configure**. 

Make sure that the ***Install Destination*** is set to *Personal Area, for your use only:*

Take note of the actual directory that is indicated, as this is the install directory for your raw files. This is where xiphos will look for these raw files. It should say something like: /home/yourussername/.sword

If you pick *System Area for All Users* as your destination option, you will likely run into root-access issues that may prevent the book text data files from being installed properly. (Perhaps this is an issue for you?)

I have not ever had do to a manual book install, but one thing you could do is verify that the texts have made it into the required destination directory. If you peek in the directory:

/home/yourusername/.sword/modules/texts/ztext

folder, you should see a folder for each bible text that you have installed (e.g. you should see a ThaiKJV folder and an asv folder after you install it). In the asv (or ThaiKJV) folder, you should see several .bzz, .bzs, and .bzv files that have the actual text data. Perhaps these are missing in your install?

Also, in the directory:

/home/yourusername/.sword/mods.d

you should see a .conf file holding config data for each book that you have installed. 

Hope this helps.

---

### Post by jakenetch on 2010-01-10
I'd tried to install Xiphos in Persistent USB ubuntu Karmic and it worked out fine. No error or odd effect had happened.


Do I have to reinstall ubuntu in my harddisk instead ?? :(:(

---

### Post by not_a_phd on 2010-01-10
I have never messed around with the wubi installs myself. I have always preferred to set up a dual boot environment instead. It seems odd to me that you would have troubles with this application in one install environment versus another. Please make sure that you are installing your texts to your home directory (as I mentioned in the previous posting). Having issues with directory privileges is the only thing that I can think of right now that could possibly be causing your errors.

---

### Post by jakenetch on 2010-01-12
I'd ended all problems by reinstalling Wubi-installed ubuntu. And now Xiphos works in its way flawlessly.

Thanks not_a_phd :D

---

### Post by dnr1128 on 2010-05-08
I've got xiphos installed.  It worked fine in karmic, but now that I have lucid, the strongs modules don't seem to work properly.  When I click on a number, it displays in the window on the right, but the definition doesn't appear.  When I minimize then maximize, it looks like the windows on the right and bottom that should have the strongs definitions in them have crashed.  I've tried reinstalling the modules, but it hasn't help.  any ideas guys?

---

### Post by nerdy_kid on 2010-05-08
maybe try bibletime?  its a kde app, but should integrate pretty well.

---

### Post by dnr1128 on 2010-05-09
Does it have different versions, as well as strongs number integration into the text and hebrew/greek dictionaries?

---

### Post by nerdy_kid on 2010-05-09
> **dnr1128 said:**
> Does it have different versions, as well as strongs number integration into the text and hebrew/greek dictionaries?

eh i dont know about the number integration, probably.  It's another sword front end, so it has a gazillion different versions.  Give it a shot :)

---

