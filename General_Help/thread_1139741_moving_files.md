---
title: "moving files"
date: 2009-04-27
forum: General Help
---

### Post by CTolley on 2009-04-27
First I just have to say that I love Ubuntu.  I still have Windows 7 on my machine, but that's just for the rare occurance of software that's not Linux compatible.  All of you here have done a great job with making the OS and providing support for the Linux stupid like me.  I have come to this site just about daily to figure something out, but this problem is too general for a search to help with.

I have my buddies external hdd that took a crap.  It crashes Windows, but I'm able to recover many things through Ubuntu.  I had to force mount it, but it's all good now.  The problem that I'm having is the 'drag & drop' of files onto my ext. hdd is coming up with errors.  I'm sure the issue is all on the bad hdd, but I want to try to move files from the terminal just to make sure I tried all options.  'Drag & drop' does work, but I've only been able to retain about 85% of his pictures.  I'm greedy and want the rest.  Now, both of the hdd's are in the media folder, but I can't figure out how to access them through the terminal.  Meaning, I can find them by cd, but I can't write one line to get into it, and since I'm copying files, that's what I need.  '~/media' tells me that there is no such file or directory in 'blah-blah/home' folder.  Which is true.  

What is the code that I need to do this?

Is [copy "folder location/folder(or file)" "new folder location/folder"] the correct input? 

Thank you for your help.

-CTolley

---

### Post by _Purple_ on 2009-04-27
All your mounted partitions are in media folder
```
cd /media
```

The command to copy
```
cp "folder location/folder(or file)" "new folder location/folder"
```

---

### Post by CTolley on 2009-04-27
Now I feel retarded.  I was all happy that I remembered the '~' sign, but it did nothing for me.  

You are awesome Purple!  But that brings me the the next question... What is the '~' used for?

---

### Post by _Purple_ on 2009-04-27
'~' refers to your home directory.
```
cd ~
``` 

is same as

```
cd /home/your_username
```

So when you type, 
```
cd ~/media
```
it means
```
cd /home/your_username/media
```

---

### Post by CTolley on 2009-04-27
And it all makes sense now.  I love this place!  Many thanks Purple.



And in case you were wondering, the hdd is just too corrupt.  It was worth a shot though.

---

### Post by Grenage0 on 2009-04-27
A lot of the time it's worth using dd (or dd_rescue) to clone the drive onto a working one.  That's helped me get files back for more people than I can recall.

---

### Post by _Purple_ on 2009-04-27
> **CTolley said:**
> And it all makes sense now.  I love this place!  Many thanks Purple.



And in case you were wondering, the hdd is just too corrupt.  It was worth a shot though.

You can try TestDisk and see if you can recover the files, though I have not used it. 
To install 
```
sudo apt-get install testdisk
```

For more details:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by CTolley on 2009-04-27
> **Grenage0 said:**
> A lot of the time it's worth using dd (or dd_rescue) to clone the drive onto a working one.  That's helped me get files back for more people than I can recall.

Correct me if I'm wrong, but if I were to clone the hdd to another, the other would have to be of the same size or greater?  Or does dd_rescue give options for which files to clone?  

*Edit:  I only ask because he has a 1TB hdd, and mine is a lowly 250GB, with only 50G free...



I will give TestDisk a try as well and report my results.

---

### Post by perrti-y02 on 2009-04-27
dd essentially takes an entire volume and clones it. you can get it to output to a .iso file which might be handy because it simply acts as a normal file

dd if=/dev/hd5 of=/home/bob/harddrive.iso

will give you a .iso that is the same size as all the data on the drive (i.e if it is a 500GB hard drive but there is only 70GB of data on it the .iso will be about 70GB)

---

### Post by perrti-y02 on 2009-04-27
I didn't actually answer your question. As far as I know the new drive needs to be as large as all the data. I don't think you can choose what to clone because you are cloning a VOLUME not the files.

Feel free to correct me if I am talking total rubbish

---

### Post by CTolley on 2009-04-30
Sorry for my failings to reply.  I have been elated with the results of TestDisk.  dd_rescue looks to be a little deep for my skills, so out of fear of screwing everything up, I didn't try it.  If it was my hdd I would have tried, but it's not.  With TestDisk I was able to recover 10.1GB of 10.5.  That is a win in my book.  Now that that worked he will be buying a new hdd and we will transfer his videos.  TestDisk did take about 15 hours to move that 10.1GB on a USB connection though.  I don't know if the time matters to those that care, but there it is.  Also, it took limited resources.  I was still able to watch movies and surf the net while transfering files with no notible difference.

---

### Post by _Purple_ on 2009-04-30
Glad to know that you managed to recover most of the files :)

---

### Post by CTolley on 2009-05-01
Oh it's great.  Him and his wife were estatic, especially since most of the lost pictures were of their last base in Italy.  And, now that we have something that mostly works, he's going to purchase another hdd and we will attempt to recover everything.  Thank you much for the link Purple.

-Tolley

---

### Post by CTolley on 2009-05-03
How do I remove the files from my system now?  I can't delete from gdm because the file belongs to root.  rmdir works in Terminal, but it's a long process since I have to remove all of the files before I can remove folders...  Am I able to boot gdm as root?

---

### Post by _Purple_ on 2009-05-03
You can open GUI with root privilege 
```
gksu nautilus
```

Or you can remove from CLI

```
sudo rm -rf /path/to/directory 
```


Be careful while using these. If you type any thing wrong or click on the wrong file, it might cause damage beyond repair.

---

### Post by CTolley on 2009-05-03
I used nautilus since I have less worry about typing in the wrong name there.  But, it worked great.  This system is so easy once you learn the right things to type...

---

