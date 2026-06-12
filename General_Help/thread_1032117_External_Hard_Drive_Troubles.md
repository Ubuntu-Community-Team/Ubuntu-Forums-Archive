---
title: "External Hard Drive Troubles"
date: 2009-01-06
forum: General Help
---

### Post by fknyeah on 2009-01-06
So last night I was on my external hard drive getting some different Music to put onto my Laptop.  In doing do I noticed a couple albums that I wanted to place under folders for the artists that they belonged to, some of which I found to be duplicates.  I went to bed thinking that everything was okay.  But NO.  Now I go back to my Hard drive to watch a movie tonight and find that... WHAT??? I now only have 70 folders of music on it.  Before I had a couple hundred!

Is there a reasonable explanation for something stupid I could have done?

The hard drive seems to still be 3/4 full, yet there aren't nearly enough files showing for it to be as full as it says it is.  This leads me to think that the files might be easily recoverable.  How could I go about that?

Please ask me anything you need to!  I need help.  This is a Huge problem as I am an audio file and I NEED MY MUSIC!  I don't know what I'll do without it.

---

### Post by logos34 on 2009-01-06
sounds to me like the files are all still there, but somehow got moved inside of others.  Do a spot spot search and see if any show up where they shouldn't be.

---

### Post by fknyeah on 2009-01-06
either its not working or i'm not doing what you want me to do.
What exactly should I be doing, I've never had to deal with anything like this before.

---

### Post by logos34 on 2009-01-06
post output of 

df


If you run this: 

sudo du -h --max-depth=1 /media/yourmusic

and any of your album folders look abnormally large, that might be an indication of misplaced files inside

---

### Post by fknyeah on 2009-01-06
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            152051968  48207572  96181396  34% /
tmpfs                   516056         0    516056   0% /lib/init/rw
varrun                  516056       220    515836   1% /var/run
varlock                 516056         0    516056   0% /var/lock
udev                    516056      2808    513248   1% /dev
tmpfs                   516056       104    515952   1% /dev/shm
lrm                     516056      2004    514052   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1            488384000 376235336 112148664  78% /media/Big Bertha

---

### Post by fknyeah on 2009-01-06
Big Bertha is the name of the Ext HDD

this is what I got after typing the other line
du: cannot access `/media/BigBertha': No such file or directory

---

### Post by logos34 on 2009-01-06
It's two words (space).

try

/media/"Big Bertha"

or 

/media/Big\ Bertha
(forward slash+SPACE+TAB)

---

### Post by loboc on 2009-01-06
You are an audiophile and a poor speller.

---

### Post by fknyeah on 2009-01-06
thanks loboc, you've made a great point. I made mistakes, I'm fine with that. I am indeed human.
Moving on...
here is the output:
> sam@honus-wagner:~$ sudo du -h --max-depth=1 /media/"Big Bertha"
71G	/media/Big Bertha/Movies
du: cannot access `/media/Big Bertha/Music/Antics In The Forbidden Zone': Input/output error
sam@honus-wagner:~$ sudo du -h --max-depth=1 /media/"Big Bertha"
[sudo] password for sam: 
du: cannot access `/media/Big Bertha': No such file or directory
sam@honus-wagner:~$ sudo du -h --max-depth=1 /media/Big\ Bertha
du: cannot access `/media/Big Bertha': No such file or directory
du: cannot access `/media/Big Bertha/Music/lcd sound system': Input/output error
du: cannot access `/media/Big Bertha/Music/LCD Sound System - sound of silver': Input/output error
du: cannot access `/media/Big Bertha/Music/Lee \'\'Scratch\'\' Perry & The Upsetters - Roast Fish Collie Weed & Corn Bread': Input/output error
du: cannot access `/media/Big Bertha/Music/lee hazelwood': Input/output error
du: cannot access `/media/Big Bertha/Music/Lee _Scratch_ Perry': Input/output error
du: cannot access `/media/Big Bertha/Music/Lee _Scratch_ Perry & The Upsetters': Input/output error
du: cannot access `/media/Big Bertha/Music/levon helm - dirt farmer': Input/output error
du: cannot access `/media/Big Bertha/Music/London Calling The Vanilla Tapes': Input/output error
du: cannot access `/media/Big Bertha/Music/Lou Reed-Berlin(Remastered)(Darkside_RG)': Input/output error
du: cannot access `/media/Big Bertha/Music/Louder Than Bombs': Input/output error
du: cannot access `/media/Big Bertha/Music/Licensed To Ill': Input/output error
du: cannot access `/media/Big Bertha/Music/Mad Professor & Lee Perry': Input/output error
du: cannot access `/media/Big Bertha/Music/Madness - Complete Madness [MP3@320kbps][Original Recording Remastered] 2003': Input/output error
du: cannot access `/media/Big Bertha/Music/Mastodon - Blood Mountain': Input/output error
du: cannot access `/media/Big Bertha/Music/Meddle': Input/output error
du: cannot access `/media/Big Bertha/Music/Medeski Martin & Wood': Input/output error
du: cannot access `/media/Big Bertha/Music/Mezzanine': Input/output error
du: cannot access `/media/Big Bertha/Music/MF Doom and Madlib': Input/output error
du: cannot access `/media/Big Bertha/Music/MGMT': Input/output error
du: cannot access `/media/Big Bertha/Music/Mgmt': Input/output error
du: cannot access `/media/Big Bertha/Music/Modern Lovers-Modern Lovers-1976': Input/output error
du: cannot access `/media/Big Bertha/Music/Modest Mouse - We Were Dead Before The Ship Even Sank [2007]': Input/output error
du: cannot access `/media/Big Bertha/Music/Moe.-The_Conch-2007-SAW': Input/output error
du: cannot access `/media/Big Bertha/Music/Moe_': Input/output error
du: cannot access `/media/Big Bertha/Music/mondo generator - a drug problem that never existed': Input/output error
du: cannot access `/media/Big Bertha/Music/Moon Pix': Input/output error
du: cannot access `/media/Big Bertha/Music/Motorhead - The Best Of Motorhead 2 Cds 2000 320Kbps Demons Eye': Input/output error
du: cannot access `/media/Big Bertha/Music/Movies': Input/output error
du: cannot access `/media/Big Bertha/Music/MTV Party To Go Platinum Mix': Input/output error
du: cannot access `/media/Big Bertha/Music/muddy waters - fathers and sons': Input/output error
du: cannot access `/media/Big Bertha/Music/The Smiths - Hatful of Hollow': Input/output error
du: cannot access `/media/Big Bertha/Music/The Smiths - The Queen is Dead': Input/output error
du: cannot access `/media/Big Bertha/Music/untitled folder': Input/output error
du: cannot access `/media/Big Bertha/Music/untitled folder 2': Input/output error
du: cannot access `/media/Big Bertha/Music/untitled folder 3': Input/output error
du: cannot access `/media/Big Bertha/Music/untitled folder 4': Input/output error
du: cannot access `/media/Big Bertha/Music/untitled folder 5': Input/output error
du: cannot access `/media/Big Bertha/Music/untitled folder 6': Input/output error
260G	/media/Big Bertha/Music
1.8M	/media/Big Bertha/Other
4.0K	/media/Big Bertha/RECYCLER
491K	/media/Big Bertha/System Volume Information
25G	/media/Big Bertha/TV
355G	/media/Big Bertha
sam@honus-wagner:~$ sam@honus-wagner:~$ sudo du -h --max-depth=1 /media/"Big Bertha"
bash: sam@honus-wagner:~$: command not found
sam@honus-wagner:~$ [sudo] password for sam: 
bash: [sudo]: command not found
sam@honus-wagner:~$ du: cannot access `/media/Big Bertha': No such file or directory
> sam@honus-wagner:~$ sudo du -h --max-depth=1 /media/Big\ Bertha
> du: cannot access `/media/Big Bertha': No such file or directory
> 


---

### Post by skizeee on 2009-01-09
Im having a similar if identical problem...

My external HDD was lent to a friend with about 287gigs of music. I got it back bang! nothing there my Macbook when you click on the music folder just does nothhing when the drive is plugged into my eeepc with 8.10 the folders have locks on them and the contents looks corrupted or jumbled up....

Im a noob to and this stumps me... it was fine before...

---

### Post by Growbag on 2009-01-09
You haven't said what filesystem is on the disk, but by the folder structure I'm guessing it's NTFS.

Did you move the files and folders while using Windows or while using Linux?

It could have been caused by not unmounting the drive properly before unplugging it.  Whenever you use an external drive, **ALWAYS ALWAYS** unmount/eject/safely remove the device before pulling the USB cable out!

Then wait another few seconds before removing too just to be extra safe!

I know that doesn't help you in this case, and I am sad for you in that respect, but it is good advice for the future.

If it is an NTFS volume, you might want to mount it on a Windows system and either check the disk there, or find a good recovery programme and start work on it.

You might even find that the standard Windows disk check will fix it up, but don't hold your breath ;).

If you have enough disk space available on another drive, you could make a clone copy of the USB disk for safety before working on it.  It will copy the entire disk "as is" so that you can restore it (to it's current faulty state) if you make a mistake and lose everything.

I wish you luck :).

---

### Post by skizeee on 2009-01-09
Thanks heaps for your reply but the drive has always been exclusively Mac format theres no windows machines in this house.

but are you saying that a recovery of somekind might help?

---

### Post by skizeee on 2009-01-09
Sorry correction the mac says it is in MS-DOS FAT-32 format the MAC cant do anyting for the disk but if I plugged it into my Ubuntu 8.10 machine is there something I could do?

---

### Post by bullium on 2009-01-09
Try this instead:

sudo du -h --max-depth=1 /media/Big\ Bertha

The backslash \ after Big is an escape character in linux. Basically tells the system how to deal with the space between "Big" and "Bertha".

---

### Post by fknyeah on 2009-01-10
Now it won't even mount.

---

### Post by fknyeah on 2009-01-17
I'm getting this message:

$LogFile indicates unclean shutdown (0,0) Failed to mount '/ dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose on action:
Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.
Choice 2: If you don't have Winows then you can use 'force' option for your own responsibility.  For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/Big Bertha-o force
Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1/media/Big Bertha ntfs-3g force 0 0

I'm not sure what I should do.  What is the safest option?

---

### Post by lavinog on 2009-01-17
> **fknyeah said:**
> I'm getting this message:

I'm not sure what I should do.  What is the safest option?

Your best bet is to connect it to a windows computer, and unmount it.
if you have the time you should run checkdisk from windows on it.

---

### Post by fknyeah on 2009-01-18
how can i force the hard drive to mount?

---

### Post by jdogg5293 on 2009-01-18
im sorry im a newb but how do you start a new thread

---

