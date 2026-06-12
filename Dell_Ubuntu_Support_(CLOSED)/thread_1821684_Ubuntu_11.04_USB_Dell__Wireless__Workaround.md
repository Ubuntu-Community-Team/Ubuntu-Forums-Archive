---
title: "Ubuntu 11.04 USB Dell  Wireless  Workaround"
date: 2011-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bayouoldguy on 2011-08-09
I think I have a work around for those who want to try Ubuntu 11.04 from a USB flash drive....

for those trying to run (review) Ubuntu 11.04 on their Dell D6 XX Laptops
      (or other laptops using a BCM 4311 Wireless card....)

 I tried to test Ubuntu 11.04 by using a USB flash drive, & could not get a wireless
 connection, even after trying many Ubuntu help guides. I eventually found this  "work-around" thru various internet searches.

1. Get a USB flash drive of >2 GB available unused space.
2. Go to: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)  & download your copy
         of Ubuntu 11.04 to your DESKTOP.
3. Go to Step 2 & read how to create a USB Flash drive/Ubuntu  11.04.
         The "show me how" instructions are good. Be careful to just download & RUN the
         "Universal USB Installer", as the site may confuse you.
4. Go to Step 3 of the Guide, which is re-booting your computer & selecting
         " Run from the USB Drive".  You may have to go into your BIOS setup & move the
         Boot sequence of USB port to above the "Hard drive" in the sequence.
5. Once you get Ubuntu 11.04 up & running, do not select "get additional drivers",
         as the USB Drive is where the "Synaptic Package Manager" attempts to get the
         Driver.
6. You will need to "Hardwire" an internet connetion to your laptop, & you will see
         an internet connection @ the page-top on the right.
7. Now you can go to the "Synaptic Package Manager" & get-install "b43-fwcutter"
         Ubuntu supported Driver. The Internet Connection app will show you DO NOT HAVE
         THE FIRMWARE. The USB Drive does not have it on the drive !. Any attempt to
         download it will end up " Not Found".
8. You could now run in "Terminal" on Ubuntu   {lspc -nn | grep 0280} to verify
         that you have a : Broadcom Corporation BCM4311 802.11b/g WLAN[14e4:4311](rev 01).
9. Set up your Wireless connection in the Ubuntu run for your "SSID" Name, 
         "Infrastructure", go to "wireless Security" & set your router,or access point,
         to ( WPA & WPA2 Personal) or what you are set up for & put in your passcode 
         if you use one.
10. Get on-line & go to : [https://launchpad.net/ubuntu/maverick/i386/firmware-b43-](https://launchpad.net/ubuntu/maverick/i386/firmware-b43-)
         installer ( if you are running a i386 chip ). Look for & download on the page a      

         file: firmware-b43-installer_4.150.10.5-4_all.deb(5.1 KiB). Click on this download
         & I believe it will show up a download box & ask you to "extract & install".
11. My computer immediately found my wireless network & I was up & running !.

12. The files on the USB stick do not include the "Firmware" for "b43" & a "Synaptic"
         download did not provide it for some reason. I did "store" the download file
         on the USB drive for future use.

13. Now you can "play" with Ubuntu 11.04 before installing it, & for all I know,
         you may have to repeat these instructions when you install the new version.
         Many Ubuntu discussions indicate the "Broadcom STA driver"  is not working
         for may Dell systems trying to use 11.04......Good Luck, from Cajun country !!,
         .........George

---

