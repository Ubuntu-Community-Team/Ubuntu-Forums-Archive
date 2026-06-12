---
title: "file permission issues"
date: 2009-01-27
forum: General Help
---

### Post by Gebastram on 2009-01-27
Hi, I'm a Web Designer currently working for my dad ([www.fxeng.com](www.fxeng.com)).
I got a new computer recently and switched to ubuntu.

I need to update the web site but I can't because I can't get permission to save the files.

My dad downloaded the files from the website and put them on a CD.
I copied the folder with the files to my Home directory and then I used Screem HTML editor to update the files but when I try to save them it says, 

"Failed to save [file_name]
Access Denied"
](*,)

Any help on how I can fix the problem? Thanks!

---

### Post by dcstar on 2009-01-27
> **Gebastram said:**
> Hi, I'm a Web Designer currently working for my dad ([www.fxeng.com](www.fxeng.com)).
I got a new computer recently and switched to ubuntu.

I need to update the web site but I can't because I can't get permission to save the files.

My dad downloaded the files from the website and put them on a CD.
I copied the folder with the files to my Home directory and then I used Screem HTML editor to update the files but when I try to save them it says, 

"Failed to save [file_name]
Access Denied"
](*,)

Any help on how I can fix the problem? Thanks!

This will give you access to change the ownership to whatever:

```
gksudo nautilus
```

---

### Post by cdtech on 2009-01-27
Which type of web server are you using? Is this something you set up yourself? Is this an Apache server?

This could help solve the issue.......

---

### Post by carolinason on 2009-01-27
Take ownership of the folder that you copied with the code below, then you'll be able to edit the files.```
sudo chown -R yourusername:yourusername /home/yourusername/directory_you_copied
```

---

### Post by Gebastram on 2009-01-27
> **carolinason said:**
> Take ownership of the folder that you copied with the code below, then you'll be able to edit the files.```
sudo chown -R yourusername:yourusername /home/yourusername/directory_you_copied
```

Nothing Happened

sebastian@Dino:~$ sudo chown -R sebastian:sebastian fxeng.com
[sudo] password for sebastian: 
sebastian@Dino:~$ 

I tried editing files after that still nothing
(fxeng.com is the name of the directory)


the web server is GoDaddy

---

### Post by jerome1232 on 2009-01-27
I know when I copy files off a cd they retain the read-only permissions.

What are the permissions currently on these files?

```
ls -l /path/to/files
```

My *guess* is you simply need to remove the read only flag

```
chmod -R ug+w /path/to/files/
```

---

### Post by Gebastram on 2009-01-27
sebastian@Dino:~$ sudo chown -R sebastian:sebastian /home/sebastian/fxeng.com
sebastian@Dino:~$ 

still didnt work...

should i do this under su?

---

### Post by Gebastram on 2009-01-27
sebastian@Dino:~$ ls -l /home/sebastian/fxeng.com
total 51140
-r-xr-xr-x 1 sebastian sebastian      612 2008-09-15 23:40 ContactUs.html
-r-xr-xr-x 1 sebastian sebastian   875084 2008-09-15 23:40 Corkey_tiles.jpg
-r-xr-xr-x 1 sebastian sebastian     4122 2008-09-15 23:40 Endorsements.html
-r-xr-xr-x 1 sebastian sebastian     2237 2008-08-13 23:57 files.zip
-r-xr-xr-x 1 sebastian sebastian     2644 2008-09-15 23:40 Home.html
dr-xr-xr-x 2 sebastian sebastian     4096 2009-01-27 05:07 Images
dr-xr-xr-x 2 sebastian sebastian     4096 2009-01-27 05:07 index_files
-r-xr-xr-x 1 sebastian sebastian      701 2008-09-15 23:40 index.html
-r-xr-xr-x 1 sebastian sebastian      789 2008-09-15 23:40 LogoFrame.html
-r-xr-xr-x 1 sebastian sebastian     4501 2008-09-18 22:57 Mirage.html
-r-xr-xr-x 1 sebastian sebastian 51333988 2008-09-09 17:45 mirage.mov
-r-xr-xr-x 1 sebastian sebastian     3446 2008-09-15 23:40 MoaB.html
-r-xr-xr-x 1 sebastian sebastian       43 2008-09-15 23:40 pixel.gif
-r-xr-xr-x 1 sebastian sebastian     1111 2008-09-15 23:40 ProductLinks.html
-r-xr-xr-x 1 sebastian sebastian     1114 2008-09-15 23:40 ProductLinksold.html
-r-xr-xr-x 1 sebastian sebastian     1927 2008-09-15 23:40 RetailStores.html
-r-xr-xr-x 1 sebastian sebastian     1653 2008-09-15 23:40 Reviews.html
-r-xr-xr-x 1 sebastian sebastian     1837 2008-09-15 23:40 sc-but-03.gif
-r-xr-xr-x 1 sebastian sebastian     4285 2008-09-15 23:40 Spitfire.html
-r-xr-xr-x 1 sebastian sebastian     3070 2008-09-15 23:40 TumbleWeed.html
-r-xr-xr-x 1 sebastian sebastian     2258 2008-09-15 23:40 view_cart.gif
-r-xr-xr-x 1 sebastian sebastian     2733 2008-08-12 02:02 welcome.html
sebastian@Dino:~$ chmod -R og+w /home/sebastian/fxeng.com
sebastian@Dino:~$ 

still nothing...

---

### Post by jerome1232 on 2009-01-27
Yeah they aren't writeable (I made a typo before should be a u instead of an o)

Try running the fixed command then follow it up with an ls -l to make sure the permissions changed. And no you don't need to run this command as root.

---

### Post by carolinason on 2009-01-27
you need the write permission bit set for the owner

```
chmod -R 755 /home/sebastian/fxeng.com
```

-rwxr-xr-x file name

---

### Post by Gebastram on 2009-01-27
my dad downloaded the directory on a USB drive and set the properties to read write and whatever else, and it works now.

Thanks for the help anyway guys!

LINUX COMMUNITY ROCKS HARDER THAN WINDOWS!

---

