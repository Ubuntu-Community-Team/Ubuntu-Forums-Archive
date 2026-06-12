---
title: "Gimp Help"
date: 2009-02-04
forum: General Help
---

### Post by Indyviews on 2009-02-04
I have been five weeks plus working to get everything working and now I am at a point of changing a few photos (taken in the last month) and backing them up so I can completely eliminate everything if need be. I am so far from my real problems that I feel hopeless. I have googled and searched forums until I am literally sick.

I have been using Gimp, changing and saving photos etc. Now all I get when trying to save is I don't have permission. I have done all of the file sharing and permissions that I can find and have also done the 'gksudo nautilus' before working in Gimp...nothing. Just give me suggestions and I will try anything I haven't already tried.

It was working..now it doesn't. Same way with Virtualbox. 

Different Question: If I dual boot....Windows 2000 first and then Ubuntu: Can I make it so that Ubuntu will come on automatically after so many seconds? I wish to only use W2k once in a while in order to use my scanner....nothing else.

---

### Post by philinux on 2009-02-04
Take one of your pictures that are causing a problem and right click on it. Click properties then permissions. Post a pic of what you see.

Sounds like permissions are not what they should be.

---

### Post by Indyviews on 2009-02-04
Hi **Phil**, I see the problem is the "Read Only". I changed it to read & write and it works. I never thought about checking this. May I ask  what caused them to change to 'read only', and should I just expect to change permissions after every photo folder I make?

I made a screen copy but see no way to post it from my computer..only from a url. I do this all the time on other forums.

Thanks a lot for your help!

---

### Post by philinux on 2009-02-04
If the folder is in your home folder i.e /home/username then it will be read/write. Files in /home are not owned by you by default.

To attach a screenshot click the paperclip icon in the message reply pane.

---

### Post by Indyviews on 2009-02-04
Here is the screenshot before I switched it to read/write. The files I have been working on is in the Home folder....four folders or levels down. I have notice that photos in this particular folder are 'read only' while photos in other folders at the same level as this folder are 'read & write'. Can I change this folder to 'read & write'?

---

### Post by jespdj on 2009-02-04
Did you copy those pictures from a CD-ROM? Ubuntu tends to remember the file permissions, and when you copy files from a read-only CD-ROM, the copies on your harddisk will also be made read-only.

---

### Post by Roger Mudd on 2009-02-04
Look into the chmod command, which can be used recursivley on directories.
Linux permissions are certainly more secure than Windows, but can hamstring users a bit when compared to the carte blanche offered by Microsoft. Actually being able to use/edit your files is important, despite the inherent dangers of a weaker permission system. I've run into very similar issues after moving files over from a NTFS-formatted external backup drive.

---

### Post by Indyviews on 2009-02-04
All of the photos in this folder are straight from my memory stick and I have worked on a few of the photos before.

---

