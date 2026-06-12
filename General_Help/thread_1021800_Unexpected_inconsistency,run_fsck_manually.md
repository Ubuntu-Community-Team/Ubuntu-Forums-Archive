---
title: "Unexpected inconsistency,run fsck manually"
date: 2008-12-25
forum: General Help
---

### Post by kindlinux on 2008-12-25
I have a problem,this happened in august,but I have gotten around it,and problem is still there...

One day I was starting up my computer,and fsck was checking my filesystems.The suddenly,A message came up like the one on the title of this post(Unexpected inconsistency,run fsck manually).

I attempted to do what it said in this month and it gave me a waring saying:
e2fsck 1.40.8 (13-Mar-2008)
/dev/hda***(device is hidden for privacy) is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

Should I do it?,or just keep pressing ctrl+d like it says,when it has the unexpected inconsistency warning while linux is booting,to get around it?

Thank you...:-?

---

### Post by albinootje on 2008-12-25
> **kindlinux said:**
> 
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

It's possible that you have a typo or syntax error in /etc/fstab
Can you post the output of the following :
```

cat /etc/fstab

```

---

### Post by kindlinux on 2008-12-25
> t's possible that you have a typo or syntax error in /etc/fstab
Can you post the output of the following :
Code:

cat /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda*
UUID=92ef199d-c805-4a63-820d-71c7dd5cf688 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda*
UUID=0abc22b3-866c-429e-bdd5-e362254ce705 /home           ext3    defaults        0       2
# /dev/hda*
UUID=D8E41ED9E41EB9A8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda*
UUID=b50fec53-d2fd-4810-8be3-b7ab77ded596 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

end of copy and paste...
(*-maked out because of privacy)

---

### Post by Herman on 2008-12-26
My idea would be to boot your Ubuntu Hardy Heron or Intrepid Ibex live CD and open GParted. 
Just go 'System'-->'Administration'-->'Partition Editor', (GParted), you will be asked to type your password, and when GParted opens, it will show you a graphical view of your partitions.

Find the partition you want to check, (your Ubuntu partition), and right-click on it.
Probably you will then be able to click 'check', but if the option is 'greyed out', just click 'unmount first'. (Never, ever attempt to run a file system check on a partition while it's mounted).
After you click 'check', click 'apply' on the toolbar, then 'apply again in the confirmation window. 
A new window will open with a sliding bar moving crosswise backwards and forwards for a little while. 
When that has finished, your file system will probably be fixed!

You can click the 'Details' arrows to read all the drop-down menus that tell you what happened. It doesn't hurt to read them even if you don't understand it, you might be able to understand a little of it.

Then close the window and when you're ready, close GParted, (unless you have more partitions to check or something else to do), and reboot. 

Remove the Live CD and boot into your Ubuntu and it should be all fixed, good as gold!

Regards, Herman :)

---

### Post by albinootje on 2008-12-26
> **kindlinux said:**
> 
# /dev/hda*
UUID=D8E41ED9E41EB9A8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
Change the 0 1 in that line to 0 0 to prevent file-checking attempts by Linux for that NTFS-partition.

---

### Post by Herman on 2008-12-26
> Change the 0 1 in that line to 0 0 to prevent file-checking attempts by Linux for that NTFS-partition.:) Hey, well spotted there, albinootje! 
I agree!

Regards, Herman :)

---

### Post by kindlinux on 2008-12-26
Anyone else has ideas?
(I will try the ideas above...):-k

> 
Quote:
Originally Posted by kindlinux View Post
# /dev/hda*
UUID=D8E41ED9E41EB9A8 /media/hda1 ntfs defaults,umask=007,gid=46 0 1
Change the 0 1 in that line to 0 0 to prevent file-checking attempts by Linux for that NTFS-partition.

How do I change the ¨01¨?,do I just have enter that UUID line with the edits into the command line.

---

### Post by albinootje on 2008-12-26
> **kindlinux said:**
>  How do I change the ¨01¨?,do I just have enter that UUID line with the edits into the command line.

```

sudo gedit /etc/fstab

```
Then find that line, and at the end change the 1 into a 0
Save & exit gedit, the text editor.
Reboot to test whether this helps against the filesystem check problems.

---

### Post by cariboo on 2008-12-26
If you are consistently getting the message that there is a problem with your hard drive. I would suggest booting from a Livecd and running fsck on your unmounted hard drive.

Jim

---

### Post by kindlinux on 2008-12-26
> 
Code:

sudo gedit /etc/fstab

Then find that line, and at the end change the 1 into a 0
Save & exit gedit, the text editor.
Reboot to test whether this helps against the filesystem check problems.

I typed in sudo gedit /etc/fstab,but I got this:
blue@hppavilion:~$ sudo gedit /etc/fstab
sudo: gedit: command not found

I did type in gedit though and the terminal told me it is not installed...so am going to install it,and get back to this post.

About the live cd,is knoppix good?

---

### Post by albinootje on 2008-12-26
> **kindlinux said:**
> I typed in sudo gedit /etc/fstab,but I got this:
blue@hppavilion:~$ sudo gedit /etc/fstab
sudo: gedit: command not found

I did type in gedit though and the terminal told me it is not installed...so am going to install it,and get back to this post.


Are you using Kubuntu or Xubuntu ?
You can try this for Kubuntu :
```

sudo kate /etc/fstab

```
Or for Xubuntu :
```

sudo mousepad /etc/fstab

```

Knoppix used to be very good as a Live cd, haven't tried it for a while though.

---

### Post by kindlinux on 2009-01-18
I used fsck on Damn small,but it's not working.It says filsystem has unsupported feature(s) (/dev/hd4)

and to get a new version of e2fsck...

So I think that means I will have to go back and install a newer version of fsck on xbuntu then...

---

### Post by kindlinux on 2009-01-18
ok,its fixed...

I dowloaded and burned a rescue cd named insert:
[http://linux.softpedia.com/get/System/Diagnostics/INSERT-146.shtml]("http://linux.softpedia.com/get/System/Diagnostics/INSERT-146.shtml")

It has gparted,so I ran the live cd,and it gave nice desktop.
After that I ran gparted and it let me fix and check the filesystem.:P


Anyway guys thanks for the help...:KS
Have a lively day...

---

