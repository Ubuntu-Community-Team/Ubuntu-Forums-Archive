---
title: "Ipod Nano"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Pedricko on 2005-11-27
Hi, I'm a noob when it comes to Mp3 players and have just purchased a new ipod nano (in a rather fetching black).

Trouble is I have NO idea how to get my mp3s onto it I have connected the USB cable and got the 'do not disconnect' message, and have downloaded GtkPod, and tryed to synch my library to it - no avail!

Any step by step tips for an ipod noob?

[EDIT] Im also using a USB 1.1 (poor me) connection, but the pod is mounting and appears on the desktop

---

### Post by Brent Dax on 2005-11-27
I've been using the Banshee music player to copy music to my iPod nano (white).  You can install it from the Universe repository; it's very similar to iTunes.

---

### Post by sevenrechlin on 2005-11-27
try doing:

$sudo apt-get xmms*
$sudo apt-get amarok*

and then run amarok and use it to place music on your ipod.

Edit: btw, keep the * at the end.

---

### Post by quietglow on 2005-11-27
Hmm...I've been using GTKpod and like it quite a bit. I would like to have combined player and ipod updater a la itunes. I'm checking Banshee out right now.

---

### Post by Pedricko on 2005-11-27
Using banshee right now, I have no idea how to get tracks from my library to the ipod, and when I clicked the Ipod button (next to volume) and went into advanced I got a 'No' next to something to do with writing.

EDIT: Write support: No

---

### Post by quietglow on 2005-11-27
FWIW, 5 minutes with banshee and I'd already prefer it to gtkpod and rhythmbox--for one thing, it does the work of both of these in one app.

Its also got a very snazzy "about" pane :-) (as the web page points out!)

---

### Post by Pedricko on 2005-11-27
Argh all the errors seem to be stating my ipod as un-writable... how do I format it?

---

### Post by sevenrechlin on 2005-11-27
Hmm not sure did you try amarok as well? It's a combined iPod writer or whatever and an amazing media player for linux.

---

### Post by Brent Dax on 2005-11-27
[QUOTE=Pedricko]Argh all the errors seem to be stating my ipod as un-writable...[/QUOTE]
A couple more things: first, try running "touch /mnt/ipod/test.txt" at the command line.  That will try to create a file on the iPod.  If that doesn't work, can you run the command "mount" (without any arguments) and copy/paste the output?

---

### Post by Iandefor on 2005-11-27
Ipods come formatted with the HFS filesystem. If you don't have the packages to access HFS, then you can't access your Ipod. If you don't have them, go to a terminal and type in```
 sudo aptitude install hfsplus hfsutils
``` My preferred Ipod manager of choice is [Yamipod.]("http://www.yamipod.com/main/modules/home/")

---

### Post by features on 2005-11-27
[QUOTE=Pedricko]Argh all the errors seem to be stating my ipod as un-writable... how do I format it?[/QUOTE]

I do seem to remember, when I first got my pod, that you have to format it (as FAT) on a windoze machine first.  Preferrably in iTunes.  I'm not sure whether that's still the case, but if you've got such a machine lying around being useless, then try that...

Mark

---

### Post by Pedricko on 2005-11-28
On my ipod the about section says:

Capacity 1.8GB
Available 1.4GB
Version 1.0 
S/N - Probabally for the best not to put that on
Model - MA099FB
Format - Windows


I've installed the HFS tools, and I tried the touch /mnt/ipod thing and it said it couldnt be done, and I dont know how to install the tar.gz file from yamipod?

Help?

(Is there any tools specifically for the nano? As it supports pictures, album art, notes (what format?), a calender and a contacts menu?

DAMN YOU WINDOW$!

---

### Post by Pedricko on 2005-11-28
Anyone? Sorry about the bump but I dont want to send this ipod nano back!

---

### Post by features on 2005-11-28
Can you please plug your ipod in and, in a terminal, type 
```
mount
``` and
```
ls -l /media/
```
and tell us what it says about your ipod.   lt should be something along the lines of 
```
/dev/sda1/ on /media/ipod/
```
and there should be an item in /media/ called ipod.  This is where Ubuntu puts your ipod by default, not /mnt/ipod.

In whatever pod program you use, go to the preferences and change where it looks for your iPod to where the mount command says it is.  For gtkPod, which is what I use, it's in Edit --> Preferences, at the top of the "General" tab.

If it can't be changed in the program you want to use, then you can change where your system mounts the ipod to suit the program.  Post back if you want to do this and I'll go through it step by step.  

The about info that you posted is telling me that the format is alrady FAT, though I may be wrong, which is why the mount command is handy.  If it is HFS, then you will need to install the hfsutils, as you have done, though I'm unsure of how well they work with the various pod utilities.

---

### Post by Brent Dax on 2005-11-28
> This is where Ubuntu puts your ipod by default, not /mnt/ipod.
You're right, of course; /mnt was a think-o.  Sorry.

Please, please, *please* run the "mount" command.  It can tell us a lot, like whether it was mounted read-only or not.

---

### Post by Pedricko on 2005-11-28
pedro@ubuntu:~$ mount
/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /boot type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/ipod type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
pedro@ubuntu:~$ ls -l /media/
total 12
lrwxrwxrwx  1 root  root     6 2005-11-20 17:30 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2005-11-20 17:30 cdrom0
lrwxrwxrwx  1 root  root     7 2005-11-20 17:30 floppy -> floppy0
drwxr-xr-x  2 root  root  4096 2005-11-20 17:30 floppy0
drwx------  6 pedro pedro 4096 1970-01-01 01:00 ipod
pedro@ubuntu:~$

and my ipod folder is in Media, ill check the settings in GTKpod which is so far the easiest looking program for me

[EDIT] My GTKPod uses /media/ipod too

[EDIT 2]

I add the Dir i want on my ipod in gtkpod, and when I hit sync I get this message:

You did not import an existing itunesDB ('media/ipod/ipod_control/iTunes/iTunesDB') this is most likley incorrect and will result in the loss of the existing database.

Press OK if you want to proceed now or cancel to skip storing if you cancel you can import the existing database before calling the function again.

I dont have an iTunesDB if I've never used iTunes

---

### Post by features on 2005-11-28
Cool.  Thanks for doing that, it makes it so much easier to see whats going on. 

I think everything looks OK there.  At least it's the same as my machine. ;)  so if you change gtkpod to look at /media/ipod instead of /mnt/ipod then you should be good to go! 8)

Mark

---

### Post by Pedricko on 2005-11-28
"'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted."

---

### Post by features on 2005-11-28
[QUOTE=Pedricko]"'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted."[/QUOTE]


Ahhh, forgot about that bit. :???:  I got around that by putting it on my Windows partition and letting iTunes look at it:  it creates the iTunesDB file which gtkpod can then work with.  You should only need to do it once.

You could also go to [this]("http://neuron.com/~jason/ipod_archive.html") page, where they have links to a sample DB. The theory is: copy the iTunesDB to your ipod then let gtkpod sort it out.  **Be warned though, that I have not tried this**, and if it "wrecks" the pod, you'll definitely have to reformat it on a windows machine. 

Hope this helps,

Mark

---

### Post by Pedricko on 2005-11-28
Please explain to me how to re-format and is it a tricky process

---

### Post by features on 2005-11-28
[QUOTE=Pedricko]Please explain to me how to re-format and is it a tricky process[/QUOTE]


Assuming you're doing it on a windows box:

1)Startup iTunes (install first from [www.apple.com/itunes]("http://www.apple.com/itunes") if you need to)
2)Plug iPod in to your computer.
3)A wizard will pop up.  You can name your pod etc.  Don't register it, unless you feel like it.  Same goes for filling it.  It may also suggest that there is new firmware available for it.  That's OK, update it.
4)If the wizard doesn't pop up then you can right click-->update (and options) on the ipod entry in the source list in iTunes.
5)Eject the iPod.  Done.

Not too scary, just involves too much Redmond (and possibly Cupertino) ;)

---

### Post by Pedricko on 2005-11-28
(hopefully) problem solved - a friend with another nano and windows is gunna drop a few tracks on mine in the effort that the iTunesDB will initialize on my pod allowing me to load it up myself.

---

### Post by clsman3585 on 2006-04-26
The problem I'm having is that my ipod nano won't even mount! The message I'm getting when trying to manually mount it is this "mount: can't find ipod in /etc/fstab or /etc/mtab". I am probably just an idiot so would someone please help me out.

---

