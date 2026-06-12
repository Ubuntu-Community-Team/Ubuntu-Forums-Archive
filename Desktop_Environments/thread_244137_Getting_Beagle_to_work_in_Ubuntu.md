---
title: "Getting Beagle to work in Ubuntu"
date: 2006-08-26
forum: Desktop Environments
---

### Post by rjdohnert on 2006-08-26
I have only been able to get Beagle working on my desktop, laptop is a no go.  Anyone had any luck with getting beagle to work?  Its an 800mhz Intel processor so I dont know if speed has much to do with it.

---

### Post by janhenderson on 2006-08-26
> **rjdohnert said:**
> I have only been able to get Beagle working on my desktop, laptop is a no go.  Anyone had any luck with getting beagle to work?  Its an 800mhz Intel processor so I dont know if speed has much to do with it.

I'm no expert but I had problems with beagle and here's how i fixed them. 

First, unsinstall the one you have, including its configuration files 

sudo aptitude purge beagle 

then, go to your home folder and delete a folder called .beagle (dotbeagle). It will be hidden because of the dot. If you are using nautilus then do this

press ctrl-l and then you'll see a location bar. In that type 

/home/<your-username>/.beagle

and delete the contents 

If you're using kubuntu, then you do just the same using konqueror

delete all the contents in the .beagle directory 

now, you can reinstall beagle 

sudo aptitude beagle 

ok, if you're using ubuntu go to 

    * System -> Preferences -> Sessions
    * Sessions 

Startup Programs Tab -> Add/Edit/Delete

and enter the following 

beagled 

Which stands for beagle daemon, make it start at startup when you log in into ubuntu. Now if you want it to start now, before you log out and log in again, just type in beagled at a command line and type enter, and it will start in the background. Alternatively, If you want it to start in the foreground so you can see what it's doing, do type in the following 

beagled --fg --debug

and in case, any time, you get a message saying beagled is already running, you can replace it 

beagled --replace 

and you can combine those two above

beagled --replace --fg --debug

If you're running KDE this is how to start beagled on startup

use conqueror to go to /home/<your-username>/.kde/Autostart 

right-click and choose create link to application... 
in the dialog that appears type under the general tab: beagled, then switch to the application tab, and type 

Name: beagled 
Application: beagled

Then click OK. You should see an icon that says beagled.desktop now in that folder

If you're using kde then get kerry 

sudo aptitude install kerry 

and use kerry-beagle in kde for your searches

---

### Post by janhenderson on 2006-08-27
> **rjdohnert said:**
> I have only been able to get Beagle working on my desktop, laptop is a no go.  Anyone had any luck with getting beagle to work?  Its an 800mhz Intel processor so I dont know if speed has much to do with it.

Did it work for you? Please let the forum know so others who have a similar problem would know if these instructions were useful or not.

---

### Post by ralanyo on 2006-10-20
I did this and it worked.  Well kinda... I cannot run the "beagled" command. It gives me the following error.

*Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.*

However,  I have found that If I manually add the paths to be included for the index and then run.

*beagled --fg --debug*

It indexes them.

I am kind of new to beagle, and not sure this is the way the program is designed to work. However, it is working.

I thought that beagle was supposed to automatically index everything.

If anyone has any other suggestions, I am open to them.

Thanks

---

