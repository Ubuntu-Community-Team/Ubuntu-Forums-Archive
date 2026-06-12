---
title: "Ploting software for osciloscope"
date: 2010-01-07
forum: Education &amp; Science
---

### Post by phoenox on 2010-01-07
[SIZE=2]Hi,

I have a digital storage osciloscope piece of hardware that I would like to get working in linux.  The device is a DSO-8500 made by Link instruments.  

There is no real support for linux for the software that comes with the osciloscope.  Writing to the manufacturer, they suggested using virtualbox.  I may end up doing this if I have to.  

The other option I have been considering is taking some open source graphing program native to linux and adding a USB interface to import the osciloscope data, as well as a controller for the osciloscope.

I have some programming experience, mostly in c, but I have never taken on a project of this scope before.

I am hoping someone here can suggest a graphing program that could make this project possible, or a better approach to getting this hardware working.

Thanks
[/SIZE]

---

### Post by not_a_phd on 2010-01-08
Might I suggest gnuplot for your plotting needs. It is possible to set it up to plot from streaming data. 

Pulling in the data stream from an unsupported USB connection may be somewhat difficult. Do you know if byte stream is ascii or binary? 

Having just gone through the effort to talk to an unsupported USB modem, I know that it is possible to inform the operating system of a character device on a ttyUSB stream. Perhaps you can use a similar process to inform linux of your O-scope to get the basic data flowing on a /dev/ttyUSB# device, and then use the [CODE]screen /dev/ttyUSB#[/CODE/ command to sniff the data and check out the format. 

Once you have the stream set up (and understood), you can use gnuplot to plot the data. It is easier to plot if it is ascii data, but it can also plot binary data as well.

---

### Post by phoenox on 2010-01-09
Thanks.  It looks like gnuplot should work.  I got it installed and running now, and have made a few simple plots with it.  Seems like a very versatile program.

I have no idea how the data is encoded.

I think now I will head over to the developers forums to find out more about talking to an unknown USB device.  I'm also going to keep talking to the manufacturer to see if they can give me any help.

If you are interested my new thread is here:
[http://ubuntuforums.org/showthread.php?p=8637535#post8637535](http://ubuntuforums.org/showthread.php?p=8637535#post8637535)

---

