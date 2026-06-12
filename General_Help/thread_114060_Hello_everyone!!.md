---
title: "Hello everyone!!"
date: 2006-01-07
forum: General Help
---

### Post by alpha128 on 2006-01-07
First I wanna thank the folks at ubuntu/kubuntu for the great work they have done. I've been a OSS (GNU/Linux, FreeBSD) user for almost 10 years and I have to say that Ubuntu/Kubuntu is as close to fully polished as any Linux distro I've ever seen (and trust me, I've jumped from distro to other free unixes and back through all that time). So again thank you and now for my question:

Well, even though I've used Linux for a pretty long time (stopped using MS Windows alltogether in 2000), now I'm actually switching friends and family to linux now that I feel that it's as close to easy as MS to use in a novices desktop, except that in this case I'm trying to switch my girlfriend's machine to Kubuntu (mainly because I know she'll get a kick out of amaroK and Kopete), and everything works well EXCEPT the fact that she speaks Mandarin Chinese, and well, scim/skim don't work well in Kubuntu 5.10. So the question is, has there been any improvement in scim/skim compatibility in kubuntu 5.10, and are there any .deb packages I can install, or am I stuck with having to either install Gnome/Ubuntu (except that she really likes KDE 3.5.0 very much), which has better support for scim? Any help would be much appreciated! 

Thanks for listening!!

Ron

---

### Post by GoldBuggie on 2006-01-07
Perfect integrated support of scim/skim isn't really supported but following this howto
[http://www.ubuntuforums.org/showthread.php?t=94447]("http://www.ubuntuforums.org/showthread.php?t=94447")

you will get a workable scim solution. With that guid you will get working language input in all apps. You will have to change some things for chinese since that one is mostly for japanese. Some trouble are still there. The skim icon in the systray isn't working and installing firefox 1.5 from the web gives problems. But downloading the later firefox from the repository supplied in the howto should work.

Getting scim/skim to work in the next version of kubuntu seems to be on the go and looks promising. But until then we will have to live with what we got. But I can happily say that the above howto has helped me do all the writing I need when I was in Japan and is hopefully sufficiant for your needs as well.

Btw the repository that I'm using is from the chinese ubuntu distro. Maybe you should look into installing the chinsese ubuntu?

---

### Post by alpha128 on 2006-01-08
Hey man, thank you very much for your reply! Well, I tried every step on the link you gave me, and well, I did have Japanese which is great and all, but I couldn't find a way to install the scim-chinese and scim-tables-zh packages. Apt was telling me that the installed version of scim and skim required a different set of packages rather than the ones on the repositories. If you have any ideas I'd appreciate it. And well, thanks again for helping me, I truly appreciate it.

Ron

---

### Post by GoldBuggie on 2006-01-08
Using the above mentioned guide and installing scim AFTER you have added the new repositories and doing a update you should be left with version 1.4.2.  That is the version you have installed right? You can check which you have installed by doing ```
sudo dpkg -l | grep scim
```. Then when you have installed that version you should be able to install scim-tables-zh etc. If you want a direct look at what the repositories give you use your webbrowser and go to the http repository link directly.
[http://archive.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/]("http://archive.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/")

You will see the scim directories and you can download the .deb's there directly. Since I've installed the 0.5.3 version of scim-tables-ja, I'm pretty sure the zh table will work as well. If apt complains like it does for you then make sure you don't have any old versions installed. You can also try and use the force install for apt.
```
sudo apt-get -f install <package-name>
``` But that shouldn't be necessery. So check your versions and use the above link for downloading the debs to your harddrive if you feel that is easier than using synaptic.

If you are unsure the please paste the the output of *sudo dpkg -l | grep scim* and *sudo dpkg -l | grep skim* and I will try and help you from that

---

