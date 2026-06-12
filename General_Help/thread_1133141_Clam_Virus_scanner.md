---
title: "Clam Virus scanner"
date: 2009-04-22
forum: General Help
---

### Post by JohnPta on 2009-04-22
I am trying already for a massive amount of times out of 147 days to "Update Signatures" from the Internet for ClamTK anti virus software. However every time I try to do that I get the message in the window "Unable to retrieve updates. Try again later." Where am I going wrong? 

P.S. I did also try and started the software from the "Terminal" after I logged in as "Root" user.

---

### Post by lovinglinux on 2009-04-22
The solution to your problem is [here](http://ubuntuforums.org/showthread.php?t=428412). But I recommend using the new [BitDefender](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html). I tried Clam and Avast, but BitDefender is the best so far. See the discussion [here](http://ubuntuforums.org/showthread.php?p=7112886).

---

### Post by JohnPta on 2009-04-24
> **lovinglinux said:**
> The solution to your problem is [here](http://ubuntuforums.org/showthread.php?t=428412). But I recommend using the new [BitDefender](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html). I tried Clam and Avast, but BitDefender is the best so far. See the discussion [here](http://ubuntuforums.org/showthread.php?p=7112886).

I am browsing now already for nearly two days through the "BitDefender" website where it is INDEED mentioned that the Linux version is down loadable. However I always get to an "exe" file which to my knowledge is for Microsoft. Where is the Linux file? Could you be so kind and give me a more specific address in the website of "BitDefender"? 
Thanks.

---

### Post by lovinglinux on 2009-04-24
> **JohnPta said:**
> I am browsing now already for nearly two days through the "BitDefender" website where it is INDEED mentioned that the Linux version is down loadable. However I always get to an "exe" file which to my knowledge is for Microsoft. Where is the Linux file? Could you be so kind and give me a more specific address in the website of "BitDefender"? 
Thanks.

The site is really terrible. Follow the instructions below. You have to search for the file that says "for Unices".

Open [this page](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html) the click the download button, fill and submit the submission form, then get the real download link from your e-mail. Install the software, then go back to the previous page and click the button to request a license. Fill the license form in the program preferences page.

---

### Post by dcstar on 2009-04-24
> **JohnPta said:**
> I am trying already for a massive amount of times out of 147 days to "Update Signatures" from the Internet for ClamTK anti virus software. However every time I try to do that I get the message in the window "Unable to retrieve updates. Try again later." Where am I going wrong? 

P.S. I did also try and started the software from the "Terminal" after I logged in as "Root" user.

The **clamav-freshclam** package does the updates automatically, are you using it?

---

### Post by JohnPta on 2009-04-26
> **dcstar said:**
> The **clamav-freshclam** package does the updates automatically, are you using it?

Yes that package is installed but I can not find it in order to activate it.

---

### Post by JohnPta on 2009-04-26
> **lovinglinux said:**
> The site is really terrible. Follow the instructions below. You have to search for the file that says "for Unices".

Open [this page](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html) the click the download button, fill and submit the submission form, then get the real download link from your e-mail. Install the software, then go back to the previous page and click the button to request a license. Fill the license form in the program preferences page.

I was already on that web site and downloaded the first of the list below and when the software started unpacking the 41Mb package It gave the message that the file was corrupted? But was that the right package?
Ok, in the meantime, I will try to down load it again.

This is the message I get after downpoading!
/home/jan/Downloads/Bitdefender.png




[DIR]	Parent Directory	 	 -
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run	09-Mar-2009 17:30 	41M
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run.md5	09-Mar-2009 17:30 	96
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.ipk.run	09-Mar-2009 17:30 	41M
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.ipk.run.md5	09-Mar-2009 17:30 	96
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.rpm.run	09-Mar-2009 17:30 	41M
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.rpm.run.md5	09-Mar-2009 17:30 	96
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run	09-Mar-2009 17:30 	40M
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run.md5	09-Mar-2009 17:30 	95
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.ipk.run	09-Mar-2009 17:30 	40M
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.ipk.run.md5	09-Mar-2009 17:29 	95
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.rpm.run	09-Mar-2009 17:29 	40M
[ ]	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.rpm.run.md5	09-Mar-2009 17:29 	95
[ ]	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.deb.run	09-Mar-2009 17:29 	34M
[ ]	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.deb.run.md5	09-Mar-2009 17:29 	101
[ ]	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.ipk.run	09-Mar-2009 17:29 	34M
[ ]	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.ipk.run.md5	09-Mar-2009 17:29 	101
[ ]	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.rpm.run	09-Mar-2009 17:29 	34M
[ ]	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.rpm.run.md5	09-Mar-2009 17:29 	101
Apache Server at download.bitdefender.com Port 80

---

### Post by lovinglinux on 2009-04-26
> **JohnPta said:**
> I was already on that web site and downloaded the first of the list below and when the software started unpacking the 41Mb package It gave the message that the file was corrupted? But was that the right package?
Ok, in the meantime, I will try to down load it again.

If you are running 64 bits, then yes, otherwise use the i586.deb.run file.

---

### Post by JohnPta on 2009-04-26
> **lovinglinux said:**
> If you are running 64 bits, then yes, otherwise use the i586.deb.run file.

I am using a board which support  Socket-AM2 (940 pin) bassed AMD Athlon-AM2 with 2.0Gts 16x16 Hyper Transport processors. I assume it is a 64 bit CPU.

---

### Post by JohnPta on 2009-04-26
> **lovinglinux said:**
> If you are running 64 bits, then yes, otherwise use the i586.deb.run file.

Ok I also downloaded the 586 file, same result. See attachment.

What now??? :-(

---

### Post by lovinglinux on 2009-04-26
> **JohnPta said:**
> Ok I also downloaded the 586 file, same result. See attachment.

What now??? :-(

Make sure the permissions of the file are allowing to execute it as program and run it in the terminal with sudo.

---

