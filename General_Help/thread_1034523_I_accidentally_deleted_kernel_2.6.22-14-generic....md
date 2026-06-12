---
title: "I accidentally deleted kernel 2.6.22-14-generic..."
date: 2009-01-08
forum: General Help
---

### Post by marmaladeskies on 2009-01-08
Feel free to laugh at me.  I was trying to clear up some space by deleting the local files in Synaptic (the residual config ones) but managed to click on and delete the local files instead... which included kernel 2.6.22-14-generic.  So when I start up my computer, grub just says Error 15:  File not found.  And I obviously can't get in through recovery mode either since I deleted the kernels...

So right now I just got on the live cd, wondering what to do.  Specifically, how do I get my kernel 2.6.22-14-generic back?

Thanks!!

---

### Post by louieb on 2009-01-08
Boot to the Live DC and chroot  to the harddrive install. then use synaptic or apt to install the kernel again. 

become root
     
     ```
sudo su 
```mount your / partition
            
```
mkdir /mnt/os
mount /dev/??? /mnt/os 

```chroot into it
     
     ```
chroot /mnt/os 

```Now you should be able to use synaptic to install the kernel.
Good Luck.

---

### Post by MighMoS on 2009-01-08
> **louieb said:**
> 
     ```
chroot /mnt/os 

```Now you should be able to use synaptic to install the kernel.
Good Luck.

Assuming you launch synaptic using the command (in the same terminal) ```
gksu synaptic
```Otherwise, it would just use the LiveCD synaptic.

---

### Post by marmaladeskies on 2009-01-10
Thanks, I think we're on to something, but gksu synaptic just outputted:

(gksu:8505): Gtk-WARNING **: cannot open display: :0.0

Also, I'm beginning to fear that I removed more than that one kernel.  Can someone help me out by checking their synaptic local/obsolete files (IIRC) and see what I'll need to install?

Thanks everyone, I think I'm getting close.

---

### Post by caljohnsmith on 2009-01-10
It looks like you might need to set up your chroot environment a little more completely in order to make it work; how about trying:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
apt-get purge linux-headers-2.6.24-14-generic linux-image-2.6.24-14-generic linux-restricted-modules-2.6.24-14-generic linux-ubuntu-modules-2.6.24-14-generic
apt-get install linux-headers-2.6.24-14-generic linux-image-2.6.24-14-generic linux-restricted-modules-2.6.24-14-generic linux-ubuntu-modules-2.6.24-14-generic
ls -l /boot
exit
```
You'll need to change the sdaX above to whichever is your Xubuntu partition, and please post the output of all the above commands.

---

### Post by marmaladeskies on 2009-01-10
The output of:  'sudo cp /etc/resolv.conf /mnt/etc/resolv.conf' was  'cp:  cannot stat '/etc/resolv.conf': No such file or directory''

The apt-get purge command outputted 'Package linux is not installed, so not removed'

apt-get install outputted 'E:  Couldn't find package linux-headers-2.6.24-14-generic'.

I'm thinking I might have messed this up beyond what I had imagined...

---

### Post by caljohnsmith on 2009-01-10
If you don't have a /etc/resolv.conf file when running the Live CD, that means you most likely don't have an internet connection set up from the Live CD. In order to reinstall that kernel, you'll need internet connectivity so you can download it. If for some reason you can't access the internet from your Live CD, another option would be to go to packages.ubuntu.com, manually download those kernel packages listed after the "apt-get install" command in my previous post, transfer them to your Ubuntu desktop via maybe a USB stick, and then you could install them manually. If that's the only alternative you have, let me know, and I can give you the specific commands to try it out. Otherwise hopefully you can get an internet connection while using the Live CD.

---

### Post by marmaladeskies on 2009-01-10
Very strange, I do have an internet connection; I tried again and the resolv.conf line worked, but it still can't find the packages..

---

### Post by caljohnsmith on 2009-01-10
Can you please post the full output of all the commands? That might give us a better clue what the issue is.

---

### Post by marmaladeskies on 2009-01-10
Sorry about that.  ```
root@ubuntu:/# apt-get purge linux-headers-2.6.24-14-generic linux-image-2.6.24-14-generic linux-restricted-modules-2.6.24-14-generic linux-ubuntu-modules-2.6.24-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.24-14-generic

root@ubuntu:/#  apt-get install linux-image-2.6.24-14-generic linux-restricted-modules-2.6.24-14-generic linux-ubuntu-modules-2.6.24-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.24-14-generic


```

---

### Post by MighMoS on 2009-01-10
I just remembered this, if you still have SOME kernel installed, then running "sudo update-grub" should find it (while you're in the chroot). What happens if you just tell it to install "linux-image" "linux-restricted-modules" etc, without the versions?

---

### Post by caljohnsmith on 2009-01-10
OK, how about we try a different approach by running Synaptic from your Xubuntu install:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /tmp /mnt/tmp
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
xhost +
sudo chroot /mnt
su -l [COLOR="Blue"]<username>[/COLOR]
export DISPLAY=:0.0
gksudo synaptic &
```
Replace <username> above with your Xubuntu user name. If all goes well, Synaptic Package Manager should open; in Synaptic, go to Settings > Repositories, and make sure all the repositories are enabled. Then try installing the following packages:
```
linux-image-2.6.24-14-generic
linux-restricted-modules-2.6.24-14-generic
linux-ubuntu-modules-2.6.24-14-generic

```
If you run into problems, please post the output in the terminal for all the commands in addition to letting me know what happened. We can work from there if you want.

---

### Post by marmaladeskies on 2009-01-11
Everything seemed to work until the last line:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
sudo mount -ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /tmp /mnt/tmp
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ xhost +
access control disabled, clients can connect from any host
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su -l jr
jr@ubuntu:~$ export DISPLAY=:0.0
jr@ubuntu:~$ gksudo synaptic &
[1] 8770
jr@ubuntu:~$ Error copying '/home/jr/.Xauthority' to '/tmp/libgksu-8bfq31': No such file or directory

```

Then a window pops up saying: Failed to run synaptic as user root.
Unable to copy the user's Xauthorization file.

Again, I really appreciate your time and effort.  There's no way I could fix this on my own.

---

### Post by caljohnsmith on 2009-01-11
OK, how about right after doing the "cp" command to copy the resolv.conf file, try doing this command:
```
sudo cp ~/.Xauthority /mnt/home/jr/
```
Let me know if that works or not, and we can go from there.

---

### Post by marmaladeskies on 2009-01-11
Interesting, the error changed:
```

jr@ubuntu:~$ gksudo synaptic &
[1] 8884
jr@ubuntu:~$ Error copying '/home/jr/.Xauthority' to '/tmp/libgksu-fcyqNA': Permission denied

```

And I got this popup:  
Failed to run synaptic as user root.
Unable to copy the user's Xauthorization file.

---

### Post by caljohnsmith on 2009-01-11
My mistake, I overlooked the fact that the ownership of the .Xauthority file would change to root when you use the sudo cp to copy it; but you have to use sudo since you want to copy that file to your home directory, yet you aren't currently logged in as that user. So after you copy that file over, how about doing:
```
sudo chown jr:jr /mnt/home/jr/.Xauthority
```
Just make sure you do that before the chroot command. Let me know how that goes or if you still run into problems (hopefully I haven't overlooked anything else :)).

---

### Post by marmaladeskies on 2009-01-11
I got this:

```

ubuntu@ubuntu:~$ sudo chown jr:jr /mnt/home/jr/.Xauthority
chown: `jr:jr': invalid user

```

This was before chroot and after i cp'ed... hmm, I may restart and try again...

---

### Post by caljohnsmith on 2009-01-11
I agree, how about rebooting, and then do all the following commands:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /tmp /mnt/tmp
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo cp ~/.Xauthority /mnt/home/jr/
xhost +
sudo chroot /mnt
su -l jr
sudo chown jr:jr ~/.Xauthority
export DISPLAY=:0.0
gksudo synaptic &
```
I think that should work, but let me know if you run into problems.

---

### Post by marmaladeskies on 2009-01-11
```

jr@ubuntu:~$ sudo chown jr:jr ~/.Xauthority
sudo: unable to resolve host ubuntu

```

:-/

Hmm.  I'm thinking I unfortunately may need to change something in my /etc/hosts/?  What exactly I would have to change, I do not know..

---

### Post by caljohnsmith on 2009-01-11
OK, how about trying the following commands instead:
```
sudo mount /dev/sdaX /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /tmp /mnt/tmp
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo cp ~/.Xauthority /mnt/home/jr/
xhost +
sudo chroot /mnt
chown jr:jr /home/jr/.Xauthority
su -l jr
export DISPLAY=:0.0
gksudo synaptic &
```
If you still get an "unable to resolve host" error with any of the commands, like the last gksudo command for instance, then try this instead:
```
sudo mount /dev/sdaX /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /tmp /mnt/tmp
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo cp ~/.Xauthority /mnt/root
xhost +
sudo chroot /mnt
export DISPLAY=:0.0
synaptic &
```
And if that doesn't work, let me know what the error is, and then when you are outside of the chroot environment (in another tab in the terminal for example), please post:
```
cat /etc/hosts /etc/hostname /nnt/etc/hosts /mnt/etc/hostname 
```
And we can work from there.

---

### Post by marmaladeskies on 2009-01-11
I tried the first code sequence, with no errors.  This is what the last line looked like:

```

jr@ubuntu:~$ gksudo synaptic &
[1] 8775

```

And synaptic didn't open.

The second sequence worked.  Synaptic opened, I enabled the repositories, a few didn't work:

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.

But I think these are inconsequential.

Looked for the following files:
linux-image-2.6.24-14-generic
linux-restricted-modules-2.6.24-14-generic
linux-ubuntu-modules-2.6.24-14-generic

I couldn't find any of them.  I could find them all with 2.6.22-14 and 2.6.4-16, but none with 2.6.24-14.

When I couldn't open grub, it said it was because I didn't have 2.6.22-14 kernels, so I have begun to install those.

I'll update you when it's finished, and hopefully working properly.  Thanks so much for all your help!!!  You really have no idea how much I appreciate it.

---

### Post by caljohnsmith on 2009-01-11
My apologies, I see that the commands I gave you way back in post #5 would probably have worked if I didn't have the typo having you try to download the "2.6.[COLOR="red"]24[/COLOR]-14-generic" kernel packages instead of the "2.6.[COLOR="red"]22[/COLOR]-14-generic" kernel packages that you originally mentioned. At least it was a good learning experience for me to know what it took for you to get Synaptic from your Ubuntu install working from your Live CD. Let me know how it goes about installing the 2.6.22-14-generic packages, but you'll probably be fine now that you figured out the real issue. :)

---

### Post by marmaladeskies on 2009-01-11
It worked!  Don't worry about the typo, the point is everyone is perfect now, and we've both learned a lot in the process.  I think this makes three times kind people have saved my *** from my own stupidity on this forum.  You guys are the best, and hopefully I've learned my lesson!

---

### Post by caljohnsmith on 2009-01-11
Glad to hear the kernel reinstalled OK and everything is good in LinuxLand again. Cheers and have fun with your Ubuntu install. :)

---

### Post by cpare on 2010-09-06
Thanks for this post - it also solved my problem!

---

### Post by !nkubus on 2011-01-22
> **caljohnsmith said:**
> OK, how about we try a different approach by running Synaptic from your Xubuntu install:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /tmp /mnt/tmp
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
xhost +
sudo chroot /mnt
su -l [COLOR="Blue"]<username>[/COLOR]
export DISPLAY=:0.0
gksudo synaptic &
```
Replace <username> above with your Xubuntu user name. If all goes well, Synaptic Package Manager should open; in Synaptic, go to Settings > Repositories, and make sure all the repositories are enabled. Then try installing the following packages:
```
linux-image-2.6.24-14-generic
linux-restricted-modules-2.6.24-14-generic
linux-ubuntu-modules-2.6.24-14-generic

```
If you run into problems, please post the output in the terminal for all the commands in addition to letting me know what happened. We can work from there if you want.

You saved my life my kernel were deleted by the tool ailurus :)

---

### Post by meanmrmustard on 2011-03-13
Two years laterI find this thread and my bacon is saved!
Thanks to all.

---

### Post by lifutushi on 2011-04-20
I always did the same mistake. So I always keep a DEB version of my customized kernel somewhere and do dpkg from a liveCD after chroot. works everytime

---

