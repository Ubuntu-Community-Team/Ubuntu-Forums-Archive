---
title: "Jaunty Data Loss Warning"
date: 2009-05-16
forum: General Help
---

### Post by Xyem on 2009-05-16
Okay, Jaunty has really dropped the ball here.

I accessed another PC using 'Connect to Server..' and SSH, and started moving a folder over to the local machine.

The file transfer died prematurely ( I wasn't watching it ) and the ENTIRE DIRECTORY ON THE REMOTE MACHINE WAS DELETED. Damn.

I don't trust Jaunty ( maybe gvfs/Nautilus more specifically ) with my files anymore as this isn't the first time it has screwed it up, resulting in lost data.

Just posting it here as a warning. In the meantime I'm not sure whether to do a minimal install, stay with Intrepid or move to another distro entirely as Jaunty has just been a nose-dive in terms of Ubuntu experience.

---

### Post by paradigm2 on 2009-05-16
> **Xyem said:**
> Okay, Jaunty has really dropped the ball here.

I accessed another PC using 'Connect to Server..' and SSH, and started moving a folder over to the local machine.

The file transfer died prematurely ( I wasn't watching it ) and the ENTIRE DIRECTORY ON THE REMOTE MACHINE WAS DELETED. Damn.

I don't trust Jaunty ( maybe gvfs/Nautilus more specifically ) with my files anymore as this isn't the first time it has screwed it up, resulting in lost data.

Just posting it here as a warning. In the meantime I'm not sure whether to do a minimal install, stay with Intrepid or move to another distro entirely as Jaunty has just been a nose-dive in terms of Ubuntu experience.

How exactly did you do the transfer.  I don't get it.  Did you use sshfs?  Scp?  No probably samba?

Anyway using move as opposed to copy over a network file system is a bad idea in general.  It's safer to use copy, verify that it all was copied correctly, THEN delete the old copy.

I'm not saying it isn't a bug or wrong, but you took a risk because many more things could have gone wrong.

---

### Post by lovinglinux on 2009-05-16
> **paradigm2 said:**
> Anyway using move as opposed to copy over a network file system is a bad idea in general.  It's safer to use copy, verify that it all was copied correctly, THEN delete the old copy.

I'm not saying it isn't a bug or wrong, but you took a risk because many more things could have gone wrong.

I agree.

Which distro were running on each side? I think the problem is on the remote machine. Even when you move the files instead of copying them, the local copies are not deleted if the transfer is not fully completed. So I think the files were deleted after the transfer.

---

### Post by Xyem on 2009-05-16
I mounted the other machine using the SSH option of 'Connect to Server' in Nautilus. Just the standard cut and paste of a directory.

I have ( freshly installed and updated ) Jaunty running locally and Intrepid running remotely. The transfer didn't complete ( I was left with a zip file of 2.6mb instead of >100mb ) but the entire directory it was in was removed on the remote machine anyway, despite an incomplete transfer.

Jaunty has given me loads of problems, especially in regards to Nautilus crashing ( and then not being restarted ).

I don't think it is a problem with the remote machine because I have done this a lot when I had Intrepid installed locally and didn't have any issues at all. It has only cropped up since I started using Jaunty.

---

### Post by lovinglinux on 2009-05-16
> **Xyem said:**
> I have ( freshly installed and updated ) Jaunty running locally and Intrepid running remotely. The transfer didn't complete ( I was left with a zip file of 2.6mb instead of >100mb ) but the entire directory it was in was removed on the remote machine anyway, despite an incomplete transfer.

So, I think the problem was in the [color=#33CC00]**remote machine**[/color] (Intrepid). It shouldn't delete the directory if the files weren't completely transferred to the [color=#FF0000]**local machine**[/color] (Jaunty), unless the [color=#FF0000]**local machine**[/color] (Jaunty) considered the file transfer to be completed, but didn't saved it properly.

Well, I do a lot of sshfs transfers between two computers on the same local network. The source machine is running Jaunty and the destination machine is running Intrepid. I never had a single problem. When I was running Hardy on the source machine I had a lot of issues with Nautilus crashing, but the original files weren't deleted when the transfer was interrupted by the crash. Since I installed Jaunty from fresh I didn't have a single Nautilus crash. I usually transfer files with 200 Mb to 1.5 Gb.

---

### Post by Xyem on 2009-05-16
I don't see why the conclusion that the remote system is at fault was so rapid to come to. I didn't have *any issues for months* when both machines were running Intrepid, it has only arisen when Jaunty was introduced.

GNOME uses gvfs, not sshfs, for remote SSH mounts which, guessing by the protocol, uses SFTP in the background. Seeing as there is no "move" command in SFTP that I know of, the "get" action must have died/been canceled/aborted but gvfs went ahead and issued the "delete directory" command regardless. That is my immediate line of thought anyway..

The remote machine wouldn't have any idea that it shouldn't remove the directory therefore the local machine, therefore Jaunty, would be the one at fault.

Or do you know something I don't?

---

### Post by lovinglinux on 2009-05-16
> **Xyem said:**
> I don't see why the conclusion that the remote system is at fault was so rapid to come to. I didn't have *any issues for months* when both machines were running Intrepid, it has only arisen when Jaunty was introduced.

GNOME uses gvfs, not sshfs, for remote SSH mounts which, guessing by the protocol, uses SFTP in the background. Seeing as there is no "move" command in SFTP that I know of, the "get" action must have died/been canceled/aborted but gvfs went ahead and issued the "delete directory" command regardless. That is my immediate line of thought anyway..

The remote machine wouldn't have any idea that it shouldn't remove the directory therefore the local machine, therefore Jaunty, would be the one at fault.

Or do you know something I don't?

I don't know the technical aspects behind this situation. I'm just guessing actually. I'm still happy with Jaunty and I have less issues than with Hardy.

I just think the thread title and warning is too harsh on Jaunty. There is no proof that it was the culprit, this type of data loss could happen on any distro and it could be avoided. Besides, is not like a huge data loss due to an ext4 partition going nuts. You just lost a file being moved trough the network. Nothing really surprising about that.

Please don't take this personally. Is just my opinion. ;)

---

### Post by Xyem on 2009-05-17
> Please don't take this personally. Is just my opinion.
I'm not taking it personally and I appreciate you sharing your opinion. I guess I'm just struggling to understand how you come to point fingers at something that has worked for months instead of the variable that changed..

> I just think the thread title and warning is too harsh on Jaunty. It's just a warning and it only starting happening since I installed Jaunty. I think it is pretty appropriate.

> There is no proof that it was the culprit, this type of data loss could happen on any distro and it could be avoided. Yes, by fixing the code.

> Besides, is not like a huge data loss due to an ext4 partition going nuts. You just lost a file being moved trough the network. Nothing really surprising about that. What if I was transferring a ~30GB /home directory and it died 100mb in and then proceeded to remove the other 30GB of personal data? *That would be significant data loss* and I'm fairly sure anyone would be surprised to find that out. Especially seeing as it *shouldn't do that*.

Anyway, this should serve as a warning at least, so others may know to be careful when using gvfs to transfer files or that they are not alone if they experience this issue. Here is to hoping I am the only one.

---

### Post by M0nk3Ee on 2009-05-17
Just reporting that i am having similar issues.  I havn't suffered data loss yet but nautilus does crash quite regularly when transferring large files (700meg) through ssh. It halts the files transfer, closes the nautilus windows, then the desktop icons disappear.  

I don't think this used to happen on intrepid.  Both computers are running jaunty and both were upgraded as appose to fresh installs, don't know if that makes a difference.

it doesn't seem to crash when transferring the same files through the wired connection instead of the wireless on my laptop however that could be that it is copying for less time because the connection is quicker.

Any thoughts?

---

### Post by Xyem on 2009-05-17
I suggest try using sshfs if you are okay with dropping to the command line. If it works, that'll indicate that you are experiencing a gvfs/nautilus issue, not sftp/scp/ssh.

---

