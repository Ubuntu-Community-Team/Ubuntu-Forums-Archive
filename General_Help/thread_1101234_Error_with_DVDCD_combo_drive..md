---
title: "Error with DVD/CD combo drive."
date: 2009-03-20
forum: General Help
---

### Post by berrypievision on 2009-03-20
My drive is a DVD R/RW CD rewritable drive, and it runs CD's just fine, but it does not run DVDs at all.  I just get this message:

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I have no idea what is wrong, I have other issues with the computer, but I doubt they are related, as this seems like a software issue.  Can you guys help?

---

### Post by mb_webguy on 2009-03-20
What application are you using that you get that error?

---

### Post by berrypievision on 2009-03-20
No application, I just try to run the disk via a folder.  It reads the data, as it even says the name of the movie I am trying to run, yet it just spits out that maybe theres no data and that DBus thing.

---

### Post by mb_webguy on 2009-03-20
What happens when you try to navigate to the disc in the terminal (i.e. "cd /media/cd-rom" or whatever your drive is mounted as)?

---

### Post by berrypievision on 2009-03-20
Um, if I go into a terminal and put in media/cdrom0 it tells me its a directory.  How does that help?

---

### Post by mb_webguy on 2009-03-20
Did you use "**cd** /media/cdrom"?

---

### Post by berrypievision on 2009-03-20
Wait, I did run it in a terminal, and here's what I got:

tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ /media/dvdrom0
bash: /media/dvdrom0: No such file or directory
tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ sudo /media/cdrom0
[sudo] password for tyler: 
sudo: /media/cdrom0: command not found
tyler@tyler-desktop:~$ cd /media/cd-rom0
bash: cd: /media/cd-rom0: No such file or directory
tyler@tyler-desktop:~$ cd
tyler@tyler-desktop:~$ cd: media/cdrom0
bash: cd:: command not found
tyler@tyler-desktop:~$ cd media/cdrom0
bash: cd: media/cdrom0: No such file or directory
tyler@tyler-desktop:~$ run cd
bash: run: command not found
tyler@tyler-desktop:~$ cd
tyler@tyler-desktop:~$ media/cdrom0
bash: media/cdrom0: No such file or directory
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$  /media/cd-rom
bash: /media/cd-rom: No such file or directory
tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ run /media/cdrom0
bash: run: command not found
tyler@tyler-desktop:~$ cd /media/cdrom0
tyler@tyler-desktop:/media/cdrom0$ play
The program 'play' is currently not installed.  You can install it by typing:
sudo apt-get install sox
bash: play: command not found
tyler@tyler-desktop:/media/cdrom0$ gxine
bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/tyler/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvb.channels_conf points to a non-existent location /home/tyler/.xine/channels.conf
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item media.video4linux.video_device points to a non-existent location /dev/video0
warning: configuration item media.wintv_pvr.device points to a non-existent location /dev/video0
warning: configuration item decoder.external.real_codecs_path points to a non-existent location 
warning: configuration item decoder.external.win32_codecs_path points to a non-existent location /usr/lib/codecs
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.27-11-generic
  machine: i686
X-Video Extension version 2.2
video_out_xv: Xv image format: 0x32595559 (YUY2) packed
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
video_out_xv: Xv image format: 0x32315659 (YV12) planar
video_out_xv: Xv image format: 0x59565955 (UYVY) packed
video_out_xv: Xv image format: 0x30323449 (I420) planar

---

### Post by berrypievision on 2009-03-20
I'm assuming its some driver issue.  I hate when I run into those.

---

### Post by mb_webguy on 2009-03-20
> **berrypievision said:**
> Wait, I did run it in a terminal, and here's what I got:

tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ /media/dvdrom0
bash: /media/dvdrom0: No such file or directory
tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ sudo /media/cdrom0
[sudo] password for tyler: 
sudo: /media/cdrom0: command not found
tyler@tyler-desktop:~$ cd /media/cd-rom0
bash: cd: /media/cd-rom0: No such file or directory
tyler@tyler-desktop:~$ cd
tyler@tyler-desktop:~$ cd: media/cdrom0
bash: cd:: command not found
tyler@tyler-desktop:~$ cd media/cdrom0
bash: cd: media/cdrom0: No such file or directory
tyler@tyler-desktop:~$ run cd
bash: run: command not found
tyler@tyler-desktop:~$ cd
tyler@tyler-desktop:~$ media/cdrom0
bash: media/cdrom0: No such file or directory
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$  /media/cd-rom
bash: /media/cd-rom: No such file or directory
tyler@tyler-desktop:~$ /media/cdrom0
bash: /media/cdrom0: is a directory
tyler@tyler-desktop:~$ run /media/cdrom0
bash: run: command not found
**tyler@tyler-desktop:~$ cd /media/cdrom0**
tyler@tyler-desktop:/media/cdrom0$ play
The program 'play' is currently not installed.  You can install it by typing:
sudo apt-get install sox
bash: play: command not found
tyler@tyler-desktop:/media/cdrom0$ gxine
bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/tyler/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvb.channels_conf points to a non-existent location /home/tyler/.xine/channels.conf
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item media.video4linux.video_device points to a non-existent location /dev/video0
warning: configuration item media.wintv_pvr.device points to a non-existent location /dev/video0
warning: configuration item decoder.external.real_codecs_path points to a non-existent location 
warning: configuration item decoder.external.win32_codecs_path points to a non-existent location /usr/lib/codecs
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.27-11-generic
  machine: i686
X-Video Extension version 2.2
video_out_xv: Xv image format: 0x32595559 (YUY2) packed
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
video_out_xv: Xv image format: 0x32315659 (YV12) planar
video_out_xv: Xv image format: 0x59565955 (UYVY) packed
video_out_xv: Xv image format: 0x30323449 (I420) planar

That line I made bold is the first thing you typed that's actually a command, or anything close to what I asked you to type.  Typing random stuff into the terminal usually won't get you very far.  :)  It also worked, as you can tell from your shell prompt immediately afterward.  Please put a disc (preferably one that has something on it) into the drive and enter the following command in the exactly as I typed it.  You may want to copy and paste just to be sure.```
mount | grep cdrom
```
If that command gives you anything at all, then the disc is being mounted, which means that your drive is working at least that much, and you should try opening the disc with some other application, like VLC.

If you get some error message, post it here and we'll keep trying to figure out the problem.

---

### Post by berrypievision on 2009-03-20
When I try to play the disc in VLC, it just tells me the dbus message and tells me I cannot mount the dvd.

Typing mount | grep cdrom in the terminal with the media/cdrom0 doesn't do anything, sorry.

I think the issue is the DVDs just wont mount.  I have no idea why, but it keeps tell me it wont mount and adds a Dbus error message.

---

### Post by berrypievision on 2009-03-20
Here's what I get when I try to mount it from the terminal:

tyler@tyler-desktop:/media/cdrom0$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tyler/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tyler)
tyler@tyler-desktop:/media/cdrom0$ mount disk
mount: can't find disk in /etc/fstab or /etc/mtab
tyler@tyler-desktop:/media/cdrom0$

---

### Post by mb_webguy on 2009-03-20
Ok, after a bit of research, I found a [link]("http://ubuntuforums.org/showthread.php?t=779992") that might be helpful.  Start reading with post #3, and try what they suggest.  Make sure you type everything exactly as they type it.  Copy and paste is probably a good idea.

Unfortunately, I have to get some sleep.  If the above solution doesn't work, hopefully someone else will jump in and keep trying to help.  Otherwise, I'll be back in about 12 hours or so.

---

### Post by berrypievision on 2009-03-20
No worries, you guys have been a big help already.  Just glad you put up with my novice computer skills and major computer problems.

It says no medium found as well as not able to mount.  I guess the issue is its not reading the data on the disc, yet it still says the dvd title on the screen.  Weird.

Update:

I tried one of the things the thread said to do, it didn't help.  I'm pretty sure however, this is a software issue, as I tried loading up the LiveCDs of Ubuntu and Mandriva that I have, and they boot just fine.  So I wonder why Ubuntu is not mounting my DVDs...

---

### Post by mb_webguy on 2009-03-20
Well, then you could try reinstalling the software packages dealing with the disc drive.  Mark the following packages for reinstallation in Synaptic: libcdio7, libcdaudio1, libdbus-1-3, libdbus-glib-1-2, libhal1, hal.

---

### Post by mc4man on 2009-03-20
Why don't you just put a dvd in the drive, wait a moment and then copy and paste this into a terminal, press enter and post the output. It will under a *cdrom heading list your drive, the device node, dev links, mount point and if the media (your dvd) is mounted and if so, properly.

```
sudo lshw -C disk
```

If everything ck.'s out you can then see why no playback

---

### Post by berrypievision on 2009-03-21
When I do that sudo command, I get this:

  *-disk                  
       description: ATA Disk
       product: WDC WD1600JB-00F
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 15.0
       serial: WD-WMAES3021328
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=fa96fa96
  *-cdrom
       description: DVD writer
       product: DUW1616/ARR
       vendor: AOPEN
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1020
       serial: 5AOPEN   DUW1616/ARR     1020050719AOPAB0371040
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

---

### Post by berrypievision on 2009-03-21
Wow, interesting development.  It seems burned DVDs, such as my disktros of linux and other OS's, run just fine.  Only commercial dvds don't run!  Why the hell is that?!  Can someone help me out on that?

---

### Post by berrypievision on 2009-03-21
I did do some reading, and can the problem be I might lack the win32 codecs?  I read about them and I don't think I have them.

This is odd, my other Linux's run commercial dvds just fine.  Why is UBuntu crapping out on them?

---

### Post by mc4man on 2009-03-21
running this will ck. on libdvdread3 and install libdvdcss2, (should be all vlc needs), gstreamer players would also need some gstreamer-plugins, can be installed manually from synaptic or as an all in one by installing ubuntu-restricted-extras

```
 sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/install-css.sh

```

---

### Post by berrypievision on 2009-03-22
I've already installed libdvdread3 though.  It didn't help in the least.  I also have the restricted package installed.  Does nothing.

I've never had an OS be so resistant to something so specific before :)!

---

### Post by berrypievision on 2009-03-22
I'm guessing it's some codec or what not I'm lacking that is preventing commercial dvds from playing.  I'm not just talking films on DVD, I'm talking video games, and whatever that happens to be commercial and on a dvd.  I have read Win32 Codecs are needed, but I haven't the slightest clue what that is or how to get them, and that's about as much as I know.  Ubuntu sure is difficult...

---

### Post by berrypievision on 2009-03-24
Guess I've hit a crossroads again?  Does anyone know a place where they specialise in this sort of situation, where they could help me with this?

---

### Post by berrypievision on 2009-03-24
Strange, now I can play certain DVDs just fine.  Wow.  I'm still running into problems with some DVDs, like Quake 4 (it tells me I lack permission, which is odd, as I am the only user on this computer), but certain DVDs, like my Return of the Jedi one, run just fine.  Very weird.  Any idea why this is going on?

---

### Post by berrypievision on 2009-03-24
Well some commercial dvds run fine, like some of my Star Wars DVDs, run fine, but others, like my Quake 4 and Elf: Special Edition, do not run fine at all.  Do you guys know what could be causing this specific issue?  Thank you.

---

### Post by goathunter on 2009-04-11
Hi all. I am having a similar problem with my dvd writer in my acer laptop. Reads ubuntu boot cd's and audio cd's fine but won't read or detect anything else and won't burn at all, always giving input/output errors

sudo lshw -C disk gave me this 
> marcus@marcus-laptop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: ST960812A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.06
       serial: 5PJ1BW6R
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a315a315
  *-cdrom
       description: DVD writer
       product: DVDRW SOSW-833S
       vendor: Slimtype
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: VRS2
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: signature=0001f669
marcus@marcus-laptop:~$ 


Any help would be much appriciated. BTW I installed all the codecs mentioned above.

---

### Post by goathunter on 2009-04-11
bump

---

