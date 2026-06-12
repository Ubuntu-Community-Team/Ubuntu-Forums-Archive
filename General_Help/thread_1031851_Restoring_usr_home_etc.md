---
title: "Restoring /usr /home /etc"
date: 2009-01-05
forum: General Help
---

### Post by Miikee on 2009-01-05
A while ago my hard drive went bad.  I have been able to tar my old /home /usr and /etc folders and save them to a flash drive.

I saved each of these folders because previously I had to write several fixes to the files inside these folders to get Ubuntu working how I wanted it to on my computer.

Now I have reinstalled Ubuntu on a clean hard drive, and I want to get Ubuntu running how it use to before the hard drive went bad.

Will just overwriting the newly installed folders with my backed up folders work?  Will this restore the old Ubuntu?

When I try to overwrite /home or /usr, it tells me the device is in use (due to me being logged on as the user I'm trying to overwrite in /home, having the terminal open, or running the gui).... how do I prevent these errors?  Will it work if I am logged in as root in a TTY?

Or am I going to have to start completely from scratch?

I have been working on this for a long time, Any help or suggestions is greatly appreciated.  Thank you

---

### Post by mike2357 on 2009-01-05
I suggest you look at the --strip option of tar.  By using it, you can still extract from your tar files, and have the extracted files go somewhere other than /usr, /etc, etc.  Then, you can pick and choose the files you want to copy to the live versions.

Run, "man tar" for details.

I haven't tested the command but something like this may work:
cd some_temporary_directory
tar --strip 1 xvf tar_file

Incidentally, an experienced UNIX systems administrator once told me to avoid using absolute path names when creating tar files.  Better to use the command "cd /; tar cvf tar_file home" than "tar cvf tar_file /home".  The reason is that you have more flexibility if you want to restore.  Fortunately, the version of tar that comes with Ubuntu has the --strip option.

---

### Post by heindsight on 2009-01-05
If you have a live cd, you could boot from that, mount your hard drive and then copy everything from the backup. /etc and /home shouldn't give you any problems. 

restoring /usr may lead to interesting situations though. you'll most likely have problems unless you first install all the packages that you used to have installed: some programs may depend on the existence of files which you haven't backed up and you probably want the package manager to have a record of those packages being installed otherwise you'll run into problems later eg. if you want to remove software.

Finally, everything will probably not be exactly the way it was before. Many programs keep data under /var and since you didn't back that up some things will probably not be quite the same (as a simple example, many games keep high score lists in /var/games so you'll have lost all of those...)

---

### Post by Miikee on 2009-01-05
Yup /var was the other one that I was trying to make room for on the flash drive but skipped it.  I think it maybe best just to start completely fresh with the installation instead of trying to always work with a screwed up installation.  So I will just start fresh and maybe copy some of the backedup files with --strip as needed.

However, in the future, how can I easily prevent this from happening?  What is the best way to back up everything (including settings, installed programs, etc.)?  And how do I restore these afterwards?

Thank you for the help.

---

### Post by logos34 on 2009-01-05
> **Miikee said:**
> 
However, in the future, how can I easily prevent this from happening?  What is the best way to back up everything (including settings, installed programs, etc.)?  And how do I restore these afterwards?


I have a separate /home partition.  I simply use partimage to make a .gz or .bz2 image of / once a week, and backup /home to .tgz archive. I find it very easy

You could even backup /var/cache/apt/archives to AptOnCD cd/dvd

---

