---
title: "doesnt linux need file extensions?"
date: 2009-04-12
forum: General Help
---

### Post by wolfheart_2001 on 2009-04-12
i posted asking how i can view the file extension of files.

i recieved answers saying that linux dont need extensions..ithink that sounds strange..can any one explain this to me???

and how i can show up extensions if they were disabled?

regards

---

### Post by unutbu on 2009-04-12
The default filesystem format on Ubuntu is ext3 (soon to be ext4).
ext3 has no concept of file extension. So a file called "song.mp3" is simply a file named "song.mp3". The filesystem pays no special attention to the ".mp3" part.

Some programs may react differently to files based on the pattern of letters it finds after the last period, but that is a choice the programmer made. Other programs can recognize the mime-type of a file based on its contents, rather than its name.

Your file browser shows the entire name of the file. If a file is named "song", then it simply has nothing recognizable as a file extension.

---

### Post by lovinglinux on 2009-04-12
> **wolfheart_2001 said:**
> i recieved answers saying that linux dont need extensions..ithink that sounds strange..can any one explain this to me???

I guess Linux can detect the file type, most of the time.

> **wolfheart_2001 said:**
> and how i can show up extensions if they were disabled?

They are not disabled. I don't know if Nautilus can hide extensions, but if you see some files with extensions and others without, it just means the others don't have extensions at all.

---

### Post by wolfheart_2001 on 2009-04-12
Thank you guys

see you again for more QA :guitar:

---

### Post by CatKiller on 2009-04-12
> **wolfheart_2001 said:**
> i recieved answers saying that linux dont need extensions..ithink that sounds strange..can any one explain this to me???

Files often know what type of file they are. This is specified by the MIME-type, generally included in the headers of the file as something like *text/html*. The Operating System can look at these headers and work out what type of file it is looking at, and use this information to decide what to do with that file.

Having file-type metadata encoded in the filename is not a great idea for a number of reasons. There are quite a few articles on the Internet about it. Unfortunately, the widespread use of DOS, which encoded this information in the filename because it was too limited to put it anywhere else, has meant that people expect filename extensions to have some meaning - including software developers, unfortunately. This has had the unfortunate side-effect of meaning that some applications, even on Linux, use the filename extension for filtering filetypes, even though there's not really any reason to. In my view, those applications should be considered broken, but given the widespread use of filename extensions amongst users this is probably not that popular a view.

---

### Post by wolfheart_2001 on 2009-04-12
> **CatKiller said:**
> Files often know what type of file they are. This is specified by the MIME-type, generally included in the headers of the file as something like *text/html*. The Operating System can look at these headers and work out what type of file it is looking at, and use this information to decide what to do with that file.

Having file-type metadata encoded in the filename is not a great idea for a number of reasons. There are quite a few articles on the Internet about it. Unfortunately, the widespread use of DOS, which encoded this information in the filename because it was too limited to put it anywhere else, has meant that people expect filename extensions to have some meaning - including software developers, unfortunately. This has had the unfortunate side-effect of meaning that some applications, even on Linux, use the filename extension for filtering filetypes, even though there's not really any reason to. In my view, those applications should be considered broken, but given the widespread use of filename extensions amongst users this is probably not that popular a view.

ok...if i saw a file in any directory in linux it would be very bad if i dont know if its a library, an application, a document, a script, an image or any thing else.
i just want to know how do users identify which application is suitable to open the file if they dont know its file extension??

---

### Post by coffeecat on 2009-04-12
> **CatKiller said:**
> This has had the unfortunate side-effect of meaning that some applications, even on Linux, use the filename extension for filtering filetypes, even though there's not really any reason to. In my view, those applications should be considered broken, but given the widespread use of filename extensions amongst users this is probably not that popular a view.

I agree. I got involved in a thread a little while ago where the OP wanted advice on how to batch convert JPEGs to PDFs, saying it was tedious to individually convert each file by renaming it from filename.jpg to filename.pdf. I and others pointed out that he hadn't actually converted the files; he now had just a bunch of JPEGs with pdf extensions. :|

But I was intrigued. I tried renaming a couple of JPEGs and it was interesting to see how different apps reacted. And it was then I made the pleasing discovery that Evince (pdf document viewer) can read and display image files including JPEGs.

**wolfheart_2001**, Apple MacOS, being a Unix-derived OS, behaves just like Linux in this respect. It's just that filename 'extensions' are hidden by default in MacOS. That's because Apple people like everything clean and tidy. :wink:

---

### Post by CatKiller on 2009-04-12
> **wolfheart_2001 said:**
> ok...if i saw a file in any directory in linux it would be very bad if i dont know if its a library, an application, a document, a script, an image or any thing else.
i just want to know how do users identify which application is suitable to open the file if they dont know its file extension??

Why do you need to know? 

If it's in your Home folder, you put it there, so you should already know. The OS will attempt to identify its filetype for you, and display an appropriate icon based on what it thinks the file is. It will also try to pick what to do with the file for you, which will change the context menu and so on.

If it's not in your Home folder then you don't need to fiddle with it anyway. And if there is something that you need to change, like a configuration file or what-have-you, then it will be *text/plain*. Also, files in UNIX-like OSes generally place their files based on their function. There is more information on that [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"). So documentation would go in /usr/share/doc, configuration files would be in /etc, libraries would be in /lib or /usr/lib depending on what they are libraries for, binary files would be in /bin or /usr/bin depending on what they are for, and so on.

---

### Post by lovinglinux on 2009-04-12
> **wolfheart_2001 said:**
> ok...if i saw a file in any directory in linux it would be very bad if i dont know if its a library, an application, a document, a script, an image or any thing else.
i just want to know how do users identify which application is suitable to open the file if they dont know its file extension??

As I already explained in your other thread:

> **lovinglinux said:**
> You can distinguish them through the icons and through the "Type" column in the file browser. Lots of files are just plain text documents, because Linux stores configurations in text files. Compare the "Type" column with the corresponding icon and soon you will be acquainted with each file type.

You can also right-click the file and select "Preferences". It will show the file info, including the MIME Type.

---

### Post by wolfheart_2001 on 2009-04-12
> **lovinglinux said:**
> As I already explained in your other thread:



You can also right-click the file and select "Preferences". It will show the file info, including the MIME Type.

Its just confusing..as i said, its my first time to use linux

But thanks for your help

regards

---

### Post by lovinglinux on 2009-04-12
> **wolfheart_2001 said:**
> Its just confusing..as i said, its my first time to use linux

But thanks for your help

regards

No problem.

Can you already identify a file type using the file browser? Try starting with a file you already know what it is, like an avi video. You will see a movie thumbnail or an icon, depending on your settings (default is thumbnail), then look on the column named "Type". It will show that the file is an "AVI video". Then look other files like images and text documents, the icon and the "Type" description will change for each file type.

Is confusing when you switch from Windows, but soon you will be acquainted with this.

---

### Post by lovinglinux on 2009-04-12
BTW, to see the column with file type you need to select the list view in the file browser main menu. Go to "View >>> View as list" or hit CTRL+2. If you want to view the file type while browsing using the Icon view ("View >>> View as Icons" or CTRL+1) then you need to change the file browser preferences. Go to "Edit >>> Preferences" then select the "Display" tab, then select the first drop-down menu and select the "Type" option. This will put the file type description below the Icons in the Icon view.

---

### Post by pbpersson on 2009-04-12
There are exceptions to this rule in Linux.

Being a.....well, I am still somewhat of a newbie.....when I am using Gimp and I change the file extension to JPG when saving a file, Gimp knows what I want and it converts the file to JPG format.

I don't even know how I am SUPPOSED to be doing this in Gimp if I am not supposed to be using file extensions.

I need file extensions, otherwise I think I would go crazy.

However, I have made that mistake.....I don't remember how, but I ended up with PNG files with JPG extensions on my web site - I could view them fine in Ubuntu but none of my Windows friends could see them :confused:

---

### Post by CatKiller on 2009-04-12
> **pbpersson said:**
> There are exceptions to this rule in Linux.

Being a.....well, I am still somewhat of a newbie.....when I am using Gimp and I change the file extension to JPG when saving a file, Gimp knows what I want and it converts the file to JPG format.

The GIMP offers you options on which format you want to use when you are saving a file, PNG, JPEG, bitmap, and so on. One of these options is "file type by extension." The GIMP is available for Windows too, and so the developers have to try to accommodate Windows users.

---

### Post by CatKiller on 2009-04-12
> **wolfheart_2001 said:**
> Its just confusing..as i said, its my first time to use linux

The Windows way of doing things is absurdly confusing if you're already used to doing things a different way. There are a number of things where the Windows way is different from the way everyone else does things. As you get used to the fact that things can be done a different way, you'll start to find these differences less confusing.

Good luck!

---

### Post by Rinzwind on 2009-04-12
Think of it like this:

Let's say I have a .JPG that I rename to .PNG. What inside the file changed for it to be a .PNG? -> Nothing it is still a .JPG. Therefor: the name is not the way to verify what a file is.

By the way: in my opinion the way Windows does it the OS should also do the conversion when renaming. If I do **copy images.jpg image.png** I should end up with a PNG. They rely on the extension so they should also take care of the file being of the type the extension indicates.

---

### Post by soltanis on 2009-04-12
BTW if you are ever on the command line and need to identify a file type, use the command

```

file _________

```

That'll quickly open the file, look at its contents, and tell you what kind of file it thinks it is.

Examples
```

; file a.out
a.out: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), not stripped

; file starcraft
starcraft: symbolic link to `.wine/drive_c/Program Files/Starcraft/'

; file test.pl
test.pl: a /usr/bin/perl script text executable

```

---

### Post by 3rdalbum on 2009-04-12
If you think that being able to determine the type of a file is some sort of magic, then you're right - it's "libmagic"! :-)

But let's see an analogy. A car enthusiast doesn't need to look at the badges on the back of a car in order to know what car it is. They can tell by what the vehicle looks like, how big it is, what noise the engine makes. If you put a Ferrari badge on the back of a Suzuki, that doesn't suddenly make it a Ferrari, and no person in their right mind would start treating the car as though it was a high-performance Italian-designed sportscar.

---

### Post by Slim Odds on 2009-04-12
> **unutbu said:**
> The default filesystem format on Ubuntu is ext3 (soon to be ext4).
ext3 has no concept of file extension. So a file called "song.mp3" is simply a file named "song.mp3". The filesystem pays no special attention to the ".mp3" part.

Actually, no file system has the concept of connecting a "file extension" with a file type. All of them (ext3/4, FAT32, NTFS, etc.) just have file names with dots. It's applications that make the distinction. In Windows, it would be cmd.exe or explorer.exe that would decide what application to launch based on the character combination after the last dot. Same in linux with bash or nautilus.

> Some programs may react differently to files based on the pattern of letters it finds after the last period, but that is a choice the programmer made. Other programs can recognize the mime-type of a file based on its contents, rather than its name.This is true. Applications can always read the file and decide to act based on the contents and not just the filename.

Someone also mentioned MacOS. But it's a little unique in that it has an entire "resource fork" that contains additional information about a file. This includes which application that the file "belongs to".

---

