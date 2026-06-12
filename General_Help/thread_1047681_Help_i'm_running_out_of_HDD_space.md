---
title: "Help i'm running out of HDD space"
date: 2009-01-22
forum: General Help
---

### Post by 2j4ez on 2009-01-22
Ok here goes

Ive done a copy of several home movies. My laptop only has 1DVD burner so ubuntu made a image of the disc.

Where are these stored? i want to delete them and get some of my space on my hdd back

I searched for .img and iso but nothing 

please help thanks

---

### Post by vandorjw on 2009-01-22
If you don't know what the file is called, then I recommand to you to open "Disk Usage Analyzer" and scan the entire filesystem.

It will graphically represent your Hard Drive.

this should help you easily find what is taking all the space. (Since large files get a larger portion of the graph.

once you found it, remove it if you are sure you don't need it.

---

### Post by Coreigh on 2009-01-22
I *think* the images are stored in a folder in your home folder. What did you use to do the copying with? Look for a folder by the program name that is inside your home folder. It will likely be a hidden folder so you will have to make hidden folders visible. 
Command line is ```
ls -al
```

---

### Post by unutbu on 2009-01-22
The file is probably in your home directory. The command
```
find ~ -type f -mmin -60 -print
```
will print the name of all files in your home directory that have been modified in the last 60 minutes.

If it isn't in your home directory, you could try
```
sudo find / -type f -mmin -60 -print
```
This command will search your entire hard drive. You'll have to recognize the name of the file. Hopefully that will be pretty obvious. This command may take 10--15 minutes, depending on the size of your hard drive.

---

### Post by drs305 on 2009-01-22
You can run this command to search your entire system (anything mounted) for files larger than 1GB:
```

sudo find / -size +1G  # 1 GB
sudo find / -size +500M  # 500MB

```

Don't forget to empty your trash (or root's) if you don't use "rm" or SHIFT-DELETE to delete the files.

---

### Post by jimv on 2009-01-22
The files are in /tmp and end with .toc

---

### Post by 2j4ez on 2009-01-23
they seem to be only temp files just turned it on and my hdd space has gone back back down thanks for your help

---

