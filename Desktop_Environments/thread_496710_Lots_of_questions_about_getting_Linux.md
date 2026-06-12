---
title: "Lots of questions about getting Linux"
date: 2007-07-09
forum: Desktop Environments
---

### Post by gamelord12 on 2007-07-09
Okay, I have Vista, and now that I'm ready to completely wipe XP out of my life (I dual-boot between XP and Vista), I feel that as a nerd, I should have tried Linux by now, and I hear that Ubuntu is really nice.  So, before I start anything, I've got some questions:

1) I hear that Logitech devices tend to not work on Linux because people can't figure out how to code drivers for them or whatnot.  I have a Logitech MX1000 laser mouse and a Quickcam STX.  It's very important that my mouse works.  Will it?

2) Is there a client for Linux that will let me use AIM?  How about a client that will let me use AIM and all the features offered by 6.1 (video chatting, especially...if my web cam from the above program will work)?

3) I originally partitioned my hard drive with Partition Magic installed on my XP drive.  I won't be able to use that for my partitioning needs obviously, now that I'm going to be re-formatting that partition.  Does Ubuntu have a built-in partitioning tool?  If not, is GPartEd REALLY easy to use?

4) I'm a beginner programmer in C++.  Is there a compiler/IDE out there for me?

5) Any free applications for porting games over?  I believe my UT2004 will work on Windows and Linux, but other than that, I may be SOL.

6) Why is it that all the Linux-based OSes out there are held in such high regard?

7) Is there built-in help within Ubuntu for using the CLI?

8) What are the advantages of using the CLI, and what does it do that Vista or OS-X can't do with graphics?

9) What do I need to make an absolutely gorgeous interface?

10) Once I get all set up, how shall I go about showing off my Ubuntu partition?

---

### Post by goatflyer on 2007-07-09
Here's some answers:

1) I hear that Logitech devices tend to not work on Linux because people can't figure out how to code drivers for them or whatnot. I have a Logitech MX1000 laser mouse and a Quickcam STX. It's very important that my mouse works. Will it?


Pop in a Live CD and give it a try... it won't install anything and you can see if your hardware works.


2) Is there a client for Linux that will let me use AIM? How about a client that will let me use AIM and all the features offered by 6.1 (video chatting, especially...if my web cam from the above program will work)?


I use 'gaim' but its now called 'pidgin'.  there are plenty of chat programs on the live cd also

3) I originally partitioned my hard drive with Partition Magic installed on my XP drive. I won't be able to use that for my partitioning needs obviously, now that I'm going to be re-formatting that partition. Does Ubuntu have a built-in partitioning tool? If not, is GPartEd REALLY easy to use?


yes and yes.

4) I'm a beginner programmer in C++. Is there a compiler/IDE out there for me?

Yes, with Ubuntu open a terminal and type:

sudo apt install build-essentials

this will give you gcc, make, and so on.


5) Any free applications for porting games over? I believe my UT2004 will work on Windows and Linux, but other than that, I may be SOL.

Not sure.   Check out wine-hq, cedega, etc.

6) Why is it that all the Linux-based OSes out there are held in such high regard?

They're FREE dammit! :)   not to mention you don't get orphaned by refusing to buy the next version.  You keep control of your own computer.

7) Is there built-in help within Ubuntu for using the CLI?

There are man pages for each command, but there are some general Linux command line web pages out there.

What are the advantages of using the CLI, and what does it do that Vista or OS-X can't do with graphics?

You can paste command sequences that people send you in forum replies.

9) What do I need to make an absolutely gorgeous interface?

Compiz or Beryl.  But this is a subjective question.

10) Once I get all set up, how shall I go about showing off my Ubuntu partition?

sudo fdisk -l /dev/hda

or else

System>Administration>Disks

---

### Post by gamelord12 on 2007-07-09
Where can I get the Live CD?  I downloaded the regular .iso for Ubuntu but didn't see any other links for a Live CD.  Are they both on the same .iso?  Also, would I only have to double-click on my drive with the Ubuntu disc to run the Live CD?  If my mouse isn't supported with the OS itself and I needed to download drivers to make it work, would I be able to do that with the Live CD?

---

### Post by aysiu on 2007-07-09
The **Desktop CD** is both a live *and* installer CD.

---

### Post by bcmiller on 2007-07-09
I just wanted to add to the good response you already received.

> **gamelord12 said:**
> Okay, I have Vista, and now that I'm ready to completely wipe XP out of my life (I dual-boot between XP and Vista), I feel that as a nerd, I should have tried Linux by now, and I hear that Ubuntu is really nice.  So, before I start anything, I've got some questions:

2) Is there a client for Linux that will let me use AIM?  How about a client that will let me use AIM and all the features offered by 6.1 (video chatting, especially...if my web cam from the above program will work)?

Video and Voice chatting will not work.  You will be able to text chat on any network but there is no reliable voice or video chatting available in linux (key word reliable)

> **gamelord12 said:**
> 3) I originally partitioned my hard drive with Partition Magic installed on my XP drive.  I won't be able to use that for my partitioning needs obviously, now that I'm going to be re-formatting that partition.  Does Ubuntu have a built-in partitioning tool?  If not, is GPartEd REALLY easy to use?

The Ubuntu Install will do this be default, just pick the parition that has XP as your install partition.
> **gamelord12 said:**
> 5) Any free applications for porting games over?  I believe my UT2004 will work on Windows and Linux, but other than that, I may be SOL.

You will not be porting any games over that are not open source.  Projects like wine and Cedega provide an application layer that mimics a windows install.  I haven't had much luck with them in the past but some people like them fine.  UnrealTournament and other games that use OpenGL instead of DirectX are easier to use.
> **gamelord12 said:**
> 6) Why is it that all the Linux-based OSes out there are held in such high regard?

The basis of all of this software is the [Free Software Foundation]("http://www.fsf.org") and thier idea that you should have the right to modify and distrubute any program you use on your computer.  Around 1998 or so the word "Open Source" was invented to replace "Free Software" and because of this people sometimes miss the larger idea of why this exists.  

That and... it's based on Unix that is much more stable and secure.  So when you can get security without giving up your freedom it is a good thing.

> **gamelord12 said:**
> 7) Is there built-in help within Ubuntu for using the CLI?

man pages are great plus this site should be useful.  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

> **gamelord12 said:**
> 8) What are the advantages of using the CLI, and what does it do that Vista or OS-X can't do with graphics?

It's less about what it can do and more about how easy it is to get help via the CLI.  If you look in this forum you will see a lot of commands given to solve problems.  Saying type this "...."  then after that type this "..." can do the same as a page worth of "first click here".  You can explain how to get things done quicker.

Plus you can use a script that will automate a lot of things for you, for an example of this look for Automatix. (I am not recommending that you use Automatix, but it's a great example of what can be done with a CLI).

> **gamelord12 said:**
> 9) What do I need to make an absolutely gorgeous interface?
Compiz-Fusion is great (It's a merge of Beryl and Compiz)  and you can visit [www.gnome-look.org](www.gnome-look.org) to customize your icons etc... for Ubuntu and [www.kde-look.org](www.kde-look.org) for Kubuntu.

> **gamelord12 said:**
> 10) Once I get all set up, how shall I go about showing off my Ubuntu partition?

Does this mean how to make a video?  look for "screencast"

---

### Post by scott_g on 2007-07-09
> **gamelord12 said:**
> 
1) I hear that Logitech devices tend to not work on Linux because people can't figure out how to code drivers for them or whatnot.  I have a Logitech MX1000 laser mouse and a Quickcam STX.  It's very important that my mouse works.  Will it?


I have a MX3200 Logitech Keyboard/Mouse combination (Laser Mouse), and it worked out of the box for me.  Also, I have a logitech webcam, not sure of the model, but it sounded similar to yours.  It again worked right out of the box without the need for extra drivers and such.

Scott

---

### Post by gamelord12 on 2007-07-09
I'm running off the Live CD now.  I'm very impressed with how little RAM it uses.  Though I miss my 3D desktop effects and a live search feature (like Spotlight, not the Windows Live search engine), I'm only using about 200 MB rather than 1 GB.  I take it that once it's actually installed, programs will load faster, correct?

I am having a problem with Rhthmbox.  It doesn't want to play any of my music, or maybe I just don't know how to add a folder to the library (I went through and hit Add, but none of the files in it show up).  I can't even play songs off of my iPod, even though it can see all the files on it, it just doesn't want to play them.

Another thing: I've got a UXGA monitor and yet it won't let me put my resolution any higher than 1024x768.  Graphics driver issue?  I've got a GeForce 7900 GTX.  I probably won't be able to install it if I'm running off the Live disc though, huh?

---

### Post by bcmiller on 2007-07-09
The music and graphics issues are very easy to fix after you have it installed.  

You will just enable the restricted drivers that will allow you to play mp3 and dvds etc...

It will run faster on your harddrive than it does on the CD.

---

### Post by fflarex on 2007-07-09
For search, try adding the deskbar applet to one of your panels. If that doesn't quite cut it for search, beagle is amazing and there are several apps that give it a pretty slick graphical interface too. Or... Google Desktop just got a Linux counterpart, but I don't think that's exactly what you're looking for. As far as 3D desktop effects go, nothing beats Compiz Fusion (though it's beta software and and somewhat difficult to install).

Are your music files in MP3 format? Some formats are not supported out-of-the-box due to licensing restrictions, but this is fairly easy to fix. There are guides all over the web and these forums.

I can't help you with graphics, sorry. This was my biggest hurdle when I switched over as my ATI card was not supported by the Live install CD (so I couldn't even run the Live CD). If it's a relatively common card though, you should have no trouble finding instructions on how to get it working correctly. Also, I'll just note that you should make sure wireless works if you need it. Most people who have bad experiences with Linux are because of either graphics or wireless.

And yes, it will be much faster once it's installed.

---

### Post by gamelord12 on 2007-07-09
Well just based on the fact that it's something different and I'll be running XP through a virtual machine for the few programs that I need it for, I'll use my XP partition for Ubuntu.  I'll get to it sometime in the next week or so.  I told my dad how it didn't use many resources and he said that after I show him the features and he decides whether he likes it or not, he may put it on our old 2001 Gateway for some faster performance and less fear of viruses.  If this comic ([http://xkcd.com/c272.html](http://xkcd.com/c272.html)) is anywhere near accurate, the computer should be safe even from my family, who seem to be magnets for every type of malware under the sun.

Thanks guys!  You'll probably see me around some of these boards more in the future.

---

