---
title: "how do I install firefox on kubuntu 5.04 ppc without internet?"
date: 2006-01-10
forum: General Help
---

### Post by tenev on 2006-01-10
is there an installer for firefox that can run on kubuntu 5.04 and get me a mozilla firefox browser installed? konqueror is driving me nuts as it won't load my internet connection applet. I have easily installed java in /usr/java/, now i need to load the plugin on a browser but the only browser i see on kubuntu 5.04 is konqueror.
i tried downloading a tar file. it extracts the package. none of the files in the package are executable and i don't even know where to put the extracted folder. i tried downloading opera, same story...

please help me out. i am looking for an installer that i can download from my windows machine and move it over to my powerpc on a removable device.

thanks for your help.

---

### Post by Glass Casket on 2006-01-10
If you have internet, use Adept which is located in System. Find Firefox from the huge list, click on it then click install. Then go on top and click Commit Changes.

---

### Post by tenev on 2006-01-11
[QUOTE=Glass Casket]If you have internet, use Adept which is located in System. Find Firefox from the huge list, click on it then click install. Then go on top and click Commit Changes.[/QUOTE]

i don't have internet. that's why i need firefox, to get on the internet via java plugin.

---

### Post by Drain on 2006-01-11
[QUOTE=tenev]i don't have internet. that's why i need firefox, to get on the internet via java plugin.[/QUOTE]

You can go to the Ubuntu software repositories [here]("http://archive.ubuntu.com/ubuntu/"), and under the directory "pool/main/m/mozilla-firefox/" there are a whole bunch of *.deb package files for firefox. You'll want the one called "mozilla-firefox_1.0.7-0ubuntu0.1_powerpc.deb"  

Download that, copy it to your Ubuntu distrobution, and you should be able to install it from the command line. Open up a terminal, and type the following: 

sudo dpkg -i mozilla-firefox_1.0.7-0ubuntu0.1_powerpc.deb 

Enter your password as needed. 

If when installing the package, you have complaints about "missing dependencies" - go back to the Ubuntu software repositories, and grab the necessary files, installing them in the same way as the firefox package.  I am not sure what packages firefox depends on, so there might be several of these that you have to grab - believe me, it's a lot easier when you have internet up and going, and then it's just a simple "sudo apt-get install" whatever.... 

Which leads me to a question - how do you usually connect to the internet with this machine? Modem? Wireless? Ethernet? Because I'm not sure if installing firefox on your computer is going to solve your problem.

---

### Post by tenev on 2006-01-12
[QUOTE=Drain]You can go to the Ubuntu software repositories [here]("http://archive.ubuntu.com/ubuntu/"), and under the directory "pool/main/m/mozilla-firefox/" there are a whole bunch of *.deb package files for firefox. You'll want the one called "mozilla-firefox_1.0.7-0ubuntu0.1_powerpc.deb"  

Download that, copy it to your Ubuntu distrobution, and you should be able to install it from the command line. Open up a terminal, and type the following: 

sudo dpkg -i mozilla-firefox_1.0.7-0ubuntu0.1_powerpc.deb 

Enter your password as needed. 

If when installing the package, you have complaints about "missing dependencies" - go back to the Ubuntu software repositories, and grab the necessary files, installing them in the same way as the firefox package.  I am not sure what packages firefox depends on, so there might be several of these that you have to grab - believe me, it's a lot easier when you have internet up and going, and then it's just a simple "sudo apt-get install" whatever.... 

Which leads me to a question - how do you usually connect to the internet with this machine? Modem? Wireless? Ethernet? Because I'm not sure if installing firefox on your computer is going to solve your problem.[/QUOTE]

Hello Drain. thanks for the instructions. I will give it a try. I have LAN Ethernet but my network has this authentication tool for each user called Firebox... it's quite annoying bc you need to have a browser window (with java applet loaded and authenticated) minimized whenever you want to use the internet...that's one of the things that comes with my job, unfortunately.

Edit: That's a lot of packages. I downloaded 4 out of 9 or 10, but as i started installing the first package, other dependecies were needed so i give up. maybe i will wait till i get on a direct internet connection. is there an easier way??

---

