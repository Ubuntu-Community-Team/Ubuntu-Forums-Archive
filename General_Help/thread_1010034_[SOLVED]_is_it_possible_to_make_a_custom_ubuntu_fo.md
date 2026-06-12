---
title: "[SOLVED] is it possible to make a custom ubuntu for asusEEEpc"
date: 2008-12-13
forum: General Help
---

### Post by cmay on 2008-12-13
hi.
i have an asus Eeepc which i installed ubuntu eee on. i do not want the xandros at all. the problem is that the ubuntu eee does not find my ordinary wired network. its a model 701sd . i been playing around with other distros on usb sticks using unetbooting and i can not  find a distro that "works out of the box". while i like to play around with this i have found sysremaster and isomaster and i been thinking about if i can make a custom linux distro very easy or simple by somehow adding or replacing to the iso image. this would be great to have a plain ubuntu or debian that simply uses anohter kernel and has the drivers needed and set up per default. if that can be done using the instructions on how to make ones own customized live cd or distro found in the offical ubuntu docs i would try to this. 

can anyone tell me if it is possible and how much it would take. i have all the time needed to this but i do not want to waste my time doing something i dont know if can be done or how to do it before i begin.
 
thansks for reading this.

---

### Post by mdebusk on 2008-12-13
> **cmay said:**
> the ubuntu eee does not find my ordinary wired network.

Did the Xandros install see it?

Are you sure it isn't a hardware problem?

Have you tried [Eeebuntu]("http://www.eeebuntu.org/")?

---

### Post by cmay on 2008-12-13
> Did the Xandros install see it?
yes. and it works perfect

> Are you sure it isn't a hardware problem?
yes. only thing is that if it breaks now after i removed xandros i will maybe never know if i dont get it working. 

> Have you tried Eeebuntu?
donwloading the eeebuntu-2.0nbr.iso right now. i tried the standard edition. 

i have made the usb startup sticks on two usb sticks using unetbooting. one plain ubuntu one eeedebian.img which i am going to install if the eeebuntu fails. 
the i tried crunchbanglinux , eeexubuntu and debian lenny live. all  of them can not connect to ethernet. i am sure it was working with xandros in it but when i updated the xandros after only two hours of playing wiht it it simply killed the installation. all desktop icons and backgrounds was missing after the update. so i installed ubuntu eee in it and it works perfect other than the standard network.

my plan: 
 i want to try now using debian from the eee debian project and see if i can get everything working and then follow the how to make a custom live cd instructions there is a sticky in the other os tread and maybe get it to work. i am not sure if it can be done however. there is only 4 gigabyte space on the harddisk and other than that it is not easy to make a custom cd  with out a cd burner for it. i have only usb sticks for it. 
 is it doable over some coffee and a cpouple of days ?

---

### Post by cmay on 2008-12-13
[http://wiki.debian.org/DebianEeePC/Model/701SD](http://wiki.debian.org/DebianEeePC/Model/701SD)

this explains it. 

this is however then just a matter of geting the driver compiled and stick it in a custom-livecd then the way i see it. (understand it) if i can somehow get that to work. i am going to install debian  from these install instructions here withing the next hour or so and i hope i can make it work. :)

---

### Post by ju2wheels on 2008-12-13
[http://wiki.eeeuser.com/](http://wiki.eeeuser.com/)
Check the Custom Eee Linux Distros section.

I would personally recommend Ubuntu Eee (different from eeebuntu).

---

### Post by cmay on 2008-12-13
i have tested all my linux choices now. i am typing this from crunchbang linux standard edition running from a usb stick and  this is the ONLY one that finds my internet connection. i have tried install debian lenny yet since i fear it wont work with the driver for my internet anyway. but i will install crunsh bang linux on it now. and if i can use remaster sys to create a small custom eee pc freindly image i will try to do that. and install debian when lenny is released as stable 

crunshbang linux almost works staright out of the box on this model. not sd card however. the rest seems to work. 

for those wiht the same problem and model i reccomend it. and backtrack 3 should have the drivers for the wireless and can be also used as usb stick distro using unetbootin.

i will mark tread as solved as this matter is concerned but if i find something really useful for others i will post it sometime.
thanks for your time .

---

### Post by ju2wheels on 2008-12-13
Ubuntu Eee has out of the box support for the wireless. They also include an optimized kernel specifically for the Eee. Also included are fixes for sleep and hibernation if you use your SDHC card as /home.

---

### Post by snowpine on 2008-12-14
Hi Cmay,

Any variant on Ubuntu 8.04 or 8.10 (Ubuntu, Xubuntu, Crunchbang, etc.) can be made to run on the eee by installing a custom kernel from Array.org. You can read how I installed Crunchbang on my eee 900ha here: [http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/](http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/)

The array.org kernel is the exact same one used in Ubuntu eee and eeeBuntu, two eee-specific distros.

The array.org kernel is not necessarily the only way to get Ubuntu working on the eee, but I found it to be very easy. My SD card works fine. Good luck!

---

### Post by cmay on 2008-12-14
:) @snowpine :)
thanks for posting the instructions. i have attached a screenie from my crunchbang linux install on a asus EeePc 701sd which i installed and followed your instructions. i will play around with sysremaster and make a custom crunchbang iso image and if that works i can install this for others as well.
 thanks all of you.

btw.
i did make a iso image using sysremaster already but it did not work the first time. i have the page on how to make a custom ubuntu bookmarked and i will try once more and if it works i will maybe write a small how to if that could be of use for anyone.

---

