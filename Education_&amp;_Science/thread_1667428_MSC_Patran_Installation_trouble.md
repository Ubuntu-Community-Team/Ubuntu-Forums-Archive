---
title: "MSC Patran Installation trouble"
date: 2011-01-14
forum: Education &amp; Science
---

### Post by Sphoneix on 2011-01-14
Hi all,

I just finished installing MSC Patran (CAE) but can't get it to open. The installation guide tells me to go to a terminal, go into the directory where I installed Patran and type in %patran. This does absolutely nothing because there is no such command as that. I also tried this command.....


owner@owner-VGN-AR570E:~/MSC/patran_x64/2010/bin/exe$ ./p3
./p3: error while loading shared libraries: libpskernel.so: cannot open shared object file: No such file or directory

I have been looking all over the internet to try and find out how to install libpskernel.so but I have not found anything. Can anyone help? Thanks.

---

### Post by Sphoneix on 2011-01-17
I solved the issue, I was missing some packages for rdm and libXM that I got from the synaptic package manager.

---

### Post by ubufala on 2011-01-21
> **Sphoneix said:**
> I solved the issue, I was missing some packages for rdm and libXM that I got from the synaptic package manager.


Hi Sphoneix!.
How did you manage!??

I'm have the same trobles you had.
When I launch /install_dir/bin/patran
I recieve the error message "Segmentation Fault", 
while I launch /install_dir/bin/exe/p3
I recieve the same error that you had. 
Which packages did you install?

Thanks a lot!!

---

### Post by cntmn8td2006 on 2011-10-05
I was also stumped with the same problem. What hindered me were numerous missing installations. The installation guide for Patran is pretty crummy in regards to installing Patran on Linux. Apparently they use Unix and Linux interchangeably even though Linux is a Unix like OS and not actually Unix. I noticed what I think are some errors in OP's original post.

The user should go to the installation directory and type "./patran" in order to start Patran, not "%patran."

The rdm should be rpm. As for LibXm, try this command

ln &#8211;s /usr/lib/libXm.so.4 /usr/lib/libXm.so.3 

This command points the old libXm to the newer libXm. Patran then fired up for me.


One last thing, from the MD Nastran 2010 release guide, they offer a lot of support. I have included the information below.

> Technical Support
For technical support phone numbers and contact information, please visit:
[http://www.mscsoftware.com/Contents/Services/Technical-Support/Contact-Technical-Support.aspx](http://www.mscsoftware.com/Contents/Services/Technical-Support/Contact-Technical-Support.aspx)
Support Center ([http://simcompanion.mscsoftware.com](http://simcompanion.mscsoftware.com))
Support Online. The Support Center provides technical articles, frequently asked questions and
documentation from a single location.


---

### Post by cntmn8td2006 on 2011-10-07
Please note that Ubuntu is not on the list of compatible operating systems. 

Source: Patran 2011 Istallation PDF


[IMG]http://i.imgur.com/xkPTa.png[/IMG]

---

