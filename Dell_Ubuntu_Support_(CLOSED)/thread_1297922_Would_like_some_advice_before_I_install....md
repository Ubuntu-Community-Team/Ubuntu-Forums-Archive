---
title: "Would like some advice before I install..."
date: 2009-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ppillard on 2009-10-22
Hello all,

I am about to attempt to install Ubuntu on my Dell Inspiron 1525 laptop.  I previously had Vista on it (which I hate), and now it has become corrupted and will no longer boot.  I have a desktop as well that I have installed Ubuntu on (single boot system, no windows), and I love it.

If I had my druthers, I would install strictly Ubuntu on this laptop, but I have two reasons to include some version of windows on it as well: Itunes and my wife, who insists that I have some version of windows.

However, I understand you can use Wine to run windows applications under Ubuntu.  Does this require windows to be installed as well, or no?  

Next, does anyone have some advice before I embark on this?  I have the harddrive of the laptop out and I was gonna repartition it and format it on another windows laptop that I'm posting this thread from.

I have tried to install Ubuntu in the past on this dead notebook (before it died) while it was running Vista, but it always puked at me most of the way thru partition build process for a dual boot system.  I always just figured this was due to the silliness of Vista.

Whatever happens, I don't want to put Vista back on this machine. If I absolutely HAVE to have a version of windows on there, it will be XP.

Any advice on the best plan of attack?

---

### Post by jimmah6786 on 2009-10-22
> **ppillard said:**
> Hello all,

I am about to attempt to install Ubuntu on my Dell Inspiron 1525 laptop.  I previously had Vista on it (which I hate), and now it has become corrupted and will no longer boot.  I have a desktop as well that I have installed Ubuntu on (single boot system, no windows), and I love it.

If I had my druthers, I would install strictly Ubuntu on this laptop, but I have two reasons to include some version of windows on it as well: Itunes and my wife, who insists that I have some version of windows.

However, I understand you can use Wine to run windows applications under Ubuntu.  Does this require windows to be installed as well, or no?  

Next, does anyone have some advice before I embark on this?  I have the harddrive of the laptop out and I was gonna repartition it and format it on another windows laptop that I'm posting this thread from.

I have tried to install Ubuntu in the past on this dead notebook (before it died) while it was running Vista, but it always puked at me most of the way thru partition build process for a dual boot system.  I always just figured this was due to the silliness of Vista.

Whatever happens, I don't want to put Vista back on this machine. If I absolutely HAVE to have a version of windows on there, it will be XP.

Any advice on the best plan of attack?

ppillard,

Hello, I tend to find when setting up a dual booting machine, it is easiest to install windows first then to install Ubuntu. Grub, the boot loader used with Ubuntu, is able to see both partitions easily. While Vista or Windows boot loader can only see itself.

Regarding wine, wine does not require a windows os to be installed or for the i386 folder files to be available. It is a separate entity altogether. For programs that work with wine please visit their site..i think its winehq.com. There you can search through their AppDB for applications that have been tried and their success rates with other users. I believe as of now iTunes does not work (please correct me) with wine. However if you need iTunes for an iPod, I am pretty sure that Rhythmbox will be able to detect it, unless it is a Ipod touch or iPhone. 

Another idea if you wife insists that you have windows os installed on your computer is to run a virtual machine of windows using VirtualBox. This will allow you to have a strict Ubuntu installation and allow you to run Windows XP(or other flavors) on to of it. Not partitioning need for this.

Additionally, wine you can pretty much use any windows program. The only windows programs that I tend to have difficult running through wine are M$ Games and applications that require the new .NET 3.5 framework.

Anyway,

Hope this was helpful and best of luck,

Jim

---

### Post by Dennis N on 2009-10-22
Post #2 has good advice for you. Definitely install Windows first. WINE is not a Windows OS replacement. I have some programs running under WINE but not always 100% correctly. Some run 100% correctly, others occasionally crash at certain times (or not work at all) where they don't in Windows. As mentioned, check [http://www.winehq.org/](http://www.winehq.org/) for compatability reports.

I have an XP/Ubuntu notebook dual boot setup which works fine. Ubuntu installer takes care of the partioning very well. BTW, Ubuntu can access files on the XP partion which is handy.

---

### Post by adempewolff on 2009-10-22
if you need a windows replacement for 100% compatibility with windows pogramsyou can use virtualbox to run your windows vista from within ubuntu.

---

### Post by MelDJ on 2009-10-22
virtualbox will be quite useful if your wife is doing day to day activities. then, you dont need to install windows with ubuntu. and if windows crashes, you dont lose a lot

---

### Post by ppillard on 2009-10-22
So Virtualbox does not require an install of windows to be present to work?

And Rhythmbox will detect and sync to an ipod (I don't have a touch)? What about purchasing music and podcasts?

---

### Post by pablo180 on 2009-10-22
Virtualbox basically just installs and then runs windows as an application in Ubuntu so you'll need your Windows XP disc when you 'install' it on Virtualbox. I have never used it, but I have used similar applications, they just create a virtual hard drive that you can use for windows without having to reboot. 

If you are using the Dell 1525, I wouldn't bother with Jaunty if I were you. Mine is barely usable with Jaunty as Xorg uses 50-60% CPU at idle! Some problem with the new graphics drivers or something. 

Intrepid was fine though, but you might just want to skip it and try Koala.

---

### Post by Dennis N on 2009-10-23
VirtualBox is a good solution as mentioned. I use it to run another Linux distro with Ubuntu as a host. Lots of people install Windows in VirtualBox with Ubuntu as the host OS. As mentioned, you need a Windows installation disk to do this. There are licensing issues to consider, so you may want to look into that.

Google for tutorials on all this. There are lots of them. Also the VirtualBox manual should be studied.

---

### Post by MelDJ on 2009-10-23
for more info on virtualbox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by ppillard on 2009-10-25
Hmmmm, good input.  I just finished an install of Jaunty on my Dell before I read the last few posts.  However, it seems to be running really well.  Very quick and cool.  Install was a breeze, I'm very impressed.  

I figure I'll give Ubuntu a try as a stand-alone OS and see if I can show my wife how she can do all she normally does with the stock apps that come with Ubuntu (all she does is word processing and browse the web). Worst case scenario, I format and re-install with Windows this time (let's hope not).

I am trying to use Rhythmbox with my Ipod and while I have installed the mp3 and aac plugins, and I can see my ipod and it's contents, and I have downloaded some podcasts to put to my ipod, copying such files to the ipod has proven impossible so far.  I get no error messages of any sort, just a silent failure to meet my syncing requests.  What's the scoop?

---

