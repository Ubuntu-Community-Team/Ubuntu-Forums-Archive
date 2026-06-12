---
title: "Compiz effects not worjing"
date: 2011-04-05
forum: Desktop Environments
---

### Post by hijiz on 2011-04-05
on my old ubuntu i used compiz for window management. now i installed compiz in my new laptop however none of the efects work i tried using expo, wobly windows and more but nothing happens. how do i fix this?

---

### Post by 3Miro on 2011-04-05
First go to System -> Prefs -> Appearance and check the Desktop Effects tab to make sure you are not running "None".

It is possible that your hardware doesn't support the effects, can you give us the model of your video card?

---

### Post by hijiz on 2011-04-06
Something wierd happens when i switch the effects from none to normal or extra and close nothing happens and when i open apearence again none is selected. 

Also im sure my computer suports effects i used compiz on it before i upgraded to 10.10 and effects worked perfectly.

---

### Post by 3Miro on 2011-04-06
> **hijiz said:**
> Something wierd happens when i switch the effects from none to normal or extra and close nothing happens and when i open apearence again none is selected. 

Also im sure my computer suports effects i used compiz on it before i upgraded to 10.10 and effects worked perfectly.

First thing to do is to go to the terminal and type:
```
compiz --replace
```
Then look at the error message. It may be the case that while you can run compiz, some of its extra effects are not supported by your video card. Try to disable some of the animations in CCSM.

Another thing to look at:

What is your video card? You should go to System -> Admin -> additional Drivers and make sure the drivers are installed properly (like if you have Nvidia video card). If the driver is already installed, then you should reinstall it:

1. Remove/Deactivate the driver.
2. Reboot.
3. Activate the Driver.
4. Reboot.

---

### Post by hijiz on 2011-04-06
Thanks compiz --replace gives me the following.
> emilio@emilio-Aspire-one:~$ compiz --replace
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
emilio@emilio-Aspire-one:~$ 


---

### Post by 3Miro on 2011-04-06
You should reinstall Compiz-Config-Settings-Manager, something went wrong there. Also, make sure you have Windows Decorations enabled and you have the decorator command setup as:
```
gtk-window-decorator --replace
```

Also, what video cars is this?

---

### Post by hijiz on 2011-04-06
I use an acer aspire one so i think my card is Mobile Intel(R) 945 Express Chipset Family (Microsoft Corporation - Prerelease WDDM 1.0) (Intel(R) GMA 950), but im not sure.

---

### Post by 3Miro on 2011-04-06
> **hijiz said:**
> I use an acer aspire one so i think my graphics card is Mobile Intel(R) 945 Express Chipset Family (Microsoft Corporation - Prerelease WDDM 1.0) (Intel(R) GMA 950), but im not sure.

OK, there is no driver to reinstall, however, Intel video is somewhat weak and probably doesn't support all of the fancy effects. Reinstall CCSM and then check the windows decorations plugin. Try it again and post the output here.

---

### Post by hijiz on 2011-04-06
ok i reinstaled compiz when i add the command 
> gtk-window-decorator --replace 
nothing seems to happen. although once it did install the compiz gnome pakage i didnt copy the outcome.

---

### Post by realzippy on 2011-04-06
..maybe your card is blacklisted.
Run:
```
SKIP_CHECKS=1 compiz
```

..does compiz start?

---

### Post by hijiz on 2011-04-06
No compiz dosnt open and this is the output.
> Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/emilio/.compiz/session/10ab9cbeeb390d110f130201323917621300000010600000"


---

### Post by 3Miro on 2011-04-06
> **hijiz said:**
> ok i reinstaled compiz when i add the command 
 
nothing seems to happen. although once it did install the compiz gnome pakage i didnt copy the outcome.

This command should be entered inside CCSM in the Windows Decoration plugin. There is a place there to put the command. Then you should try tot start compiz again (from terminal with compiz --replace) then give us the error.

---

### Post by 3Miro on 2011-04-06
> **hijiz said:**
> No compiz dosnt open and this is the output.

Go to Home -> Places, then hit Ctr + H and find 
```
.compiz/session/10ab9cbeeb390d110f130201323917621300000010600000
```

then delete the file.

Then try again.

---

### Post by realzippy on 2011-04-06
*Mobile Intel(R) 945 Express Chipset Family (Microsoft Corporation - Prerelease WDDM 1.0) (Intel(R) GMA 950), but im not sure.*

..to be sure,run:
```
lspci |grep VGA
```

Also suggest to reinstall compiz.
If you still having trouble,run [forlong's script]("http://forlong.blogage.de/entries/pages/Compiz-Check").

---

### Post by realzippy on 2011-04-06
Sorry for confusing the thread.Will be out now and watch things going...

---

### Post by hijiz on 2011-04-07
Thanks to every one miro3 thank you especialy you were right problem solved.

---

