---
title: "emachines t2245 modem"
date: 2008-12-21
forum: General Help
---

### Post by dvotruba on 2008-12-21
First, Thanks for the great OS and support, I do not like Windows as it is not user friendly.

I am building old systems to give to needy kids.

I have an emachines t2245 running UBUNTU GREAT, original dial up modem, and i can not get it to find or recignise the modem. I want to set it up for free dial up internet service for a needy family.

Thanks
Doug

---

### Post by AnonCat on 2008-12-21
Does that emachines contain a smartlink compatible modem?  I installed linux on an emachines T2895 and managed to get the modem working after some hair pulling, but I'm not sure if the model you mentioned uses the same modem.  

You might try visiting this page for more info:

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

I could find the driver package I compiled for the emachines I used and give it to you if you wish.  I'll try to find a link to it real fast.

---

### Post by AnonCat on 2008-12-21
Below is a link to the driver packages (if it's smartlink compatible).  Let me know if you have any further questions.  Also, I noticed that these drivers make the nvidia drivers very unstable on the emachines I used for some reason.  You might end-up having to use the onboard video if you want to use the modem. 

[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/)

---

### Post by dvotruba on 2008-12-22
Thanks for your help I will give it a try

---

### Post by dvotruba on 2008-12-22
I don't know how to copy the file to the root and then exicute it?:P

---

### Post by AnonCat on 2008-12-23
Which files specifically didn't run?  Have you installed slmodemd and tried typing the following into the terminal (after going into the directory that holds the modem files of course):

sudo mknod -m 600 /dev/slamr0 c 242 0
sudo modprobe ungrab-winmodem
sudo modprobe slamr
sudo slmodemd -c YOUR_COUNTRY /dev/slamr0

That should be all it takes to make the modem work initially though you'll have to edit the wvdial.conf file in /etc with the passwords, etc that you need to login to the ISP.  It's been awhile since I've used that driver.  Let me know if something isn't clear and I'll reinstall the drivers so I can give you better instructions.  Also, let me know which kernal version you downloaded.  I notice that sometimes they forget to include files in the archives.

---

### Post by AnonCat on 2008-12-23
I'm not sure which steps you've already done, but try this and see if works without error (I'm assuming you're from the USA).

1. navigate into the directory holding the driver files you downloaded and load the terminal to paste the following:

2. sudo apt-get install sl-modem-daemon 

2. sudo mknod -m 600 /dev/slamr0 c 242 0

3. sudo modprobe ungrab-winmodem

4. sudo modprobe slamr

5. sudo slmodemd -c USA /dev/slamr0

if step 5 doesn't work try these alternatives

sudo slmodemd -c USA /dev/slamr0 hw:1

sudo slmodemd -c b5 /dev/slamr0

sudo slmodemd -c b5 /dev/slamr0 --alsa hw:1

If these things work the next step is to configure wvdial which is pretty straight forward.  If none of this works get back to me and I'll install the drivers on my system to see where I went wrong.

---

