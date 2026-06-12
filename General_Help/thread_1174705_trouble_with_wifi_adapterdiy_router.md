---
title: "trouble with wifi adapter/diy router"
date: 2009-05-31
forum: General Help
---

### Post by scales on 2009-05-31
Hi all. I am still a little bit of a newb to linux but am trying to build a ubuntu based router. I have a zd1211 capable wifi usb dongle which is supported by the current 2.6.28-11 kernel. My trouble is that the 1211rw drivers built in do not support "master mode". I have found a site 
[http://zd1211.wiki.sourceforge.net/VendorBasedDriver](http://zd1211.wiki.sourceforge.net/VendorBasedDriver)

which details on how to build the zd1211b driver which does support it. Initially I tried to compile under the ubuntu 9.04 but ran into errors when runing make. After several hours of help from the irc channel and a linux experienced friend, I decided that it was either the kernel version or gcc. I found another site which went through the process and they had used ubuntu 7.04. So I installed the older version of ubuntu and low and behold I got it to compile. Since I would rather have the latest supported ubuntu version, I decided to try and use ubuntu 9.04 again but with a different version of gcc, the same one found in ubuntu 7.04 (gcc4.1). It installed fine into 9.04 since it was still in the repos, but compiling was not successful. I have since then gotten more advice and concluded that the problem has to do with the kernel.

When trying to compile from 9.04 i got some error involving "eth_copy_and_sum". I found another comment online that said


> In order to avoid errors and compile the driver version 2.21.0.0 with recent kernels you should modify the source file zd1205.c and substitute this:
eth_copy_and_sum(skb, pData, length, 0);
for this:
memcpy(skb, pData, length);
This is a very poor solution but it works: tested with 2.6.23.1-23.fc8 kernel (Fedora 7.92 test 3)
And remember: to bring up the wireless interface you must "ifconfig ethX up" it first.  

So I did that but unfortunately still ran into errors (here is the output [http://pastebin.ca/1441172](http://pastebin.ca/1441172))

Right now I would like to do one of two things:
1. somehow get the driver to compile on the newer kernel (9.04)
2. install ubuntu 7.04 but i need repos to finish setting it up as a router.

Anyone have any suggestions? I would greatly appreciate it! thanks.

---

### Post by Legace on 2009-05-31
Download:
[ftp://ftp.a-link.com/wl54usb/CD_v6.19.0.0.zip](ftp://ftp.a-link.com/wl54usb/CD_v6.19.0.0.zip)

Follow instructions in the PDF file located in **/CD_v6.19.0.0/Linux**.

Don't know if it works for Jaunty, but it worked for me with 8.10 and should work for Jaunty too.

---

### Post by scales on 2009-05-31
Awesome! i dunno how i didnt find this i have been hunting all over the internet for days!  Thanks i will check it out and post my results :)

---

### Post by scales on 2009-05-31
> Don't know if it works for Jaunty, but it worked for me with 8.10 and should work for Jaunty too. 

bummer:(.  i tried to compile it in jaunty and i get the following error code.  [http://www.pastebin.ca/1442812](http://www.pastebin.ca/1442812)
(i just have the headers and build essential installed by the way)

---

