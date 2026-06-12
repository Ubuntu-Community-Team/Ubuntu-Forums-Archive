---
title: "Did I loose my files?"
date: 2009-03-23
forum: General Help
---

### Post by kiprit on 2009-03-23
First of all, my apologies if this is an already solved problem but I am reading everything I can since two days but I couldn't find the solution. 

So here is my problem:
I am running on Ubuntu Intrepid 8.10... The other day I had a problem deleting a folder in my Trash, so i went to the trash folder and used the  command sudo rm -Rf ... to empty it. After a flow of letters telling me that the files in the trash cannot be deleted, the terminal got stuck at a line and my system crashed.

After I made a force restart I first had a grub error, I decided to fix grub using live cd but then I realized that it is not just the boot folder but almost all my data is missing.

I was thinking to attempt to recover data using testdisk. But I noticed something. When I start with Live CD and check the properties of my ubuntu partititon it shows that 3.5 GB is used... this is exactly the size before the crash. However when I select all the files that I can see, enable show hidden files and check the size, it is 319MB.

So the question may be so simple and overly stupid, but where is my data? Is it deleted? Or simply did it become so invisible that I cannot see  with live cd... if this is the case, is there a way to reveal it?

I'll appreciate so much if someone can help me solve this...

---

### Post by sudo make sandwich on 2009-03-23
Do you remember the exact path of where you were when you typed that command? And the exact command you typed?

Bear in mind that it's a mighty powerful command in Linux and you want to be *very* sure you about to do exactly what you mean to before you press that enter key. The -f flag in particular.

If it was your own trash you were trying to cull, it's unlikely you should have needed to use sudo at all. Did you get a permission error first to make you try the command with the sudo prefix?

Listening to the symptoms, it does sound like you've deleted more than you should; there's no way you should be affecting the actual operating system orgrub if you executed that command from within /home.

---

### Post by kiprit on 2009-03-23
Thanks for the quick reply,

I am pretty much sure that I did type the command from /.local/share/Trash/ folder. 
I needed the sudo command because the file in the trash wouldn't be deleted with right click 'empty trash'. My stupidity was  that I was doing 28 things at the same time and didn't remember the empty trash command and googled it... and copy and paste the top answer without thinking so much about it....

Is it possible that my files are there and I cannot access them from the live CD?

---

### Post by s.dalas on 2009-03-23
i think "sudo" is right.
When you are in terminal from home you can't do anything to crash the sysytem. when you try to do anything more from what you have privileges to do it always asks for a sudo command. 
Remember the exact path you typed before you put the rm command.
It sounds that you deleted almost everything...

---

### Post by s.dalas on 2009-03-23
> **kiprit said:**
> 
Is it possible that my files are there and I cannot access them from the live CD?

With the 350mb used space that you mention above there is no chance off being there. But wait and for someone with more experience to have his opinion. Otherwise reinstall from live cd and don't format the drive.

---

### Post by kiprit on 2009-03-23
Thanks for the help anyway. 
One last thing though, can you have any guess of how I can have 3.5GB used space when i check the properties of the drive and 350MB when i check the files that I can access.

---

### Post by s.dalas on 2009-03-23
> **kiprit said:**
> Thanks for the help anyway. 
One last thing though, can you have any guess of how I can have 3.5GB used space when i check the properties of the drive and 350MB when i check the files that I can access.

Oops i didn't understand this!! Of what you said right now only one think comes in my mind. You have all of your files there, and the 350MB of access files are the "user files" and the rest are root files. I cant think of something else. Why you don't reinstall from live cd without formating?? Maybe something with the users priveleges broken. 

(I have to go out for a job. I'll be back in about an hour and i hope that you have find the solution since then. I'll check again when i come back)

---

### Post by kiprit on 2009-03-23
Thanks again man...

I will try to see to play with user privileges. I am keeping the reinstallation as a last option. Because if i have really deleted some of my files, i should avoid putting anything to my hard disk because this will reduce my chances of recovery.

Thanks for the suggestion this may save my life...

---

### Post by s.dalas on 2009-03-23
Have you done anything?

---

### Post by kiprit on 2009-03-23
File permissions did not work, I am trying to recover some of my deleted files... and it is taking long. after that i will reinstall and see what happens...

---

### Post by hyper_ch on 2009-03-23
you have no backup?

---

### Post by kiprit on 2009-03-23
I have a backup for most of my things...
But my I had not backed up my emails for a week or so... and i need to save them... I had finally organized my firefox bookmarks :) a couple of hours before the crash. These two are basically what i need. the rest... I have backed up.

---

### Post by hyper_ch on 2009-03-23
implementing automatic regular backups is IMHO a must...

---

### Post by kiprit on 2009-03-23
learned my lesson...

---

### Post by hyper_ch on 2009-03-23
there are some recovery tools... search the forums for it.... maybe they can help getting data back.

---

### Post by kiprit on 2009-03-23
yes i am trying them...

thanks!

---

