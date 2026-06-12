---
title: "Screen Res. Problem"
date: 2008-10-25
forum: Desktop Environments
---

### Post by Xero117 on 2008-10-25
I have a problem with the Screen res on Ubuntu 8.10 Beta and well I enable my video card which I have a nVidia GeForece FX 5200 and well the only screen res. I have is 800x600 like how can I make it go higher than that? like on Windows I have it at 1024x768 and I want it like that.. how can I do that?

Thanks,
Xero117

---

### Post by Pccw9 on 2008-10-25
To do this, go to system>prefences>Screen Resolution and change it there

---

### Post by Xero117 on 2008-10-25
it won't let me change it...I have only 800x600, 640x480, 400x300, 320x240. but nothing else...

---

### Post by Neo Adventist on 2008-10-25
For my Ubuntu 8.04 install, I had to change my monitor type from "Plug and Play" to "LCD Screen 1280x1024" 

Try that.

---

### Post by hictio on 2008-10-25
I'm sorry, when you say that you:
> 
enable my video card which I have a nVidia GeForece FX 5200


does it mean that you donwloaded the NVIDIA driver?
I'm not using 8.10, but on 8.04,not until I have installed the driver I wasn't able to sue my laptop's native resolution.

---

### Post by penbrock on 2008-10-26
I just installed also and have the very some issue.
:confused:

---

### Post by penbrock on 2008-10-26
> **Neo Adventist said:**
> For my Ubuntu 8.04 install, I had to change my monitor type from "Plug and Play" to "LCD Screen 1280x1024" 

Try that.

Sorry to be a newbie but just where do you change the monitor settings to 1280x1024 from plug and play?

---

### Post by hictio on 2008-10-26
> **penbrock said:**
> I just installed also and have the very some issue.
:confused:

But you rebooted the Ubuntu box after installing the drivers, right?
Also, which drivers are you installing? On the 2 occasions I installed Ubuntu (8.04, again) on boxes with NVIDIA cards, the ones that worked -that only worked actually- were the ones that Ubuntu provided.

---

### Post by penbrock on 2008-10-26
> **hictio said:**
> But you rebooted the Ubuntu box after installing the drivers, right?
Also, which drivers are you installing? On the 2 occasions I installed Ubuntu (8.04, again) on boxes with NVIDIA cards, the ones that worked -that only worked actually- were the ones that Ubuntu provided.

I have not gone and gotten any drivers from anywhere. The system did change one the first time I logged on. Under System -> Admin -> Hardware Drivers   it only shows " Nvidia accelerated graphics driver (latest cards)  and checked enabled.

---

### Post by Xero117 on 2008-10-26
well I downloaded the driver and enabled it, when I login the screen res. is too big...and I can't really do anything...so idk what to do

---

### Post by hictio on 2008-10-26
> **Xero117 said:**
> well I downloaded the driver and enabled it, when I login the screen res. is too big...and I can't really do anything...so idk what to do

Have you looked on "System -> Preferences -> Screen Resolution"? Is there any resolution listed there?

---

### Post by Neo Adventist on 2008-10-27
> **penbrock said:**
> Sorry to be a newbie but just where do you change the monitor settings to 1280x1024 from plug and play?

***I'm going to assume you're using Ubuntu 8.04***
***Mind, my video card is a UniChrome Pro IGP***
***This may or may not work you you***

Go to System-->Preferences-->Main Menu

On the left side of the pop-up window, under Applications, click "Other"

On the right side of that same pop-up, click the checkbox by "Screens & Graphics" and close the window.

Go to Applications-->Other-->Screens & Graphics;   enter your password

Under the "Screen" tab, you should see "Model:  Plug & Play".  Click on "Plug & Play"

Under "Manufacturer" click "Generic" and under "Model" click on "LCD Panel" with the maximum resolution you want. Click "OK"

Click "Test"

If that resolution test fails, try the next smaller resolution.  Setting a resolution too high may crash the X video server, so be careful.

---

