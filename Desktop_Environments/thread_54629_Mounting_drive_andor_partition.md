---
title: "Mounting drive and/or partition"
date: 2005-08-05
forum: Desktop Environments
---

### Post by bim54 on 2005-08-05
I know this has been posted, but in multiple places making it difficult to sort out.
I have a fresh install of Kubuntu on a dual boot with XP.  The Primary Drive is partitioned with XP and Linux.
I have a second drive that I want to be able to read/write to and I have it formatted to  fat32. These are the instructions I've followed up to the part of editing the fstab, 

I've followed these directions in being able to mount the drive when I'm logged in, but I want to it to mount at boot up.
The problem I'm having is editing the fstab because it's read only.  Can someone please give me a step by step instruction on doing that?  Like I said, I'm not understanding what I've read so far because it's bits and pieces from multiple posts.
Thank you.

Other issue.
Sometimes (quite a lot) when I go to use "Kuser" from the System menu, it doesn't open.  It just "thinks" and then nothing.  Is there a problem with that or am I doing something else wrong.
Again, this is a clean install of Kubuntu at this stage with no modifications to anything other than running the updates in Kynaptic and installing Firefox.

---

### Post by daller on 2005-08-05
If its a cleaninstall of Kubuntu, the partition is probably already mounted...

Use "sudo vi /etc/fstab" to edit fstab!

---

### Post by bim54 on 2005-08-05
I want the drive contents to come up when I boot.  I don't want to have to do this:

[B]Q: How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows

   4. To mount Windows partition

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

   5. To unmount Windows partition

sudo umount /media/windows/

[/B]
Every time I boot into Kubuntu

Regarding the editing of the fstab using  "sudo vi /etc/fstab" to edit fstab!"

It opens up, but how do you edit fstab once it's open?  When I move the cursor to the end of the text, it stops at the ~ and I can't add another line.
I am not use to using some of these txt editors in Linux.  This is the line I'm trying to add to the end of the fstab.

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by JLTB on 2005-08-06
Hi,

VI is a text editor (he used it in the command 'sudo vi fstab').  VI is pretty tricky to learn (no flames please ....) it took me at least a few months to get really efficient with it.

Basically to get your job done ... edit the file as daller described then press 'i' or INSERT to go into insert mode.  Then change whatever you need to.  Finally press ESC to go back into command entering mode, and type ':wq' (no quotes please!) to write the file and quit (you're probably seeing how this is cryptic but does make some sense by now).

That should get you along in VI for now.  Try using nano or pico if you want a simple text editor.  There are some good VI tutorials and manuals online ... google should get you there (this post has a few decades of redundant FAQ in it already ;-))

GL

---

### Post by lukem on 2005-08-06
brim54

VI is a great editor, but it does require some learning time.  You might also want to try the editor "gedit".  It works well and also has a bit more of the "look and feel" of editors you may be familiar with.  Just try:

sudo gedit /etc/fstab

Preceeding the command with sudo will allow it to be opened as root (so you can edit and save it).  When you use sudo this way it will ask for your password (your regular password).  The cursor will not move as you enter the password so don't be alarmed at this, just hit enter when you finish.

Good luck
luke

---

### Post by Copter on 2005-08-06
hi!

i agree that vi is kinda tricky and imo quite hard to begin with. gedit is gnome editor. assuming that you are using KDE (thread in kde section) i would recomend kate in graphic interface and nano in terminal.

good luck!
copter :]

---

### Post by bim54 on 2005-08-07
This is solved.  Took me a while to figure this out but playing and crashing and playing and etc....., but I got the other drive to mount on boot up and visible.
Thanks to ALL for their help on this.  If you ONLY knew just HOW green I am at Linux in general, you'd be buying me a beer.  :)

On a side note.... when I was checking out the screen savers and seeing that the OpenGL ones ran like a drunk dog, I was just about to toss in the towel on this all together.  I followed the instructions regarding this and got the correct driver up and running along with putting the NVIDIA settings in the Menu>System.

I did manage to stumble through it using vi

Again... thanks all...  \\:D/

---

