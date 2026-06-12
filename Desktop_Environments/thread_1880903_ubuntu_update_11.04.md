---
title: "ubuntu update 11.04"
date: 2011-11-14
forum: Desktop Environments
---

### Post by piosif on 2011-11-14
I just updated to Ubuntu 11.04, and I think everything went well, but now that I try to start my computer, on my desktop there are no menu bars, neither on top nor on the bottom.
The only thing that the computer lets me do is to right click, making a small menu pop up, which lets me enter the my general files, which when I try to open don't do so.
Pressing F1 i can also reach a window that gives me information about Ubuntu 11.04, but with no contras so as to be able to do something.
Can somebody please tell me what to do?

---

### Post by Frogs Hair on 2011-11-14
Restart and log into Classic Ubuntu from the session list below the greeter box . The list will appear  after the user name is entered . 

If you have an Nividia graphics card you may need to install a the recommended proprietary driver from additional drivers to run Unity . During a clean installation  you would get a message indicating this if all is well  .   

Try to login to Ubuntu after installing the driver if this fails reboot ,  from the session list log into the recovery console and when the terminal opens run the following command .```
unity --reset
```

Wait until the task is done running and reboot .  See the link for tweaks .[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by piosif on 2011-11-15
Thanks a lot for your answer. I am in a different time zone, in Greece, and that si why I had not answered earlier.
The problem is that When I reboot, i am asked my name and password, and for some reason I have those two things wrong, so I can´t go anywhere beyond that. I don´t know if there is anything else I could do in order to make the menu bars appear, and be able to organize my computer again?
If not, could you tell me if it is possible to reinstall a Ubuntu update, and do things all over again? When I am on the desktop, doing a right click I can enter a small menu that can lead me to open up the Script folder. There I can see (but not open up) all my files. I can also go into a 
gnome2 folder, and also into a 
nautilus-scripts folder. this last one has two options:
MakePlymouth, and
MakeSplash.
In the gnome2 folder, I can open a document that automatically open up the Firefox browser, which gives me an access to the Internet.
I will appreciate any help you can offer me.

---

