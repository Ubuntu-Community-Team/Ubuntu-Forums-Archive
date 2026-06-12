---
title: "General Questions From Installation"
date: 2009-04-28
forum: General Help
---

### Post by dstein on 2009-04-28
Upon upgrading to Ubuntu 9.04, I ran into a bunch of problems that took me a lot of time to solve. Fortunately, everything is resolved and I learned some things along the way. I have a bunch of questions that came up that I was unable to find answers to. Answering any of the following questions would be greatly appreciated.

Is there any general purpose linux or ubuntu books that you recommend. I did not have internet access when I ran into trouble, and a general-purpose book would have been very useful. For the problems I had, I think a general-purpose linux/unix book would have been more useful than an Ubuntu-specific book, since I had to run commands from the recovery terminal. However, a book that also included Debian/Ubuntu material, such as dpkg and aptitude would have been helpful as well. Again, I know that there is so much available on the internet, but I did not have access to a browser, and I would like to have a book on my shelf for such times.

What happened to xorg.conf? With such broad entries, how does X know which video drivers to load? What facility is now used to edit which driver is loaded and its settings? (from above, I am looking for the type of book that addresses such questions)

Is there any web browsers (textual) that can be run from the terminal. There were a few times that this would have been very helpful from the recovery console. Again, this is the type of material I would like to be covered in the book I am looking to purchase.

How can I mount and access a flash drive from recovery mode? I am used to plugging in the drive from within gnome and having everything load automatically.

After reverting back to integrated graphics and still having problems, I ultimately got my video working correctly by adding a deb entry to sources.list for newer drivers. However, doing so also adds a bunch of available upgrades to update-manager that I don't want installed, so I unchecked. Is there any way to have update-manager permanently ignore these, or configure the deb entry to only access the one file I need, not everything in that repository?

Thanks.

---

### Post by tommcd on 2009-04-28
> **dstein said:**
> 
Is there any general purpose linux or ubuntu books that you recommend. 
The linux bible book is a good general purpose linux book. I have the 2006 edition:
[http://www.amazon.com/Linux-Bible-2009-KNOPPIX-openSUSE/dp/0470373679](http://www.amazon.com/Linux-Bible-2009-KNOPPIX-openSUSE/dp/0470373679)
This is a good Ubuntu specific book. I read the 1st edition:
[http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590599918](http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590599918)
In general though, the info in books is limited compared to what is available online. I have lots of files saved on my computer from stuff I read online. It is a big help if I forget something and I need a quick reference. I would suggest building a library like this yourself. When ever you read something useful.... save it!
> **dstein said:**
> 
What happened to xorg.conf? With such broad entries, how does X know which video drivers to load? What facility is now used to edit which driver is loaded and its settings? 

See the xorg stuff from the 8.10 release notes. This still applies to 9.04:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)
> **dstein said:**
> 
Is there any web browsers (textual) that can be run from the terminal.
There is **links** and **lynx**. They are both in the Ubuntu repos. They have a bit of a learning curve though.
> **dstein said:**
> 
How can I mount and access a flash drive from recovery mode? 

Create a mount point for the drive and then mount it to that mount point.
> **dstein said:**
> 
After reverting back to integrated graphics and still having problems, I ultimately got my video working correctly by adding a deb entry to sources.list for newer drivers. However, doing so also adds a bunch of available upgrades to update-manager that I don't want installed, so I unchecked. Is there any way to have update-manager permanently ignore these, or configure the deb entry to only access the one file I need, not everything in that repository?

You can run: "sudo aptitude hold pkg_name" to hold a package. This works in Debian. I assume it works in Ubuntu also. You can run: "sudo aptitude unhold pkg_name" to unhold the package.

---

### Post by kpkeerthi on 2009-04-28
[A Practical Guide to Linux(R) Commands, Editors, and Shell Programming by Mark G. Sobell]("http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131478230/ref=sr_1_1?ie=UTF8&s=books&qid=1240902895&sr=1-1")

[Practical Guide to Ubuntu Linux by Mark G. Sobell]("http://www.amazon.com/Practical-Guide-Ubuntu-Linux-Versions/dp/0137003889/ref=sr_1_1?ie=UTF8&s=books&qid=1240902959&sr=1-1")

xorg-server now uses hotplug. It means that now it discovers and configures your hardware dynamically.

[Lynx]("http://en.wikipedia.org/wiki/Lynx_(web_browser)")

To mount your flash drive from command-line
1. ```
sudo mkdir /media/usbflash
``` 
2. ```
mount /dev/sdb -t auto /media/usbflash
```
* /dev/sdb => The device name could be different for you. You can find the device name using:
```

sudo fdisk -l

```
* -t auto will work for most filesystem types. Filesystem-specific values can be found [here]("https://help.ubuntu.com/community/Fstab").

---

