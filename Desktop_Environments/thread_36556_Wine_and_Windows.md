---
title: "Wine and Windows"
date: 2005-05-23
forum: Desktop Environments
---

### Post by YaAqoB on 2005-05-23
Hi. I have got my windows drive mounted as a read only drive.
I want to use DVDShrink as I can't get DVDRip to install.
If i go to my mounted windows drive and use wine to run DVDShrink it starts fine and every thing appears to be fine. Except I can't access my dvd rom.
Is there a way that I can do this or do I have to use wine to install DVDShrink to my linux partition?(Which I am having huge issues with) :)

---

### Post by sonny on 2005-05-23
I've try [this](http://www.ubuntuforums.org/showthread.php?t=36112) a couple of day ago, and it went fine and now I have dvdshrink and dvddecrypter working perfectly... you may want to give it a try.

---

### Post by YaAqoB on 2005-05-23
THanks for your reply.
I have been trying this but when it comes to the part about installing dvd encryptor it tries to install it to c:\program files\ which of course is a read only NTFS partition.
WHen I run winesetup I get the following error:

james@YaAqoB:~$ winesetup
CBase::AutoConf:GetWinInstalls: unable to grep /mnt/WindowsDrv/msdos.sys: child process exited abnormally
CBase::AutoConf:GetWinInstalls: unable to grep /mnt/WindowsApps/msdos.sys: child process exited abnormally


Any ideas?

---

### Post by sonny on 2005-05-25
mmmm... when it says c: it means the wine C drive, as you should know, wine creates a "partion" in its folder, wich is in /home/usrname/.wine/fake_windows/Program Files

that's the path on wich you should be installing dvddecripter, because you don't have write permission to your mount in windows. If you do have permissions I would recomend you to create a windows-linux "exchange" partition, so you can share for both sides.

Anyway... you should look up for this folder and that would be all.

---

### Post by YaAqoB on 2005-05-25
Here is the screen shot of the error I get when trying to install it.
[IMG]http://www.nabc.org.nz/Screenshot.png[/IMG] 
Anyone have any clues?

---

### Post by jdong on 2005-05-25
First of all, if you seriously want to use WINE, install the latest version. [http://www.winehq.com/]("http://www.winehq.com/") has an APT repository for Ubuntu (warty and hoary), and I also provide virtually the latest WINE via Ubuntu Backports, too.
 
I recommend the latter, because I try to stay in line with Ubuntu much more than WineHQ does. See the link in my sig for more information on adding Backports to your APT sources.list, **making sure you use a mirror site**, given by the Mirrors link. Then, perform an upgrade via apt-get or Synaptic, and you'll be running a very up-to-date WINE.

---

### Post by YaAqoB on 2005-05-25
Thanks for your help.
The version I have  is the latest from the Ubuntu Backports.
To tell you the truth I don't want to use WINE. I just can't live without DVDShrink.
Don't worry though, I have now given up. I'm going to just keep winodws installed.
Thanks agin for your help.

---

### Post by jdong on 2005-05-25
Hmm, weird.
 
Oh well, that's WINE for ya... early alpha, almost 0.9, eventually will be stable. :D
 
 
There are ways to dvd-shrink using transcode and friends natively under Linux. I found a howto a while back on Gentoo's forums. That worked quite nicely, but it is a bit tedious and may appear daunting (all console-based).

---

