---
title: "mounting XP partitions in VBox &amp; guest Ubuntu 8.10"
date: 2009-03-13
forum: General Help
---

### Post by nichos on 2009-03-13
Tried various sugestions on how to mount my XP partitions in VBox with no luck.

All I can see is as per screenshot below.

When I dual boot XP- Ubuntu 8.10 all partitions (c.d.e.f.g) mounted from the word go & could work in them. 

Any help please, I am absolute illeterate in Linux lingo.

[[img]http://img246.imageshack.us/img246/2249/screenshotk.th.png[/img]](http://img246.imageshack.us/my.php?image=screenshotk.png)

---

### Post by kestrel1 on 2009-03-13
With virtual box you need to set up a shared folder & anything in that folder can then be seen in Ubuntu.

---

### Post by nichos on 2009-03-13
Thanx kestrel,

Tried that, came out of Ubuntu, & in VBox Settings I typed C:\, D:\ etc in Settings > shared, but nothing happened.

Please see screenshot of what I did & failed

Can you show me when I went wrong, in idiots terms how to please?   ..........nick

[[IMG]http://img17.imageshack.us/img17/3972/vboxo.th.jpg[/IMG]](http://img17.imageshack.us/my.php?image=vboxo.jpg)

---

### Post by kestrel1 on 2009-03-13
Try this: [http://blogs.sun.com/tao/entry/virtual_box_shared_folder_between](http://blogs.sun.com/tao/entry/virtual_box_shared_folder_between)
You want to install the VBoxLinuxAdditions-x86.run to get this to work, I would think. Not actually tried it yet.

---

### Post by nichos on 2009-03-13
Please note screenshot in my post #1 above showing what I hope I have installed "VBoxLinuxAdditions-x86.run", in full screen & free mouse pointer.

I keep geting these below whatever I type in Terminal, what should I use for "sharename" or for partition name, my XP partitions are shown in the screenshot below.  ........Thanx..........nick

x@x-Virtual:~$ sudo mkdir /mnt/tao_xp
[sudo] password for x: 
mkdir: cannot create directory `/mnt/tao_xp': File exists
x@x-Virtual:~$ 
x@x-Virtual:~$ 
x@x-Virtual:~$ sudo mount.vboxsf TAO /mnt/tao_xp
mount.vboxsf: mounting failed with the error: Protocol error
x@x-Virtual:~$ 



x@x-Virtual:~$ sudo mkdir c:\ExcelS
x@x-Virtual:~$ sudo mount.vboxsf sharename ~/c:\ExcelS
mount.vboxsf: mounting failed with the error: Protocol error
x@x-Virtual:~$ 

[[IMG]http://img24.imageshack.us/img24/5354/xpparts.th.jpg[/IMG]](http://img24.imageshack.us/my.php?image=xpparts.jpg)

---

### Post by kestrel1 on 2009-03-13
OK, have a look at this thread:[http://forums.virtualbox.org/viewtopic.php?f=3&t=2279&start=15](http://forums.virtualbox.org/viewtopic.php?f=3&t=2279&start=15)

---

### Post by kestrel1 on 2009-03-13
OK, I think I have found out what you needs to do. I got it working.
Make the share in the VirtualBox control panel & give it a sensible name: Data or what ever you want, but leave it as a single word & no dashes etc.
Then make a mount folder in your guest ```
sudo mkdir /media/data
```
Then mount it with:```
sudo mount -t vboxsf data /media/data
```
Note: do not use uppercase characters in the ID 'data' & that should be the same word that you named the share in the control panel.
Hope that makes sense & helps.
To open the share browse to the /media/data folder.

---

### Post by Slim Odds on 2009-03-13
> **kestrel1 said:**
> Then mount it with:```
sudo mount -t vboxsf data /media/data
```Note: do not use uppercase characters in the ID 'data' & that should be the same word that you named the share in the control panel.


Also, don't run this command from within the /media directory. It will also fail with a "protocol error".

The reason is the duplicate names (data).

---

### Post by kestrel1 on 2009-03-13
Fair point Slim.
Another way around this would be use a different name for the ID & share name to the mount point. so it could look like this```
sudo mount -t vboxsf dataxp /media/data
```
Obviously change the share name to the same as dataxp.

---

### Post by Slim Odds on 2009-03-13
> **kestrel1 said:**
> Fair point Slim.
Another way around this would be use a different name for the ID & share name to the mount point. so it could look like this```
sudo mount -t vboxsf dataxp /media/data
```Obviously change the share name to the same as dataxp.

True, or just don't be in the /media when you mount that stuff....

I kind of like to have the sharename and the mount point name the same.....

---

### Post by nichos on 2009-03-14
sharename, media, data .................... what on earth are these?.

Sorry chaps, been trying for 4 yrs to get to grips with Linux jargon & failed miserably.

Can't you put it so that an illeterate can understand, idiot's approch?

nick

---

### Post by Slim Odds on 2009-03-14
> **nichos said:**
> sharename, media, data .................... what on earth are these?.

sharename is the "name" of the "shared" folder that you define in VirtualBox.

unix (which is really what linux is) uses "mount points" to locate partitions for data. /media is a place that linxu puts removable "media" (which really means that in this example that it's the wrong place to put this, but that's another story).

data was just a "name" that was being used for one of the "shared folders" (and in this case also the mount point). data is a generic name for, well, data.

It's not as hard as you make it out to be.

---

### Post by nichos on 2009-03-14
Thanx chaps,
so what do I type  in to be of any use here.

I showed you screenshots on # 3 & 5 above of my XP partitions's names, but when I type them in settings still nothing happens

What do I extrapolate these words "data", "media" "vboxsf" etc with to suit my system?

Please see screenshot below for what happens to me.   ........nick


[[IMG]http://img220.imageshack.us/img220/8412/screenshotxxvirtual1.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotxxvirtual1.png)

---

### Post by kestrel1 on 2009-03-14
I notice that it keeps failing with a protocol error.
Have you installed the virtualbox additions to Ubuntu?
Also I see you tried mounting to dataxp & data, is either of those the name that you have used in the VirtualBox settings for your shared folder?

---

### Post by nichos on 2009-03-14
No, I tried two other names C:\ & C:\ExcelS, but neither worked.

[[IMG]http://img17.imageshack.us/img17/4558/screenshotxxvirtual.th.png[/IMG]](http://img17.imageshack.us/my.php?image=screenshotxxvirtual.png)

---

### Post by kestrel1 on 2009-03-14
That is because of the bad characters in the name ':\'
The share needs a sensible name, see the attached:
[ATTACH]106378[/ATTACH]

---

### Post by nichos on 2009-03-14
I am trying to mount my XP directory   C:\ExcelS(C: ) 
That is its name as you can see in screenshot of my post #5 page 1

Now what would you say are sensible commands to insert in VBox Settings to make it show me my XP C:\ directory? and how would you enter them in these:-

sudo mkdir /media/data

sudo mount -t vboxsf data /media/data

or in this perhaps:- sudo mount -t vboxsf data /media/data

---

### Post by kestrel1 on 2009-03-14
Can you post the same screen that I posted above? If you use advanced on the forum you can add an attachment.

---

### Post by kyphi on 2009-03-14
Why are you trying to mount partitions in VirtualBox?

You install operating systems in VBox as guests of the host system.  You also install the guest additions and set up a shared folder that can be accessed by both host and guest.

I currently have 4 operating systems installed in VBox in Ubuntu.

Can you enlighten me as to what you are trying to achieve?  I may be able to help out.

---

### Post by kestrel1 on 2009-03-14
> **kyphi said:**
> I currently have 4 operating systems installed in VBox in Ubuntu.
Only four :) I currently have ten, Windows 7 & server 2008 included :D

---

### Post by kyphi on 2009-03-14
They come and go.

Then you should be quite familiar with VBox.

I cannot make heads or tails out of this question: mount points in VBox? dual booting in VBox?

---

### Post by kyphi on 2009-03-14
nichos, to set up a shared folder:

VirtualBox must be closed and guest additions must have been installed in XP.

1. create a folder in your Home directory and name it vboxshared.
2. in a terminal type ```
VBoxManage sharedfolder add XP -name vboxshared -hostpath /home/nichos/vboxshared
```
(Change nichos to your homefolder name)
3. in XP (in VBox) go to "Run", type CMD and type ```
net use x: \\vboxsrv\vboxshared
```

---

### Post by kestrel1 on 2009-03-14
Yes you could say I am familiar, but still learning myself :)
I use VBox in Ubuntu & Windows. My Windows machine at work has about 12 or more Virtual machines. Various Linux varients & Windows.

---

### Post by kestrel1 on 2009-03-14
> **kyphi said:**
> nichos, to set up a shared folder:

VirtualBox must be closed and guest additions must have been installed in XP.

1. create a folder in your Home directory and name it vboxshared.
2. in a terminal type ```
VBoxManage sharedfolder add XP -name vboxshared -hostpath /home/nichos/vboxshared
```
(Change nichos to your homefolder name)
3. in XP (in VBox) go to "Run", type CMD and type ```
net use x: \\vboxsrv\vboxshared
```
I think you will find he is going the other way. XP is the host Ubuntu is the guest.

---

### Post by kyphi on 2009-03-14
> XP is the host Ubuntu is the guest.

How sad.

That explains the riddle - thanks kestrel1

---

### Post by Slim Odds on 2009-03-15
> **kyphi said:**
> VirtualBox must be closed and guest additions must have been installed in XP.

The first part is not true.... the virtual machine can be running.

---

### Post by nichos on 2009-03-15
sorry chaps, I am utterly confused with all the above.

BUT, you made me think, ..........what do I need to mount my XP partitions for, when I can minimize the VBox linux & work on them in XP.

Thank you very much for trying to help me.

You are excelent Pals, others said .....go read the books....

Regards,     ..............nick

---

