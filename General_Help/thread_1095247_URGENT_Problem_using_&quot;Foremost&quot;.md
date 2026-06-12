---
title: "URGENT: Problem using &quot;Foremost&quot;"
date: 2009-03-13
forum: General Help
---

### Post by chrini on 2009-03-13
I am in desperate need of help!!! 

I recently ran Foremost to recover some lost files and I mistakingly ran exactly what I found on a site without doing much research. This is what I ran:

```
sudo foremost -t jpeg -i /dev/sda1

```

Once it was done I had only 48 MB of disk space left out of an initial 1.7 GB of free space (note: I am running Ubuntu 8.10 on a VM with only 4 GB of freespace). So I know it found quite a few files... however, I cannot (FOR THE LIFE OF ME) find where the "output" folder was created. 

It is said that it is created in the folder of which Foremost is ran (can't find that either)... I did a disk analysis and can't seem to figure out where the ~1.7GB of files is located.

Any know where the default location of the "output" folder is located? 

Any help is MUCH appreciated!

-Nick

P.S. After some research I found very few sites that said to "make sure the output folder exists prior to running foremost." Does that mean I'm screwed?

---

### Post by chrini on 2009-03-13
Nevermind!!! I found it!

For those of you who run into this same problem:

If no specific location is specified when running the command, your output folder is (at least mine was) placed in your /Home folder. I knew this, but when I initially opened the folder there was not data... this is because I did not "own" the folder. 

Do a chown on the folder (and sub-folders) and your problem will be fixed.

---

### Post by masil on 2009-03-25
I have exactly the same problem: I ran Foremost and filled up my hard drive.

In my case the output file created by Foremost showed up in the home\username folder (without my having changed its ownership or permission rights), which I deleted because it showed up as having no content. The output folder is not in the trash or anywhere else that I can find.

My hard drive, however, is still full.

As suggested by chrini below, I tried the command

sudo chown -R username home

to change the ownership of the \home folder, including subfolders, but I get this:

chown: cannot access `home/username/.gvfs': Permission denied

---

