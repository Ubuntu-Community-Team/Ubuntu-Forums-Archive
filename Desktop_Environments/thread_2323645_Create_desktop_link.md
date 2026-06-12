---
title: "Create desktop link"
date: 2016-05-06
forum: Desktop Environments
---

### Post by dkolars on 2016-05-06
Using 14.04, LTS 64bit...  Had a crash recently, and realized that the link to a LibreOffice spreadsheet was actually to a different file than the one I thought it was.  I have a "Data" directory on a 2nd HDD, and assumed that the link on the desktop was opening that file.  Guess it wasn't, as after the crash, I opened that file and saw that it was a LOT different that I had left it via the desktop link.

So, how does one create a link on the desktop to a file that will open THAT file?

---

### Post by Dennis N on 2016-05-07
As I understand it, you have a desktop link to a file (target), but you want the target to be a different file?
If:
link = link name
file2 = new target

1) cd to Desktop
2) run this command: [FONT=Courier New]**ln -sf <full path to>file2 link**[/FONT]

Fill in the correct full path. -sf options remove the old link and creates a new one.

---

### Post by dkolars on 2016-05-07
Not exactly... I have other hard drives, and I store all my data from programs on HD2.  In my '/' directory are the programs.  So, I set the path in the programs to point to the data directory.  For LibreCalc it's like "HD2/Alldata/CalcData/xxx.odf" or the like...  Then, when I click on that file, it opens LibreCalc, and off we go.  BUT, if I put a link on the desktop to that file, Xubuntu copies that file to the "/home/me/Desktop" folder and all changes I make are done to that file, NOT the file on my HD2.    I want the link on my desktop to open the file on HD2, NOT be a duplicate file.

---

### Post by Dennis N on 2016-05-07
A hypothetical scenario:

A symbolic link could make a copy of a file using the same name if you used "save as..." and saved to another folder. The link would continue to point to and open the original, however which would be unchanged after the "save as...".  This gets you two different versions. Then, from LOC you could have opened that copy instead of the original. done some more editing, and saved. Now you have two different versions going, not detectable if you open from LOC with "Recently used...".   

All hypothetical, but possible. Whatever happened, the solution is to retarget the desktop link to the same file that LOC is using.

---

### Post by dkolars on 2016-05-07
Thanks, got it fixed.  I was operating under the assumption that, like in previous versions and Windoze, I could drag and drop and that would create a sym link...  I opened the drive from the Desktop with File Manager, and right-clicked file and selected "Send to..."  and 'poof', there is the option for a desktop link.  I almost never use File Manager, but use Krusader instead, having been spoiled by Norton Commander when it first came out many moons ago.... 2-pane file managers make life sooo much easier...  But, cannot create sym link!!  Thanks again.

---

### Post by mc4man on 2016-05-07
At least with nautilus DnD is sometimes a move (hand w/arrow) & sometimes a cp (hand w/+) Some files are always a move no matter the location.

---

