---
title: "Unrecognised USB camera. How to access?"
date: 2009-01-02
forum: General Help
---

### Post by Morat on 2009-01-02
Can anyone help?

I have bought a cheapie kids digital camera from Loyds the Chemists. It's labeled as a "budz my first digital camera". My Ubuntu Gutsy does not recognise it as a USB drive so how can I access it? It came with a driver disk which of course only works on XP. Windows does not see it except through the driver application.

lsusb lists it as 
Bus 005 Device 006: ID 0979:0226 Jeilin Technology Corp., Ltd 

if that helps at all. I have no idea where to go from here.

Running Gutsy (7.10). Newb question: How do I actually confirm the exact version of the important systems?

--- Morat.

---

### Post by phonixor on 2009-01-02
have you tried installing cheese?
then just start cheese and see if that works..

---

### Post by Nathan_M on 2009-01-02
Is the disc that came with it actually a driver disc? Often they're just instruction manuals and extra software nobody actually wants. Does it actually say "driver" on the disc? If you look at the contents, is there anything to indicate there are drivers to be installed? If it isn't a driver disc, then the problem is probably something fairly simple. If it is, there might still be a solution, but I don't think I'd be able to find it on my own.

---

### Post by albandy on 2009-01-02
I've been searching and I found it in 
[http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
this means that it will be supported soon or possibly is supported in a newer kernel version (try upgrading to ubuntu 8.10)

---

### Post by Morat on 2009-01-02
Booted an 8.10 liveCD and lsusb now says:
Bus 003 Device 003: ID 0979:0226 Jeilin Technology Corp., Ltd JL2005A Toy Camera

So that is an improvement, at least it knows it is a camera and gives me the model number. I then downloaded gphoto2 and ran gphoto2 --auto-detect and it failed to detect.

I will have a look at cheese (whatever that is)... Done that. It said "No camera found". And it is a kids digital camera rather than a webcam so I don't think cheese is really the app I want. I need to get the photos from the camera onto the computer.

The disk that came with it does appear to install a driver and an application to use the driver. The only way I can access the camera from XP is through the supplied program. XP itself does not recognise the camera.

Many thanks for the replies so far. If I can't get this working under linux, Wifey may finally force me to revert to Windows, which would be a shame after 4 or 5 months of Linux. Any further suggestions?

--- Morat.

---

### Post by albandy on 2009-01-02
Try gtkam
sudo apt-get install gtkam

---

### Post by Morat on 2009-01-02
> **albandy said:**
> Try gtkam
sudo apt-get install gtkam

No luck, sadly. If I do [Camera]->[Add camera...], it gives me this great long list. The [Detect] button says "No cameras detected" and I don't know which in the great long list to try.

Since gtkam is just a front end to gphoto2 and gphoto2 --auto-detect fails to find it, I'm not surprised that gtkam also fails.

If I do gphoto2 --list-cameras | grep 2005, it comes back with nothing so I can only assume it is not yet supported though I did see it in a list somewhere that implied it was.

Maybe I should contact the gphoto2 developers and ask them, though I don't like to hassle oss developers since there is not much I can contribute in return for their hard work.

Are there any other tools I might be able to try?

--- Morat.

---

### Post by oxman on 2009-01-02
> **Morat said:**
> 

Are there any other tools I might be able to try?

--- Morat.

I have been trying to get a microscope camera working on my box. The procedure I followed is to find the chip set that the camera uses and see if there is a driver or kernel patch that will work on it.

---

### Post by Morat on 2009-01-02
Looking at versions and release notes etc, I find that I am not using the latest stable version.

apt-get install gphoto2 installed gphoto2 2.4.0 and libgphoto2 2.4.2. The latest stable versions of these are both 2.4.3 (from [http://sourceforge.net/project/showfiles.php?group_id=8874](http://sourceforge.net/project/showfiles.php?group_id=8874))

The release notes for libgphoto2 2.4.3 say
jl2005a driver:
   * Imported from TRUNK, for new small factor cameras.

so it looks like I need at least the latest version of libgphoto2. What is the best way of installing these? I am happy with sudo apt-get install but this is going to need more. Do I download the libgphoto2 package, 'tar -xvf' it, go into its folder and do 'make all' or something along those lines or is there a switch I can give to apt-get to tell it which version to install?

--- Morat.

---

### Post by andresmh on 2009-01-04
What worked for me was to enable ubuntu-backport and update-proposed and then do an update to the latest kernel and related modules.

---

### Post by Wolfhere on 2009-03-29
> **albandy said:**
> Try gtkam
sudo apt-get install gtkam

Worked for me. I could open my DCIM after installing gtkam. Prior to install, I coould browse and copy photos only through gspot

---

