---
title: "Help: How do I install the software for facial recognition in Ubuntu UNR 9.04?"
date: 2009-06-06
forum: General Help
---

### Post by ShapeShifter499 on 2009-06-06
Hi, my name is Lance and I've been pulling out hairs trying to install this software. The software I'm talking about is suppose to be able to log you in, by facial recognition, and I found it on this post on another form, LINK: [html]http://groups.google.com/group/linux-biometrics/browse_thread/thread/55dd4428f1ddf80b[/html] So my question how do I install this? Could someone give me a step-by-step on it? I'd appreciate it a lot, thanks.


INFO ABOUT MY LAPTOP/NETBOOK

I have a Acer Aspire One Netbook that has 120 GB total storage, 1 GB ram, web cam, 8.9 inch screen, one mouse touch pad, built-in wireless(no G3/G4 cell wireless). 3 usb ports, 2 memory card slots, one ethernet port, one vga port, and one headphone and microphone port. In the color blue.

WHAT OPERATING SYSTEM ON IT

Three Partitions

First Partiton: Windows recovery for acer 

Second Partition: Windows XP SP3

Third Partition: Ubuntu 8.10---Updated--->Ubuntu 9.04----Installed Extra---->Ubuntu Studio----Installed Extra---->Ubuntu Netbook Remix---NOW--->Ubuntu Netbook Remix Studio Edition

---

### Post by ShapeShifter499 on 2009-06-06
*bump*

---

### Post by ShapeShifter499 on 2009-06-07
*bump*

---

### Post by ShapeShifter499 on 2009-06-07
*bump*

---

### Post by 3rdalbum on 2009-06-07
The page you linked to has installation instructions, admittedly not very in-depth as the poster seems to have limited English skills. Where are you getting stuck in the instructions?

> 
Dear All,

My name is Elisardo González and I am member of  jbioapi project. My
partners and me have made a BSP to provide user face verification
using a webcam to take the face snapshot.
You can find the binary files at [http://www.gts.tsc.uvigo.es/~eli/AutomaticFaceBSP/](http://www.gts.tsc.uvigo.es/~eli/AutomaticFaceBSP/)
We use the OpenCV library to perform automatic face detection, so we
can select the best user face photo without the user collaboration,
and use it to perform the verification.
We have tested it on Ubuntu distribution with bioapi_1.2.3_i386.deb
<http://www.qrivy.net/%7Emichael/temp/bioapi_1.2.3_i386.deb> and
pam_bioapi-0.2.1.tar.gz
<[http://www.qrivy.net/%7Emichael/blua/pam_bioapi/](http://www.qrivy.net/%7Emichael/blua/pam_bioapi/)
pam_bioapi-0.2.1.tar.gz>,
and it works.
For installation:
1- OpenCV and ImageMagic libraries are required.
2- Create a folder called haarcasacadefiles inside of /root/ directory
and copy there the attached XML files.(required for the automatic face
detection)
3- mod_install -i libautomaticfacebsp.so

The BSP UUID is  {0x26, 0x3A, 0x41, 0xe0, 0x71, 0xeb, 0x11, 0xd4,
0x9c, 0x34, 0x12, 0x40, 0x37, 0x00, 0x00, 0x01} or
{263A41e0-71eb-11d4-9c34-124037000001}
||
We have tested it with pam-bioapi  following the instructions of  "How
to enable fingerprint reader" guide ([http://www.thinkwiki.org/wiki/](http://www.thinkwiki.org/wiki/)
How_to_enable_the_fingerprint_reader)
...

auth       sufficient   pam_bioapi.so
{263A41e0-71eb-11d4-9c34-124037000001} /etc/bioapi/pam/ :0.0



---

### Post by ShapeShifter499 on 2009-06-07
I'm getting stuck at [html]3- mod_install -i libautomaticfacebsp.so[/html] that step gave me errors. Also I'm not sure if I install both  bioapi_1.2.3_i386.deb AND pam_bioapi-0.2.1.tar.gz I did install the first one,  bioapi_1.2.3_i386.deb, so my questions are, one which ones do I install?, two how do I activate the program once installed right?, and last I'm not so sure that the way I installed OpenCV and ImageMagic was correct, how do install them correctly?

---

### Post by ShapeShifter499 on 2009-06-07
Also I didn't understand how to install pam_bioapi-0.2.1.tar.gz

---

### Post by 3rdalbum on 2009-06-07
This seems to require more specialised knowledge that I don't have. I hope somebody else can help. If there is no reply to this thread in the next day or so, maybe try the Security Discussions or Hardware forum.

---

### Post by ShapeShifter499 on 2009-06-08
*bump*

---

### Post by Crimsonite on 2009-07-02
I *seem* to have installed it alright, but it took some messing with. Follow all the links - the thinkwiki page's instructions on installing pam_bioapi was particularly useful.

However, now that it seems to be installed, I don't know what to do to test it... :D

I've been using an old copy of Visionics FaceIt in windows for a while with a basic USB webcam. I was hoping for a linux alternative now that I'm migrating more and more to linux on my desktop.

---

