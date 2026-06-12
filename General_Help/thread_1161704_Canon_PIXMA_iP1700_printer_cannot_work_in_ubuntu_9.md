---
title: "Canon PIXMA iP1700 printer cannot work in ubuntu 9.04"
date: 2009-05-17
forum: General Help
---

### Post by flex on 2009-05-17
After I upgrade to ubuntu ,my printer (Canon PIXMA iP1700) cannot work.I try to re-install the driver but it still cannot work. Anybody can give some advice ? Thanks !

---

### Post by frodon on 2009-05-18
Moved to general help

---

### Post by baAng on 2009-06-16
Hello,

I also had the same problem, but after a few hours googling around, I found a blog that give a complete instruction on how to install the driver. It is in Bahasa Melayu/Indonesia, I translated it. 
This steps should able to run on Canon printer types of iP1880, iP1700 and iP1980 


Okay, let start!

1) First download the zipped file that contains the drivers here [iP1880 + iP1700]("http://www.box.net/shared/pmepfyq428") 
put the downloaded file at your Desktop.

2) Open the terminal and run this commands line by line.
```
cd ~/Desktop/iP1880+iP1700
sudo dpkg -i *.deb
```

3)Open **System &#8594; Administration &#8594; Printing &#8594; New Printer** and choose your printer type (for me Canon iP1700). Click forward.

4) Don't choose **Select Printer from Database**, choose **Provide PPD File** instead

5) Then choose canonip1800.ppd by navigating the windows according to this 
*/usr/share/cups/model/canonip1800.ppd*

6) Give name to your printer (Such as iP1700 or iP1880) and click Apply.

7) Restart your Linux Box.

8. After the restart process finish, open the terminal again and run this commands line by line.
```
cd /usr/lib
sudo ln -s ./libtiff.so.4.2.1 ./libtiff.so.3
```

9) Now, you should be able to print :popcorn:

Cheers!!

acknowledgement : [Install Offline]("http://install-offline-ubuntu.blogspot.com/2009/04/canon-ip1880-ip1700-ip1980-printer.html?showComment=1245140273224#c7514199433456817922")

---

### Post by sammasaurus on 2009-06-17
AHH!  Thank you SO much!  I switched to linux probably 10 months ago, and haven't been able to find a single method to make my printer work until now.  You've just made my life so much easier <3

---

### Post by jtmedin on 2009-06-23
Ok i have an ip1700 & started to follow ur steps. I assumed one must unzip the file into a iP1880+iP1700 directory. However, after step 2 i have unmet dependencies. cnijfiler-common & cnijfilter-ip1800series as i remember. What do i do now? TIA

---

### Post by zerolab on 2009-07-12
> **jtmedin said:**
> Ok i have an ip1700 & started to follow ur steps. I assumed one must unzip the file into a iP1880+iP1700 directory. However, after step 2 i have unmet dependencies. cnijfiler-common & cnijfilter-ip1800series as i remember. What do i do now? TIA
jtmedin,
most likely you need to install libcupsys2.
when you try to install via ```
dpkg -i *.deb
``` scroll through the messages.

do a ```
sudo apt-get install libcupsys2
``` and that should solve the unmet dependencies for cnijfilter-*

---

### Post by KenJean on 2009-08-08
Just wanted to report that everything works as mentioned above.

First I had to install libcupsys2, then I followed baAng's instructions to the letter.

It works. It works. IT WORKS !!!! And here I thought I had to buy a new printer.

Many thanks to all.

:popcorn:

---

### Post by Snackmafia on 2009-10-25
THANK YOU SO MUCH FOR THIS! It worked!  I can PRINT! Haha

---

### Post by whyameye on 2010-03-10
The directions above cause a broken dependency in 9.10 "Karmic". For Karmic follow these directions:
[http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900)

and use the ip1900 ppd included with the link above.

---

