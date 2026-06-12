---
title: "Noob... where do I start?"
date: 2006-01-02
forum: General Help
---

### Post by catalytic on 2006-01-02
Really don't know where to start.....:( 

I am currently running Windows XP on an AMD athalon XP 2000. I have one already partitioned drive. C: has windows and all my programs 9.99GB with 167MB free, and D: which has all my music etc 64.5BG with 16.9GB free.

I have chosen Ubuntu warty to install. I have to image burned to a cd all ready to go.

But where do I start? Been doing a lot of reading but, I just can't seem to understand the actual steps. Having never used Linux or installed an operating system before, it may as well be in another language.

What is the first step?
I want to install Ubuntu on my D:, so I have to partition it, I want 10GB for Ubuntu. Do I partition after installing Ubuntu or before?

Do I have to reformat my whole D:? Will this mean I loose everything I have on that drive? Even if I make a back up and store this on my C: which I don't want to touch? Basically can I undo it if I delete it? Do I have to delete everything?

Can I just buy an external USB hard drive and install it on that? or do I need to add more to my existing hard drive?

How do I clear space so that Ubuntu is at the start of the drive?

I really want to use Linux, I HATE WINDOWS, I have nothing but problems with error messages and the windows update killed my internet a few days ago. It just seems like this is a little to hard for the average user like me.

I would like to know the easiest way I can do this. I have tried the live CD, but you really can't do anything more than browse the web with it, I would like to play games, and download torrents, use it as my main OS.

Thanks

---

### Post by professor_chaos on 2006-01-02
Dont use Warty, you should really use breezy, or at the very least hoary!

Partition before if you want, or you can put your faith in the Ubuntu partitioner during install process. (Make sure to backup your data first. You probably know this, but partitioning is not a failsafe process.

No format of your entire HD needed. Just a partition. 

If using an external drive (more complicated) you need to be sure your bios can boot to a usb device.

You dont need ubuntu at the start of the drive, but you can try to place a partition (ext3) at the start of the drive if you want.

Step1a.) Backup data
Step1.) partiton with Partition Magic (or other) in windoze. OR Began install process and you will come to a part in the installation to partition. At this point you can cut the drive into 2+ partitions. One for windoze and one for ubuntu (and you can make another fat32 partition if you want to share (writable by both OS's) data between these diff OS).
Step2.) Finish install and Start having fun

Don't be afraid to use the forum search function, or to use google to find common problems you might be having. I know your questions are somewhat common questions for new users and there are probably lots of threads about all of this. Post more questions if you have them.  Good luck.

---

### Post by catalytic on 2006-01-03
LOL Thanks! I read somewhere that wart was easier to install with XP. What's the difference between warty and breezy? No more blank cd's left!

So my next question would be how do I partition my D:? I know I have to defrag first...
So if I use the Ubuntu partitioner during the install, can I restore my backed up data when or if something goes wrong?

---

### Post by handy on 2006-01-03
Automatix:  [http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

Might be a good reason to think about a Breezy install!  :p 

Virtually all of this Open Source software is in a constant state of flux, being improved ALL the time.

So with few exceptions it is always improving, the latest stable version of anything these days is the way to go.

Re: Partitioning your xp drive, PartitionMagic (runs on windoze) has been my friend for a long time now, there is a free *nix clone of this software called QTpart.

Read these for more  partitioning info:

[http://www.mepis.org/node/6336](http://www.mepis.org/node/6336)

[http://www.linuxquestions.org/questions/showthread.php?t=259326](http://www.linuxquestions.org/questions/showthread.php?t=259326)

Good Luck

handy

---

### Post by Iandefor on 2006-01-03
[quote=catalytic]LOL Thanks! I read somewhere that wart was easier to install with XP. What's the difference between warty and breezy? No more blank cd's left!

So my next question would be how do I partition my D:? I know I have to defrag first...
So if I use the Ubuntu partitioner during the install, can I restore my backed up data when or if something goes wrong?[/quote] Warty Warthog was the first release, and was primarily a pilot of sorts. They released it, and then went in and changed the most prominent problems/requests, and then released it again. The new version they called Hoary Hedgehog, where they did something similar. They went in and changed things they thought it was important to fix, and they released it and called it Breezy Badger. They're doing the same thing to Breezy right now, and the next release will be called Dapper Drake.

If all you're going to do is format D:, then there's no need for defragging.
It'll delete all the data on the partition. I suggest you get it on some kind of external media, and then, if you need to go back to Windows, format it to a Windows disk and copy everything back. 

> 
Do I partition after installing Ubuntu or before?
 You partition the disc in the Ubuntu installer, right before it goes in and installs everything to disc.

> 
How do I clear space so that Ubuntu is at the start of the drive?
I really want to use Linux, I HATE WINDOWS, I have nothing but problems with error messages and the windows update killed my internet a few days ago. It just seems like this is a little to hard for the average user like me.
I would like to know the easiest way I can do this. I have tried the live CD, but you really can't do anything more than browse the web with it, I would like to play games, and download torrents, use it as my main OS.
 
You don't need to clear space so it's at the start; just make it install to D:.
If you want to be able to boot Windows after installing Ubuntu, [see the wiki]("https://wiki.ubuntu.com/WindowsDualBootHowTo"). Good luck getting Ubuntu set up to use as your primary OS!

---

### Post by catalytic on 2006-01-03
Thank you people for your help!

Just to confirm... Do I HAVE to format D:? if I do I will loose everything I have on there right?

darn... I'm out of discs.....noooooo, looks like I will have to wait a while.

So Breezy is the one you suggest?

I'm so eager to get it all up and running, now that I know I can somehow managed to install it!

I'm defragmenting D: at the moment (hadn't bothered to for ages so thought, may as well) Taking a long time, but I have a nice chunk of empty space at the end.

Time to go play with the Live CD a bit more.... thanks again, least I know where to come for my next Q&A!

---

### Post by handy on 2006-01-03
Have a look here:  [http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)

handy

---

### Post by Iandefor on 2006-01-03
[quote=catalytic]Thank you people for your help!
Just to confirm... Do I HAVE to format D:? if I do I will loose everything I have on there right?
darn... I'm out of discs.....noooooo, looks like I will have to wait a while.
So Breezy is the one you suggest?
I'm so eager to get it all up and running, now that I know I can somehow managed to install it!
I'm defragmenting D: at the moment (hadn't bothered to for ages so thought, may as well) Taking a long time, but I have a nice chunk of empty space at the end.
Time to go play with the Live CD a bit more.... thanks again, least I know where to come for my next Q&A![/quote] 

Well, you can resize D: and make a new partition, which it sounds like you're doing anyways.
Yes, the suggestion is to use Breezy. It's much more polished than Warty.
If you're on a broadband connection, there are ways to install Breezy from a Warty installation. I can help you with that after Warty's been installed. 
You're welcome to the Ubuntu forums for help anytime! We're here to help each other!

---

### Post by catalytic on 2006-01-03
Just need to understand something a little better....
The NFTS file system is read only in linux, what exactly does that mean?

For example I could read a microsoft word file in linux but I wouldn't be able to edit it or create a new one?

Or is it more complicated than that? Would my windows programs run in linux or would I need to reinstall them in Linux?

This will make the final decision for me.. is it worth having linux when I still use windows for a majority of stuff?

Maybe I should be asking what can linux do for me that windows can't?

---

### Post by catalytic on 2006-01-03
[QUOTE=Iandefor]Well, you can resize D: and make a new partition, which it sounds like you're doing anyways.
Yes, the suggestion is to use Breezy. It's much more polished than Warty.
If you're on a broadband connection, there are ways to install Breezy from a Warty installation. I can help you with that after Warty's been installed. 
You're welcome to the Ubuntu forums for help anytime! We're here to help each other![/QUOTE]
Oh great ta!!
Asked the other half to buy me some blank cd's and he bought dvd's.
So looks like I will need to know how to switch to Breezy from Warty. I may as well do it tonight or tomorrow.
I have a 20Mbps ADSL2+ connection so shouldn't be a problem there! ; ) ; )

---

### Post by gerbman on 2006-01-03
[QUOTE=catalytic]Just need to understand something a little better....
The NFTS file system is read only in linux, what exactly does that mean?

For example I could read a microsoft word file in linux but I wouldn't be able to edit it or create a new one?

Or is it more complicated than that?[/QUOTE]No that's about all it means. Just can't make changes to the NTFS partition.

[QUOTE=catalytic]Would my windows programs run in linux or would I need to reinstall them in Linux?[/QUOTE]Windows apps won't run in Linux unless you use something like an emulator, such as Wine or Crossover Office. There are others, too, but I've only used Crossover...it seems to work pretty well.

[QUOTE=catalytic]This will make the final decision for me.. is it worth having linux when I still use windows for a majority of stuff? Maybe I should be asking what can linux do for me that windows can't?[/QUOTE]After switching I found that the only thing holding me back from complete freedom from Windows was MS Office, which IMO is far superior to Open Office 1.1, but not so much so compared to 2.0. 2.0 is very good, but I haven't used it much because I just use Crossover. The most important thing that Linux gives me that Windows does not is control. I don't feel like I'm in control of things using Windows and that I'm more productive in Linux. Along with that control comes the occasional headache, but the only thing that headaches lead to is a better understanding of Linux and more control (and perhaps much loss of sleep ;p)

Good luck.

---

### Post by catalytic on 2006-01-03
Thanks Gerbman... that clears it all up. I think I have done pretty good for one days worth of learning. I'm pretty confident I can pull this install off now on my own. 
I'll keep you all updated, might wait until tomorrow, but I'm getting is all ready now.
It looks like it will be easier for me to partition using the install disc. I'll put warty on and hopefully you lovely folks will help me switch over to breezy, or is there a way I can copy the breezy iso onto DVD?

At least I have some media now to back up my whole D: so that made the decision go ahead a lot easier, I couldn't bear to loose my collection of every south park ep there is!!!

---

### Post by handy on 2006-01-03
[QUOTE=catalytic]Just need to understand something a little better....
The NFTS file system is read only in linux, what exactly does that mean?[/QUOTE]

You can not Write to, or Delete from an NTFS drive.  You may open certain types of files, copy files from NTFS to your Ubuntu drive.

I have a Fat32 drive which I use as a middle ground, both operating systems can see it & use it freely.

[QUOTE=catalytic]
For example I could read a microsoft word file in linux but I wouldn't be able to edit it or create a new one?[/QUOTE]

This depends on the application you are using & if they are compatible with your data.  Some data is some isn't accessible via equivalent free software app's.


[QUOTE=catalytic]
Or is it more complicated than that? Would my windows programs run in linux or would I need to reinstall them in Linux?[/QUOTE]

Your windoze prog's except for a very few games will not install.
You can install WINE, so as to be able to then install some windoze applications & games, with varying degrees of success.  You can also install VMware, which allows you to then install windoze on Ubuntu, this is a personal choice, it will be slower due to emulation tasks of the cpu.

[QUOTE=catalytic]
This will make the final decision for me.. is it worth having linux when I still use windows for a majority of stuff?

Maybe I should be asking what can linux do for me that windows can't?[/QUOTE]

Give you a community of helpful people willing to share their time & knowledge for your benefit for free, 24 hours a day, 7 days a week...:KS

Do you appreciate Iandefor's kind offer to help you from Warty to Breezy???

All the best,

handy

**[EDIT:]**  Ahh, Gerbman, your a faster typer than me... ;-)

---

### Post by gerbman on 2006-01-03
[QUOTE=handy]**[EDIT:]**  Ahh, Gerbman, your a faster typer than me... ;-)[/QUOTE]But you make a good point. The forums here are simply great. The IRC channels are good for support as well. 

Catalytic, I don't see any harm in installing Breezy to begin with, though it isn't hard to upgrade from an earlier version.

---

### Post by Iandefor on 2006-01-03
> **catalytic]Oh great ta!!
I have a 20Mbps ADSL2+ connection so shouldn't be a problem there!  said:**
>  
  *20 Mbps*? My word! I only have 512 kbps; but it's only about $6 more per month than dial-up, so it's not so bad for a poor family like mine :). [quote] So looks like I will need to know how to switch to Breezy from Warty. I may as well do it tonight or tomorrow. Okay! I'll post how to now:

When Warty is up and running, open up a terminal and type in
```
sudo cp sources.list warty_sources.list
``` The above is entirely optional; it's just in case you need the warty sources, but you should *never *mix your sources; ie, you should never use a breezy repository in the same sources.list file as a warty repository is in.
Okay, got that? now, type in the following in the terminal:
```
sudo "gedit /etc/apt/sources.list"
``` which will open up a text editor. You should see a bunch of lines that look like this:
```
deb http://archive.ubuntu.com/ubuntu warty universe
deb-src http://archive.ubuntu.com/ubuntu warty universe
``` if you're with me so far, go through and change all the lines that look like the above so that any instance of 'warty' is changed to 'breezy'. The above lines should become 
```
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
``` Save the file, and return to the terminal. Type in 
```
sudo apt-get update
``` and then, when that's done, type in 
```
sudo apt-get dist-upgrade
``` It'll download and install the new breezy versions of all the packages (and all the new packages in breezy, etc).

EDIT: Assuming you can write and boot to the DVD discs you have, you can get the DVD Release (which is a combination Live DVD/Install Disc). So far, they have only mirrors in Europe, but you should still be able to download them. Here's the [Netherlands Mirror]("http://nginyang.uvt.nl/breezy/"). I think it will be easier than upgrading from Warty.

---

### Post by handy on 2006-01-03
[QUOTE=gerbman]But you make a good point. The forums here are simply great. The IRC channels are good for support as well. [/QUOTE]

IRC?  This will sound strange I know, I've been in IT support professionally for 10 years, BUT, I have never had the need to look into IRC!!  What's the story Gerbman?  Or anyone else for that matter!

Cheers,

handy

---

### Post by catalytic on 2006-01-03
Thanks guys! This forum rocks...
I'm used to getting flamed in forums as soon as I ask a noob question.

20Mbps second.. one word iiNet. Pretty popular in WA though I'm in Vic.

I very much appreciate you all taking the time to answer my noob questions!
:o 

I think I have learnt more today than I have since I last studied. I think I can grasp it all now, I'm backing up as I type. 
Should be able to complete install tomorrow. Fingers crossed!

The more I learn the more I'm liking Ubuntu... so thanks again!
I noticed that you do indeed feel as though you have more control with Linux. 

If I was a bird I'd poop on Bill Gates
( I think I just found my signature)

---

### Post by gerbman on 2006-01-03
[QUOTE=handy]IRC?  This will sound strange I know, I've been in IT support professionally for 10 years, BUT, I have never had the need to look into IRC!!  What's the story Gerbman?  Or anyone else for that matter!

Cheers,

handy[/QUOTE]

The channel is at irc.freenode.org, and the channel name is #ubuntuforums. It's pretty common to get an instant reply to most questions. 

Cheers!

---

### Post by Iandefor on 2006-01-03
> **catalytic]
Thanks guys! This forum rocks...
I'm used to getting flamed in forums as soon as I ask a noob question.
[/QUOTE]

I've heard that new users get flamed a  lot on other forums said:**
> 20Mbps second.. one word iiNet. Pretty popular in WA though I'm in Vic.
iiNet, you say? Never heard of it. Funny, seeing as how I live in Bellingham, WA. I'll check it out.

> 
I very much appreciate you all taking the time to answer my noob questions! I think I have learnt more today than I have since I last studied. I think I can grasp it all now, I'm backing up as I type. 
Should be able to complete install tomorrow. Fingers crossed! The more I learn the more I'm liking Ubuntu... so thanks again! I noticed that you do indeed feel as though you have more control with Linux. Again, it is no problem for me. Good to hear that you're learning faster than before!
Yeah, I like the control Linux gives you over the computer.

>  If I was a bird I'd poop on Bill Gates
( I think I just found my signature) Good deal; took me a while to find mine.

---

### Post by handy on 2006-01-03
[QUOTE=gerbman]The channel is at irc.freenode.org, and the channel name is #ubuntuforums. It's pretty common to get an instant reply to most questions. [/QUOTE]

I'm allmost embarassed to ask, what software do I use? :confused: 

Sorry for slightly diverting the thread.

Thanks again,

handy

---

### Post by wounded on 2006-01-03
[QUOTE=handy]I'm allmost embarassed to ask, what software do I use? :confused: 

Sorry for slightly diverting the thread.

Thanks again,

handy[/QUOTE]Assuming you are in Ubuntu :P Applications > Innernets > XChat

---

### Post by catalytic on 2006-01-03
I've never used IRC either, hadn't had a reason to. Yahoo chat sort of scared me off anything like that.

One time I must have had about 15 messages coming in at once from visa hunters (is you know what I mean).

I only really started getting into the technical side of things, since I got ADSL. So now one of my past times is finding ways to use all this great bandwidth and protect my computer at the same time.

Maybe the IRC channels here are worth a look, I like Whirpool Broadband Forums too, great info about ISP's, check it out Iandefor, you'll find plenty of info about iiNet there. The first provider in the country I believe to offer speeds greater than 1500/512. 

Sorry I have to brag a little I have 20000/1024, one of the reasons I'm curious to try linux, is I'm wondering if this would speed me up a bit.

I sync at that speed but realistically from a multi thread download from a good ftp I max out at 3000Kbps.
Internet security is starting to be more important to me these days. I have been getting port scanned, my curent firewall sygate, blocks them but I wanted to try another one.

So I downloaded and installed Outpost, read somewhere it was pretty good....
It was either that or the fact I didnt' restart windows after it updated hours earlier, but as soon as I installed it my pc went spacko. So run in safe mode removed program. Reboot and my net has gone.
Literally all of the internet protocols and network adapter has disappeared, according to windows anyway.

Everything appeared to be working fine, but windows couldn't recognise my internet protocols, DHCP, TCP/IP, DNS nothing was running. I called microsoft support... what a joke!
We can pass you onto a technical support person, but it will cost you $50!
As I don't even legally own a copy of windows, I decided it was time to tell em where to stick it in another way.

So now I'm here, I've joined the other side, but still have to travel to the dark side every now and then! : )

---

### Post by Iandefor on 2006-01-03
[quote=catalytic]Maybe the IRC channels here are worth a look, I like Whirpool Broadband Forums too, great info about ISP's, check it out Iandefor, you'll find plenty of info about iiNet there. The first provider in the country I believe to offer speeds greater than 1500/512.[/quote] 
I'm intrigued as to how they manage such speeds, but I think, for now, my cheap broadband is good enough for me. I use the Internet primarily for browsing and instant messaging; I don't need 20 Mbs. When I download a big video (Star Wreck,  anyone?), which happens rarely, I can easily leave the computer on long enough to download it and go off to read a book or watch a movie in the meantime. But I'll keep iiNet in mind for when I need such speeds.

---

### Post by handy on 2006-01-03
Internode has a really good rep' too, that's where I'll be going as soon as it's financially viable to tell Telstra where to go.  (24 month plan :(   I had ISDN, there was no other way.  :confused: ) 

Why do I feel there is some kind of similarity between Telstra & M$ ??

Thanks for the IRC input.

handy

---

### Post by celluloid on 2006-01-03
Oh Telstra, terrible Telstra, I'm currently with them 512kbps ADSL, looking to change suppliers shortly, contract almost expired :)

---

### Post by catalytic on 2006-01-03
I'll put it this way internode would have my buisness if they had a DSLAM at my exchange. 
iiNet service has a way to go... but $49 a month for 10GB/10GB at 20Mbps is the best value for me. As well as the added bonus of VOIP calls. Very cheap.

Anyway... it took me until 11pm lastnight to backup everything. I still think I might be at risk of loosing things, but nothing I can't get back again.

I'm a little nervous.... I'm about the just read over everything again and get started. Ubuntu here I come!

---

### Post by catalytic on 2006-01-03
> **Iandefor]*20 Mbps*? My word! I only have 512 kbps said:**
> Netherlands Mirror[/URL]. I think it will be easier than upgrading from Warty.

Damn wish I had of read that last part before I filled up all my DVD's with backup files. LOL
But good thing is they are re-writable, I really don't want to copy over anything though.
It doesn't sound too compicated to change from warty to breezy, should I just give it a go?

EDIT: Looks like it had to be warty, the files is 2.9gb my dvd's are only 2gb won't let me put more than that on them. Oh well...

---

### Post by catalytic on 2006-01-03
oops

---

### Post by catalytic on 2006-01-03
Ok  lost already....
The partitioning doesn't seem to work.
I have only one hardrive that is already partitioned into 3.

So am I right in assuming I cannot repartition it? If I do it would wipe the system clean therefore I would loose all my files and windows?

I selected the partition that I wanted to resize I typed in 10GB pressed enter nothing happened.

Is there another way I can do this?

---

### Post by professor_chaos on 2006-01-03
I don't know the method/program your using to partition. But you can always delete/resize partitions. I think moving partitions is a bit more risky, but you shouldn't need to do that. Say you have three partitions. 1.) NTFS 2.) Someformat 3.) Someformat. You may want to (if you want to dual boot), depending on the size of your drive, format the 2nd partition to fat32 of a size of ohhh, lets say 1-5GB. This fat partition is read/write by both windoze and linux. So it will serve as a shared space. Then resize/format the 3rd partition 5-10+GB as ext3. Then put ubuntu here.
If your in need of more space, try resizing the NTFS partition, that is if your willing and able to steal space from windoze. At work I dual boot for flexability, and every 6months I find myself resizing that partition to steal more and more unused space.

Ohh and formating a partition is different that formating a drive. You can format a partition and keep other partitions unchanged. Remember to take your time during the installation/partition process of Ubuntu. Make sure you double check the drives that you choose to format. Writing down the sizes of these paritions is a good way to double check.

---

### Post by catalytic on 2006-01-03
It seems I've hit a bit of a wall.....
The first partition listed there is 10GB and is the windows I don't want to touch that
The second partition is the 64.5GB which is the one I wanted to re partition and make one that is 10GB for the install.
Problem is I'm really not sure how I do this. 
I spent all day backing up, and I don't think I did it right. So know I'm going to try and use this backup utility that will put my whole hard drive image on dvd's. 
Funny thing is my Ubuntu Breezy cd's that I ordered arrived today!
If only I had waited one more day....
Someone suggested it may be better if I do the partitioning in windows, the option during the install doesn't make sense to me, I'm scared I'll delete windows and wont be able to get it back.

---

### Post by Iandefor on 2006-01-03
What is the option that is confusing you, exactly?

---

### Post by travislepp on 2006-01-03
Hi catalytic,


My 2 cents worth:

1. I think the first thing you need to do is make sure you can restore / view the files you have backed up.

2. To resize the second partition you really have two options either try to resize it (parted or qtparted), which you still risk losing the data in the resize (qtparted crashed on my machine) or delete the partition(s) and recreate it with your required new sizes (I'd use fdisk (I think it's on the ubuntu live cd's) ([http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4))](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4))).

3. The changes you make on a partition won't take effect until you save them so if you break something / do something silly then quit without saving and everything should be fine.   

4. I found partitioning the hardest part of the install and I have worked with linux for a few years now.  It could be clearer / simplier.  

5. Sometimes you have to just have faith :)

Good Luck and hope this helps.

---

### Post by catalytic on 2006-01-03
I'm starting all over again.. totally lost now....

All I did was copy the files from my hardrive to a DVD, I only backed up drive c: in an actual backup file. Is this enough? 
at the moment and frantically trying to find a tool that will take a whole system snapshot and install it on the 5 dvd's that I have.

I'm looking at paragon partition manager at the moment and I'm really confused, not sure which one I'm meant to resize, or do I create a new one, and I'm not sure how I do this.

Really confused here....:confused:

---

### Post by catalytic on 2006-01-03
Hopefully that worked.... no it didn't. Trying to paste and image I just wanted to show you what my drive partitions look like.

C: Primary NFTS 10GB 7GB (used) 3 GB (free)
*: Extended        64.5GB
D: Logical NFTS 64.5GB 47.8GB 16.8GB
*: Primary (free) *7.8GB* OOOPS it is actually 7.8MB

This is what paragon is showing me, I see the same in the Ubuntu partition part of the install.

Not sure what I do. Or how to do it.

At least I have the proper version of Ubuntu to install now.

---

### Post by catalytic on 2006-01-03
OK I have resized the partition now I can create one. Which file format should I choose? Is it NFTS or Ext3FS? It is 12GB, Do I then make two more partitions one 500mb for swap and the orther 1.5GB for home?

Is this correct?

I'm using paragon this one formats them for me, I think I'm on the right track just need confirmation.

Thanks

---

### Post by professor_chaos on 2006-01-03
If I'm understanding you right, you have windoze on the 10GB partition, and 65GB free. You only want to use ~12GB for ubuntu. Thats fine, then you will want to split the second 65GB partition into two partitions (if you only want 12GB for Ubuntu). If I recall right, the format doesn't matter, because ubuntu will automatically reformat the partition (someone correct me if I'm wrong about this).

Basically, Ive found the easiest thing to just create some partition that you plan to devote to Ubuntu. Then during the install, you can just select this partition. Now that I'm comfortable with the ubuntu partitioner, I just use that instead of using some other 3rd party product. I find it acceptable to use a single partition for /home and / (ie. root). So you can just make one partition. 

Just backup files from windoze that you can't bear to lose and then create a partition (ext2 or ext3). And try the install, choosing this parition. You dont need to make a partition for swap, as you can do this during the install process. Don't be completely scared of the ubuntu partitioner. I know it can be daunting for a newbie because of its non-graphical interface and the fact that newcomeers might not know what / and /home mean and for that matter swap. But if you have your important files backed up, you really don't have anything to lose. Think of it as a learning experience.

---

### Post by catalytic on 2006-01-03
It wont let me create a new partition in Ubuntu. So I don't think I will go ahead with it. I only want to istall it if I do not loose all my data, it wont let me do that.

The partitioner in Ubuntu makes no sense to me, I will try one more time with the partitioning tool. It says it formats the drive though, does that mean I loose it all?
Someone said don't format it, so how can I make a partition ext3 from NFTS without loosing all of th data on my drive?

This is making even less sense than yesterday...... I think I just have to wait until I meet someone that could do it for me. I literrally don't know anyone that could install it for me.

---

### Post by steveneddy on 2006-01-03
You realize that he is going to frag the HD and all will be lost. Can't you see the blantant inexperience here? Someone hold his/her hand....please.

---

### Post by Iandefor on 2006-01-03
[quote=steveneddy]You realize that he is going to frag the HD and all will be lost. Can't you see the blantant inexperience here? Someone hold his/her hand....please.[/quote] You think Catalytic's hand should be held during partitioning, you do it yourself. I'm helping as I can. I have little experience setting up multiple operating systems; therefore, I'm trying to restrict my aid to what I *do *know.

---

### Post by professor_chaos on 2006-01-03
catalytic, I want to help, but I get confused as to exactly what your doing. Where are you stuck? When you get stuck, try and provide as much information as possible.

 I want to make sure of the options you are choosing during the install.

At this screen what do you see??

[IMG]http://www.mrbass.org/linux/ubuntu/install/006partitionauto.png[/IMG]

If I remember right (and you can really help me out here) since you only have on physical disc your screen looks just like this one. Instead of selecting the first option (erase hard drive) select the second option manually edit partition table. Then, if you have these other non-windoze partitions (I'm not sure if you made these) then you can select these partitions. I can't remember this install screen, but if you can't select the other paritions (ie, the 65GB non-windoze partition) then you should try the guided partition process. 
It important to note here, that anything at this point is not going to do modify your disk at all until you get to this screen. 
[IMG]http://www.mrbass.org/linux/ubuntu/install/008partitionwarning.png[/IMG]

So go through this part, and play around with it until it makes sense. You can always choose to not write changes to disk and retun here to ask more questions about where your stuck. If you do this, try and write down what you see on the screen so we can guide you better. Good Luck.

---

### Post by gravediggers on 2006-01-03
Catalytic,

You were doing so well up till now on the learning curve - don't give up!

The partition that is currently your d: drive (65GB) - do you want to keep anything that is on it, or not? If you only want to keep the c: drive (windows), then the cleanest way is to remove the d: partition off the disk, and it becomes 65GB of unallocated space. Then you can create a new partition of whatever size and format you desire, and leave 10plus GB of unallocated space for breezy. When you install breezy, the installer will see the unallocated space and offer to use it.

---

### Post by gravediggers on 2006-01-04
chaos - i don't see any pics in your post. did u put then there or is there a forum problem?

---

### Post by carlosqueso on 2006-01-04
If you're having trouble partitioning your HD, try using Mandriva's installer program.  It has a component called DiskDrake that should walk you through the partitioning process.  You can then install Ubuntu (or any other OS) over Mandriva.  This is what I did and had no problems whatsoever.

---

### Post by catalytic on 2006-01-04
Thank you all for your comments :smile: 

I am still trying here.. have to learn somewhere right?

When I get to the partitioning screen I select partition manually, then I don't know what to do next.

There is the option there to change the file system on the drive I want to partition (which is D: in my case) 
I choose the ext3
I then select the size and enter the size I want (this is the part that did nothing for me when I typed in 12GB)
When I come back to the partitioning screen the my D: drive has a skull next to it instead of a smily face. So I'm assuming that it means I would loose all data on my drive if I went ahead.
I can't get it to resize the partition.

I don't wan't to loose what's on D:, problem is windows hasn't got enough room to even perform the backup. So I can't save it all. I have all the important stuff on disks, but if there is a way to not loose it then that's what I'm trying to do.

I hope that makes a little more sense.... again sorry I was just having a little dummy spat before, every darn partitioning program that I tried was only a trial version.

I am going to try using Paragon Partition Manager Pro 7 a little later to see if that worked. I used the virtual trial one and found that I could do exactly what I wanted (but of course it was only a trial so it wouldn't actually commit the changes!!)

I'll have another look at the install CD and try the guided one again, I just got scared last time because I got a message that said "you have not finnished the installation process your system may be unstable"
everything was fine but that worried me a bit.

---

### Post by catalytic on 2006-01-04
WOOT!!
I did the partition successfully using Paragon.

I think I'm ready to istall!

:p :p :p

One more question should the swap partition also be in the ext3 format?

---

### Post by dcraven on 2006-01-04
All this talk of C:, D:, defragging stuff makes me feel like I've time travelled backwards about 8 years.

:D
~djc

---

### Post by jannol on 2006-01-04
No swap is just swap, no file system at all or something like that, It's good you got it but I was just about to try and simulate and make a demo but I guess I am to late... :eek:

---

### Post by catalytic on 2006-01-04
Not going well at all... i'm getting frustrated....:mad: 

I can't get past the partitioning part of the installation no matter what I do.
I have 10GB partitioned and ready to go, that part worked fine. I also created the swap and that's where the problem is.

I cannot get rid of the skull icon, I have selected to partition it as swap, I have selected the size of 500MB, it does it. 
Come back to the partition screen and there is still a skull there. I select finnish partitioning and commit changer nothing happens. No error message, just doens't move off that screen.

What's going on?

---

### Post by jannol on 2006-01-04
Ok, I am very tired right now but take a look here [http://linux.jannol.com/ubuntu/partition_setup/ubuntu_partition.mpeg](http://linux.jannol.com/ubuntu/partition_setup/ubuntu_partition.mpeg) I put some shots from my simulation there and they are ordered as I done it.

I always choose manual when I do this stuff since it isn't really that difficault but it is easy to miss something.

I also made a small live demo :rolleyes: but in win you probably need vlc ([http://ftp.snt.utwente.nl/pub/software/videolan/vlc/0.8.4a/win32/vlc-0.8.4a-win32.exe](http://ftp.snt.utwente.nl/pub/software/videolan/vlc/0.8.4a/win32/vlc-0.8.4a-win32.exe)) player to play it. It is not very fun since it is slow cause my comp memory was almost empty while recording but anyways, if you look at it, you can just pause and go back etc.

Come back with more questions if it still is unclear.

I'll be back in approx 5 hours.

demo here [http://shr.jannol.com/ubuntu/partition_setup/ubuntu_partition.mpeg](http://shr.jannol.com/ubuntu/partition_setup/ubuntu_partition.mpeg) approx 6 mb

Ohh I forgot, the sim is actually based on just one disk with 2 partitions but same basic principle...

now I am off to bed :-P

---

### Post by catalytic on 2006-01-04
Thank you : ) : ) ; ) 

I managed to get onto an old pal that lives not far!! But I am going to keep going and get this up and running!! Everyone has been so helpful and I really appreciate it hopefully I will report back with good news!

---

### Post by catalytic on 2006-01-04
Thank you very very much Janno. It's really funny the different ways that people learn. As soon as I saw what I was meant to do I got it. 
I'm also kicking myself that I didn't figure that out sooner, because it was a waste of time doing the partitioning with partition manager. I ended up deleting what I had done and doing it there anyway!
In the end it all went smoothly, no problems. Now to get used to the new environment. 
I don't think the colours agree with my eyes, so that's the first thing, figure out how to change it.
Also I prefer to use Opera as my browser is this compatible? I guess I'll go find out!

Thank you so much everyone, you have been so helpful. :smile:

---

### Post by catalytic on 2006-01-04
Ok Ubuntu is still confusing me I have it running, my drives are showing on the desktop but I can't access them, apparently I don't have permission to access them.
They appear to be mounted, I just installed Opera but I can't see it anywhere. This wiki isn't very easy to find what I'm looking for... sorry to be a pain.

---

### Post by Perfect Storm on 2006-01-04
write: opera in the terminal and opera starts. You can also make it as application launcher or add it to your applications tab.

```
smeg
```

Pick **Internet** and click **new entry**

Name: Opera
command: opera
Icon: /usr/share/opera/images/opera_48x48.png

edit: spell mistake

---

### Post by jannol on 2006-01-04
you should really install Automatix and run in, it does pretty much all the good stuff. [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by professor_chaos on 2006-01-04
glad your up and running catalytic

---

### Post by handy on 2006-01-05
Solve one, onto the next...

Computers are a perfect environment for problem solving, & this community makes it sooo much quicker & more fun.  :KS   

Even makes the otherwise impossible not just possible but history  ;-)

Catalytic, have a look here you may find some help, for what you are going through & are about to go through.

[http://ubuntuforums.org/showthread.php?t=88639&page=2](http://ubuntuforums.org/showthread.php?t=88639&page=2)

Great that you're up & running...

handy

---

### Post by catalytic on 2006-01-05
I really want to give it a go, but it's just beyond my limited knowledge.

I haven't been able to install any games, 

I can't figure out why I can see my windows files only with the sudo nautilus command.

I simply do not understand where things are being saved to or what the file names mean.

I can't find a list or a guide that tells you what commands to type in.
(basically I saved a game and don't understand what command I have to type to play it, as I can't see where it is saved)

Wine????? Ok I installed it I know what it is meant to do, but where is it?
Typed in wine in the terminal got to the help file, which I do not understand.

I have been searching but obviously not hard enough, this info has to be there somewhere but I can't find it. I'm just finding that the documentation and help files are no help to me at all. So I now have to just admit that I was too ambitious in thinking I could actually use linux.

I feel silly having to come in here every five minutes to ask a question, I'm trying to be patient, but there is so much to read and most of it I just don't understand.

Problem is how do I now undo what I have done? Don't worry I don't expect an answer to that one. I really don't want to give up so soon, but without the help files or diagrams in front of me I just can't understand this OS.

I would like to play some online games that don't require 3d graphics, I would like to download mp3's and be able to listen to them in linux and in windows.

I understand how you download things, either through a command (which I don't know), or throught the synaptic thing. I downloaded hexen game, but I don't know where it is or how I can play it. 
I downloaded Enemy Territory, don't know where that went or how I get to it.

---

### Post by catalytic on 2006-01-05
> **handy]Solve one, onto the next...

Computers are a perfect environment for problem solving, & this community makes it sooo much quicker & more fun.  :KS   

Even make the otherwise impossible not just possible but history   said:**
> http://ubuntuforums.org/showthread.php?t=88639&page=2[/url]

Great that you're up & running...

handy
Thanks Handy that link is a good one!

---

### Post by handy on 2006-01-05
Catalytic, what you have been going through in the days that you have been dealing with this problem is **VERY** stressful.  The learning curve you are on has looped the loop ***_twice_***.  

Back off some... Allow yourself atleast a month to **start** to feel at home with Ubuntu.  

Stress comes from not thinking/feeling that there is enough time to do...  What ever it is.

Stress comes from an unhealthy attitude, change the attitude for a happy one, it's allways our choice.

The welcoming Ubuntu community will give you steady support as you allready know, everyone here knew absolutely nothing about computers once.  It takes time, & time is what we all have here, time to help one another.

Go slower, don't keep piling on more problems, read stickys & wikis, before you know it all this is long gone & you'll be burning DVD's, while your playing World of Warcraft online.

handy

---

### Post by catalytic on 2006-01-05
I'm trying to have an open mind, but I don't seem to be getting anywhere still.

I just used the synaptic package installer to install doom and other games there that i thought were good. While installing the poker one it failed. The installation stopped.

I can see some of them in the menu, but how do I find doom?

---

### Post by jannol on 2006-01-05
Here comes a few words of mine... I see linux and open source as a fun experince where I slowly improving both my knowledge and prosperous. As I think of it is kinda like my home. I change furnitures from time to time, buy new cool stuff when I find it. I feel the same with linux plus a whole lot other benefits, it doesn't cost me any money, I have a great time with the open source communities, I don't need to be afraid my computer gets worse when I change it, well in the beginning it went wrong a few times and I reinstalled but thats what I have to do all the time with win, even after 9 years of knowledge win still breaks for me so I stopped using it.

Actually I have learned to get patince and with that I got harmony with my self and a whole lot of fun. As a small metafor kinda thing, what if you got a call from IKEA and they said, Hi Catalyctic, we have found that your bookshelf is to small for some books so we can have it rebuild for you if you like, we also offer more colours and materials of it now, and free of cost of course.

Thats kinda what it is like with open source and linux.

Yes I have felt frustrated sometimes but it was some time ago now, open source is a whole new concept of well beeing, fun and freedom.

I said I be short so thats was few words from me :lol:

handy, really great post ;) 

...and about things you installed that do not show up in the menu, there is an Application Menu Editor in System Tools but if you need to try something fast and not found it you can press Alt+F2 and type the application name ex.
```
doom
```
sometimes the binary naming of an application can be different but thats not very often, if you ex install opera you start it with opera.

All the binary (like exe files) is inside /usr/bin and /usr/local/bin.

The best command to begin with inside a terminal window is
```
man man
```

---

### Post by professor_chaos on 2006-01-05
Yes, it seems your trying to tackle quite a bit. You have probably used M$ Windoze for quite some time, and have become used to the way that OS worked (or didn't). You'll need to give some time to relearn this new OS. Lots of things are just different, and to make things harder on newcommers from widoze, users want to not only do everything they were doing, using every program they were using, and read/write to everywhere they were before in windoze. 

I went from a 100% windoze 0% linux to
75% windoze (in a real state of confusion and doubt if I could live with this new OS that was so different)
There was a short period of 50/50 dual booting, but by then I realized that there were only a few things that I couldn't currently do in Ubuntu that I was doing in widoze. So I decided to take the plunge and now I'm a very happy 100% Ubuntu. 

This whole process took 9-12months. So I recommend you take it slow and recognize the differences and benifits of linux, and decide over time if it's the right OS for you. If you decide you will stay with Ubuntu/Linux you still will likely have bumps (maybe some big and frustrating) ahead of you. But remember, everything you figure out, will make you a more confident knowledgable user.

Good luck.

---

### Post by catalytic on 2006-01-05
Thanks guys, you are right and what you both say makes a lot of sense to me! I actually hadn't used a computer for about 5 years. Until 18 months ago I decided to go back to school and get my high school certificate, and I was doing Info Tech. 

I also did some art courses which relied on me learning to use Adobe Photoshop. So my whole reason for gettting a computer was so that I could learn, and find something that I had a real interest in and pursue as a career.

Anyway I got a computer so I could dable in some digital art and design, I had to learn windows, which I still don't like. But I remember what a challenge it was to learn photoshop, it was frustrating. Basically over 6 months I taught myself using tutorials.

So I have to just look at linux as that, a hobby, something that I want to learn more about. I'm really not good at understanding the help files, I learn better from examples or trial and error. The only problem is when you make a mistake and can't fix it!

I'm in windows at the moment, I think I need a break from it today, gotta do some tests with my ADSL filter. Thanks again :p

---

### Post by catalytic on 2006-01-05
Well happy to say I'm getting somewhere!

I just figured out the command I needed to install Enemy Territory through the terminal. It's downloading now! I figured out where it was getting saved to!

I also logged in as root this time, and amazingly I now have access to my files without the nautilus command.

So thanks guys, your advice helped.

Oh, and I figured it out by the way from scimming through the started guide. I swear its a different one, but probably the same one. I just looked harder this time! ;) [http://ubuntuguide.org/](http://ubuntuguide.org/)

Anyway thanks guys your advice really helped. I'll just take it slow and before you know it I'll be able to pass the knowledge on to someone else.

---

### Post by handy on 2006-01-08
It's amazing how much more we can see / understand, when we are not in a hurry. :razz:   

Sleep helps too!

handy

---

