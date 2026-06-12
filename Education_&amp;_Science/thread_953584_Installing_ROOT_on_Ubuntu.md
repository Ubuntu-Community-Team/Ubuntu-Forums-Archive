---
title: "Installing ROOT on Ubuntu"
date: 2008-10-20
forum: Education &amp; Science
---

### Post by gemmala on 2008-10-20
Hi,

I've just started doing research in High Energy Physics, and I'm wondering if it's possible to use Ubuntu to work from home - I need to install ROOT. Has anyone out there done it (the instructions on the website don't work), or am I going to have to trade Ubuntu for Scientific Linux?

---

### Post by Toet on 2008-10-20
When I try the binary version I find on this website:

[http://root.cern.ch/root/Version520.html](http://root.cern.ch/root/Version520.html)

By downloading this file:

[ftp://root.cern.ch/root/root_v5.20.00.Linux.slc4.gcc3.4.tar.gz](ftp://root.cern.ch/root/root_v5.20.00.Linux.slc4.gcc3.4.tar.gz)

And unpack it and run ./root from the root/bin directory, I seem to have a working ROOT.

But I do not know if that is what you want.

---

### Post by fguo79 on 2008-10-22
I have been using ROOT on my Kubuntu 8.04 for almost 6 months now. I don't think there is any thing special about installing ROOT on ubuntu than any other Linux distibution. All you need to do is just follow the instructions on the ROOT webpage, download the source file and compile it yourself. of course make sure you have the build-essential package installed on your ubuntu for the compiling work.

---

### Post by ssam on 2008-10-23
ROOT has recently entered debian, and will be in the repos in ubuntu intrepid (due out by the end of october).

---

### Post by jalirious on 2008-10-29
root 5.17/04 on 'gutsy' ubuntu 7.10 (or 8.04) is done easily 

include the following line in your /etc/apt/sources.list 

deb [http://mirror.phy.bnl.gov/debian-root/ubuntu](http://mirror.phy.bnl.gov/debian-root/ubuntu) gutsy main contrib 

[if you have added any other root related repositories, e.g. for clhep, remove them] 

apt-get update 
apt-get upgrade
apt-get install root-system

[either igmore warnings/errors, or learn how to add public keys to your list, in a rush]

then in your synaptic install

libroot-minuit5.17 
root-plugin-minuit2

Takes roughly 2 minutes all together.

---

### Post by 080729jk on 2008-10-30
&#32431;&#31929;&#30340;&#20804;&#24351;&#22992;&#22969;&#26469;&#33258;&#20116;&#28246;&#22235;&#28023;&#65292;[**&#28145;&#22323;&#33402;&#26415;&#20889;&#30495;**](http://www.chuncui.net/szysxz.htm) &#22240;&#20026;&#21916;&#27426;&#33258;&#30001;&#21644;&#20805;&#28385;&#28608;&#24773;&#30340;&#29983;&#27963;&#65292;&#36208;&#21040;&#19968;&#36215;&#12290;&#24444;&#27492;&#20043;&#38388;&#31616;&#21333;&#32431;&#31929;&#65292;&#20026;&#20102;&#24515;&#20013;&#30340;&#37027;&#20221;&#20449;&#24565;&#21644;&#39556;&#20658;&#65292;&#39281;&#21547;&#28608;&#24773;&#30340;&#24037;&#20316;&#21644;&#29983;&#27963;&#12290;[**&#28145;&#22323;&#20154;&#20307;&#25668;&#24433;**](http://www.chuncui.net/szrtsy.htm)&#32431;&#31929;&#26159;&#20010;&#23478;&#65292;&#21253;&#21547;&#25152;&#26377;&#21592;&#24037;&#21644;&#23458;&#25143;&#65292;[**&#28145;&#22323;&#20010;&#20154;&#20889;&#30495;**](http://www.chuncui.net/szgrxz.htm) &#22312;&#36825;&#20010;&#22823;&#23478;&#24237;&#37324;&#65292;&#27809;&#26377;&#34394;&#20266;&#30340;&#38754;&#23380;&#65292;[**&#21271;&#20140;&#20154;&#20307;&#25668;&#24433;**](http://www.chuncui.net/)&#21482;&#26377;&#20154;&#19982;&#20154;&#20043;&#38388;&#35802;&#25370;&#30340;&#38754;&#23545;&#65292;&#26469;&#21543;&#65292;[**&#19978;&#28023;&#20154;&#20307;&#25668;&#24433;**](http://www.chuncui.net/shrtsy.htm)&#25105;&#20204;&#26399;&#24453;&#20320;&#21152;&#20837;&#36825;&#20010;&#22823;&#23478;&#24237;&#12290;

---

