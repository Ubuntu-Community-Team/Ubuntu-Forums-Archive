---
title: "Would like help moving data from SuSe box to Ubuntu box via home network"
date: 2005-02-09
forum: Desktop Environments
---

### Post by zaba on 2005-02-09
Greetings,

Please forgive me if I am not going about this the right way. This is my first time posting to the Ubuntu forums, and am mindful of the community... If I'm doing it wrong, it's out of ignorance, not malice. 

Anyway, I got a new computer in December and Ubuntu has been working just great on it ever since. My old computer (running SuSe) has been gathering dust. I finally got off my duff last night and tried to move my data from the SuSe box to the Ubuntu box. 

I tried directly connecting the machines via crossover cable. No joy. 

Both machines are currently connected via a Motorola Wireless Broadband Router (WR850g). 

I can "see" each computer from the other one... I have been able to pull up the SuSe screen on Ubuntu via VNC and vice versa. I have also been able to SSH (and FTP) into the SuSe box from the Ubuntu box via the command line. 

I installed Samba (following the directions from the unofficial starting guide) on the Ubuntu box and have Samba client running on the Suse box. With that, I can see the Ubuntu box on the SuSe box. 

Here's my problem: I can't for the life of me figure out how to get the data from one machine to the other. When I pull up Samba in the SuSe box, it doesn't allow me to write to the Ubuntu box. When I pull up Samba in the Ubuntu box, it doesn't see the SuSe box as being on the network. 

I think, maybe I could copy everything via the command line, but it would be immensely better if I could have some sort of GUI to do it with. I tried using gFTP to get to the SuSe box via SSH and it never connects. 

Any thoughts? 

Thanks for any assistance.

---

### Post by angrylittleman on 2005-02-09
Welcome to the community!!!! 
there are few ways to go about this.  If you fire up synaptic, you can install SWAT which is part of webmin.  There should be a how to in the HOWTO section.  That gives you "gui" from your browser to configure samba.

Hm, when you ftp into the suse box, can you dl files from it?  routing should be ok here, if you can ssh and ftp into it or run vnc.  you are half way there :P

If you want, you can get an smb.conf file and modify it for your machine....it sounds much scarier than it is....

---

### Post by rosslaird on 2005-02-09
Data is passed between my two Linux systems (one on Debian, one on Ubuntu) every day with an automated run of rync using ssh. For the data in my home directory, it just does this:

rsync -e ssh -varuzP /home/my_home/ other_computer:/home/my_home/

To go the other way, I'd use:

rsync -e ssh -varuzP other_computer:/home/my_home/ /home/my_home/ 

To do this once (i.e. to copy/sync all data in a given directory from your old machine to the new one), just run the equivalent command above (substituting your directories and the name of your remote system).

To automate it (i.e. with cron, so that data goes back to the "old" system for backup every day), you need to create ssh passwrod-less logins. There are many tutorials about how to do this (use Google).

Yes, the gui is more friendly. But rsync is, by far, the best tool for data syncing and backup. (Be careful, though: if you accidentally reverse the destination and source, you can overwrite the data you want to copy!)

All you need is rysnc (apt-get rsync) and ssh. Get rysnc, then from a command line try this:

ssh other_computer

(substitute the host name of the other computer, or the ip address (e.g. 192.168.2.101). You wil get a message about host authentication. Accept it. Then you will be asked for your password. Make sure you have a username on the other system that's the same as the one you're using from the local machine. If not, use:

ssh username@other_computer

You *should* be able to login. "exit" gets you out, and back to the local machine. If this works, then all you need to so is:

rsync -e ssh -varuzP other_computer:/directory_name/ /directory_name/

(The last directory name on the line above is for the destination directory on the local machine. The trailing slashes matter). So, to copy/sysnc old "data" directory to new machine:

rsync -e ssh -varuzP old_machine:/home/whomever/data/ /home/whomever/data/

This will create a "data" dir on the local machine and copy all remote files in "data" to it. Next time you run rsync it will sync the files. (If you have a different username on the old machine, use rsync -e ssh -varuzP username@old_machine:/home/whomever/data/ /home/whomever/data/ ).

If you are worried about overwriting data, just create a test directory on the local machine to test this out.

Hope this helps.

Ross

---

### Post by zaba on 2005-02-10
rsync looks like it is going to do the trick! Thanks rosslaird!

A few things to note: 

angrylittleman: SWAT wouldn't work. Using apt-get (or Synaptic) it said it was dependent on an older version of Samba than what I have running. Tried to install an older version of Samba and got a message saying that the version of Samba I wanted was dependent on an older version of some library or another... I could see the whole process of chasing down all the older dependencies as being a pain... I'll probably try out SWAT when the dependencies are updated...

Oh, yeah, I lived in "Cornville" for quite a few years, myself... often right off of I-80. 

For those who are going to do something similar to what I did, rsync needs to be installed on BOTH computers (as far I can tell... that's the only way I got it to work.) And, I think (although could definitely be wrong), it appears that everything you want to transfer needs to be in a folder... which, for me, will actually work out better... I don't need *everything* off the old computer (i.e. don't need Firefox, since OO.o, etc.)... But things I do need (bookmarks from Firefox) can all be shoved into one folder and then hit the rsync right before sleep. 

Thanks for your help, all!

---

### Post by rosslaird on 2005-02-10
I'm glad it worked out.
I think you're right: rsync does need to be on both machines. I forgot to mention that (as well as host of other details that it sounds like you figured out on your own).

> it appears that everything you want to transfer needs to be in a folder... 

Well, everything needs to be somewhere with a /, and since in Linux everything is allocated by / locations, everything will be in a folder. But I think you mean how to access files across multiple folders in one step. For that you need multiple arguments or multiple lines in a script. I use multiple lines in a script that runs every night. One line copies my home directory (all of it) to my other system, another copies over my documents to my web server, another copies certain configuration files to the other system, and another line pulls in my website files from my web server to my local machine. I have things going three ways. It works very nicely. 

Cheers.

Ross

---

### Post by blixtra on 2005-02-10
Probably the easiest way for a new user is to use the "Connect to Server..." dialog in nautilus and connect via ssh then simply pulling them over.  This is relatively slow though and is probably not suitable for large amounts of data (3Gb+).  Samba and nfs seem faster for me.  I do this when I need to get something quickly form my Suse box.  The nice thing with this method is you've got an icon on your desktop that you just need to enter the password for later.

...and no command line needed.

Chris

---

### Post by Rule on 2005-02-10
i've always used scp it works great :)

all I do when moving folders is "scp -r <folder> <username>@<IP>:/home/<username>" I wonder if tis made any sense  :?

anyways thats how I do it.

Rule

---

### Post by Reb on 2005-02-10
scp is very nice... it's never caused me trouble.

---

### Post by zaba on 2005-02-15
[QUOTE=blixtra]Probably the easiest way for a new user is to use the "Connect to Server..." dialog in nautilus and connect via ssh then simply pulling them over.  This is relatively slow though and is probably not suitable for large amounts of data (3Gb+).  Samba and nfs seem faster for me.  I do this when I need to get something quickly form my Suse box.  The nice thing with this method is you've got an icon on your desktop that you just need to enter the password for later.

...and no command line needed.

Chris[/QUOTE]

Cripes, that was TOO easy! Just what I was looking for... The other ways have been extremely helpful, too... rsync via command line is just fine, but a GUI interface is really good to have, too. Thanks for the tip!

---

### Post by Davepet on 2005-02-15
I've got a slightly different networking problem.

My network consists of a  Xandros/win desktop & a Ubuntu/win laptop. When the laptop is booted into Ubuntu, I can browse shares on the desktop (either Xandros or win), but it is painfully slow. By that I mean it takes several *minutes* to update after clicking on a directory. Transferring files is also quite slow.

The other problem is that from the desktop, Ubuntu is asking for a password before letting me browse it's shares. The system passwords don't work & I didn't set any other passwords for shares...is there a default password that I've missed?

Thanks,
Dave

---

