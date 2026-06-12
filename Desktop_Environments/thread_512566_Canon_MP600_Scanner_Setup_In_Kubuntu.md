---
title: "Canon MP600 Scanner Setup In Kubuntu"
date: 2007-07-29
forum: Desktop Environments
---

### Post by wcj786 on 2007-07-29
These procedures were put in another post, but I thought it might be advantageous for this to be the first entry in a new post, so people would not have to go searching around to find it.  These steps were what allowed the scanner to work for me in **Kubuntu**.

For those looking to get there Canon MP600 scanner working, I found a web page that shows how to get a Canon scanner to work in Dapper, here, but had to slightly modify it, due to the MP600 working on the 0.13.0 back-end. Here are the steps I took to get it to work.

1) Downloaded the drivers to Desktop

2) cd Desktop

3) sudo apt-get install alien libpng3
    sudo alien scangearmp-common-1.00-1.i386.rpm
    sudo alien scangearmp-mp600-1.00-1.i386.rpm
    sudo dpkg -i scangearmp-common_1.00-2_i386.deb
    sudo dpkg -i scangearmp-mp600_1.00-2_i386.deb

At this point, it was suggested  that you should be able to run **scangearmp**. This did not work for me. That is not to say it is wrong, it might be that the person who suggested it had other software that allowed it to run, where I didn’t,  so I then did the following:

4) sudo apt-get install build-essential
    wget [http://home.arcor.de/wittawat/pixma/...0.13.0.tar.bz2](http://home.arcor.de/wittawat/pixma/...0.13.0.tar.bz2) 
    sudo tar xjf mp150-0.13.0.tar.bz2 -C /usr/src
    cd /usr/src/mp150-0.13.0/
    sudo make
    sudo ./scan -L

5) sudo cp libsane-pixma.so /usr/lib/sane/libsane-pixma.so.0.13.0
    sudo ln -s /usr/lib/sane/libsane-pixma.so.0.13.0 /usr/lib/sane/libsane-pixma.so.1
             (The web page states to modify **dll.conf**, but I found that **pixma **was already in the file.)

6) sudo vi /etc/udev/rules.d/45-libsane.rules (I use **vim **as my editor.)

At this point, I added the following lines in this file (in the area that had the Canon AiO/scanners):

    # Pixma MP600
    SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="1718", MODE="664", GROUP="scanner"

7) sudo /etc/init.d/udev restart

This is the end of the directions from that webpage, but at this point, the scanner still did not work for me (and **scangearmp **was not showing up in my K Menu under Graphics).

So, I started looking in the **/etc/sane.d/dll.d** folder to see if there was anything in there that might be causing the problem. I identified that the only file in that folder was **hplip**. So , I copied that file, then modified it, naming the new file **pixmalip**. I added the following four lines in the in the new file:

    # dll.conf snippet for pixmalip
    #

    canonaio  (this is the last line of the file and does not include the comments in the parentheses)

In the **sane.d** directory, I also modified the **canon.conf **file to look like:

    #canon.conf
    # Canon Pixma MP600             (This was not there originally.)
    usb 0x04a9 0x1718                 (This was not there originally.)
    #/dev/scanner                         (This was not commented out originally.)
    #/dev/sg0

After doing the above steps, I got the **scangearmp **program to run and scan for me. I am sure there may be steps that I took, that might not be necessary, and there may be a better way of doing this, but this is what worked for me.  I do not profess to know how to program in Linux.  The steps I took were more of a "follow the procedures on the web page" approach, with some slight modifications, due to the differences in equipment and files.

The last few steps that included adding the **pixmalip **file and modifying the **canon.conf **file seemed like the logical thing to do.  I am not claiming that this procedure will work for everybody, just that it worked for me.  If anybody can identify a better way to provide the scanner capability, or modify the above code to work more efficieantly, please do not hesitate to post that info.

---

### Post by wcj786 on 2007-07-31
All, I am looking for feedback on this.  Did this procedure help you?  Did it work for you?  Does anybody see a problem with the procedure?  Please post your comments and let me know.

---

