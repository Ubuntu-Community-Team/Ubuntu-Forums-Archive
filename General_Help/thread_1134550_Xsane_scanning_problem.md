---
title: "Xsane scanning problem"
date: 2009-04-23
forum: General Help
---

### Post by CrusaderAD on 2009-04-23
I have an epson stylus NX100 with a flatbed scanner and I can't seem to get it to work. I get it to print but when I use xsane to scan I get this error:

failed to open device 'v4l:/dev/video0': invalid argument

What's the deal? Is there another scanning program out there?

---

### Post by thirdrev on 2009-04-29
You could try this:
[http://ubuntuforums.org/showthread.php?t=977591&highlight=xsane+error+during+i%2Fo](http://ubuntuforums.org/showthread.php?t=977591&highlight=xsane+error+during+i%2Fo)

---

### Post by CrusaderAD on 2009-04-29
Cool, thanks. I'll give this a shot.

---

### Post by chudder on 2010-06-27
My printer has always worked but not the scanner.

I found a workaround program for this for my NX100.  

Xsane doesn't support this model, even though it says it does.  Epson doesn't have any drivers or programs but Avaya supplies a few for them. 

Avaya makes a program called Image Scan! for Linux which works for basic scanning without the bells and whistles.

**To get it directly go to:**

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

If the **Avasys Download All-in-Ones (Multifunction Inkjet Printers)** page appears then skip to the **Downloading** section at the bottom of the post.

**Navigation to the Site**
Or if for some reason the link doesn't work, here is how to navigate to the page, go to:

[www.epson.com]("www.epson.com") then click on **Drivers and Support** 

Find your model and then click on **Other** when given a choice for which operating system.  

Then click **Download Now** 

Read the agreement and then click **Accept**

Then click **Epson All-in-Ones (Ink Jet)**

click **Leave**

Scroll down to the radio buttons and click **Epson Stylus NX100/SX100/TX100/TX101/TX105/TX106,Epson ME 300**

Go to the bottom and fill out the distro and other information

Scroll down to the **Scanner Driver** section, if your printer is working you can ignore the top section (The Printer Driver Section).

**Downloading**
Download the **iscan-data_1.0.0-2_all.deb** package and then download the **iscan_2.25.0-1.ltdl7_i386.deb** (This is the one specifically for Ubuntu 8.10 or later, not the regular DEB package)

Install them with dpkg in the order you downloaded them and now you can scan.  The program directory is Applications>Graphics>Image Scan! for Linux

---

### Post by tykmo on 2010-09-28
¨iscan-data_1.3.0-2_all.deb¨ and  ¨iscan_2.26.0-3.ltdl7_i386.deb¨ are the latest deb packages but package installer is telling ¨[COLOR="Red"]Error: Dependency is not satisfiable: iscan-data[/COLOR]¨

---

