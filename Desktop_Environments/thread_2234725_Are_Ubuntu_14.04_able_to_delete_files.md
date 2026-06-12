---
title: "Are Ubuntu 14.04 able to delete files ???"
date: 2014-07-16
forum: Desktop Environments
---

### Post by tiana2 on 2014-07-16
I have a folder with ~20000 files, the files are small size ~7kb. I select all and click move to trash, and my computer freezing, process named nautilus eating all of my pc resources 2GHz CPU and 3GB RAM. What i have to do to fix this stupid problem

Win 7 is able to do this for less than 2 min on the same machine.

---

### Post by ubudog on 2014-07-16
This is probably happening because you're moving so many files to the Trash at once, and not deleting them.  If you want to **permanently** delete them, click once on the folder in nautilus, and press Shift+Delete.

---

### Post by tiana2 on 2014-07-16
the same situation, delete only 40-60 files and freezing again, and computer is absolutely unusable until i restart it or BIOS automatic restart it for CPU overheating.

---

### Post by oldos2er on 2014-07-16
You mention Windows, are the files on an NTFS partition? I'd think deleting the folder (instead of all the files in the folder) from terminal may be fastest.

---

### Post by mooreted on 2014-07-16
Lets say I have a folder named Utopic_Unicorns with thousands of files and I wanted to remove all those files. I would simply open a command prompt and type:

rm -rf Utopic_Unicorns 

If I wanted to keep the folder and just delete the files I would do:

cd Utopic_Unicorns 
rm *

BE CAREFUL! If you don't use "rm -rf" or "rm *" correctly you can delete everything on your hard drive. However, when used properly it's much easier than using a file manager and a lot faster. In general the command line tends to be quicker and easier than a GUI.

---

### Post by at_first_light on 2014-07-16
Using the rm command in the terminal might help avoid freezing. 

Manpage for rm = [http://manpages.ubuntu.com/manpages/trusty/en/man1/rm.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/rm.1.html)

---

### Post by ian-weisser on 2014-07-17
> **tiana2 said:**
> What i have to do to fix this stupid problem

You have to report the bug to Nautilus developers so they can reproduce it.
Then they can fix it.

---

### Post by yancek on 2014-07-17
I think this would more likely come under the classification of a 'pebkac; error than a bug.  The OP states a desire to delete and moving to Trahs isn't deleting and there is minimal information.

---

### Post by 3rdalbum on 2014-07-18
While I agree that Nautilus shouldn't hang while performing operations on even a massive number of files, the best way to delete 20,000 files is to use the terminal. It will be quicker than the GUI.

You mentioned that you were able to use Windows 7 to delete the files; is this hard disk formatted as NTFS? If so, then that's probably part of your problem. Writing to NTFS filesystems is slow and CPU-bound on Linux due to it being a non-native filesystem.

---

### Post by tiana2 on 2014-07-18
The file system is EXT, variant with WIN 7 is not a option, because i don't have win on this machine any more. Variant with terminal is not a good option. I think something about different file explorer, can you help me with this??

---

### Post by 3rdalbum on 2014-07-19
> **tiana2 said:**
> The file system is EXT, variant with WIN 7 is not a option, because i don't have win on this machine any more. Variant with terminal is not a good option. I think something about different file explorer, can you help me with this??

Try installing Rox Filer or Thunar.

Why isn't using the terminal an option for this? Why have you got 20,000 tiny files into a single folder anyway? And if they are all in the one folder, why not just delete the folder and recreate it (if needed)?

I'm afraid I don't know why you would need to regularly delete 20,000 files from a folder; it sounds like you might be doing something wrong in the first place.

---

### Post by buzzingrobot on 2014-07-20
As a guess, perhaps Nautilus does some buffering and 20,000 files puts it over the edge.

Also don't understand why using  'rm' isn't the answer.

Does 'EXT" mean the original EXT Linux filesystem created about 20 years ago?

---

