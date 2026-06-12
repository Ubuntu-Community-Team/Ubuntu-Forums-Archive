---
title: "Capture custom Linux OS image using inbuilt Linux applications?"
date: 2016-09-09
forum: Development CD/DVD Image Testing
---

### Post by sd.hussain on 2016-09-09
Hello. I have an issue. 


I want to know if I can capture any Linux OS custom image using an Linux in-built app?
Example -  I can use SysPrep to capture Windows image, but how do I go about capturing Linux image by using inbuilt linux app?


Because after capturing, I want to use WDS (Windows Deployment Service) through Server 2008 R2 to deploy the windows and Linux images on new systems. I don't want to use any third party applications to capture the Linux image. 


Please help. Thanks.

---

### Post by TheFu on 2016-09-10
Not sure I understand what you mean, but you can make "images" at different levels with these tools.  

dd.
partimage.
clonezilla.
fsarchiver.

3rd party?  Everything is 3rd party on a Linux system - perhaps you mean non-commercial? All of these are in the normal Canonical repos - at least I think they are, but didn't check.

Only dd is already on most systems. It makes a bit-for-bit copy of whatever you point it at. That can be an entire HDD, a partition (of any type), files, devices, whatever.  It is smart in how stupid it is. That is a blessing and a curse. It is up to the user to use it properly. If you copy an entire HDD device, you get the partitions, file systems, any encryption, files and directories laid out like they were in the original.  If you copy at the partition level, then you get everything below the partitioning. Of course, the targets need to have enough room to hold the data from the source. The target needs to be proper for what the source provides.  Shoveling an HDD image into a partition won't work, for example.  dd won't check that before starting.  Often, the bits at the end of a device/partition aren't important.  dd is dumb enough to let us use it even when this is the situation, but WE are in control and take responsibility for any issues.

Often, it is smarter to clone a system using tools that work at a higher level.  Something like fsarchiver will compress a file system into a group of files that can be deployed to a new partition/LV while resizing.  This can be very handy.  

After cloning a system, there are probably a few minor things that need to be fixed.  I haven't done this with 16.04, but with 14.04 and prior releases, just the hostname and udev rule(s) for any network adapters needed to be fixed on a system with DHCP.  If static IPs are used, then those will need to be fixed too.  A tiny script run just after the cloning could fix those things in less than a second.

Hope this is helpful.  If it doesn't answer the real question, please expand and explain more.

---

### Post by sd.hussain on 2016-09-11
Thank you so much for the reply. Also I wanted to ask, if any of the options in linux like the DD option will let me clone the Linux installed image after making changes to it. 
Example: Can I install a fresh Linux and then install other applications on it. Then go on to clone that OS using DD to deploy from the WDS?


Thank you.

---

### Post by TheFu on 2016-09-11
I have no idea what WDS is. You can clone anything with dd.  It is stupid, so you are expected to be smart. Those disk duplication devices you see - those use dd.  Most of the disk cloning software included with new HDDs the last 20 yrs use dd too, they just put a slight GUI in front.  Meh.

I suspect you really don't want to use dd.  If I were trying to deploy the same OS to 100-50,000 systems and I controlled the disk size, then I'd create the "master" images for each partition using fsarchiver and write a little script that 
a) creates the partitions on the target as desired - there would be /, /home, /var and a swap partition
b) uses fsarchiver to unpack each of the partitions into the correct target partition
c) modifies the few items that need to be changed - hostname and network device name.

For fewer than 100 systems, I'd just use **cobbler** to install a base system then use **ansible** to make it look like I needed.  Ansible is what devops teams use to make 5-1000 servers - that can be from building the server to enforcing policy items periodically (every hour, every day, every week, on-depand, when ever).

All of these things are free to use and come with source code so changes can be made if you can't get the community to meet the priorities you may have. That is important for a business.

---

### Post by sd.hussain on 2016-09-11
Thank you for replying back again. WDS is Windows Deployment Service which is used to deploy OS images on other connected systems. WDS is configured on server and then the images are added to it.  

Basically what I have to do is - 
1. Freshly install Windows and Linux
2. Add some applications on it
3. Clone then as they are
4. Add the images to WDS that will be configured on Server
5. Deploy the same images to other connected new systems through the Windows 2008 Server R2
6. Make sure they dual boot with Windows and Linux. 

So in Windows, I am able to clone the custom Windows OS using the inbuilt application called SysPrep and it does clone the whole new OS with the same settings applied to it. I want to do the same with the Linux but I am not sure if DD can do that? 

Also, I am not allowed to use any 3rd party application to complete the work as it is one of the requirement. So, if there is nothing like SysPrep in Windows, then I am kinda like stuck with DD now. 

Is there any link where dd is explained briefly to clone a custom drive?

Thank you for the reply's.

---

### Post by TheFu on 2016-09-11
"3rd party application" doesn't compute for Linux. **everything** is a 3rd party app, except the kernel itself.  ls is the 3rd party app, dd is, mv is, cp is .... If you are stuck with packages that are included inside a distribution, then you are fine.  Everything I've suggested is in Ubuntu already. Plus the machine used to create the source doesn't mean that the target needs to have any of those utilities.  Linux is highly, highly customable.  It is a different way to think than from the MSFT/Commercial software way of thinking.  There are over 20,000 packages that are "part" of Ubuntu - most are not installed by default, but that is easy to change.  Perhaps becoming more familiar with the idea of a repo and PPA would be helpful?

BTW, dd will clone Windows too, but it won't remove device drivers like sysprep does.  That isn't how Linux works and it doesn't need to work that way unless you've done/loaded proprietary drivers for some reason (and there are good reasons for this).

At this point, you need to check out the manpages for each of the tools AND try them. It isn't like you have anything to loose by trying each.  Play with them for an hour each while reviewing the manpage - that will answer more questions than I can hope to.

---

### Post by Bucky Ball on 2016-09-11
Just a note: be aware that, as stated, dd is dumb and consequently, it's nickname is 'disk destroyer'. It DOES expect you to be smart. One false move and it will live up to its nickname. In other words, if you decide to use dd, BE VERY CAREFUL! It takes no prisoners if you make a mistake. It will completely wipe and overwrite whatever you point it at, no questions asked. No 'are you sure'? Nothing. 

Just saying. Some people expect it to be friendly. It's not and there's no coming back once you jump. :)

---

