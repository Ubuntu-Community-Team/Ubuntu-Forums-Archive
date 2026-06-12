---
title: "Nautilus - Apply Permissions to Enclosed Files Non Functional"
date: 2008-11-26
forum: Desktop Environments
---

### Post by BeigeGenius on 2008-11-26
When clicking on the "Apply Permissions to Enclosed Files" button under the permissions tab in a folders properties does not set owner permissions for files and folders within that folder!

Same result when running as root.

---

### Post by taurus on 2008-11-26
Where does that file/directory (folder) locate?  Is it on a ntfs filesystem?

---

### Post by BeigeGenius on 2008-11-26
it is any folder on any partition.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/165113](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/165113)

It is disgraceful that a bug like this one has been left un-fixed for over 12 months. The only other way to quickly alter all files and sub-dirs of a folder is through chmod in the CLI.

However the fact still remains that the gui button is there but isn't fully functional or misleading!

---

### Post by TuxPrincess on 2008-11-28
I wondered why that never worked.
I am amazed that a bug like this has been left so long without being fixed. It goes to show that even though ubuntu is maturing fast the rate at which bugs are fixed isn't!
The only way is chmod from the command line I'm afraid. Gnome hasn't gotten everything figured out yet.

---

### Post by mahavishnu on 2008-12-28
I'm having a hard work altering permissions for files and folders, one by one, backed up from a DVD.

All the files copied from the disc is root owned.

Since "apply permissions to enclosed files" didn't work I've found this topic.

Is there a simply way to manage this bug?
It's annoying change owner of folder and files one by one.

thks.

---

### Post by Roasted on 2009-10-18
> **mahavishnu said:**
> I'm having a hard work altering permissions for files and folders, one by one, backed up from a DVD.

All the files copied from the disc is root owned.

Since "apply permissions to enclosed files" didn't work I've found this topic.

Is there a simply way to manage this bug?
It's annoying change owner of folder and files one by one.

thks.

I hate to dig up an old thread, but I can't help but to want to offer a response to this.

Let's say you have a folder known as /media/storage, and you want storage + everything inside to be owned by fred:fred

sudo chown -R fred:fred /media/storage

The -R is key - it means it'll change all files/folders inside to those exact ownership. I can change ownership and permissions of all files/folders on my backup drive - all 380gb worth - within 10 seconds.

---

### Post by BeigeGenius on 2009-11-10
As mentioned above there is currently a bug report on launchpad for this bug!

Pity that ubuntu is making progress in 'usability' but is still lacking a feature which is standard in other operating systems (windows, mac etc.) without the need to jump into the terminal and run chmod/chown recursively!

---

### Post by Roasted on 2009-11-10
> **BeigeGenius said:**
> As mentioned above there is currently a bug report on launchpad for this bug!

Pity that ubuntu is making progress in 'usability' but is still lacking a feature which is standard in other operating systems (windows, mac etc.) without the need to jump into the terminal and run chmod/chown recursively!

Actually, I'm failing to understand why there is a bug report. The more I use Ubuntu, the more I realize that this is not a bug.

If you are the owner of the folder, you can change permissions to it accordingly. I've tested it numerous times. 

Jason owns /media/storage. If I go through the GUI and select "Apply Permissions to Enclosed Files" they indeed get the intended permissions. 

But, it does not change the group ownership. Meaning if jason:samba owns /media/storage, but everything inside storage is owned by jason:jason, then hitting "Apply Permissions to Enclosed Files" WILL change PERMISSIONS - but not the group. The group is part of ownership, not permissions. Permissions are read/write/execute. Group + Owner = ownership.

So, in short, if you own the folder and use "Apply Permissions to Enclosed Files" it does work. However, it does not change group (group is part of ownership - not permissions).

I've also noticed that if you use this, you may notice the permissions may not be entirely applicable. I used this feature on a folder of pictures, but when I checked the permissions in terminal, they came down as read/execute, not read/write/execute like I set the parent folder in the graphical interface. But then I noticed something. How CAN you write to a picture file? You can't. It's just... a picture. You can write to a folder. You cannot write to a picture. That's why if you hit "Apply Permissions to Enclosed Files" it does indeed apply the permissions to folders and certain files that CAN be written to, but other files that aren't applicable, it doesn't even bother assigning that permission to them (such as the picture example above).

It seems as if Linux is smart enough to determine what files we can and can't by nature write to, which is why it appears as if this feature doesn't entirely work when indeed it does. If you run chmod -R from terminal, then you're forcing the permissions on all files/folders, that's why it appears like chmod -R works and it makes "Apply Permissions to Enclosed Files" not work entirely.

But, like I said - they both work. chmod -R from terminal forces the permissions. "Apply Permissions..." button just applies them, and it does do its job - it's just important to remember that it doesn't force permissions on files that cannot be applied to the permission in question (aka like I said above - you can't write to a picture file, hence why it doesn't show up as read/WRITE/execute and just read/execute).


Just remember it doesn't take group with it since group is not a permission - it's an ownership... Which, if you NEED all files/folders that get stored into a folder to retain the same group ownership, go into terminal and run sudo chmod g+s /YourFolder. g+s sets the group so all files/folders created in that directory get the parent folder group ownership.

aka /media/storage = jason:samba. if I chmod g+s /media/storage, everything I put inside /storage gets the group "samba" assigned to it automatically.

But please note = if fred:samba owns /media/storage, then me (jason) CANNOT change permissions on a folder I don't own. This is done intentionally for security reasons. Only fred can make those changes, unless jason is listed as "administrator of this system" and does it from sudo in terminal.

---

### Post by siabost on 2009-11-13
Hi Roasted,

I think I understand what you're saying but the basic problem is the ownership logic, particularily for new users e.g.

I've introduced a previous Windows user to Ubuntu 9.10 & he's delighted with it!
He is some distance away and is non-technical when it comes to computers so I did a short desktop video which I burned to a CD as a data file and sent it to him.
He dragged the video file onto his desktop and is now perplexed as to why he can't (easily) get rid of it.
I am presuming the following: I made the file so it has me as owner till it gets burned to disk. When my friend dragged it to his desktop, since I don't exist as a user on his computer, rather than giving the user who is dragging it in ownership Nautilus hands it to root! 
I think that that default is wrong and ownership should default to the active user rather than root. 
To use your example: if Fred & Jason are both users on a computer then it makes sense that one can't delete/change the other's files unless they choose it to be so i.e. group ownership. If Fred isn't a user on Jason's computer it doesn't make sense that files he gives to Jason are copied to Jason's computer as root. Or am I missing something?

Is there a GUI alternative to running ```
sudo chmod g+s /YourFolder
``` in Terminal? Maybe in Folder Preferences?

Also does this work for the complete Home Folder? i.e. ```
sudo chmod g+s /home
``` and would he also need to run the equivalent of ```
sudo chown -R username:username /home
``` to change ownership of any previously added files?

Many thanks. ;)

---

### Post by Roasted on 2009-11-13
siabost - 

I completely understand where you're coming from. I took a lot of classes in computer + network security, so I can relate to users issues both as a technical computer user and as somebody who just needs to get his work done. The reality is (and I promise I'm not putting your buddy down) - so you really want a "basic" user to have easy access to changing advanced ownership permissions in the GUI? Something like that I believe should be kept at the terminal level - a place where novice users don't really play around in.

Again, it's not to step on any toes, but I can understand why things are lined up the way they are. You can change permissions on files/folder via "Apply Permissions to Enclosed Files" as long as you own the folder. Who owns the folder? YOU. If you own it, you have control, therefore you can change whatever you want. 

I am unsure of why the video file in question errored out for your buddy. I just did a quick test here at work. At home, I have Ubuntu Jaunty running with the user "jason". At work, I have Ubuntu Jaunty running on a desktop behind me with the user "administrator." I have a CD I burned at home with the user jason. When I put that CD in my work desktop (which has the user administrator) and I drag/drop a file from the CD to my desktop, the permissions come down as administrator as the owner.

Think about it like this. Jason may have burned the files to the CD, but that's to the CD. When you bring files from any media (such as a CD) and drop it to your system, your SYSTEM now has control of that file. That file is therefore controlled by the user of the system. Since administrator was the active user who dragged + dropped the file on the desktop from the CD (therefore, "creating" it) then administrator gets assigned as the active owner of that file.

All in all, I'm unsure of how your buddy ran into this issue. Dig up some more info from him and post back and we'll surely get his problem straightened out!

---

### Post by siabost on 2009-11-14
Hi Roasted,

I think I have a rather sad admission to make here - I'm in a bit of a Linux enclave here. Work PCs & most friends comps are dominated by Wins & Macs!

Thus I haven't had the opportunity (and as there is only user on my Ubuntu 9.10) to see with my own eyes what happens when a CD burned file is dragged onto a different user's desktop. I have only my friend's eyes to tell me what his video file problem is. Since then I've phoned him and he's given the location of the file as /media/cdrom0/... - i.e. he's still got the CD in the drive and as it's a CD-R so **that's** why he can't delete it! I don't blame him - I should have checked out the basics first!#-o

Just did a quick test with a data CD here &, sure enough, while the file is on the CD it has owner as root. As soon as I drag it to my desktop I gain ownership of it. As my set-up is the default set-up re ownership & permissions that will also be my friend's set-up. And that's a relief!

> Jason may have burned the files to the CD, but that's to the CD. When you bring files from any media (such as a CD) and drop it to your system, your SYSTEM now has control of that file. That file is therefore controlled by the user of the system. Since administrator was the active user who dragged + dropped the file on the desktop from the CD (therefore, "creating" it) then administrator gets assigned as the active owner of that file.

I fully agree with the logic above - that's what I was worried **wasn't** happening!

And I also agree it would not be a good idea to have the default set-up changed via the GUI - I didn't want my friend delving too much into the Terminal at this early stage. But as it stands there's no need.

Apologies for wasting your time, but thanks for the information.

As I said, my friend is absolutely delighted with his Ubuntu & his compatriots (originally sceptical - interestingly, full of erroneous preconceptions re Linux) are becoming a little jealous:D!

One successful convert - only 95%ish of the rest to go...

Thanks

---

### Post by Roasted on 2009-11-14
Wasting? Naw. I'm happy to help where I can. Like I said, I don't view Ubuntu as hard - just remember, it's just very different! Once you get the jist of it you can understand what the OS is thinking, which is pretty damn cool.

Just remember this forum exists for these exact reasons.

Also - about your friend - For his learning sake, did you explain to him that deleting the file off of /media/cdrom0 is the same as deleting the file off of the cd rom drive in Windows? No matter what OS - that doesn't work. :P 

Happy Ubuntu'ing! :guitar:

---

### Post by markackerman8@gmail.com on 2009-11-29
I am still frustrated that recursively changing owners permissions in Nautilus is NOT working like it says even ubnder sudo, and this is such a major hassle for newbies, and even me a user for 1 1/2 years, arghhhh

---

### Post by XubuRoxMySox on 2009-11-29
Try installing PCManFM from the repositories. It's a sweet little lightweight file manager (ordinarily part of the LXDE desktop, but it's modular).

Highlight the folder you want to edit permissions for, then choose **Tool** and then **Open Current Folder as Root**. From there you click on **File**, then **File Properties**, and choose permissions for all the files in that folder.

Works for me.

-Robin

---

### Post by mazz0 on 2009-11-29
Sorry, but I can't let people get away with saying that this isn't a but because the button is only there to change permissions and not ownerships.

The tab in question exists to change ownership and permissions, from a UI perspective it's treating them as one thing, that's why they're grouped together in one tab, so it's obvious that you should be able to apply recursive ownership from there just like you can apply recursive permission changes.  The existing functionality is counterintuitive and just awful UI.  We're forcing people to use the terminal just to change ownership of things, and we're not even informing them that they need to do so - it looks like they should be able to do it from that dialogue and that it's simply not working, only a Linux expert can figure out why it doesn't work.  Bloody AWFUL UI.

This is absolutely a massive usability bug.  It's part of bug 1, for a start.  If Ubuntu is to be "Linux for human beings" we can't force people to use the terminal just to change the ownership of something, can we?  And if we do, at least make it obvious they need to do so - don't have a button that looks like it should do somethign when it actually doesn't (although obviously it should).

</rant>

---

### Post by Roasted on 2009-12-01
> **mazz0 said:**
> Sorry, but I can't let people get away with saying that this isn't a but because the button is only there to change permissions and not ownerships.

The tab in question exists to change ownership and permissions, from a UI perspective it's treating them as one thing, that's why they're grouped together in one tab, so it's obvious that you should be able to apply recursive ownership from there just like you can apply recursive permission changes.  The existing functionality is counterintuitive and just awful UI.  We're forcing people to use the terminal just to change ownership of things, and we're not even informing them that they need to do so - it looks like they should be able to do it from that dialogue and that it's simply not working, only a Linux expert can figure out why it doesn't work.  Bloody AWFUL UI.

This is absolutely a massive usability bug.  It's part of bug 1, for a start.  If Ubuntu is to be "Linux for human beings" we can't force people to use the terminal just to change the ownership of something, can we?  And if we do, at least make it obvious they need to do so - don't have a button that looks like it should do somethign when it actually doesn't (although obviously it should).

</rant>

In all honesty, if you know enough about file permissions to even have to change  ownership of a file, you're certainly adept enough with computers to use the terminal. If you're not, then you really shouldn't be messing with file ownership in the first place.

No matter how you slice it, basic users will stick to basic things, while advanced users want a certain way things are laid out and a certain scheme of permissions and ownerships laid in place.

The fact that I cannot change ownership in the GUI does not bother me. What bothers me is you cannot change the group recursively. Granted, it's nice that PERMISSIONS are changed, but I'd like to see the group changed too.

One nice touch I saw with Kubuntu over Ubuntu (Dolphin vs Nautilus) is that in Dolphin, you can set the GID in the GUI, meaning you can force a group on any files/folders written inside the folder you're adjusting the setting on. Nautilus requires the terminal for that, and that's something that IMO should be in the GUI. It's a nice touch. +1 Dolphin.

Setting the GID is especially useful for someone like me who has all sorts of users who back up data to my computer. Having a set GID means I can link all users into 1 group and force that group with rwx permissions on the folder. Therefore, all users can truly share files without restrictions. Again, no biggie, but it was nice to see Dolphin had it built into the GUI under "advanced permissions."

---

### Post by mazz0 on 2009-12-03
I disagree - given the unix style of file ownership and permission, changing ownership of a file on linux, for example a file copyed from somewhere where it was ownded by a different user, isn't that uncommon, nor that advanced, and it certainly isn't so advanced that it warrents use of a terminal.

---

### Post by tinmanjim on 2009-12-03
I'm semi-literate using Ubuntu (Karmic); when forced to use the command line, I can usually figure out fairly simple things given time, patience, and good search terms, but mainly I would prefer to use a GUI interface, as that minimizes the learning curve and command memorization issues. Also, believe it or not, I'm by far the most "computer savvy" person among my friends and family; trust me, outside of your hand-coded world it's a pretty common phenomenon.

I've got a few "economically challenged" friends with older hardware that Windows has problems with. I'd like to set them up with Ubuntu, because of it's stability and (more or less) user-friendliness.

The only reason I hesitate is because when I go to set them up, the twin issues of permissions and ownership come up. I can, of course do some searching and experimentation to take care of this... then when, in a few months, it comes up again for someone else, I've got to do the same searching and experimentation; a bit easier and faster this time because I remember some of the terms that worked the last time. However the odds of remembering the specific commands and the order in which to use them is vanishingly small.

So the question really boils down to: Is Ubuntu to be the reserve of "Command Line Geeks", or would we rather see market share increase? If we're constantly touting the benefits of Linux to our non-geek buddies, wouldn't it make sense that these less-than-savvy folks be able to actually use the system without spending the months or years the devotee is willing to take to learn all of the ins and outs of the CL?

It seems to me that it might be a good idea to include in the installation a button that allows the installer to set comprehensive permissions for the "Home" directory, or at least make it so that the button so well hidden at the bottom of the permissions tab of the properties dialog could perform a similar function. After all - if *you* don't choose to use it, how does it affect *you*, and why do you care that someone else finds it easier (more user-friendly) to have less stringent security?

I agree that on a laptop or in a dorm setting these might be serious concerns, but when setting up a desktop inside a private dwelling I think some of the security just might be a bit of overkill: thus my call for the option at install time.

Rant complete...

---

### Post by Roasted on 2009-12-03
> **mazz0 said:**
> I disagree - given the unix style of file ownership and permission, changing ownership of a file on linux, for example a file copyed from somewhere where it was ownded by a different user, isn't that uncommon, nor that advanced, and it certainly isn't so advanced that it warrents use of a terminal.

Maybe not to you, but I work in a school district where I have to help out teachers and all staff with computer problems. You'd be surprised what kind of issues I come across that were ID 10 T errors.

Although I'm a terminal junkie, I still like the ease of doing things in the GUI. And although Dolphin on KDE has more options (Advanced Permissions) set up in a more practical manner in the GUI, as opposed to Nautilus on Gnome, KDE still has its limitations too - proving that Linux as a whole decided, perhaps some of these permissions DO need to remain at the terminal level.

---

### Post by mahavishnu on 2009-12-06
> **Roasted said:**
> I hate to dig up an old thread, but I can't help but to want to offer a response to this.

Let's say you have a folder known as /media/storage, and you want storage + everything inside to be owned by fred:fred

sudo chown -R fred:fred /media/storage

The -R is key - it means it'll change all files/folders inside to those exact ownership. I can change ownership and permissions of all files/folders on my backup drive - all 380gb worth - within 10 seconds.
works perfect here !!
didn't think it was so simple, thanks.

---

### Post by pearldrums on 2009-12-06
Forgive me if the answer is in this thread already and I have missed it but most of it is a little bit above me and a lot of debate about how things *should* be done. I'm having issues using "chown". I copied a bunch of files from an old instillation into my new instillation and they were all given only root permissions. Heres how I tried to remedy it:
```
levi@levi-desktop:~$ sudo chown -R levi:levi /home
chown: cannot access `/home/levi/.gvfs': Permission denied
levi@levi-desktop:~$ 
```

what am I missing?

---

### Post by pearldrums on 2009-12-06
> **pearldrums said:**
> Forgive me if the answer is in this thread already and I have missed it but most of it is a little bit above me and a lot of debate about how things *should* be done. I'm having issues using "chown". I copied a bunch of files from an old instillation into my new instillation and they were all given only root permissions. Heres how I tried to remedy it:
```
levi@levi-desktop:~$ sudo chown -R levi:levi /home
chown: cannot access `/home/levi/.gvfs': Permission denied
levi@levi-desktop:~$ 
```what am I missing?

Ok, disregard my message. I'm not sure what /home/levi/.gvfs is, but the permissions of everything else got changed and all is well. Sorry about that. And thanks for the info!

---

### Post by tinmanjim on 2009-12-06
> **pearldrums said:**
> Ok, disregard my message. I'm not sure what /home/levi/.gvfs is, but the permissions of everything else got changed and all is well. Sorry about that. And thanks for the info!
I had the same issue, and thinking the chown had failed (the 'permission denied' message might lead one to believe that), kept trying and reading and researching and trying again. 

Can anyone enlighten me as to what that's about?

---

### Post by Francewhoa on 2010-04-15
Thanks dixiedancer. It works :) Much easier than command line for me. I'm a user not a coder.

---

### Post by ottabaub on 2010-05-14
Recently I upgraded my laptop from 9.10 to 10.04. I cloned my partitions before and after using Clonezilla Live onto a USB drive. (If you've never used Clonezilla, try it. It rules!) 

Last night I decided to move the files from the USB drive to my desktop computer. I couldn't do it. I didn't have needed permissions. The files belonged to root. So I pressed **Alt-F2** and ran *gksudo nautilus*. I right clicked on each folder, selected **Properties**, clicked on the **Permissions **tab and changed the owner to me, "bob". Each time I clicked on the **Apply Permissions to Enclosed Files** button.

Once again I tried moving the files to my desktop and, once again, I was denied. I opened the folders and discovered that the files were still owned by *root*. I didn't understand why. To solve the problem I made the folders shareable and moved them that way.

But today I was still curious about why the "permissions" didn't change and that's what brought me to this discussion. After reading _Roasted's_ most excellent explanation, I get it. Yes, it is confusing especially for those of us who have been nurtured by Microsoft for many years. File ownership and file permissions are two different things. The **Apply Permissions to Enclosed Files** button does just what it says. It does not promise to change ownership of the files, just permissions. So, if you don't own them, you can't change them.

Computers operate on literal commands. If you've ever written a program you'll understand. They will do what you tell them to and nothing more. Computers, unlike human beings, do not ***assume***. Whoever programmed the **Apply Permissions to Enclosed Files** button did it correctly and literally by making it do no more than what it says. 

In another discussion, I found this:
> [FONT="Courier New"]sudo chown -R $USER:$USER /media/disk
chmod -R 755 /media/disk[/FONT]
I tried it and it works. I could have skipped the second line and used the GUI but at this point, this was easier. 

Ubuntu is not Windows. I enjoy the challenge of learning how to use it and the knowledge that, while not perfect, Ubuntu (by extension, Linux) gives the user much more with less hassle (if you've used Vista you understand) and, because of the way other users share their experiences and knowledge in forums like this one, it provides one with an overall sensation that comes as close to a ***warm and fuzzy feeling*** as anything technological I've ever experienced. Not bad for free, open source software.

---

