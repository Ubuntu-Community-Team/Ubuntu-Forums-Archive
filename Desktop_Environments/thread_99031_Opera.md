---
title: "Opera"
date: 2005-12-04
forum: Desktop Environments
---

### Post by Rebajas on 2005-12-04
Hiya,

I'm not sure whether I should ask here or at Opera but I'm tired and I reckon I'll get more useful info here.

I have installed Opera browser version 8.51 and it seems to have gone well - no errors anyway.

The problem though is where has it been installed? I have look all over my computer and cannot find it; no link from Applications menu, nothing on the desktop and no sign of any folders on the drive itself.

Also, how do you do a search within Ubuntu? I looked all over the file manager but saw nothing...

Thanks in advance,

Rebajas.

---

### Post by flopsy on 2005-12-04
Try one of the following commands in a terminal (the ones at the beginning are faster)

which opera
dpkg -L opera
find /usr -name opera

To search, use Places > Search For Files...

---

### Post by Noelinho on 2005-12-04
If you're looking just to launch it, then just open the terminal and type 'opera'.

---

### Post by migueljacq on 2005-12-04
Did you install it from downloading the tar/deb files on the Opera site? Wherever it downloaded, then, would be where you told it to extract to. 
There is an .opera directory in your home directory, if you are viewing hidden files. I don't know if it's where it got installed, though, or where it just keeps your settings, cache etc.

Yeah, Opera doesn't seem to automatically put itself in the applications menu. I run a custom launcher simply with the command 'opera' and it works. This, I believe, also works if you press ALT+F2 (the 'Run' command) and type in 'opera'.

Similarily, you can then add Opera to your applications menu by using the Applications Menu Editor (SMEG)

---

### Post by Rebajas on 2005-12-15
Hi, thanks for the replies - I will have a go at finding Opera when I get home this weekend and let you know how I got on.

For reference, in case someone else looks at this thread needing an answer to this question - I installed from the Opera repositories through the advance installer on Ubuntu 5.10.

Cheers.

---

### Post by wylfing on 2005-12-15
If I understand right, there's no entry in any of the menus for Opera, right? I'm pretty sure you have to make one manually. I don't know why Opera's debs don't do this automatically, but hey...

So fire up Applications > System Tools > Applications menu editor. Find a nice spot for adding an Opera entry (say, Internet) and click New Entry.

Name: Opera
Command: opera %s

Click the "No Icon" button and browse to /usr/share/opera/images and find an icon that works for you (Opera_48x48.png is a reasonable choice).

HTH

---

### Post by linbetwin on 2005-12-15
Opera probably IS in the Menu editor. Try deselecting and reselecting it the close the menu editor.

---

### Post by BobSongs on 2005-12-16
[QUOTE=flopsy]Try one of the following commands in a terminal (the ones at the beginning are faster)

which opera
dpkg -L opera
find /usr -name opera

To search, use Places > Search For Files...[/QUOTE]

I use:

```
whereis opera
```

---

### Post by Madpilot on 2005-12-17
Adding Opera to the menu - and lots of other useful stuff - is covered in the Ubuntu wiki's Opera article:

[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

Note that adding stuff to the Applications menu is even easier now in Breezy - that page still shows the pre-Breezy method of manually editing .desktop files.

---

### Post by EvilBill on 2005-12-18
Thanks for the set-up tips, **wylfing** :) 

I really like Opera 8.51, it's only been a couple days that I have been using it, but it seems faster than FireFox 1.5. 

It probably is just a matter of personal taste I guess, they both are good.

---

