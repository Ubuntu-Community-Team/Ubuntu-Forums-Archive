---
title: "Two machines running Ubuntu; how can I keep an intersection of data in sync?"
date: 2011-04-20
forum: Desktop Environments
---

### Post by randizzle on 2011-04-20
I have two computers running Ubuntu; a desktop which is my primary work machine and a laptop which I use when mobile for both work and school (note: the primary drive in laptop exceeds the storage capacity of the primary drive in the desktop by a small factor)

What would be ideal is if I could reasonably assume that at any moment any change to user data on my desktop would be present on laptop. I realize this is might be a bit of a fantasy but I wonder how close I can get.

I can think of a couple ways to hack together some scripts to somewhat approximate this but I cannot be the first person to want this behavior.

Can anyone suggest any software or have any other advice?

---

### Post by Copper Bezel on 2011-04-20
Well, Ubuntu One is designed to do exactly what you want, via selective syncing, and could be configured to apply to both documents or data and your settings. I just use Dropbox, personally, as it's more versatile and dependable for syncing data (esp. with a Windows machine,as I have to do for work) but it does require you to keep everything in the Dropbox folder. (Interestingly, though, if you use a symbolic link to a file on one end, the real file will appear on the other, so you could reasonably put links to your major folders on the hone machine in the home machine's Dropbox, and the directories in full would appear in the laptop's Dropbox.)

---

### Post by oldfred on 2011-04-20
I only use laptop when we travel, but I copy Firefox & Thunderbird profiles plus some data. I originally had XP on laptop & dual boot on Desktop. But every update to XP, firewall and some changes in Ubuntu often broke my Samba, so I converted laptop to Ubuntu and started using NFS. I am in the process of converting to SSH which I think is even easier. I then have one rsync bash file on each system to update files.

The issues I have are making sure the files copy ok. As I sometime move a file from one folder to another but then the next update copies it back as it still is in the old location on the other machine. Then which is the newer copy issues.

---

### Post by IanWood on 2011-04-20
You can use xmarks  [http://www.xmarks.com/](http://www.xmarks.com/) for your browser too.

I also use Dropbox and think its great.

---

### Post by Copper Bezel on 2011-04-20
Dropbox, Ubuntu One, or another equivalent will actually fix that. I haven't played with U1, but Dropbox is very good at always keeping the most recent edit. 

Here's a method for Dropbox. It's crazy that this works, but it seems to do so, so check it out:

1. Create a .config folder in your Dropbox and move the configuration folders of any applications you'd like to sync into that directory. That is, move the config files on one machine and delete them on the other.

2. Put symlinks in their place on both machines that point back to the location of the appropriate config directory in your Dropbox folder. 

3. Profit.

Edit: Then again, the config files for a browser, including history and such, would be a huge amount of data to sync (regardless of the method.)

---

### Post by Mike V on 2011-04-20
I have a laptop only, but I boot Maverick/Natty/Arch/Fedora/openSUSE, I carry around my Firefox/Thunderbird/Chromium profiles as well as the Documents/Downloads folder and the Banshee/GNUPG configurations databases... so I have a small sync_up/sync_down script that uses rsync to upload/download the contents to my FreeNAS server.

That could be an option between your two computers:

rsync -vurtzpEogh4 --progress $SOURCE_FOLDER $DESTINATION_FOLDER

you can add a --delete option to remove everything on the destination that is not present in the source.

---

### Post by randizzle on 2011-04-22
> **Copper Bezel said:**
> 
...
1. Create a .config folder in your Dropbox and move the configuration folders of any applications you'd like to sync into that directory. That is, move the config files on one machine and delete them on the other.

2. Put symlinks in their place on both machines that point back to the location of the appropriate config directory in your Dropbox folder. 

3. Profit.
...



This is really awesome.. exactly what I was looking for. You are the man. Thank you.

---

### Post by Copper Bezel on 2011-04-22
No problem! Just go ahead and mark the thread as Solved, if you would (Thread Tools in the upper right) so the next person Googling for this solution can find it. = )

---

