---
title: "alternative harddrives/ssd's showing"
date: 2016-05-30
forum: Desktop Environments
---

### Post by rainerw2 on 2016-05-30
Greetings. Have my computers operating with 2 or 3 drives. When logging in to one, the alternative drives show in the selection bar. Although I can unlock, the drives are still in the "files" folder and therefore can be called on by going to "computer", than "home", giving access to any file in the drive.
Without giving reason, does someone know how to disable or hide this occurring feature?

---

### Post by grahammechanical on 2016-05-30
> giving access to any file in the drive.

How many users do you have on that system? We can change Permissions on the folders & files on drives and even on the drive itself. If you are the only user you may lock yourself out of those drives.

We usually need to be Administrator or Root to create folders on other drives. And that will limit the ability to Create & Delete files to when we are working as Root. So, we change permissions or ownership to allow others in the Group or all others to have more than just access. Otherwise any program will run will not be able to save to those folders & files.

Regards.

---

### Post by rainerw2 on 2016-05-31
Hi Graham the Mechanic
Sorry for the delay, had not expected such swift reply. Will be more alert next time.

There are 3 users per computer. It is the intention to log-in individually with no party being able to intrude on the alternative drive of another. Each individual will understandable be locked out of the alternative drives and be restricted to the drive on which he/she boots up. As all OS's are 'the brilliance of ubuntu', it occurs, as previously said, that alternative drives appear in the "files folder", making it possible to log in to the other drive and "snooping" on another's files without restrictions. As you will find, this way around there is no pass protection. 
(It may seem I/we are paranoid and trust no one?! - True!)
I hoped that I would find some folder in usr/share/etc. as I also attempted to get rid of the "Disks" App which is another bone of contention as anyone can from that application call on any drive and tamper with its partitions and content in turn.
Have attempted all the "out of the box thinking", failing miserable and destructively in the process. (No programming skill here!)
Any suggestion is welcome.

---

### Post by ajgreeny on 2016-05-31
How many of those three users have admin permissions and can use sudo to raise their permissions to root?
What filesystem are those "other" disks formatted to?  If they are in a linux filesystem such as ext4 it is possible to give them permissions which make them unreadable by anyone except the "owner" of the disk, but anyone who has the ability to use root permissions, ie sudo, will be able to read anything anywhere.

With regard to the disks application, you will find that only users in the admin/sudo group will be able to use it to change partitions or act on the disk, so my comment above about the other users and their admin privileges is also relevant  for this query.

---

### Post by rainerw2 on 2016-05-31
Would have liked to answer more promptly but traffic between Cape Town and Strand took 2 hours for 40 km - and that in Africa. 
Hi ajgreeny
All users on one computer have admin privileges and can use sudo commands. This said, it must be noted that a user is locking in to his very own harddrive and his very own ubuntu OS.
I am not looking for a solution to secure the harddrive or OS of each individual as this is achieved by a password on lock in to each program.

It is the oddity and possibility, of anyone that is on his program, to simply go to "Files"/"Computer"/"Home"/"Desktop" or "Documents" to enter anyone else's program, and thus all the users files.

What I envisaged is a means of all 2 or 3 harddrives to be invisible to each and every user. It would not alone help to make the HDD secure to not been visible. I attempted some protection in the BIOS. This however fails as all three users lock in via the same motherboard and CPU. They are not at the same time on the computer.

I established that even the installation DVD will show all drives and make it possible to intrude on these drives and the directories, files and folders on them - no password needed.

This is not an ubuntu flaw or a all to serious issue. If it could be solved however, it would be an extreme peace of mind for me. I could explain in more detail why it is important, but this would just inflate the subject.

Any wizards out there??[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

There are still elements in our Uinverse that defy logic.

---

### Post by ajgreeny on 2016-05-31
I understand, I hope, what you are trying to do which is to either remove the icons for the disks from the Places menu in the left hand pane of the file-manager or to completely remove access to those disks other than the OS "owned" by a particular user.

There may well be a way to do this with more knowledge than I have, but as far as I'm aware it is not going to be simple, as all separate disks show in that pane in all the file managers that I know of, and if the users of the OS in each disk has root permissions avaiklable in that OS, I do not think it will be possible to remove the ability of each user to do whatever he wants with any disk attached to the machine.

I hope I'm wrong, but I think with the ability of each user to raise their permissions to root, there is not a lot you can do to stop them if they wish to look at anything on any disk.

---

### Post by rainerw2 on 2016-05-31
Hi ajgreeny, I do agree with your assumption. The inherent functionality is obviously set to allow a user, once signed in, to 'walk' through all the directories, folders and files. I believe that this is a serious flaw in the run of things. As mentioned, I was able to boot up on another notebook with ubuntu's installation disk  and subsequently bypass the pass code of the units user and get on to her files (in her presents) , so to speak, via the back door.
My colleagues and I will make still some attempts to tweak the system, and should we succeed, I will post it in due time. Lets consider the subject closed/solved.
Thank you and "grahammechanical" for your concern and dimensional thinking. 
Kind Regards, Rainer.

---

### Post by ajgreeny on 2016-06-01
If you think this is really solved for you please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by rainerw2 on 2016-06-01
My sincerest expression of appreciation once more. Have only used the forum once before in spite of solely operating on ubuntu for years and hence my illiteracy regarding the forums function. Have declared it as "solved" as I hate to waste good time of others. As said, will still keep attending to it as time and sensible effort allows. Regards

---

