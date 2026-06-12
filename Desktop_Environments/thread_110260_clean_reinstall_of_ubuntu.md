---
title: "clean reinstall of ubuntu"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Doc504 on 2005-12-30
I have just ubuntu 5.10 on my pc--how would I do a simple clean, reinstall--that is remove ubuntu?:confused:

---

### Post by steve.horsley on 2005-12-30
The installer will not install over an existing installation. I discovered this when I tried todo a clean install to change from Hoary to Breezy. I had to use a live CD to delete the partition contents first. 

It may be that just deleting the /boot tree would do the trick - I don't know what files it actually checks for before refusing to over-install.

---

### Post by Doc504 on 2005-12-30
Thank you for the help.  When you state--try the "live CD" I'm taking that to mean the live CD that cames along with the install CD?:confused: 
I tried that "live cd" and I couldn't proceed--some error kept caming up.  Is there some simple way to install wins 98/2nd on my computer--that now just has ubuntu 5.10?  Perhaps a webpage with clear steps for newbies?:razz: 
Happy New Year!
Doc

---

### Post by kaamos on 2005-12-30
Why shouldn't it install over the old one? What problems did you have?

It should work if the partitions are cleared during the install..

---

### Post by KrazyPenguin on 2005-12-30
Are you saying that you want to Install Ubuntu 5.10 over a root partition already containing Ubuntu 5.10???

Put the install cd in the cdrom drive and boot your computer.
Now you will manually partition the Hard Drive when you get to the partitioning part.
Click where you want the root "/" partition.  Change the setting so it says something like "Yes, Partition".  It will confirm this later on.
Your home partition (hopefully you have one of these) can be set to "No, don't format" so the existing content is not destroyed.

Also remember to backup all critical system info before tampering with partitions, etc.

Hope this helps ;-)

---

### Post by bishop on 2005-12-30
Okay. I've been hunting for a topic like this for three days now. 

I didn't really *think* this through when I set everything up to begin with so I didn't create multiple partitions so that my /home directory would be separate from everything else. 

AND, I didn't really give myself time to get out of "play around with everything in sight" mode before I moved all my backup materials back to my machine. 

So ... I have just a bunch of stuff on my installation that 1) I'll never use, 2) are "half-installed" for one reason or another, and/or 3) was just "for fun". 

Now ... with XP, for instance, I can shove that CD back in and "repair" my installation and take my XP back to (basically) an "original state" without losing my data. 

Is there a way to do this with Ubuntu/Kubuntu? I'm concerned that if I do anything else at this point, I'm going to lose all my information that I put back on the machine and the machine that was holding the backup materials is currently down pending it's own reformatting and reinstallation of a dual boot system. 

So ... am I screwed? 

Thanks in advance!

---

### Post by KrazyPenguin on 2005-12-30
You can back-up everything in your /home directory , even if it isn't on a separate partition.

It is best to use a cd-rw/dvd-rw, and use 2 of them, alternate with each backup.

Here is the command to use from a terminal:
tar cvpfz /home/username/backup.tgz  --exclude=/home/username/.Trash /home/Stuff/Music /home/username

This will make a backup.tgz (compressed file) which will be saved to your /home/username directory.  You will be backing up everything in your home/username directory except for the Trash as well as another directory I named Stuff, which contains a directory Music.  This gives you an idea as to how to omit stuff and backup specific things like the Music Directory located in another directory. Hope that helps ;-)

Then after installing Ubuntu (or what ever Distro you like) , you open the file with Ark and extract and all your info will be uncompressed.
You can test this by first if you don't trust it by copying the backup.tgz off your cd (after you have burnt it) back onto your computer in a different folder.  Then extract it in that folder.

Good luck ;-)

---

### Post by bishop on 2005-12-30
This is awesome instructions. Now, the only thing that I didn't see here was email. I figured out how to "see" the hidden files and I can see all kinds of things here now. But I don't see where my email is being stored. I'm currently using Kontact. 

Thanks for this amazingly simple instructions and assistance in this pursuit.

---

### Post by KrazyPenguin on 2005-12-30
So your using Kubuntu.

I'm using Ubuntu but I do have KDE experience ;-)

And I keep really good notes as well. :) 

Your email is stored in your /home directory.

So if you back it up you will have backed up your email.
But now the question is where is the email located in your home folder???
I did a quick search for you and came up with this:
~/.kde/share/apps/kmail/mail

Open your home directory and view the hidden folders to find it.
Just back that up, which it will be after you back up your system.
Then later just copy and paste and your mail should be there.

---

### Post by bishop on 2005-12-30
Sorta. I have Ubuntu with some Kubuntu stuff installed (among a ton of other things LOL). 

Thank you again for your help here. I found that directory and I'm working on getting things compressed and backed up now. I'd like to move toward Xubuntu since I like the options and the light-ness of the package. I can install the extra stuff that I want individually from there (I think). But at least I can get a partition in place so that I don't have to go through this again if I decided to make a repeat performance of this fiasco. LOL! ;)

---

### Post by KrazyPenguin on 2005-12-30
I would suggest more than one root partition.
Make at least 2 in case you want to try another distro.
(Trust me -- you will   lol)
Mine looks like this:

1. 5GB 	Linux1 --- Used for main Linux Distro.
2.Primary 5GB 	Linux2 --- Used for secondary Linux Distro.
3.Primary 5GB	Linux3 --- Used for testing distros.
4.Extended    1GB Linux-Swap --- Used as a shared swap partition between the distros.
5.Extended  50GB  Home --- Used as a shared home directory for 3 installed Linux distros.
6.Extended  10GB Music --- Used for music storage

Hope this helps ;-)

---

### Post by briancurtin on 2005-12-30
[QUOTE=steve.horsley]The installer will not install over an existing installation. I discovered this when I tried todo a clean install to change from Hoary to Breezy. I had to use a live CD to delete the partition contents first.[/QUOTE]
this is incorrect

i've done this probably 5 times with zero problems at all

---

### Post by KrazyPenguin on 2005-12-30
I have re-installed as well.

You must choose to reformat the partition you are re-installing to or else it won't let you do it, if I remember correctly.

The text installation is a little hard to follow at first ;-)

---

### Post by bishop on 2005-12-31
My final question is this (since I have you guys here at the moment): when re-installing, will the installer allow me to create these multiple partitions? I don't recall since I just had it reformat and create a single partition when I installed the first time. 

Thanks again for all your help and advice here.

---

### Post by dragonfoundry on 2005-12-31
[QUOTE=KrazyPenguin]You can back-up everything in your /home directory , even if it isn't on a separate partition.

It is best to use a cd-rw/dvd-rw, and use 2 of them, alternate with each backup.

Here is the command to use from a terminal:
tar cvpfz /home/username/backup.tgz  --exclude=/home/username/.Trash /home/Stuff/Music /home/username

This will make a backup.tgz (compressed file) which will be saved to your /home/username directory.  You will be backing up everything in your home/username directory except for the Trash as well as another directory I named Stuff, which contains a directory Music.  This gives you an idea as to how to omit stuff and backup specific things like the Music Directory located in another directory. Hope that helps ;-)

Then after installing Ubuntu (or what ever Distro you like) , you open the file with Ark and extract and all your info will be uncompressed.
You can test this by first if you don't trust it by copying the backup.tgz off your cd (after you have burnt it) back onto your computer in a different folder.  Then extract it in that folder.

Good luck ;-)[/QUOTE]

How would you backup directly to another partition?

---

### Post by Doc504 on 2005-12-31
I had wiped my old wins98/2nd and installed Ubuntu which I love but found it difficult to connect this to the internet (perhaps it would have been better to install Ubuntu along with this old wins98?).  I did find our that using the wins98  boot disk and 98 cd, I was able to reintall wins98 but lost the Ubuntu.  Also, when I tried to re-connect to the internet, my old wins98 was not able to detect the modem (dialup) which may have been the problem when I tried to connect with Ubuntu.  Some other way to install Ubuntu (not wiping the old os) would be better>:confused:

---

### Post by bishop on 2005-12-31
Well, I've discovered that I cannot recover my emails. Moving the backup directory for the kmail gave me my email accounts and contacts list, but it does not recognize my folders or my emails. So, I've royally screwed myself on this one. Even though it's only a week's worth of email, I get close to 200 business emails a day. So far, I haven't recovered any of them. 

But, at least now I can write an article on exactly what is necessary to truly convert Windows users to Linux/?buntu. There isn't a single package out there that is user friendly enough to get one from Point A to Point B and then keep people happy enough to stay with it. I just happen to be one that likes to tinker, so I'm just plodding along. But anyone else I know that's a Windows user would have given up by now and been very unhappy with losing a ton of email (unless anyone else has ideas on how to get this stuff back).

---

### Post by Herman on 2005-12-31
Hi, bishop, I have both Ubuntu and Kubuntu, but I haven't treid this in Kubuntu yet.
In Ubuntu, I have noticed that it seems to not restore the e-mails every time right away...until I re-boot. Then all my restored items will appear. (In evolution).
Another thing I have noticed is, if I am restoring bookmarks while firefox is running, they don't seem to go in. Try restoring your email with evolution (or kmail) not running and then re-boot. You should be successful then.
I made a website partly in the hopes of making it easier for people running small businesses and farmers and who-ever, to be able to do things with Ubuntu like this right away, and help get them off to a quick start.
Don't give up on Ubuntu yet. It is a great system for business and professional use.
I'll keep an eye on this post. Let me know if it doesn't work and I'll try some experiments here with my computers and see if I can help. :D (Herman)

P.S. check my siglink, there is a page there on backing-up and restoring, but I didn't use any file compression. There's no harm in using it though.

---

### Post by bishop on 2005-12-31
That doesn't work with Kontact. On experimentation, however, I notice that if I try to recreate a directory in Kontact using the same name as before (I liked my organization), it won't do it since it says "File Exists". If I rename the (backup) directory, then try to create it again, it will let me. So it does see the directories and will even "protect" them from being overwritten, but it doesn't see them to restore them. That's just odd to me. So, generally speaking, there is no way -- SO FAR -- to restore a backup of the directories and emails for Kontact (which I really like after working with Evolution and one other that slips my mind, but this is just GUI preference speaking since the all have about the same functionality in my mind). This is a bummer but not a showstopper. 

I gave up on Ubuntu and went with Kubuntu for many reasons. My original intent with this freash install was to actually go with Xubuntu, but I discovered that there are more holes in that thing than any other flavor of ?buntu. So, I did my second fresh install with Kubuntu. Everything that I like about Ubuntu I can install separately, and everything I don't like about Kubuntu I can uninstall easily enough. Im having difficulties with some of the repositories now, but I'll figure those out when I find the threads here that helped me the first time around. (I'm just juggling a 7yr old, installs and general family mayham at the moment.) 

If I had to weigh in all the factors that made me an avid Windows fan, I could reproduce most of them (except my 3D image work) on this OS. I like it a lot with some minor caveats that don't really matter in the big picture. But I could write a lengthy article on what the "ideal" ?buntu installation would be if "da man" wanted to truly attract *and keep* Windows users. Both of these flavors have major drawbacks that make it very, very difficult to maneuvor right "out of the box". As I said, I like to tinker, so I'm always "playing" with things to get it the way I want it. I do the same thing with Windows. But many, many people either buy a system with Windows or install Windows and really don't touch it all that much except to install little things. And those are the hard core Windows users because they don't question, don't change (much) and don't really care to do anything but work straight "out of the box". There is enough here to make that happen with the ?buntu installation too. It's just not currently one of those that are the big three or four that I've seen around. 

Before I get really moving on this new installation, I'm tempted to install Edubuntu just for kicks to see how it looks and runs. LOL! I guess, since I've finally partitioned things out so that my /home directory is all alone, I *could* do that now without much of a problem at all. LOL! 

Thanks for everyone's advice and help in all this. It's been a great help and kept me from going coo-coo in my coco puffs.

---

### Post by Herman on 2005-12-31
Well I'm firing up KDE Kontact now. I'm not experienced with Kubuntu at all, and I find it as new as you do. There must be a way to do this, and I'll bet it's very simple too, we just have to play around a little.
I think Ubuntu and Kubuntu are the ultimate operating systems for business, and I think they will really take over big time in the coming year or two. All we need is better instructions so people can get to work quickly and get on with their jobs without having to waste too much time studying.
I see they are thinking of making up courses with exams so that people can become certified Ubuntu engineers, for finding employment with companies running lots of Ubuntu computers. I want to study for that, I'm not sure I'll be good enough, but I think Ubuntu has a big future.

In the meantime... if I can help with this problem now, I will be happy, but if you solve it first, then that will be okay too.
Let me see now 'Welcome to Kontact 1.1.2' -read manual....(give me some time)....:D (Herman)

---

### Post by Herman on 2005-12-31
Okay, bishop, I believe I have some good news for you and, as I suspected, it is really very simple.
Here's what I think you need to do, instead of pasting the whole mail folder, just open up both folders. I mean your back-up mail folder and your new one. Then paste the *files* inside from one to the other. (Not the whole folder). Then close everything and re-boot.
Well, to tell you the truth, I didn't even need to re-boot this time, but it seems tobe necessary quite often.

I was crazy and reckless enough to try this with files from my Ubuntu evolution mail, into my Kmail. They are 'a different breed of cat', and I did realize at the time that it wouldn't be a good thing to do. But I don't care because there are no other files in this kubuntu installation and I don't want to use kmail in it anyway. I don't mind re-installing it when I break it a little bit more.
Well, the files transferred okay, that's the good news, but for me they are unreadable, becuase they are from evolution and they aren't supposed to be done like that. There is probably a right way. The main thing is I was able to open Kmail and see that I had mail in my inbox.

So it should work for you. Let me know if it doesn't, and I'll send myself mail to another computer from a web-mail box and try again by a more respectable but more time consuming method. 
I hope this solves you problem. :D (Herman)

---

### Post by Herman on 2005-12-31
I'm sorry, let me be more specific. 
Inside your kmail folder, in your mail folder, there are drafts, inbox, outbox, sent-mail, and trash.
Inside the outbox folder, there is one called new.
I suggest pasting the files inside your back-up 'new' folder into your new 'new' folder, and so on. 
It might even work to try pasting the whole folder called 'new', it could be a permissions issue, and now that we are another two levels inside our mail folders, pasting folders be okay agian.
I'll bet there's a much faster way to do this with a command in 'terminal', that everyone knows except us. I'll have a think about that for a while....
:D (Herman).

---

### Post by Herman on 2005-12-31
```
cp -r mail /home/herman/.kde/share/apps/kmail
``` 
Here it is, bishop, that's the command.
I took a while, sorry, I got a little side tracked doing a new-year's clean out in my hotmail inbox. Then, I sent myself some junk mail, and recieved it in my other computer, and copied the whole mail folder out of it.
In my first computer, the one I was fooling around with earlier, I used that command shown above, and in an eyeblink, I fixed my kmail and restored my whole mail folder. I opened my inbox, and there was my mail! :D

Now, all you need to do is adapt that command, obviously, with your own username, and once you have proved that it works, save it on a file (gedit), and from now on you will be able to just copy it and paste it into your terminal.

Now this is a lot faster than the whole process of backing up and restoring mail in that other brand of operating system now isn't it? (Once we know how). 
:D (Herman)

---

### Post by bishop on 2006-01-01
Didn't work. 

However, what I notice is that my original backups have only a "cur" folder in each directory. If I recreate the directory from scratch, it suddenly has a "cur", "new", and "tmp" directory in each new one. Also, all the new ones look like regular directories. The old ones are "hidden" and have a period (.) in front of the names. 

Pasting a single email into the "new" directory, as you suggested does actually work. That's just a lot of email to move (and that command didn't actually do anything for me, so I'm sure that I'm not doing it right or I'm missing something important in the execution here).

---

### Post by Herman on 2006-01-01
If your 'mail' folder from your back-up is un-tarred and is pasted somewhere in your /home/username folder, that should work.
If you 'mail' folder is still inside another folder in your /home/username folder, you should either copy it and paste it into your /home/username folder before using the command, or, add the 'mail' back-up folder's actual address to the command.
For example, if it is in another folder called '31dec05bak', in your /home/bishop folder, then you will need to modify the front half of the command like this:
```
cp -r /home/bishop/31dec05bak/mail /home/bishop/.kde/share/apps/kmail
``` Did that help you? :D (Herman)

---

### Post by Herman on 2006-01-01
My back-up mail folder has three others in it, 'cur', 'new', and 'temp', however, the 'cur' is the only one that appears to contian any files that I can see. There are, in my case, four files that appear to be my e-mails when opened with 'gedit'.
You should have two hundred of them then, I hope.

Edit: If that is the case, and the command still doesn't do anything for you, try the other way again, just open your 'cur' folder and click 'file', 'select all', and , leaving that window open, open your home folder and navigate to you new 'cur' folder and just paste the whole two hundred e-mails in there at once.

---

### Post by bishop on 2006-01-01
Got it. It worked. 

Thanks!
Happy New Year!

---

### Post by Herman on 2006-01-01
Hooray! And Happy New Year to you too! :D :D :D :D :D :D 
Regards, Herman

---

### Post by bishop on 2006-01-02
Okay. I've discovered another problem ... 

When I set everything up originally, I did pick a separate partition for my /home directory. However, it would seem that my /home directory is still at root (/) instead of the partition that I picked (/dev/sda7). So, when I went to unpack an archive to my /home/bishop directory, I got the error that I didn't have enough disk space. I should have if the /home directory had been where it was supposed to be. But as it is, it's correct. I don't have enough space. All I have at sd7 is a "lost + found" directory. 

How do I get this thing to put my home directory where I wanted it to be in the first place and stay there? 

Thanks!

---

### Post by Herman on 2006-01-03
That question is definitely a tough one. I don't think I'm good enough to be able to help you with that one. If you want to attract the right attention for it, I would advise you to start a new thread somewhere and title it with the word 'partition' or 'partitioning' somewhere in the title, and explain a little bit about your problem in the text.

 I always just keep everything in the one partition, it's much tidier. Partitioning is a touchy subject, you can get into some pretty long and complicated debates over which ideas are the best.

---

