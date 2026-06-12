---
title: "Dell mini 9 says no no application installed for this file type"
date: 2009-05-03
forum: General Help
---

### Post by Boo8W on 2009-05-03
I doanloaded netbook remix  to sd card but Dell mini 9 says Couldnt display 9.04 img as there is no application installed for this file type.Help

---

### Post by mikewhatever on 2009-05-03
Please review the UNR wiki. [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR) In short, you are not supposed to open the .img file.

---

### Post by Boo8W on 2009-05-03
Did as said but when I run win32diskimager tool I keep getting "Error occured when attempting to lock volume"Anyone know what this means?Also when they talk of Device as in this statement ""run the Image Writer tool, select the downloaded image, select the target device and click on "Write to device".dont they mean the USB drive, or SD in my case?

---

### Post by snowpine on 2009-05-03
The Dell Mini 9 is not capable of booting from an SD card. You need to follow the instructions to copy the .img file to a USB thumb drive.

---

### Post by Boo8W on 2009-05-04
I put the reqiured files on USB  from sd card,yet when i run the Win32Diskimager i get "Lock error when attempting to lock the volume, Error 8"" I've read the documetnation that comes with the program but theres ono mention of error 8 or any other errors.There seems to be no successess with linux to keep you going;everywhere 1 turns there another punch in the face waiting.Anyone know whats going  on, as google has just a few results and theres no answers? ?

---

### Post by mikewhatever on 2009-05-04
> **Boo8W said:**
> I put the reqiured files on USB  from sd card,yet when i run the Win32Diskimager i get "Lock error when attempting to lock the volume, Error 8"" I've read the documetnation that comes with the program but theres ono mention of error 8 or any other errors.There seems to be no successess with linux to keep you going;everywhere 1 turns there another punch in the face waiting.Anyone know whats going  on, as google has just a few results and theres no answers? ?

I am rather confused. Win32Diskimager is a program to put the image to the USB device. If that had already been done, why did you have to run Win32Diskimager again? Otherwise, what are the files you put on the USB?
Have some patience, and I am sure you'll figure it out.

---

### Post by snowpine on 2009-05-04
Follow these steps one by one from the beginning, using a USB thumb drive (not an SD card), and I'm sure you'll be okay:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

If the first method doesn't work, there is an alternate method using flashnul.

---

### Post by Boo8W on 2009-05-05
Thanks a lot for all the help;I did it slowly, point by point as suggested and got the image written to the USB.Just a point for anyone else with this problem, have the Ubuntu remix int a different pace ,ie..folder or sd card in my case when you use the image tool from  [https://wiki.ubuntu.com/UNR#Help](https://wiki.ubuntu.com/UNR#Help) and documentation.Thanks again

---

