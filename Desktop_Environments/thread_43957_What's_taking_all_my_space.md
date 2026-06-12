---
title: "What's taking all my space?"
date: 2005-06-23
forum: Desktop Environments
---

### Post by Fuzzlet on 2005-06-23
Alright.. here's the deal. I have Ubuntu installed on an 18GB partition. Relatively fresh install (only a few days old). I installed UT2004 and a mod, so that's about 6GB there. I then tried HL2 via Cedega/WineX cvs. I copied the GCF's from my windows partition into the linux partition, and HL2 worked fine and all. But I decided it wasn't worth the HDD space and was going to leave it to playing on Windows. I deleted the GCF's, and emptied the trash (or so I thought). Yet, "df -T -h" still shows this...

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda7     ext3     18G   14G  3.4G  81% /
```

I can't figure where all that space is being taken up. The OS isn't really taking up 8GB's is it? That's even worse then windows if it really is. But I'm almost positive it isn't as before I copied those GCF's over, disk usage was WAY lower.

Any light on the matter for this Linux newbie would be greatly appreciated.

Oh, and sorry if this isn't the right place, I was totally sure where to post.

---

### Post by Skel on 2005-06-23
Well i am relativly new to ubuntu also but maybe with all the updates that you installed through apt-get might have filled more space than expect... not really sure how much space a basic install will take up...

Not sure if this is any help but... just my theory

---

### Post by Ptero-4 on 2005-06-23
[QUOTE=Fuzzlet]Alright.. here's the deal. I have Ubuntu installed on an 18GB partition. Relatively fresh install (only a few days old). I installed UT2004 and a mod, so that's about 6GB there. I then tried HL2 via Cedega/WineX cvs. I copied the GCF's from my windows partition into the linux partition, and HL2 worked fine and all. But I decided it wasn't worth the HDD space and was going to leave it to playing on Windows. I deleted the GCF's, and emptied the trash (or so I thought). Yet, "df -T -h" still shows this...

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda7     ext3     18G   14G  3.4G  81% /
```

I can't figure where all that space is being taken up. The OS isn't really taking up 8GB's is it? That's even worse then windows if it really is. But I'm almost positive it isn't as before I copied those GCF's over, disk usage was WAY lower.

Any light on the matter for this Linux newbie would be greatly appreciated.

Oh, and sorry if this isn't the right place, I was totally sure where to post.[/QUOTE]
 look in /var/cache/apt/archives. apt-get stores there the debs of each app you download using the apt-get command, dselect, aptitude or synaptic/kynaptic. Also look for the HL2 files, maybe winex/cedega stores cache copies of them somewhere.
Also do a du -h / | ~/SpaceCount.txt this will create a file called SpaceCount.txt in your home folder and put in it a list of all the files in your 18G partition along with their size in their respective units (kb, MB or GB). Open the file SpaceCount.txt in your text editor and you'll have a detailed report that wil show you which file(s) are eating up your drive's space.

Hope it helps.

---

### Post by cwaldbieser on 2005-06-24
You can use the the graphical find tools like kfind (KDE) to search for files above a certain size.  From the terminal:

```
$ cd <directory to test>
$ sudo du | sort -nr | head
```

This may take a bit, depending on how many levels of folders you have.  The idea is you change into a directory you want to test.  In your case, probably to wherever you have hda7 mounted.  Then you run the disk usage (du) command, sort the output numerically from greatest to smallest, and take the top 10 results.  This should help you narrow down the directories that have the biggest files.  The sudo isn't 100% necessary, except if you don't have permission to see what's in a folder, you can't add up the file sizes.

---

### Post by Fuzzlet on 2005-06-24
[QUOTE=Ptero-4]look in /var/cache/apt/archives. apt-get stores there the debs of each app you download using the apt-get command, dselect, aptitude or synaptic/kynaptic. Also look for the HL2 files, maybe winex/cedega stores cache copies of them somewhere.
Also do a du -h / | ~/SpaceCount.txt this will create a file called SpaceCount.txt in your home folder and put in it a list of all the files in your 18G partition along with their size in their respective units (kb, MB or GB). Open the file SpaceCount.txt in your text editor and you'll have a detailed report that wil show you which file(s) are eating up your drive's space.

Hope it helps.[/QUOTE]
 Ah. Figured it out.

/home/cory/.Trash never got cleared, so 5GB's of Steam content was sitting in there.

Thanks Ptero, your command (indirectly) led me to the answer. Thanks to everyone for the damn quick responses. Ubuntu is great so far!

---

### Post by Xian on 2005-06-24
The easiest way to research this is to install filelight and then run it as sudo. From the menu bar select FIle > Scan Directory to choose where you would like the program to work. It will then present you a graphical model of that path and show clearly where your space is being used, down to the exact folder. Just hover your mouse over the model and get precise reads on file space usage.

```
$ sudo apt-get install filelight
$ sudo filelight
```

---

### Post by Fuzzlet on 2005-06-24
I'll put that in my notes, thanks Xian.

---

