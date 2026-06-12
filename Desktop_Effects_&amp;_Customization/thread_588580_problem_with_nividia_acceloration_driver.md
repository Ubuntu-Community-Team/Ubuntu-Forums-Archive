---
title: "problem with nividia acceloration driver"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by snickers295 on 2007-10-23
i was wanting to try the compiz effects but when i enable the nividia acceleration driver and reset X my screen resolution goes down to a max of 800x600 but i need 1280x1024. if i uninstall the driver the resolution does back to normal.
please help.
i have a NV11 [GeForce2 MX/MX 400] and a gateway ev500.

---

### Post by darkazurka on 2007-10-23
Oh my. You got exactly the same card as me! GeForce2 MX/MX 400 . It worked (Desktop effects compiz-fusion) just after I installed the 7.10 system but, after I installed various apps and stuff, now it's no longer working (I can't say it's because I installed various stuff that is the problem), and I have the same problem as you. When I go "System->Administration->Screens and Graphics" it shows:
Model: Plug 'n' Play
Resolution: 800x600 at 73 Hz
..and I can only choose between 640x480 and the 800x600 I got now. This happened after I tried to "fix the system" by typing as root "dpkg-reconfigure xserver-xorg". Now that might have messed up the system even more...don't know what to do, I want my 3D acceleration back , just as after I installed 7.10 Gutsy.

---

### Post by snickers295 on 2007-10-23
thats my exact problem except when i did a fresh install i tried to enable the effects then it mess up the resolution.
maybe we will both get help from this thread.

---

### Post by darkazurka on 2007-10-23
Ok. When I had this new installed Gutsy Gibbon system, when I tried to enable the effects  (in System->Preferences->Appearance) , it asked me to enable some sort of nvidia driver, I think it gave me more than 1 option to choose from.

Now it doesn't say what I should do, but just gives me the message: "Desktop effects could not be enabled" . Then it switches back to "None".

---

### Post by darkazurka on 2007-10-31
Now , after I reinstalled Gutsy 7.10, my nvidia geforce 2 mx 400 , card works with 3D acceleration and my desktop effects can be enabled too. It must be some software I installed or some changes I made manually to the xorg.conf file that screwed everything up.

---

