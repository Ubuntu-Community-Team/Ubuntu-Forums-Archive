---
title: "Logitech Quickcam for Notebook  driver and software"
date: 2008-01-24
forum: Dell  Ubuntu Support
---

### Post by trungpt on 2008-01-24
Hello all,

I have installed Ubuntu 7.10 on my Dell laptop (xps M 1210 Model).
But the logitech quickcam seems not work. Do anyone show me how to install driver?
 Is there any quickcam viewer software in Ubuntu like Logitech Quickcam Software in Win Vista? 

Thanks,
Trung

---

### Post by linuxwizard on 2008-01-25
Try using Ekiga see if webcam get detected/works.

---

### Post by m94mni on 2008-01-25
Ekiga or cheese will show you if it works.

Unfortunately, many proprietary applications have only limited support for some cameras (Marratech, flash, etc.)

I have had luck with the latest skype beta (2.0.0.27) though.

---

### Post by trungpt on 2008-01-25
I tried Ekiga, bu it does not recognize the quickcam.

---

### Post by linuxwizard on 2008-01-25
trungpt
Did you see a error message ? Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there see what happens. If still nothing post results of command > lsusb

---

### Post by trungpt on 2008-01-27
that's good!

The Ekiga application now can detect the quickcam after I changed some setting. But the color seems not good. Do you know why? 
in Ubuntu do we have any software that can detect and control quickcam like face detection?

Thanks
Trung

---

### Post by linuxwizard on 2008-01-28
Open Ekiga > Click on  View > View mode > full view > Now under keypad click on video > now you can change settings, color, brightness, etc. Just work with the settings.

---

### Post by fragos on 2008-01-28
Proper support of color control depends on the chipset in the video camera.  The driver used in Ubuntu supports 100's of devices thanks to the French programmer that created it and keeps it up to date.  I have the same webcam and the same issue.

---

### Post by trungpt on 2008-01-28
The same quickcam works very well in win vista with [COLOR="Red"]Logitech Quickcam software[/COLOR]. Is there any software like that in Ubuntu?

Trung

---

### Post by fragos on 2008-01-28
Here's the site of the driver author: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
He appears to have a newer version than that included with Ubuntu.  He has a lot of documentation and campatibilty information.  Perhaps that will help you.  I'm going to install this latest driver myself.

---

### Post by trungpt on 2008-01-30
I saw serveral packages include: spcagui, spcaview...
So which package I should install in my pc? 
Could you pls give a further help?

Thanks,
Trung

---

### Post by fragos on 2008-01-30
Ekiga that's part of the default Ubuntu will work with the web cam.  I never tried any of those viewers but I would think any of them would work since they come from the guy that wrote the driver.

---

### Post by jeff001 on 2008-07-09
Hi 

I am absolutely a beginner in Ubuntu - I have downloaded this but cannot install it as there is no .exe file - I have read something about using target.gz in a terminal but have not got a clue apart from opening the terminal from Applications Accessories...

If there is a forum that cater for peeps like me I will :guitar: 

Thanks

J

---

### Post by fragos on 2008-07-09
Compiling is a last resort and although an option, rarely necesssary. The 1st thing to do is check if this package is already availble using the "synaptic package manager". Next look for a ".deb" package in places like [http://getdeb.net](http://getdeb.net). If you do need to compile do the following.

First you'll need to open the "synaptic" and do a search for "build-esential". Mark this package for install and click the "Apply" icon. You now have most of what's necessary for any compile. Right click the tar ball file and selecte "Extract Here". A folder will be created with the contents of the tar ball. Look in the folder and you will see text files like "read.me" and "install". Click those to examine their contents. Most likely you will see a file "configure". Open a terminal and "cd" to the folder you created. In that terminal window, run the following in that terminal". The last one will prompt you for a password, enter yours.

./configure
make
sudo make install

---

