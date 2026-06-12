---
title: "Gnome3 stoped working after i tried to make dual monitor with Nvidia"
date: 2012-07-03
forum: Desktop Environments
---

### Post by NaGeL on 2012-07-03
hello.
I just installed ubuntu 12.04 64bit on my MSI GX720 lap top that has NVidia Geforce 9600m GT. i instaled the Nvidia drivers. i dont like Unity so i installed gnome-shell which worked quite nice.  After that i tried to configure my external monitor(external VGA port) through Nvidia X control panel, which surprisingly worked till an extend, but gnome3 reverted to the classic gnome. 
I tried 
```
sudo apt-get remove gnome-shell
```than install it again with
```
sudo apt-get install gnome-shell
```but its still broken

can someone help me get it back?

---

### Post by msammels on 2012-07-03
Hey NaGeL,

how did you install the nVidia drivers? Did you do it through the restricted drivers section? There could be any number of things causing this - your card might not be able to handle the graphics of GNOME3. Also, in the login screen (assuming you still use LightDM), have you tried setting your shell back to GNOME, making sure it's not on GNOME (Classsic)?

(It probably already is, but better safe than sorry).

---

### Post by NaGeL on 2012-07-04
> **msammels said:**
> Hey NaGeL,

how did you install the nVidia drivers? Did you do it through the restricted drivers section? There could be any number of things causing this - your card might not be able to handle the graphics of GNOME3. Also, in the login screen (assuming you still use LightDM), have you tried setting your shell back to GNOME, making sure it's not on GNOME (Classsic)?

(It probably already is, but better safe than sorry).

Yes I instaled throught resrticted driver section. At first i instaled the second option that appers for NVidia drivers(updates after release? dont know exact english translation, i'm hungarian. the other option was "current") and after that i installed Gnome3. It worked marvelously. i fell in love with it. But after playing around with Nvidia's controler to set up my external VGA monitor to EXTEND the lap top's monitor(just like i use with windows.) its broke.
I tried reinstaling, dint work. tried to reinstal Nvidia drivers didnt work... change the nvidia drivers to "current" didnt work... restore the X11 config file from back up didnt work...

and yes if that LightDM is tehe default in ubuntu 12.04 than yes i am still using that , and I'm quite sure that i'm not using GNOME(classic)

---

### Post by NaGeL on 2012-07-08
hello? someone please help.
I dont want to reinstall the whole OS ...

---

