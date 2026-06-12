---
title: "Help me start Ubuntu back again !"
date: 2006-02-26
forum: Desktop Environments
---

### Post by index_0@ya.com on 2006-02-26
Hi thr,
      I re-installed Ubuntu after corrupting sources.list in apt dir for dapper upgrade . This time, just after installation , i made apt-get dist upgrade. Evry thing went up but at the last  at 99% somethin went wrong, and one of the packages was skipped .

Then somehow , i got it installed all packaes, from synaptic , and rebooted.

Evry thing was fine until X starts, 
The log file report's 
"could not load driver kbd" 
no module  called kbd 
no module defined for Core keyboard 
"could not load driver mouse" 
no module called mouse


I fixed an issue with font problem before,  from another thread, but  for this problem i searched forums and intenet but in vain, 

someone pls help ,
i want to see XGL stuffs in my system too.
and by the way , i copied log file to Windows  pC using cp command , but i could not find it !

---

### Post by index_0@ya.com on 2006-02-27
Hey guys, 
    i am really suppresed from no reply to my question !, 
   atleast if u can link me another thread , it ll be good , 
   i couldnt start my system , i dont have a linux expert nearby too ,
  

pls help 
Thx in advance

---

### Post by RAOF on 2006-02-27
What does your sources.list look like now?  Have you tried running "sudo apt-get install xserver-xorg" to get all the xserver stuff installed?

---

### Post by index_0@ya.com on 2006-02-27
i tried  sudo dpkg-reconfigure xserver-xorg ,

after all when i make a dist upgrade ,y would things like this shld happen ????

---

### Post by Mustard on 2006-02-27
Quite often when there is a failure in the installation apt-get will will instruct you to try the command below. in the error message...

```
sudo apt-get -f install
#I think this mean something like fix the missing/broken bits. :)
# Not really sure..hehehe
```

Other than that I would try..

```
sudo apt-get install ubuntu-desktop
#ubuntu-desktop is the metapackage that refers to all the dependencies 
#of the default ubuntu desktop setup
```

This should complete the install of ubuntu-desktop. *finger crossed*


Hopefully one of these commands will help you advance your install.

If you get X installed then you might need to reconfigure xorg again with...

```
sudo dpkg-reconfigure xserver-xorg
```

To attempt to start the xserver again after reconfiguring..

```
startx
#starts the xserver
```

---

### Post by Mustard on 2006-02-27
[QUOTE=index_0@ya.com]i tried  sudo dpkg-reconfigure xserver-xorg ,

after all when i make a dist upgrade ,y would things like this shld happen ????[/QUOTE]

Well, you are upgrading to a development version (Dapper), which may well be broken at the time you do the dist-upgrade.  So basically its not finished in its development yet and is not a stable final version. Its not due for final release until the June is it?  Hiccups are part and parcel of installing a development version.

If you want a stable version, then you should stick with Breezy Badger.

---

### Post by index_0@ya.com on 2006-02-27
Ok .. i agreee tht it is still in development ,,
then how come , it 's fine with the others who have completed with dapper install !!! 

y this unfortunate situation for me !!!
i dont own free internet conn anyway,, 
!!!

---

