---
title: "Choosing alternative resolutions"
date: 2006-06-01
forum: Desktop Environments
---

### Post by dapps on 2006-06-01
Hello all,

I've been using Ubuntu for a few months now for various learning and testing purposes, and have just recently switched over to use it as my primary desktop operating system.  

This afternoon I went ahead and downloaded the latest Dapper Drake 6.06 Release and installed it.  However to my surprise, during the installation process I was not asked which resolution modes I would like included with the installation; in the previous version the installer would ask which resolutions you may want installed for different monitor devices that you may use in the future.

Therefore, after the default installation process, this left me with only three resolution options: 1024x768, 800x600, and 640x480.

So, my question to you is, how can I pick a higher resolution and what is the process to doing this?  Normally I would think that I could just download the necessary drivers, but since the previous version of Ubuntu allowed be to choose the resolutions that I may run without any additional driver downloads, I am stuck as to what to do next.

Thanks in advance for your help!

---

### Post by dapps on 2006-06-01
I've just seen that a number of people have posted in regards to resolution issues.  

Could we combine these threads and come up with a solution?

---

### Post by dapps on 2006-06-09
Since my original posting I have done some digging around, and found out that I have to edit the xorg.conf file with the appropriate resolutions that I would like to use.  

However, after going into xorg.conf and replacing the existing default resolutions with only one resolution (1280x1024) I have still been unable to get the resolution set up to 1280x1024.

Anyone have any ideas as to what I could try next?  

I had hoped that the community support for a fundamental problem such as this would be better.  :(

---

### Post by m42technic on 2006-06-10
I just followed the instructions listed at [https://wiki.ubuntu.com/FixVideoResolutionHowto]("https://wiki.ubuntu.com/FixVideoResolutionHowto") a little whole ago with no problems.  Try reconfiguring xorg.  :)

---

### Post by jvictor on 2006-06-10
1)Assuming that u have the proper drivers installed for you gfx card,  U need to know the h/v freq of ur monitor and add that to ur /etc/X11/xorg.conf file

Itl look somewhat similar to this 

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70 
        VertRefresh     50-120
EndSection

Be sure of the freq or else u CAN roast ur monitor.


The next part is to add the resolution ( that ur card & monitor can support to you default "depth" section in the same file

It'll look somewhat similar to this 

 SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768"
 EndSubSection


IMHO, maybe you must search the forums b4 posting , coz there are innumerable threads that deal with this.

HTH

---

