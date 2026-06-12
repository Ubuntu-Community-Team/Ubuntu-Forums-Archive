---
title: "Trouble Installing packages"
date: 2006-07-18
forum: Desktop Environments
---

### Post by SevenRavens on 2006-07-18
I just got ubuntu on another computer. I have a linksys wireless G that needs to be installed so I can get internet. For some reason I cant get the disk to install! I know that on a windows system this disk would start up as soon as it is detected. On ubuntu it instead opens the folder with the files inside. No big deal you just click setup.exe and there it goes. Setup.exe opens up with add/remove. I wasnt sure on how to use this so I read up on it on the ubuntu website. It seems to me that add/remove is not detecting the software on that disk as a package that can be installed. 

Can anyone provide some tips for installing programs off of software? Or am I wasting my time by trying to install a linksys router. I am afraid to hear that its something that only works on windows.

---

### Post by llamakc on 2006-07-18
Are you saying that you are trying to run the Windows binary setup.exe on the LinkSys cd?

Are you trying to install some software to 'connect' to the router? Please explain your network more.

---

### Post by SevenRavens on 2006-07-18
I have a card that picks up the wireless signal from another computer in my house. In order for the computer to use that card software has to be installed. I am trying to install the binary setup.exe off of the software disk needed to use that wireless card.

---

### Post by llamakc on 2006-07-18
> **SevenRavens said:**
> I have a card that picks up the wireless signal from another computer in my house. In order for the computer to use that card software has to be installed. I am trying to install the binary setup.exe off of the software disk needed to use that wireless card.

You have a 'computer' that is broadcasting a wireless signal or you have a router that is broadcasting wireless?

On the computer you WANT to work, what card is inside of it? You can see the devices attached with the command `sudo lspci -v` from a Terminal.

Sounds like you're going about this the wrong way. You don't want to install the windows binary setup.exe at all. Let us know your hardware and we can hopefully help you from there.

---

### Post by SevenRavens on 2006-07-18
I have three computers in my home. One of them has a router that is broadcasting a wireless connection. Another one is recieving the connection from an internal card and the third one wants to be doing the same thing. I have an internal card installed in it. Its a linksys wireless-G pci adapter. Model number wmp54gs.

I tried putting in that command. It said command not found. I am guessing I did something wrong. However that card will not even be recognized if the software for it is not installed. I can already see in the device manager that it is there and it is labeled as "unknown", once the software is installed I should be able to use it as a possible method of internet connection. 

How can I install the windows setup.exe binary from the linksys CD?

---

### Post by llamakc on 2006-07-18
> **SevenRavens said:**
> I have three computers in my home. One of them has a router that is broadcasting a wireless connection. Another one is recieving the connection from an internal card and the third one wants to be doing the same thing. I have an internal card installed in it. Its a linksys wireless-G pci adapter. Model number wmp54gs.

I tried putting in that command. It said command not found. I am guessing I did something wrong. However that card will not even be recognized if the software for it is not installed. I can already see in the device manager that it is there and it is labeled as "unknown", once the software is installed I should be able to use it as a possible method of internet connection. 

How can I install the windows setup.exe binary from the linksys CD?

You can not install the windows setup.exe binary because you are not using Windows.

You are wrong about the card being able to work because of the software from the cd not being installed. 

Open the Terminal. On Gnome, this is at APPLICATIONS > ACCESSORIES > TERMINAL

type:

sudo lspci -v

Then, cut and paste that info here for us. 

What you NEED is a kernel module for your wireless adapter. With the info you paste in we can direct you to the correct WiKi page for installation.

Either the modules will be native to the kernel or will need some additional work to get running. From what I remember ndiswrapper works with that card. I could be wrong though.

Let's see that `lspci -v` output, please.

---

### Post by SevenRavens on 2006-07-18
I feel dumb asking this but could you specify what the first character in 'ispci -v' is?

---

### Post by llamakc on 2006-07-18
L but lowercase. Don't feel dumb at all. 

I wanted to mention that in the Linux kernel, a kernel module helps devices such as a wireless adapter, work. 

I believe you'll be using ndiswrapper to load the Windows native drivers.

---

### Post by SevenRavens on 2006-07-18
thank you for your help by the way. I am extremely new to linux. The only thing I know about linux is that it is different than windows. Since I took the time to learn how to build a computer from scratch I figured I might as well learn alittle about linux at the same time.

---

### Post by llamakc on 2006-07-18
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You may want to check out that page. If you do NOT have the 4306 chipset (and I'm not sure until you post that lspci output) you will have to use the ndiswrapper utility. That page is right here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by SevenRavens on 2006-07-18
it may take me a few minutes to get the message it displays as I have no way to get that message to this computer as fast as I would like.

---

### Post by llamakc on 2006-07-18
Cool, in that case we DO NOT need the whole thing. In fact, type this instead:

lspci

(without the -v)

and look for the line that looks like:

 0000:01:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


It will be something like that. What we're interested in is from Broadcom on to the end of those two lines.

---

### Post by SevenRavens on 2006-07-18
no such thing appears.

---

### Post by llamakc on 2006-07-18
This is a pci card and it is properly seated in the slot?

---

### Post by SevenRavens on 2006-07-18
Yes it is a pci card. It has been installed for about a week and it has been working all that time on windows which was previously installed on that computer.

---

### Post by llamakc on 2006-07-18
Ignore my comment about the 'Broadcom' part. Do you have any particular line for Network controller?

In the terminal you can run that command and search for 'Network' in the command's output to the screen using the command grep.

The line you would type would be:

lspci | grep Network

or

lspci | grep controller

Get the idea?

---

### Post by SevenRavens on 2006-07-18
there are three lines that say controller. USB controller. Ethernet controller. VGA compatable controller. Any of those sound good? The one that says ethernet controller says unknown device at the end of the line. Which would make sense if it were talking about my card because there's no software for it.

---

### Post by SevenRavens on 2006-07-18
the grep command didnt show me anything when I searched for network, but when I searched for controller it gave me two of the lines I spoke of before. VGA compatible controller and Ethernet Controller. The line is the same as it was when it was displayed with the lspci -v command.

---

### Post by llamakc on 2006-07-18
From what I find on the 'net you'll want to use the ndiswrapper utility and use the instructions on the second link I posted. Here it is again:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by llamakc on 2006-07-18
So, since this computer is NOT connected yet, you'll have to download the .deb packages to another computer and walk them over via floppy, cd, or usb stick to the target machine.

You want to get the one for your architecture (at the bottom of this page):

[http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)

and same with this page.

[http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)

and continue to follow the instructions....

---

### Post by SevenRavens on 2006-07-18
alright I got it and am writing it to a disk to bring it over to the other computer. I am fairly positive I know what to do from here. Can I assume that once this module is installed I will be able to choose the wireless connection as my internet connection?

---

### Post by llamakc on 2006-07-18
No, you have to follow the instructions on the ndiswrapper page. They include installing those two deb's, then retrieve the correct Windows file as documented on the ndiswrapper page @ section 2.4.

After you have loaded the ndiswrapper module, continue with that page. Hopefully you'll get to section 2.4.3 and be able to post from the newly-enabled computer.

Good luck.

---

### Post by SevenRavens on 2006-07-18
I'm alittle unclear as to how the windows driver is supposed to be extracted. cabextract and unshield are both on ubuntu? If i dont have them I can download them from the livedisk?
Are the files extracted on the working computer and then transfered over? or do I extract them once I have brought the binary driver over to the computer I want to work?

---

### Post by SevenRavens on 2006-07-18
Well I've been working on this day and I've made very little progress. Considering that mostly everything is build to work on windows can I assume that I will need some sort of software wrapper for everything I want to install? If that's the case than I will stick with windows. I've gotten to the point where I need to install the windows driver. However its the same problem as before. Its windows binary and it wont go on ubuntu. I have no extractor on my live disk it seems.

---

### Post by llamakc on 2006-07-18
Have you been trying to install this to a computer running the LiveCD?

If you had copy/pasted the contents of lspci there was a chance that the firmware could have been acquired and a native kernel driver module used instead of using Ndiswrapper.

Either way, with the piece of hardware you decided to purchase, the firmware from Windows must be used. 

I'm using a Broadcom wireless network adaptor with the BCM4306 chipset and I'm not using ndiswrapper. How'd I do it? I followed the directions on the howto pages.

The Ubuntu kernel module uses the Windows driver's FIRMWARE, not the binary setup.exe installer.

---

