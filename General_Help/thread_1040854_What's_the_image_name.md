---
title: "What's the image name?"
date: 2009-01-15
forum: General Help
---

### Post by winrowc on 2009-01-15
I am trying to recover a file on a hard drive that I desperately need with Autopsy and Sleuth kit. It says to put down the location of the image. [The add a new image section here]("http://www.sleuthkit.org/autopsy/help/index.html"). So I put in /media/disk but it doesn't work. How can I find the image file? /media/disk is the mount point, and all the files in it have /media/disk in their file structure, but putting things like /media/disk.* or things like that just adding .* to the end doesnt work., theres no image found. I've tried things like /sdb1 too, but that hasn't been working. So how can I find the image name of my slave hard drive, if its not what the file structure says it is?

---

### Post by utnubuuser on 2009-01-16
have you tried with just the "locate" comand?  Maybe do a "man locate" for arguments.
And though I've never used it, "grep" is another one that might help.

---

### Post by niteshifter on 2009-01-16
Hi,

I think you've the wrong tool here - Autopsy is meant for LEO's performing forensics work. The #1 rule in this field is You Cannot Touch The Evidence. Therefore a bit-for-bit copy of the drive is made before any analysis is performed. This copy is the image Autopsy is referring to.

Try testdisk / photorec instead. testdisk is in the repositories and includes photorec and documentation for both programs.

---

### Post by winrowc on 2009-01-17
Testdisk/photorec seemed to have worked very effectively, as I can see that I have restored my deleted files, but there was a problem. I wanted to recover a.vdi file, a virtualbox windows hard drive. So right now I have a hundred something locked folders on my desktop called recup_dir.##. In each one the file names are all f######, and they are all completely random. Is there anyway to make sense of this all. I physically have all the data back, but its all in separate locked folders that vary in size, and completely random. Is this tool only good if you are looking for one file? How could you ever find it, if you have 16,000 files in over a hundred different folders? Am I missing something, or is this the reality of data recovery?

---

### Post by niteshifter on 2009-01-17
Hi,

I should have mentioned that testdisk/photorec works best for "understood" file formats, notably the common ones of jpg, mpg, avi, pdf, etc. For non-mainsteam files - like VirtualBox' .vdi files: You're on your own. 

Some googling about doesn't give much info on this format. You could get the source for the OSE edition (and hope OSE and PUEL do vdi the same) and start with that. Methinks this would be a long term project.

IOW, brother: I think you're hosed here.

---

