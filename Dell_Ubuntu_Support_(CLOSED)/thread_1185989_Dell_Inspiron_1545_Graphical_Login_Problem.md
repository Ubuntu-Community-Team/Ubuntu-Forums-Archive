---
title: "Dell Inspiron 1545 Graphical Login Problem"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cuthbeorht on 2009-06-12
Hi All!

I am somewhat of a linux noob and I have a problem with my current installation.

I have a Dell Inspiron 1545 with the ATI HD 4330 Graphics chipset.  I installed Ubuntu on it as soon as it arrived at my door.  For a while it worked fine and now, when I booted it this morning, once I get to the login screen, it shows garbled graphics.  As far as I know, I had all the updated ATI drivers.  I really have no idea as to what the problem might be.  I have scoured Google and these forums and haven't found anything.  Any thoughts would be highly appreciated.  If you need more info, lemme know.  I don't know what would help diagnose the problem.  Thanks.

---

### Post by coffeeaddict22 on 2009-06-13
Boot up to the GRUB menu (where you select your OS), choose the recovery option, then in the menu that comes up select "Fix my Graphics" and see if that sorts it.

---

### Post by Cuthbeorht on 2009-06-13
> **coffeeaddict22 said:**
> Boot up to the GRUB menu (where you select your OS), choose the recovery option, then in the menu that comes up select "Fix my Graphics" and see if that sorts it.

Tried that, as well as all the options there to see if it would help.  Nothing does...:(  Is it a Graphics card or driver issue or is it an entirely different animal?

---

### Post by ddrichardson on 2009-06-13
Have you had a recent driver update? Is the display only garbled on the GDM screen?

---

### Post by Cuthbeorht on 2009-06-13
> **ddrichardson said:**
> Have you had a recent driver update? Is the display only garbled on the GDM screen?

For the driver update, no.  As for the GDM screen, I'm not sure what that is...  Can you clarify?

---

### Post by ddrichardson on 2009-06-13
The login screen.

---

### Post by Cuthbeorht on 2009-06-13
I'm sorry.  Please excuse my ignorance.  The GDM screen is garbled.  It looks like snow on a TV on an empty station.  The live version works fine.

---

### Post by ddrichardson on 2009-06-13
Can you login and if so is the display then working?  If not then I suspect you have a driver issue and should be able to fix it by reconfiguring Xorg.```
sudo /etc/init.d/gdm stop
sudo -dpkg-reconfigure xserver-xorg
```You'll need to switch to a virtual terminal (CTRL-ALT-F2).

I'm going to bed but someone should pick up the thread, if not I'll check in the morning.

---

### Post by Cuthbeorht on 2009-06-15
> **ddrichardson said:**
> Can you login and if so is the display then working?  If not then I suspect you have a driver issue and should be able to fix it by reconfiguring Xorg.```
sudo /etc/init.d/gdm stop
sudo -dpkg-reconfigure xserver-xorg
```You'll need to switch to a virtual terminal (CTRL-ALT-F2).

I'm going to bed but someone should pick up the thread, if not I'll check in the morning.

it worked!!!!  i did it and reinstalled the ati drivers.  Thanks a bunch!!!!!!

---

### Post by pkchill88 on 2009-09-15
i have exactly the same specifications as the one mentioned above. 
My problem is in a way different. I havent been able to get proper drivers. I could not find the drivers for HD 4330 Mobility radeon anywhere in ATI/AMD site. 

The problem now is that my screen looks stretched due to an improper screen width ratio. I do not get an option to change the screen resolution. This means that the drivers are not present.

Can someone please help me out ?!!?

---

### Post by pkchill88 on 2009-12-27
hi, i actually solved my problem with the help of a few friends.
It might seem a bit trivial. but still i am a linux newbie and many might find this useful.

For all ATI drivers, u can visit this link [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and download the drivers corresponding to your ATI graphics card. 

First find out if ur system is 64bit or 32 bit. Then choose the corresponding option. Next it asks for the category to which ur graphics card belongs to. Mine came with the laptop. Hence i chose Mobility Radeon. Then i know my card is in 4000 Series, hence chose that option. Download the Script that installs the driver.

U can run it in shell using "sh ./filename" . This opens a GUI window after sometime. It somehow did not display the text inside the buttons. Trial and Error, i clicked all possible button combintions and finally installed it. Now i went to System-->Hardware Drivers. Activated the recently downloaded Driver. After Rebooting the system, Finally i got what i wanted.  Thanks to my friends for helping me out :)

---

