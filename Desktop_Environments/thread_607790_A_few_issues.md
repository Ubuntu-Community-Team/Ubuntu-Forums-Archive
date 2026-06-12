---
title: "A few issues"
date: 2007-11-09
forum: Desktop Environments
---

### Post by Kriptonic on 2007-11-09
I am kind of new to the Ubuntu and for the most part I got all the basics to work.

Currently I am haveing a few problems where my Blue tooth mouse and keyboard wasnt  working where I found an easy fix on the forums to fix it but coudlnt get to it since it was late as hell when i found it.  But I did find for those that are interested if you pull out the USB cable and plug it back in it will detect the key board and mouse.

Another issue I am having besides being a complete noobie my sound card is not being recognized.  Now I have the Latest in Creative technology Sound Blaster X-FI 

[http://www.creative.com/products/product.asp?category=1&subcategory=208&product=14064&bypass=1](http://www.creative.com/products/product.asp?category=1&subcategory=208&product=14064&bypass=1)

Now I tried folowing the instructions on the ALSA or what ever web page

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)   but I dont know what I am doing.

I also have two more questions much more minor then the ones above.

Now my mouse has like 5 buttons Foward and Back button Middle button scroll and the left and right clicks.  Now if i was on the PoS Windows system they would have a way to configure these buttons with the driver soft ware.  How would i go about this using Ubuntu?

And although I dont have access yet to my sound card.  Similar to the mouse situation where there is software that allows me to configure options in craptastic windows how would i go about doing this on Ubuntu as well.


Let me add i do have some programing background if this helps at all.

Thanks in advanced.

---

### Post by linuxwizard on 2007-11-09
Look over this should help you.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by TeaSwigger on 2007-11-09
Hello and welcome :) I hope you enjoy your ubuntu-ing once you get settled.

No idea re: sound; I've been lucky there.

As to the mouse, in addition to the link linuxwizard provided, you might be interested in a nifty utility called btnx:

[http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)

It lets you assign custom functions to buttons and also keybindings to buttons.

---

### Post by Kriptonic on 2007-11-09
Hey I really appreciate your inputs on my mouse problem and once I look deeper into it (here in about 5 minutes) I would like to go further in depth with my sound card issue.

Fortunately i found drivers for my card.  But I am a little confused with the read me on how to install it.  Maybe some one can enlighten on this.

]Sound Blaster X-Fi Linux x86_64 Beta Driver Readme File


  September 2007


====================================================================


The purpose of this document is to describe how the X-Fi Linux device 

driver is built, packaged, and released.







Quick install


=============




1) You must have the fully configured source for the Linux kernel and 

   ALSA which you
 want to use for this device driver. Partial installed 

   kernels (e.g. From distribution makers) may be unusable for this 

   action.





2) Run one of the following commands as root in the terminal:





   ./installer
   




   OR




   ./installer --with-alsainc=<ALSA_include_directory>





  * ALSA Source Tree




   
   On 2.6 kernels, the location of the ALSA source include directory


      is parsed automatically from the running kernel.


      If it is not in the standard place, specify the path via

   
   --with-alsainc=<ALSA_include_directory>.



 
   
  On 2.4 kernels, the location of the ALSA source include directory


      must be specified via --with-alsainc=<ALSA_include_directory>.





  * Note

      If integrated ALSA is to be used to build, --with-alsainc option


      must not be specified.






Thanks in advanced.

---

### Post by Kriptonic on 2007-11-10
Let me add if i try run the ./installer it says this is only compatible with 64 bit OS.

So i went to the 64 bit ubuntu and it still says that.
so if any one has any ideas please let me know 

Thanks

---

