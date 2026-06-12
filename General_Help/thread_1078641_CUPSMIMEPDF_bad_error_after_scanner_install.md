---
title: "CUPS/MIME/PDF bad error after scanner install"
date: 2009-02-23
forum: General Help
---

### Post by smartsmokey on 2009-02-23
I installed a Brother 4-in-1. I was able to download and install the printer drivers flawlessly. To get the scanner working, I downloaded and installed the proper software from Brother, and then I had to install "Cups" or something. Right after restarting my system, I go to any pdf document, and BAM - "unable to open document/unknown MIME type." What did I do? I searched around and some people said it was the mime-info package, so I went into synaptic and tried to get the latest mime-info thing, but it says I already have it. So I guess there's 2 issues here - I'm not able to get the scanner functionality from the Brother MFC-290C, and installing various items and following the tutorials to install and get the scanner part working has caused my system to lack the ability to read and manipulate PDF files. Sounds like something in the registry maybe?

---

### Post by smartsmokey on 2009-02-23
i used these instructions (adjusting them to my personal needs of course)
[http://www.uluga.ubuntuforums.org/showthread.php?t=590793](http://www.uluga.ubuntuforums.org/showthread.php?t=590793)
It did not work

---

### Post by smartsmokey on 2009-02-23
solved. Have to run sudo xsane, then it says "alert! you're using xsane as root!" and I don't know or care what that means so I hit okay and xsane and the scanner work flawlessy. First scans came out with a lock or osmething on them, and document viewer wouldn't open them. So went into like permissions in xsane and clicked on all the buttons to make them all readable, etc. That seems to work. I set default doc viewer to Open Office writer, then swithced back to "document viewer" and now everything is fine.

---

### Post by smartsmokey on 2009-02-23
NOPE!!!!! Now I can't print. Says "not connected? Printer may not be connected"

---

### Post by smartsmokey on 2009-02-23
nobody?

---

### Post by smartsmokey on 2009-02-23
Okay I'm not able to use the printer as well as scanner, to scan you need to go to terminal and type sudo xsane and then it starts it in root. Otherwise it doesn't detect the device. Also, when you save pdf's of sanned images you need to make sure you have the settings for the permissions set to allow EVERYONE to see/read/edit them, or else it'll just show on your desktop as locked or whatever. I used some sudo chmod backend thing on usb and something else. I don't know. But the scanner and printer works, but now I can view PDF files!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by smartsmokey on 2009-09-30
i just had to come back and find this - sure enough, sudo xsane still does the trick

---

### Post by donc786 on 2010-03-21
Here is a link to the drivers from brother.  Use the brscan3 version.  It came out Feb of '10.  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)  The .deb 32 bit is what I used on 9.10. I still had to run xsane as root.

---

