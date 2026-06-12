---
title: "Understanding the folder directory system?"
date: 2007-05-30
forum: Desktop Environments
---

### Post by Genecks on 2007-05-30
I'm using Kubuntu Feisty, and I don't understand it's file-tree system. Could someone give some webpage describing what each folder is about? I see things such as usr, root, mnt, media, etc. and I don't fully understand what they are about.

---

### Post by eentonig on 2007-05-30
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html)

The best I could google in 10"

---

### Post by Genecks on 2007-05-30
Ok, so where should I save stuff, such as downloads, newly created documents, newly created images, etc.? Should I save stuff in the /home folder? Perhaps create a folder within the /home folder? That's what I somewhat already did, but I created a folder called "storage" under the username within /home.

---

### Post by eentonig on 2007-05-30
Consider the "/home/<yourname>" as the equivalent of 'My Documents' in Windows.

So yes, you should place all of your docs somwhere in there.

What I usually do after a fresh install is opening a terminal and type the following. (You can copy and paste the code as well if you like it.


> # Make sure I'm in my home folder
cd ~
# Create a whole bunch of default folders
mkdir Music   # to keep my music
mkdir Movies  #To store my movies
mkdir Documents # To store general docs
mkdir iso  # To store iso files i might want to burn
mkdir apps_temp # where I download applications that don't install through Synaptic
mkdir scripts  # to keep my own written scripts
mkdir bin  # where I install personal progs I don't want the family to use
mkdir ~/Movies/series  # creates a seperate folder for series under my movies
mkdir ~/Movies/screen # Blockbusters
mkdir ~/Movies/tv  # recorded from tv



And so on.

Also, I create some links as well, because a lot of stuff I only keep on an external HD with lots of Gigs. So under those folders, I usually have a link to an equivalent folder on my external HD. This way, I don't have to browse for it seperatly. And more important. In Amarok and progs like that, I only need to specify one directory to monitor for changes. If I add a file to any of my external folders, Amarok will find it and automatically add it to ie. my music library.

---

### Post by reckless2k2 on 2007-05-30
Did and or how did you do this in windows? It would be similar in the respect that "home" is "my documents" as the other post suggested. The link that was provided was very detailed and explanatory about what each directory is and what it's used for. If you navigate to the root of C:\ on a windows computer, you will find a similar structure or directory tree.

---

### Post by Genecks on 2007-05-30
I'm kinda old school. Lately, I've been putting stuff on C:
If given the chance (i'd probably be wrong, though), I would put stuff inside of the root folder. I don't know if that's a good idea in Linux.

---

### Post by reckless2k2 on 2007-05-30
Wel, if you are logged in as a normal user in ubuntu, you won't be able to save to the /root folder. if you mean "/" as the root folder then that wouldn't be correct either. All of your normal settings will be saved in your home folder but will be hidden to you unless you unhide them. My point is that you should then be saving your files here as well such as documents and or downloads of any kind. You can create folders/directories in your /home folder similar to windows if you like such as music, videos, documents, etc.. You get the point. Anything that you download for an install can be downloaded there as well. You'll have to escalate your privileges using sudo to install anyway so they will then be saved into the right directories. 

Quick and Dirty:

/home/yourusername = my documents - save everything here especially for central backup
/usr/local = program files - you don't touch this really unless you install something new but the install touches it really and not you. 

/tmp - this can be used to save temporary files. not really needed in your case though.

---

### Post by FuturePilot on 2007-05-30
You really shouldn't be putting anything in the "/" root directory. In fact, you really don't need to be messing around in there unless you know what your doing. Best/safest thing to do is just use your home directory and create sub directories to say organized.

---

