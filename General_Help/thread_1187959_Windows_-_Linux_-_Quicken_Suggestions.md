---
title: "Windows - Linux - Quicken Suggestions"
date: 2009-06-15
forum: General Help
---

### Post by knichel on 2009-06-15
I really want to ditch windows, but I use quicken (and a few others) and there really isn't any substitute.  I allow quicken to connect to my banks to download transactions and I do not believe there is any linux app (like kmymoney) that will do the same thing.

So,  I have my quicken data on a NTFS partition on my computer.  I installed virtual box with a windows 64 bit XP Pro.  Is there any way to mount that partition into the vbox?
OR
I was thinking of setting up another box with linux as server and share  via samba that way I can mount in the vbox or when boot into windows.  

Suggestions welcome.

--
JuJuBee

---

### Post by themusicalduck on 2009-06-15
If you look up the help documentation that comes with Vbox and search for "4.6. Folder Sharing". That page explains everything you need to do to share folders on the host with the guest.

---

### Post by knichel on 2009-06-15
Thanks for  the reply, but I have already tried that.  I do not see the shared folder when I follow the directions.  Maybe I missed something, but I have tried several times...

Attached a png to show there is no shared folder when I open windows explorer.

I shared a folder on an ntfs mounted partition on my linux host called Quicken and also shared a linux foler public_html from my home dir.  Neither of them show up.

--
JuJuBee

---

### Post by themusicalduck on 2009-06-15
I think the way I did it was by using the command "net use x: \\vboxsvr\sharename" in the windows command prompt, replacing "sharename" with the name of the shared folder as specified in virtualbox and "x" with the letter you'd like to assign the share. Like it says on the help page for command line usage. After doing that the shared folder would appear as a network share in My Computer rather than in Windows Network.

---

### Post by knichel on 2009-06-15
Thanks, but I tried that and got an error...
See attached png...
--
JuJuBee

---

### Post by Legace on 2009-06-15
I think you have to open Windows Explorer (= My Computer), click on "Tools" -> Map Network Drive and then add the shared folder through there.

---

### Post by knichel on 2009-06-15
I appreciate the assistance, but no dice...

I wonder, is it permissions issue?  Is there a vbox user I need to create to make this work?  or does my user account simply need rwx access to the folder I am  trying to share?

--
JuJuBee

---

### Post by knichel on 2009-06-15
Forgot to install the Guest Additions... My bad.. Happy now!

Thanks.

---

