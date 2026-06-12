---
title: "Ubuntu Jaunty Trash Can is broken!"
date: 2009-05-12
forum: Desktop Environments
---

### Post by Dave_Jackson on 2009-05-12
I just installed Ubuntu Jaunty 64 bit edition on my laptop today and it works fairly well with the exception of one thing. The trash can function in GNOME is completely broken by default. When you delete something, it does NOT move it to the trash can at all. It just deletes it straight away without any warning whatsoever! And no, I do not have that box checked in the Nautilus preferences telling it to do that. Therefore, it should ask me before irrevocably deleting a file. 

This happens on local files on my hard disk, not just on removable USB media. I know the confirmation to move files to the trash can is broken in GNOME (supposedly because it's a "feature") ,but I would at least like my files to go to the trash can so I can change my mind as to whether I would really like to permanently delete them. The files aren't even making it to the trash can to give me that option. 

This behavior is DANGEROUS beyond words. All someone has to do is accidentally hit the delete key on the keyboard and their file is gone permanently because it completely bypasses the trashcan without confirmation of any kind. This is unacceptable, to say the least.

Just don't tell me this is a "feature" or a "gnome-thing". I've used gnome for the last six months everyday on Fedora 10 and it would always move files to the trash can for my perusal and then only permanently delete them with my confirmation.  

I had many problems with ubuntu 8.10 and tried 9.04 today. With the exception of this trash problem, I would stick with 9.04. But if this isn't fixed very soon, I won't hesitate to switch to Fedora 11 when it comes out. As raw as Fedora sometimes is, they typically don't screw up such basic things.  

I am a full time college student who writes many research papers and if accidental deletion is this easy, then I'm just NOT willing to take that risk by using Ubuntu.

---

### Post by guzz20 on 2009-05-20
> **Dave_Jackson said:**
> I just installed Ubuntu Jaunty 64 bit edition on my laptop today and it works fairly well with the exception of one thing. The trash can function in GNOME is completely broken by default. When you delete something, it does NOT move it to the trash can at all. It just deletes it straight away without any warning whatsoever! And no, I do not have that box checked in the Nautilus preferences telling it to do that. Therefore, it should ask me before irrevocably deleting a file. 

This happens on local files on my hard disk, not just on removable USB media. I know the confirmation to move files to the trash can is broken in GNOME (supposedly because it's a "feature") ,but I would at least like my files to go to the trash can so I can change my mind as to whether I would really like to permanently delete them. The files aren't even making it to the trash can to give me that option. 

This behavior is DANGEROUS beyond words. All someone has to do is accidentally hit the delete key on the keyboard and their file is gone permanently because it completely bypasses the trashcan without confirmation of any kind. This is unacceptable, to say the least.

Just don't tell me this is a "feature" or a "gnome-thing". I've used gnome for the last six months everyday on Fedora 10 and it would always move files to the trash can for my perusal and then only permanently delete them with my confirmation.  

I had many problems with ubuntu 8.10 and tried 9.04 today. With the exception of this trash problem, I would stick with 9.04. But if this isn't fixed very soon, I won't hesitate to switch to Fedora 11 when it comes out. As raw as Fedora sometimes is, they typically don't screw up such basic things.  

I am a full time college student who writes many research papers and if accidental deletion is this easy, then I'm just NOT willing to take that risk by using Ubuntu.

I have the same problem, but i found all the deleted files at /home/USERNAME/.local/share/Trash/files but still haven't found any solution.

---

### Post by guzz20 on 2009-05-20
I found the solution, just updated my system and restart :p

---

### Post by Dave_Jackson on 2009-05-25
So a simple update now solves the problem? Thanks for letting me know, guzz20. It's great news that they have addressed this. I'll reinstall and update and see if it's fixed. I just hope they pay more attention to such release critical problems in the future. Other than this trash thing, Jaunty was generally a good experience.

---

### Post by Dave_Jackson on 2009-05-25
So I reinstalled Jaunty, applied all available updates, and restarted the computer. The trash can is still broken. I deleted some files to test it and those files only went to /home/USERNAME/.local/share/Trash/files, not to the actual trash can. So I guess I can just delete/restore files from there, even though that's not really where those files should be. So as it stands now, the problem still exist. This is very strange. Could it be some kind of problem with symbolic links or something? I'm using the encrypted home directory option on an encrypted disk, if that makes a difference. If anyone else has any other insight on this, please share it.

---

### Post by Dave_Jackson on 2009-05-25
I finally solved the issue. As Guzz20 said, it can be solved by way of a simple update. What he forgot to mention was that the Pre-released Updates and Unsupported Updates repositories (don't know which one the patch came from) need to be enabled. This is because the patch is not yet in the standard update repo for some reason. To enable these extra update repos, open the synaptic package manager, click Settings|Repositories, click the Updates tab, and check Pre-released updates and Unsupported updates. Click Close, reload the repos, click Mark All Upgrades, and click Apply. After the updates are installed, simply reboot the system and the trash problem will be solved. Hopefully this helps anyone else having the same problem and hopefully the ubuntu team puts this patch in the standard update repo soon.

---

### Post by asmoore82 on 2009-05-25
If the problem is in your preferences and you always keep the same home partition untouched,
a re-install or update can't fix it.

I'm using a /home partition from 8.04 on a fresh install and complete update of 9.04 final beta.
I never actually use the trash can but I just tested it and it's working for me.

Have you already checked the "Behavior" Tab in Nautilus "File Browser" "Edit -> Preferences" ?

EDIT: late to the party,
So I wonder is the bug specific to ext4 and/or encrypted data?

---

### Post by kickwin on 2009-06-22
Thanks Dave. You solution worked for me as well.

---

### Post by Goombie on 2009-07-03
In most cases, the location of your trash can is actually /home/username/.local/Trash/files. The trash:// syntax is just a link to that location. One way around this is to make sure that you don't have any hidden folders named .Trash-1000 on your other partitions. If those folders exist, Ubuntu will automatically move files deleted from that partition to that folder, instead of the default /home/username/.local/Trash/files folder.

---

### Post by dkolars on 2009-09-02
Well, did all that ~except~ re-install Jaunty (last resort for me)... still no go...  Copied a file and re-named it to xxx.jpg...  did a search using "Places - Search for Files" (VERY FAST), and "File Browser" (VERY SLOW)...  file is totally gone from my system.

So, will, for now, move unwanted files to new sub-dir... Hey, I'll use the one named .Trash... no one else is using it... and then delete when I feel like it!!  Too busy to devote the time for the "correct" fix just now...

Thanks... dk

---

