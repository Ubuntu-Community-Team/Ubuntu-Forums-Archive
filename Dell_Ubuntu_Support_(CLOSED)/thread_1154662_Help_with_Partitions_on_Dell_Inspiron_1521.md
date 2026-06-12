---
title: "Help with Partitions on Dell Inspiron 1521"
date: 2009-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tom.swartz07 on 2009-05-10
Hi all

Im very new to Ubuntu, but so far I like what I see!
I have just installed Ubuntu 9.04 on my Dell Inspiron 1521, as a dual boot. When I went through the setup, I selected to install 'side by side' with windows. I originally had Vista on here. 
The problem is, when Ubuntu installed side-by-side, it only sized the partition exactly large enough for the OS and absolutely nothing else. 

What are my options at this point? I cannot install any updates, the OS doesnt save any of my preferences, nor can I download any new packages. Is there an easy way to resize the partition to give me more space on the Ubuntu partition, or would I have to uninstall and re-install with a larger partition? Or is there a way to tell Ubuntu to use a different partition for future files changes?

Thanks to anyone for help!

---

### Post by lindsay7 on 2009-05-10
Ok, there is a application that should be on your system called Gparted. It can be used to partition, format, resize partitions, etc.  You can find it under system/ administration. It will be listed as partition editor. If it is not there you and get it from the add/remove menu under applications or in the Synatic package manager. When you open it if you right click on a partition you can unmount the partition. You have to unmount a drive or partition to work on it.  You can also go to the Gparted web site and down load the ISO file and burn it to a disk. It will be a "live cd" which means that you can boot from it. When you use it this way the drives and partitions will be unmonted so that you can work on them this way. The web site also has all the support info that you will need.  I like to use the live cd and it comes in handy to have it around.  If you are going to change the size of your windows drive or partition, it is best that you defrag it before you resize it so that you have less of a chance to mess up the info on that drive by resizing it. When you installed Ubuntu, there should be a "swap" partition on you computer. You normally do not need to increase the size of that partion so just leave it alone. Shrink your windows partiontion. This will give you "unallocated" space which you can then grow your Ubuntu partition into.

---

### Post by tom.swartz07 on 2009-05-10
Well thanks very much for the super quick reply! I did see on some of the other threads about gparted, so I'll give it a try! If it wasn't for the fact that I need autoCAD and a few other windows only apps, I'd reset the whole drive for ubuntu to use!

Just out of curiosity, why did Ubuntu install like that? Did I perhaps do something wrong in the installation, or is it just a common setting for it to install on a perfectly sized partition for itself?

I'll work on gparted later today and let you know if any other problems come up!

Thanks again!

---

### Post by tom.swartz07 on 2009-05-10
Just one quick question... Ive been reading up on the documentation on the gParted website, and im a little nervous as to doing this...

How safe is it for a windows OS to do this? naturally there shouldnt be much (if any) files at the end of a partition, particularly after a defrag, but there were multiple warnings about, particularly after a resize that I need, that the OS will not boot, or stop working.

If anyone has any words of encouragement, or advice on how to perform this extremely safely, I would love to know. 

Thanks!

---

### Post by ptsubin on 2009-05-10
I trust gParted than Disk managemnt in windows or ven norton partition magic. There is nothing to worry or afraid of. Just give the program its time. Don't be panic if it takes long time. DO never try to interrupt it and be keeping the AC adapter on. Why to waste time reading the documentation and warning? Give the program a try and it is the simplest through menus.

---

### Post by lindsay7 on 2009-05-10
The Ubuntu install tries to fill whatever empty disk space there is at the time. It is hard to tell why it did what it did after it is installed. The good news is the installation was fast I would guess and all you need to fo now is change a partition size.  Gparted works fine, I would not be concerned. while you are thinking about this and setting up your drive, you may want to take a look at setting up a separate partiton for your home directory. This is where all you personal files and programs go. This way when you update to a new version of Ubuntu, your home directory will stay on touched if you set it up that way.

---

### Post by tom.swartz07 on 2009-05-10
> **lindsay7 said:**
> The Ubuntu install tries to fill whatever empty disk space there is at the time. It is hard to tell why it did what it did after it is installed. The good news is the installation was fast I would guess and all you need to fo now is change a partition size.  Gparted works fine, I would not be concerned. while you are thinking about this and setting up your drive, you may want to take a look at setting up a separate partiton for your home directory. This is where all you personal files and programs go. This way when you update to a new version of Ubuntu, your home directory will stay on touched if you set it up that way.

Thanks again Lindsay! I got gParted up and i correctly gave myself a roomy 20 gigs for expansion.

**To anyone on the forums that could answer my question: does Ubuntu automatically move into the 'unspecified' drive space that I just cleared out, or do I need to resize the root partition into that cleared area?**

Thanks for the tip, Lindsay, but I dont think that Ill be keeping this laptop as my main workhorse for much longer, so in the future, Im sure that Ill be able to just wipe and start fresh with the next version. Ill definitely keep it in mind for next time though! :)

---

### Post by lindsay7 on 2009-05-10
You need to grow your root partition or the unallocated space will not be used.  You could just format that space and use it to place you data files or applications.

---

### Post by tom.swartz07 on 2009-05-10
> **lindsay7 said:**
> You need to grow your root partition or the unallocated space will not be used.  You could just format that space and use it to place you data files or applications.

Im not exactly sure what you mean.. Do I use gParted one more time for this and move the start of the partition into the new space, or is there a Ubuntu specific program that I could/should use to do this action better?

This seems to be the last thing that I need to do to get things just perfect for me

---

### Post by lindsay7 on 2009-05-11
Yes, you use Gparted. If you want to make sure that you are going to do this correctly. take a screen shot of your drive showing the partitions in gparted and post it. Then we can make sure that you have the correct instructions. If your drive shows the active partitions and some space that is called unallocated then all you need to do is use Gparted and extend your root partition into it.  If you want to just use this space for storage of your data and applications. Use Gparted to create a new partition and format it as ext3 or fat32.  Fat 32 partitons can be read and written to by both windows and Ubuntu.

---

### Post by tom.swartz07 on 2009-05-11
> **lindsay7 said:**
> Yes, you use Gparted. If you want to make sure that you are going to do this correctly. take a screen shot of your drive showing the partitions in gparted and post it. Then we can make sure that you have the correct instructions. If your drive shows the active partitions and some space that is called unallocated then all you need to do is use Gparted and extend your root partition into it.  If you want to just use this space for storage of your data and applications. Use Gparted to create a new partition and format it as ext3 or fat32.  Fat 32 partitons can be read and written to by both windows and Ubuntu.


Thanks again Lindsay, Im sorry for being such a bother.

Anyway, here's the screencap from gparted. Im assuming that Ill have to run it from the live cd to work on the partition? You had mentioned that I could change the unallocated space to FAT 32 which could be read by both Windows and Ubuntu; does that mean that it could be used as an 'in-between' drive, sort of a space that I could store windows files on, access them in Ubuntu and vice-versa?

If that's true, then Ill probably go that route. If not, then Ill just bump the Ubuntu size all the way to take up the 20 gigs available. 

Since Im still very new to this, could you please make any helpful suggestions as to the easiest and safest way to perform the task, according to what choice? 


I have a bit of a problem connecting to the internet through Ubuntu on my campus internet, so as of right now, im running all of these posts from Windows, and switching back when I need to do something. Its a problem with the wonderful Cisco Clean Access Agent not being able to run. (but thats for another day...)

Just to clarify- the Ubuntu partiton is all the way to the right, I know they might be a little small to see. 

[IMG]http://lh6.ggpht.com/_tORug_uHNu4/Sgetm4QH6VI/AAAAAAAAAEY/39Hm6GgFI5k/s800/Screenshot.png[/IMG]
After I get a reply, Im going to setup whatever methods that I need, then Im going to hit the hay- its 1am here now. pshoo haha

---

### Post by lindsay7 on 2009-05-11
"You had mentioned that I could change the unallocated space to FAT 32 which could be read by both Windows and Ubuntu; does that mean that it could be used as an 'in-between' drive, sort of a space that I could store windows files on, access them in Ubuntu and vice-versa?"

If you want to use the space for Ubuntu the you need to increase the partition sda4 first by resizing it and then increase partition sda6. You click on it and go to the menu bar and pick resize or I think you can just move the arrow at the left of the partition over to take up the unallocated space. You should use the Gparted live cd to do either of the choices above.

After looking at this again, I would suggest that you increase the size of you Ubuntu partition since is is so small.

---

