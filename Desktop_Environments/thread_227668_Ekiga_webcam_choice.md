---
title: "Ekiga webcam choice"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Blairboy on 2006-08-02
I'm really diggin hard on ekiga, but I don't have a webcam.  I had my eye on either the Logitech quickcam ultra vision or the quickcam orbit MP.  I looked around quite a bit but I couldn't find whether either of these are supported in ubuntu.  Anyone know about compatibility or if not, a pretty high end webcam that's similar to those two?  Thanks a bunch.

---

### Post by loell on 2006-08-02
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")
this driver is inluded in ubuntu dapper by default
and guess what there is orbit/sphere mp or chose from those models in the list :)

---

### Post by Blairboy on 2006-08-02
So do I have to do anything to activate the webcam when I get in or does ubuntu just recognize it when I plug it in?

---

### Post by loell on 2006-08-02
nope, just use ekiga or any other app that uses webcam.
its like plug and play :)

---

### Post by Blairboy on 2006-08-02
Bad assed.  One last thing, is there any mention of support for the quickcam ultra vision?  That's the one I've really got my eye on because it's got a bigger f stop and glass lenses.

---

### Post by loell on 2006-08-02
unfortunately no, but because its logitech webcam its more likely supported in linux, I don't know if you can do this but one way to find out is bring a livecd and persuade the computer store to test it for compatibility, boot the livecd and plug the webcam, and launch ekiga click the webcam button and if you can see images then its good to go :) ,  perhaps you know someone who had this webcam, and maybe you can test it :)

---

### Post by macewan on 2006-08-02
> **Blairboy said:**
> So do I have to do anything to activate the webcam when I get in or does ubuntu just recognize it when I plug it in?

I just tested a Creative webcam and seems to work fine. No need to dick with the modules any more. Ekiga recognized it.

---

### Post by Blairboy on 2006-08-04
That's actually a great idea, but it just came out this month, so it's not in stores yet.  But I'll keep a look out.  Thank's for the info guys.

---

### Post by voyageur_01 on 2006-08-04
Recently, I had the same problem. I wanted webcam that will work out of the box in linux. See at this page
[HTML]http://wiki.wengo.fr/index.php/Liste_des_Webcams_compatibles[/HTML]
This is in french, but there are also pictures of webcams that are known to work with wengo. I bought Labtec Webcam Pro and it works great in my kubuntu:)

---

### Post by lawina on 2007-01-30
> **Blairboy said:**
> I'm really diggin hard on ekiga, but I don't have a webcam.  I had my eye on either the Logitech quickcam ultra vision or the quickcam orbit MP.  I looked around quite a bit but I couldn't find whether either of these are supported in ubuntu.  Anyone know about compatibility or if not, a pretty high end webcam that's similar to those two?  Thanks a bunch.

I too have a Logitech Quickcam Ultra Vision. I tested it with Edgy and I can confirm 'it doesn't' work.

---

### Post by milli on 2007-02-23
lawina, can you post the USB device ID for your Quickcam Ultra vision?  And/or compare against the list at [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) please?

# lsusb

(you may need to 'apt-get install usbutils' first)

---

### Post by slogan on 2007-03-02
Hi,

I also have a Quickcam Ultra Vision and I'm trying to get it to work in Edgy. The output from lsusb is:

Bus 001 Device 007: ID 046d:08c9 Logitech, Inc. 

This USB device ID is listed at [http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/"), so I tried the following:

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo make install
sudo modprobe uvcvideo

In /var/log/messages, I get the following:

Mar  2 21:55:30 localhost kernel: [17181658.548000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c9)

When I plug the camera in, the LED does not light up. Also, Ekiga doesn't detect it.

I'm stumped; any ideas?

E

---

