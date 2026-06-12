---
title: "Good practice for backup / restore data?"
date: 2009-01-18
forum: General Help
---

### Post by UranUtan on 2009-01-18
Hi,

I am testing / playing / learning Ubuntu 8.10. Made settings in systems, configured desktop, made network config change, create some application data, etc.

Then I have a better machine, I install Ubuntu again and I would like to replicate as much as possible the working environment I had with the previous machine.

I think that a backup / restore procedure would be appropriate. What is the good practice that you would recommend?

In the Windows world, I use these approaches:

1. Image the entire hard drive. I use this method to backup a stable working and clean machine.

2. Backup the "User Data" folder where I store all my data. This approach is 100% manual. I just compress the folder using 7-Zip.

3. Application / System settings: I know where those settings are stored. There are about a dozen of them that I care about. I compress each of these config setings folder and just store them in my "User Data" folder. Of course, the restore will be entirely manual.

BTW, in Windows, I use 7Zip as my compression tool (file format *.7z). Is it supported in Ubuntu and, actually, what is the recommended compression format in Ubuntu?

Thanks in advance for any help.

---

### Post by cdtech on 2009-01-18
You could use "[[COLOR="DarkRed"]partimage[/COLOR]]("http://www.psychocats.net/ubuntu/partimage")" or you could do it the hard way and clone the package list:
```
dpkg --get-selections > package.list
```
Then on the new setup:
```
dpkg --set-selections < package.list
```
Then do a (on the new setup):
```
dselect
```
You'll need your /home partition along with your /etc (configurations). And maybe someone else could suggest other configs to move over as well........

---

### Post by adamlau on 2009-01-18
Take a look at HUBackup for something simple, CloneZilla for partition imaging.

---

