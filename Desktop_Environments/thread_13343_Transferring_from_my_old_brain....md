---
title: "Transferring from my old brain..."
date: 2005-01-30
forum: Desktop Environments
---

### Post by paulo on 2005-01-30
:confused: I have just converted to linux and have switched to Ubuntu from running a 2003 version of SOT linux. I have installed linux on a 2nd hard drive and am keeping windows XP on the old one. One problem I am having with Ubuntu is that, unlike SOT is does not automatically paste a link to my 'c' drive on the desktop - the XP drive with all my files on- and I cannot figure out how to do this through the file tree. Thus I cant get at any of my files from my old brain (music, fotos, wurk etc). How can I do this? 
Help would be much appreciated. Until then I shall re-trawl the manuals....
Other than this, I am really happy with Ubuntu and glad to have escaped from the evil clutches of borg king Bill Gates. 
Ta,
Paulo xxxxx

---

### Post by valadil on 2005-01-30
Check if you have a windows folder in /mnt or /media.  I thought ubuntu made those automatically, but I could be mistaken.  

If it does have a windows folder you can skip to the part about making symlinks.  If not, continue reading.

You'll have to edit /etc/fstab.  This is a list of filesystems, the hard drives they appear on, and where you want to mount them.  Theres a good chance your first harddrive is /dev/hda and that windows is on the first parition of it, so we're going to tell fstab to put that on a folder designated for your windows data.  Add the following line to /etc/fstab:
/dev/hda1  /mnt/windows  auto  defaults  0  0
However we don't have a windows folder yet for your drive to get mounted to, so cd into /mnt and run 'mkdir windows'

When you reboot the computer you should have your windows drive mounted on /mnt/windows.

To create a link to it, open up a terminal and cd into Desktop.  Then type the following:
ln -s /mnt/windows .
Naturally if ubuntu already gave you a windows mount in /media you'll use that instead of /mnt.

---

### Post by paulo on 2005-01-31
:confused: Thanks! 

I tried that. 

There was no precreated windows mount, so I made one. I did however have a problem with editing fstab - I am fairly new to using a command line terminal  (2 days) and can navigate and read stuff but am still fairly in the dark about how it works. I got to /etc and the typed : less fstab
to read it. I tried typing in what you reccomend: /dev/hda1 /mnt/windows auto defaults 0 0
and it says "pattern not found".
If i try "edit fstab" from /etc I get told that is not possible.
Here is the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Help!! :oops: 

 Also, what is a good way to start learning more about using command lines? The help topics in Gnome are useless - is there anything online, like a "command dictionary" with a list of the different commands to use in the terminal and what they do.
Thanks for your help. Really appreciated.
PAulo xxxxxx

---

### Post by JoWilly on 2005-01-31
[QUOTE=paulo]
If i try "edit fstab" from /etc I get told that is not possible.
[/QUOTE]

gedit /etc/fstab

(sudo gedit /etc/fstab is better than opening a root terminal)

---

### Post by jan on 2005-01-31
Get rid of Microsoft, its good for nothing.

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=paulo]:confused: I have just converted to linux and have switched to Ubuntu from running a 2003 version of SOT linux. I have installed linux on a 2nd hard drive and am keeping windows XP on the old one. One problem I am having with Ubuntu is that, unlike SOT is does not automatically paste a link to my 'c' drive on the desktop - the XP drive with all my files on- and I cannot figure out how to do this through the file tree. Thus I cant get at any of my files from my old brain (music, fotos, wurk etc). How can I do this? 
Help would be much appreciated. Until then I shall re-trawl the manuals....
Other than this, I am really happy with Ubuntu and glad to have escaped from the evil clutches of borg king Bill Gates. 
Ta,
Paulo xxxxx[/QUOTE]

The real fstab is here:

 /dev/hda1       /media/windows    ntfs    umask=0222      0       0

got it from:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by valadil on 2005-01-31
I believe you're looking for a command called man.  It's short for manual.  man command will give you info on the particular command.  man -k command will search man's database for the particular command you are looking for.  Sometimes commands are not well named so you need to search for edit text to find out that nano is a text editor.

less is a program that displays a text file but does not let you edit it.  nano is a good commandline text editor.  gedit is decent if you want a window of some sort to pop up.

The line for your fstab file that poofyhairguy gave you will work provided you use ntfs.  If you're on fat32 you need to change the ntfs to vfat.  Or you can just use auto like I suggested earlier.  Autio tries to detect the filesystem and use whatever it sees.  It hasn't failed me yet.

---

### Post by paulo on 2005-01-31
Thanks folks.
 Jan: I agree - I would like to get rid of microsoft, but I want to transfer my old files across  first mmmkay?

I used gedit and I now have a windows directory mounted and the shortcut on my desktop, but all the icons in it display as gnome footprints that will not open (and dissapear if I right click them) rather than directories (which they are). Help.

Valadil, I am on a FAT 32 filesystem, but I shall try poofyhairguy's line using auto, which seems like the best idea. 

Thanks again,

Paulo  :-(

---

### Post by kafton on 2005-01-31
Also, what is a good way to start learning more about using command lines? The help topics in Gnome are useless - is there anything online, like a "command dictionary" with a list of the different commands to use in the terminal and what they do.

You might look at [LinuxCommand.org](http://www.linuxcommand.org/)

---

### Post by JoWilly on 2005-01-31
[QUOTE=kafton]Also, what is a good way to start learning more about using command lines? The help topics in Gnome are useless - is there anything online, like a "command dictionary" with a list of the different commands to use in the terminal and what they do.

You might look at [LinuxCommand.org](http://www.linuxcommand.org/)[/QUOTE]

Yes, and after this you might also want to look at [linuxdoc.com](http://linuxdoc.com) and [The Linux Documentation Project](http://www.tldp.org).

---

### Post by paulo on 2005-02-01
:D Firstly, thanks again for all your help babysitting the newbie. 
I shall get into the sites you mention and learn this stuff.

 :confused: However, I REALLY need to get access to my windows files from Linux and still cant get it working. I have edited the Fstab, and I now have a windows folder in mnt and have mounted my windows drive to it. When I open this folder all the files are there - I recognise the names - but they all have the same icon (a footprint) and register 0 bytes. They do not open when left clicked and dissapear if right clicked. 

So I have reached the drive, but not the files. Any ideas?
Thanks,
Paulo 8-[

---

### Post by valadil on 2005-02-01
I've never seen anything like that.  Have you tried playing with the files from the commandline?  cd into /mnt/windows and try stuff like ls -lh and cat some text files.

---

### Post by paulo on 2005-02-01
When I try to cd into windows this is what i get:

bash: cd: windows: Permission denied

Then I try with sudo. This happens:

paulo@Themothership:/mnt $ cd windows
bash: cd: windows: Permission denied
paulo@Themothership:/mnt $
paulo@Themothership:/mnt $
paulo@Themothership:/mnt $ sudo cd windows
Password:
sudo: cd: command not found
paulo@Themothership:/mnt $

Arg!!

---

### Post by valadil on 2005-02-01
Try doing sudo su, this will turn you into root.  Then cd into /mnt/windows.

---

### Post by paulo on 2005-02-01
Okay. Sudo su gets me into windows. To this:

1.pfk                      exe.bat                       temp
1word.pfk                  herc.bgi                      Thumbs.db
AdobeWeb.log               hiberfil.sys                  tmp
arc2zip.exe                io.sys                        unzipped
audio                      jfc.exe                       user.dat
AUDIO INSTALLATION  FILES  msdos.sys                     winboot.ini
autoexec.bat               My Music                      win.ini
bat.bat                    nightingale pro 6             wininst0.400
bitsNpieces                ntdetect.com                  winxp
bl                         ntldr                         WUTemp
bluebyte                   opera                         x1.zip
boot.ini                   pagefile.sys                  z.cfg
bootsect.dos               pkunzip.exe                   zedit.txt
Bwgen                      pkzip.exe                     z.exe
cdrwin3                    Program Files                 zexec.hst
C-Media                    readme.doc                    zfile.hst
collport                   Recycled                      zlist.hst
com.bat                    RobotError.log                zmac1.cfg
command.com                setuplog.txt                  zmac2.cfg
config.sys                 Shortcut to My Documents.lnk  zmisc.hst
Converted Music            system bits                   ztabs.ini
Dell                       system.dat                    zx.exe
Documents and Settings     system.ini
egavga.bgi                 System Volume Information

These are my windows HD files.
Some are blue (directories?) some are green (files?).
Then this happens when I try to get into a directory:

root@Themothership:/mnt/windows # cd Documents and Settings
bash: cd: Documents: No such file or directory
root@Themothership:/mnt/windows #

I can get into a couple of the directories, such as opera and recycled files, but when I 'less' any files, there is nothing in them, or a couple lines of nonsense and squiggles. I cant get into 'Documents and Settings' or 'My Music' at all, and these are the ones I really need.

Thoughts?

PS, this is what is in my fstab at the moment:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows auto unmask=0222 0 0
/dev/hda1 /mnt/windows auto defaults 0 0
fstab (END)

The last 2 lines I have added. I have tried various different lines; all those that have been recommended to me by you all, and this is the one that at least gets me the mounted files that dont open, rather than just an empty file.

Thanks,
Paulo

PS, when I sudo gedit fstab, I get the following:

(gedit:9035): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

The gedit still works and I can write to fstab.

Does this mean anything?

---

### Post by paulo on 2005-02-01
YeeeeeeHAH!

Cracked it.
Windows directory now working fine. I think I figured out the problem: I was putting single spaces in between the parts of the commands, not hitting the TAB key. When I did this and restarted, it worked.

fstab now looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/windows    auto    umask=0222      0       0

Many thanks to y`all who posted, particularly Valadil. 
Now I can get on with learning my command lines whilest listening to some decent tunes.

Thanks very much, :D 
Paulo

---

