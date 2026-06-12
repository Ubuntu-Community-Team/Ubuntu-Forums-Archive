---
title: "How can I change the partition size?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Jordan Meeter on 2006-10-06
I have Ubuntu dual booted with Windows... How can I edit the partition to give Ubuntu more space?

---

### Post by Omnios on 2006-10-06
Most people recomend installing and using gparted to resize the partitions. Personally I got better results with qtparted and the ntfs plug in. Fist defrag you windows partition till you have anouph free space for resizing most recomend doing it twice or so. That way it will not have to transfer files. First you will have to resize, shrink the win partition and then after expand the linux partition or add a new one.

---

### Post by Jordan Meeter on 2006-10-06
Huh?

Is gparted for Windows or Linux?

---

### Post by Omnios on 2006-10-06
> **Jordan Meeter said:**
> Huh?

Is gparted for Windows or Linux?

gparted and Qtparted are free Partition Magic like programs for resizing and making partitions in Linux.

---

### Post by Jordan Meeter on 2006-10-06
> **Omnios said:**
> Most people recomend installing and using gparted to resize the partitions. Personally I got better results with qtparted and the ntfs plug in. Fist defrag you windows partition till you have anouph free space for resizing most recomend doing it twice or so. That way it will not have to transfer files. First you will have to resize, shrink the win partition and then after expand the linux partition or add a new one.
I don't understand this. So first I login to Windows. Run the defragmenter twice. Then log back into Ubuntu... Then you lost me.

Resize? Shrink? This is confusing as heck. Also, all of the drives are locked in gparted, so I can't edit them...

---

### Post by Omnios on 2006-10-06
Defragging is done to clean up your windows partition as it moves all the files to the front of the partition. This is done to eleviate any file transfer problems and also remove files from where you want free space.  

 After you can boot into Ubuntu and install gparted or qtparted from the synaptic package manager and run it in Ubuntu. 

 There are a few things about partitons. First you must shrink the ntfs partition to make space for your Linux partition which can then be resized to take up the now free space freed up from the ntfs partiton.

---

### Post by Jordan Meeter on 2006-10-06
OK, thank you for the clarification, Omnios.

Now, how do I unlock the partitions? They all have a lock next to them.

[[IMG]http://aycu35.webshots.com/image/6474/2001099506970452867_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2001099506970452867)

---

### Post by lemonsCC on 2006-10-06
Oh dear you seem confused.  Go to this site: [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Make yourself a nice liveCD.  Pop it in the drive and it follow the directions.  It will come up with a screen that will allow you to resize, etc.

---

### Post by CatKiller on 2006-10-06
You can't fiddle with a partition that's currently in use. In this case, the partitions are probably mounted, and the / partition that's locked is probably the one that's gparted is running from. I would boot from the Ubuntu Live cd to do the gparted stuff. Your swap partition will still be mounted automatically, but you can fix that with the command ```
sudo swapoff -a
```Then run gparted (it's on the Live cd) to resize the Windows partition, and then resize the ext3 partition.

---

### Post by Omnios on 2006-10-06
> **Jordan Meeter said:**
> OK, thank you for the clarification, Omnios.

Now, how do I unlock the partitions? They all have a lock next to them.

[[IMG]http://aycu35.webshots.com/image/6474/2001099506970452867_th.jpg[/IMG]]("http://allyoucanupload.webshots.com/v/2001099506970452867")

Try 
```
sudo gparted
```
In terminal

---

### Post by lemonsCC on 2006-10-06
When I used the Gparted liveCD none of the partitions mounted and I was able to resize them all.  I tried it on the Ubuntu LiveCD but had no luck.

---

### Post by IoCaster on 2006-10-06
> **Jordan Meeter said:**
> OK, thank you for the clarification, Omnios.

Now, how do I unlock the partitions? They all have a lock next to them.

[[IMG]http://aycu35.webshots.com/image/6474/2001099506970452867_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2001099506970452867)

First off you need to decide if you want to reinstall Ubuntu. Otherwise you'll be hosed if you proceed with what that image is showing.

Let me explain, the first partition hda1 is a primary partition housing windows. You can certainly shrink that down if you'd like. If you do it correctly it won't screw up your win install. The problem is with growing the linux part. You will have to delete it to grow it leftward. That means that your Ubuntu install is toast. You'll have to delete it and then create a new partition starting from the beginning of wherever you ended the win partition at. Very messy, but you can do it. You'll also notice that hda3 is an extended partition with swap (hda5) as a nested partition under that. Those will, of course, be deleted as well.

Question number one is what size do you want to shrink your win partition down to?
Question number two is what size do you wanr your swap partition to be?
How about the size of your / (root) partition?

Finally, would you like to make a /home partition to keep your personal data, docs, settings and configs in? This comes in handy if you ever want to just reinstall your OS without having to start over from scratch.

These are things you might want to consider before you proceed. Good luck.

Regards - Joe

---

### Post by CatKiller on 2006-10-06
I'm fairly sure that you can move the start of an ext3 partition without deleting it with the later versions of gparted. So you can move the start of the partition to the start of the free space, and then expand it to the right.

---

### Post by IoCaster on 2006-10-06
> **CatKiller said:**
> I'm fairly sure that you can move the start of an ext3 partition without deleting it with the later versions of gparted. So you can move the start of the partition to the start of the free space, and then expand it to the right.

Very cool. I'd like to see the documentation on that. Do you have a link to any relevant info?

Regards - Joe

---

### Post by Jordan Meeter on 2006-10-06
God damn I am screwed... I had no idea that this would be such a big hassle. All I wanted to do was resize my partition. I have no idea what I'm doing and I don't want to screw my computer up. *sad face*

I guess I will just have to leave it as it is. :(

**IoCaster:** To answer your question, I just wanted to subtract 20GB from Windows and give 20GB to Ubuntu...

---

### Post by Omnios on 2006-10-06
> **Jordan Meeter said:**
> God damn I am screwed... I had no idea that this would be such a big hassle. All I wanted to do was resize my partition. I have no idea what I'm doing and I don't want to screw my computer up. *sad face*

I guess I will just have to leave it as it is. :(

 Take your time and do a lot of reading on it. About a year and a half ago I spent about a month researching how to set up my partitions.

---

### Post by CatKiller on 2006-10-06
> **IoCaster said:**
> Very cool. I'd like to see the documentation on that. Do you have a link to any relevant info?

Regards - Joe
[GPartEd's News page:]("http://gparted.sourceforge.net/news.php")
> 04 September 2006 : GParted 0.3

It took a bit longer than expected, but finally we decided to release GParted-0.3.
This release includes one of the most exiting features since the first release;
We finally have full move support!! Although it should be considered a bit experimental, our tests worked out perfectly and we didn't see any errors so far.

[Features page]("http://gparted.sourceforge.net/features.php")

Of course, I have no idea which version of gparted is on the most recent Ubuntu live cd.

---

### Post by Jordan Meeter on 2006-10-06
Are you kidding... God. So as of right now, because of the way my drive is partitioned, I cannot edit the space?

---

### Post by CatKiller on 2006-10-06
> **Jordan Meeter said:**
> God damn I am screwed... I had no idea that this would be such a big hassle. All I wanted to do was resize my partition. I have no idea what I'm doing and I don't want to screw my computer up. *sad face*

I guess I will just have to leave it as it is. :( 

You'll be fine.

Backup all your important data. This should be standard parctise regardless of whether you're about to repartition your drive or not.

Defrag the Windows partition. As many times as you can. This will limit the number of files that need to be moved when you change the end point of the partition they're in.

Download and burn the GPartEd live cd. This will be the latest version with support for the most stuff.

Boot from the live cd.

Unmount the swap partition if it's been automatically mounted. It may well not have been with the gparted cd.

Move the endpoint of the Windows partition so that it's as small as you want it.

Move the / partition so that it's at the start of the free space.

Move the endpoint of the / partition so that it's as large as you want it.

Make a cup of tea.

Reboot.

Enjoy the extra space that you have in Ubuntu.

---

### Post by Jordan Meeter on 2006-10-06
One problem: I tested out the live CD and my mouse doesn't work. =\

---

### Post by IoCaster on 2006-10-06
> **CatKiller said:**
> [GPartEd's News page:]("http://gparted.sourceforge.net/news.php")


[Features page]("http://gparted.sourceforge.net/features.php")

Of course, I have no idea which version of gparted is on the most recent Ubuntu live cd.

It says that the latest GParted LiveCD is 0.3.1 so it should be good to go. Maybe not for the 'faint of heart', but what the heck.

Thanks - Joe

---

### Post by Jordan Meeter on 2006-10-06
Any ideas as how to get my mouse working when using the live CD? :p

---

### Post by CatKiller on 2006-10-06
> **Jordan Meeter said:**
> Any ideas as how to get my mouse working when using the live CD? :p

Ubuntu or GPartEd?

---

### Post by Jordan Meeter on 2006-10-06
The GParted CD. :]

---

### Post by lemonsCC on 2006-10-06
is this a usb mouse?  does the keyboard work?

what version of gparted?

---

### Post by lemonsCC on 2006-10-06
here is an idea....After you get your mouse working...

Could you split your windows partition into two sizes (the second big enough to hold your ubuntu partition) then use partimage (whatever its called) to clone your ubuntu partition onto the new split, then merge the two?

[no clue if  this is even remotely possible]

---

### Post by Jordan Meeter on 2006-10-06
USB mouse, keyboard does work, version 0.3, just downloaded it. Since the keyboard works, I guess I'll be using that. So here are my first questions:

The current size of /dev/hda1/ is 132.16GB. I selected that in the list, and tabbed over to Move/Resize. I see

Free space preceding: 0
New Size: 135337
Free Space Following: 0

So, when I change the "New Size" to 102400, the New Space Following adjusts, but the New Space Proceeding does not. Is that OK? Am I doing everything right so far? Can I hit Resize/Move?

---

### Post by CatKiller on 2006-10-06
> **Jordan Meeter said:**
> The GParted CD. :]

I haven't used the GPartEd cd, nor had any problems with my mouse using any live cd. But a distinctly lo-fi solution would be to look at your /etc/X11/xorg.conf file, write down what it says in the appropriate InputDevice section, boot the live cd and edit that file appropriately. Restart X (Ctrl-Alt-Backspace), and hope for the best.

There's probably some boot option that you could use to get the mouse working sensibly, but you'd have to read the gparted documentation for that. Or you could just use the keyboard. Or a different mouse.

---

### Post by CatKiller on 2006-10-06
> **Jordan Meeter said:**
> So, when I change the "New Size" to 102400, the New Space Following adjusts, but the New Space Proceeding does not. Is that OK? Am I doing everything right so far? Can I hit Resize/Move?

That's right. You can change any of the values, and the others will adjust. You should get visual cues as well - it is a graphical application, after all.

---

### Post by Jordan Meeter on 2006-10-06
I was going to hit apply, but then I saw that your next step was> Move the / partition so that it's at the start of the free space.
Do you mean move the little box with red/teal borders to the front of the grey box ("unallocated")? How can I do that with my keyboard?

---

### Post by lemonsCC on 2006-10-06
hmm with the keyboard...how are you resizing the partitions?  what keystrokes?

yes you want the colored boxes all the way to the left.

---

### Post by Jordan Meeter on 2006-10-06
What box represents / ?

And I'm using the directional keys and the tab key to get around...

---

### Post by CatKiller on 2006-10-06
> **Jordan Meeter said:**
> I was going to hit apply, but then I saw that your next step was

> Move the / partition so that it's at the start of the free space.

Do you mean move the little box with red/teal borders to the front of the grey box ("unallocated")? How can I do that with my keyboard?

You can hit Apply after each step if you wish.

If the colours are the same as the screenshot you posted earlier, then it's a dark blue box. /dev/hda2.

You should be able to do it with the same Move/Resize screen that you were using before, except this time on the ext3 partition, and by adjusting the free space preceding value. You might need to do it as a two-step process - move the partition (Apply), and then change the size. I haven't used the program that much so I don't know how intelligent it would be, nor what the limitations are.

Did you make a backup?

---

### Post by lemonsCC on 2006-10-06
you can set the "free space preceding" to 0, set the desired partition size and then let the "free space following" fill the rest of the drive

---

### Post by Jordan Meeter on 2006-10-06
> **CatKiller said:**
> You can hit Apply after each step if you wish.

If the colours are the same as the screenshot you posted earlier, then it's a dark blue box. /dev/hda2.

You should be able to do it with the same Move/Resize screen that you were using before, except this time on the ext3 partition, and by adjusting the free space preceding value. You might need to do it as a two-step process - move the partition (Apply), and then change the size. I haven't used the program that much so I don't know how intelligent it would be, nor what the limitations are.

Did you make a backup?
Yeah, I backed up all my important stuff. So basically I want the box that represents Linux in front of the box that represents Windows?

---

### Post by CatKiller on 2006-10-06
> **Jordan Meeter said:**
> Yeah, I backed up all my important stuff. So basically I want the box that represents Linux in front of the box that represents Windows?

No. You want to keep the partitions in the order that they are in.

Change the **endpoint** of the Windows partition to create some free space to the right of it. Then move the **startpoint** of the Linux partition so that it is next to the endpoint of the Windows partition again.

---

### Post by Jordan Meeter on 2006-10-06
Ok, let's start this over. I think I'm going to have *only* Ubuntu on my desktop, and only Windows on my laptop (what I'm using right now.)

Can I pop in my Ubuntu CD and just install as normal?

---

### Post by CatKiller on 2006-10-06
> **Jordan Meeter said:**
> Ok, let's start this over. I think I'm going to have *only* Ubuntu on my desktop, and only Windows on my laptop (what I'm using right now.)

Can I pop in my Ubuntu CD and just install as normal?

Sure. I think that the default option for the Ubuntu install is to use the entire disk.

---

### Post by Jordan Meeter on 2006-10-06
Ok, thanks a lot you guys. Thank you for spending the time to answer my questions and for putting up with my noobness. :KS 

-Jordan

---

### Post by lemonsCC on 2006-10-06
Hope it wasn't too painful, and maybe you learnt something in the process. :p

---

### Post by ice60 on 2006-10-07
> **Jordan Meeter said:**
> Ok, thanks a lot you guys. Thank you for spending the time to answer my questions and for putting up with my noobness. :KS 

-Jordan

hi, here's a video showing how to install Dapper. if you ever plain on having windows and ubuntu on a dual-boot you should install windows first.

also, screenshots are useful sometimes if you need help :) 
[http://video.google.com/videoplay?docid=-233292328709576403](http://video.google.com/videoplay?docid=-233292328709576403)

---

