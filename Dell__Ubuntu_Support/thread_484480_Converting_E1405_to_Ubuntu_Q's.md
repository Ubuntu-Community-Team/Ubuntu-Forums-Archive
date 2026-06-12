---
title: "Converting E1405 to Ubuntu Q's"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by logreeval on 2007-06-25
Ok, SO!

I have a dell e1405 laptop. I an thinking of converting to ubuntu. But I want to have XP, so I will have it partitioned to a dual boot. 

First, If I have it set to dual boot, can I later(without reformatting, etc...) get rid of XP all together and have the entire hard drive for ubuntu.

Is their a way to get ubuntu dell quickset software, for all the functions that dell has in them.

Does the "Media Direct" buttons and such work with ubuntu, or is their a way to make it work.

Can a logitech webcam be configured to work on ubuntu...what about a logitech mouse, wireless usb, laser.

Does wireless and lan both work on it?

I will probably have VMware server used, what is the best method of setting that up with XP on a Ubuntu.

Do you need any firewall, antivirus, etc....

Would I be able to have "Dell System Restore" on here still, as it would be handy just in case...

Does flash work.... .WMV files?, is their a windows movie maker clone for linux?

Any "Before setting up ubuntu, you should...." topics or something like that?

What about my Dell Photo 964 printer, will it work?

Thanks :)

---

### Post by DugieHowsa on 2007-06-26
so many questions... let me try to answer them...

"First, If I have it set to dual boot, can I later(without reformatting, etc...) get rid of XP all together and have the entire hard drive for ubuntu."

Yes.  You can do this using GParted.

"Is their a way to get ubuntu dell quickset software, for all the functions that dell has in them."

No.  It appears this is a Windows only application.

"Does the "Media Direct" buttons and such work with ubuntu, or is their a way to make it work."

Not sure.  My understanding of the media direct functionality is that it is OS independant.  But perhaps it boots off of some other partition?

"Can a logitech webcam be configured to work on ubuntu...what about a logitech mouse, wireless usb, laser."

Yes.

"Does wireless and lan both work on it"

Yes.  Wireless takes a little extra work, but there are plenty of articles here in the forums that explain exactly how to do it.

"I will probably have VMware server used, what is the best method of setting that up with XP on a Ubuntu."

VMWare is very intuitive to use.  Just create a virtual instance and boot it with the XP install CD.  Then just proceed as you would normallywith a physical PC.

"Do you need any firewall, antivirus, etc...."

Ubuntu has a basic firewall running by default, and also allows you to install and enable anti-virus.

"Would I be able to have "Dell System Restore" on here still, as it would be handy just in case"

Yes.  It is on a seperate partition.  On my Dell, its aabout a 3 GB partition.  Just don't delete it when using GParted.

"Does flash work.... .WMV files?, is their a windows movie maker clone for linux"

Everything works, just not out of the box.  You have to download and install flash, java, and other media plug-ins.  Most of which can be done with the Ubuntu software manager and apt-get.  There are many forum posts on how  get these plug-ins up and running.

"Any 'Before setting up ubuntu, you should....' topics or something like "

Just make sure you have your Windows system backed up.  Everything installed smoothly on my Dimension desktop.  The only small issue I had was that the video card would not go to the max resolution, but I found a posting on here that told me how to resolve it and within 5 minutes all was well.  You may also experience a small issue like this with your video card as well.  It also takes a little extra effort to get the wireless cards up and running.  I would just review some posts with regards to these topics before hand, just so you know what you are getting into.

"What about my Dell Photo 964 printer, will it work"

Not sure, put probably.  My HP 2410 PSC was discovered properly, and its pretty old.  If I were a guessing man, I would say yes.

---

### Post by logreeval on 2007-06-26
Thank you! :)

One more thing...will the "Fn + (blue button)" work on my keyboard? Because that has like, brightness of screen, volume, wireless, and so many other nice things.

And...are all the tutorials/things I need to know on this forum?, or some of it is elsewhere?

I can't wait to get this going! :D

Thanks again :)

---

### Post by DugieHowsa on 2007-06-27
As for the blue Fn button, it looks like some of them work, and some of them don't.  There are many posts in the the Ubuntu Dell Support forum with work arounds on how to get some of these things running.  There are also many posts here pertaining to the Media Direct functionality as well.  When it comes to Dell specific questions, this forum is definitely your best bet for finding out info.

---

### Post by logreeval on 2007-06-27
Hey thanks for the reply again :)

Ok, so I have been searching and apparently I am not very good, as everything I find is different.

What I want, is the easiest way to make MediaDirect NOT crash my system if I hit the button. I don't care if they work or not, I just don't want them to crash my system. I am assuming it is easier to disable it somehow...but after reading some posts, it is hidden or something?, Im confused :S. Do you know any good topics?

And it looks like the function keys work after reading a lot of posts. I will post if I have trouble.

Thanks

---

### Post by logreeval on 2007-06-27
Ok!

SO I got the Ubuntu CD downloaded(took forever) and I am actually currently talking to you on UBUNTU!!!!

Anyways, I started to installer to look at how the partitions are.

Here is what I got:

/dev/sda1 fat16 /media/sda1 size41 used33

/dev/sda2 ntfs /media/sda2 size73484 used29200

/dev/sda3 fat32 /media/sda3 size4984 used4099

free space              size8

I want to keep the dell system restore, and split the windows for a dual boot. How should I go about with these partitions?

Thanks :)

---

### Post by DugieHowsa on 2007-06-27
/dev/sda1 fat16 is the Dell diagnostic partition.  Keep this.

/dev/sda2 ntfs /media/sda2 is the Windows XP partition.  Shrink this.

/dev/sda3 fat32 /media/sda3 is the System Restore partition.  Move this to right behind the XP Partition.  This will make the remainder 1 contiguous space for you to install Ubuntu on.

---

### Post by logreeval on 2007-06-27
How do I move the system restore one?

When you say shrink, you mean, change the partition size to half, about 36500 and then there will be a new free partition?

THanks

---

### Post by DugieHowsa on 2007-06-28
Yes.  Using GParted, shrink the size of the Windows XP partition to what ever you want.  You probably want to have atleast 32 GB of free space in order for you to install Ubuntu on, so re-size it accordingly.  You can also move the restore partition in GParted to just after the Windows XP partition.  This will all the remaining free space in one, contiguous area.  This operation may take a few minutes (I think it took about 10 on mine), as it has to copy all the data from one section of the disk to another.  Just be patient, as this is a very sensitive operation.  And make sure your laptop is not running on battery.

---

### Post by logreeval on 2007-06-28
Thanks for the reply.

SO I got it installed and its running smooooth as can be. 

I was just wondering, I am having a little trouble with VLC media player, can't get it to be the default player for media files.

Also, I tried to install lokkit firewall, but when I am at the screen where it says Next and Cancel, I click Next, but the box just goes away, so I didn't really configure it i guess. DO I need an Antivirus?

I am still playing around with how to install stuff...i think im getting. Any good articles besides that first one that comes up in google?

thank you so much for your help, im loving ubuntu!

---

### Post by DugieHowsa on 2007-06-28
I am not familiar with the firewall software, but I think I know a solution for your other problem.  Just browse in nautilus (thats the file management broswer) to where your media files are.  Right click on a media file and select Properties.  In the window that opens, go to the "Open With" tab.  From here, you can pick which application you want to open by default that type of file.

---

### Post by logreeval on 2007-06-28
the problem is, VLC doesn't show up as an application. :(

---

### Post by logreeval on 2007-06-29
another quick question.

when i powered on the computer, and then closed the laptop lid, when i opened it up, the screen was off and i couldnt get it to go on. anyway i can fix that?

---

### Post by DugieHowsa on 2007-06-29
Hmmm... not quite sure what to do in either instance then.  You may want to start new threads for each of those questions.

---

### Post by logreeval on 2007-06-30
thanks for your help! :)

---

### Post by djchandler on 2007-06-30
> **logreeval said:**
> the problem is, VLC doesn't show up as an application. :(

Where are you looking for it? Under Applications, it should show up under Sound & Video. If you are trying to make it the default player for a certain type of file, find the file of the type you want it to play. Right click and go down to properties. You must have write permission on this file. Go to the tab marked "Opens With" and select VLC. It is the application with the orange and white striped highway construction cone icon.

---

### Post by logreeval on 2007-06-30
it isnt under that Open With thing. 

It does show up just like "Open wiht VLC player" but its not under the OPen wiht other application.

---

### Post by logreeval on 2007-07-01
I want to get windows off here, how do i go about getting the partitions merged?

EDIT! I got it...

---

### Post by nanog on 2007-11-23
I'd get rid of the media direct partition. It damaged my feisty partitions when I accidently activated it.

---

