---
title: "Sort order of Files ignores special characters"
date: 2015-06-20
forum: Desktop Environments
---

### Post by RayTomes on 2015-06-20
I am a new Ubuntu user on 14.04.2 using gnome. On windows I had my videos organised with playlist file names starting with "!" so that they all came to the front of the directory which was very handy. On Ubuntu it ignores the "!" and sorts them all scattered thtrough the very large directory. Is there any way to tell the files program to sort the untampered with file names so that "!" comes to the top?

---

### Post by Dennis N on 2015-06-20
Is this in the file manager? The wrong column may be selected for sorting. You may have to click of the "Name" header in the Name column to get it to sort alphabetically.  There is also a up or down pointing arrow at the right side of the header to indicate the order of sort: increasing or decreasing. if it is backwards, click again to change this.

---

### Post by Dennis N on 2015-06-20
I looked again and you are right! Sorry about that. Will look and see what can be done.

---

### Post by RayTomes on 2015-06-20
Thanks Dennis. I found this page, but it sounds a bit tricky for me.
[http://askubuntu.com/questions/115741/how-do-i-force-folder-view-sort-order-to-not-ignore-special-characters](http://askubuntu.com/questions/115741/how-do-i-force-folder-view-sort-order-to-not-ignore-special-characters)

also this one
[http://askubuntu.com/questions/422708/how-to-show-some-files-at-the-top-of-the-list-in-ubuntu](http://askubuntu.com/questions/422708/how-to-show-some-files-at-the-top-of-the-list-in-ubuntu)
it might be easiest for me to rename all my special character ones to have "." on the front.

---

### Post by RayTomes on 2015-06-20
From first link above, I tried to change locale but permission denied. How do I tell it that I am allowed to?

update-locale LC_LOCALE=C
update-locale: Unable to write /etc/default/locale: Permission denied

or will this only change it temporarily?

---

### Post by Dennis N on 2015-06-20
Behind the scenes, the file manager is probably using the Linux 'sort' command.  The default (with no options after sort) seems to use "dictionary order" which ignores everything except blanks and alphanumeric characters, and that is what we are getting.

test file, saved as sort-test.txt:
```
cfile
afile
!bfile

```

Using the sort command:

```
dmn@Daphne:~/work/testing$ sort sort-test.txt 
afile
!bfile
cfile

```

See the man page (type **man sort** in the terminal). There is no option for using ASCII codes to sort, which I believe is how Windows does it. And I saw nothing in file manager preferences.

You could preface the playlists with a number instead, 0 for example, to show them first? 

I saw the locales thing here when looking about:
[http://unix.stackexchange.com/questions/43465/whats-the-default-order-of-linux-sort](http://unix.stackexchange.com/questions/43465/whats-the-default-order-of-linux-sort)

See the first answer there. It says to use **export LC_ALL=C**. Maybe that will work for you. I didn't want to mess with that - not sure how to undo it.

Very good question, by the way.

Someone may come along here with a brilliant solution. Don't give up.

---

### Post by Dennis N on 2015-06-20
Aha! Just occurred to me: how about this? 

In file manager, you could just arrange the files by "type" (click on the "Type" column header) and that will bring all the playlist files together (but they may not show first). The filenames of the playlists display in alphabetical order as well when I did this. You could then remove the unneeded "!"

---

### Post by SeijiSensei on 2015-06-20
> **RayTomes said:**
> From first link above, I tried to change locale but permission denied. How do I tell it that I am allowed to?

update-locale LC_LOCALE=C
update-locale: Unable to write /etc/default/locale: Permission denied

or will this only change it temporarily?
You need to run commands like that with the "[sudo]("https://help.ubuntu.com/community/RootSudo")" mechanism that grants you temporary administrator privileges.  

```
sudo update-locale LC_LOCALE=C
```
Enter the password you use to log in when prompted.

From a terminal use the command "[FONT=Courier New]ls -l /[/FONT]" to see a list of [all the top-level directories]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") with ownerships and permissions.  /etc contains system configuration information so only the "root" (administrative) user can modify files in that directory.  In general as an ordinary user there are few places you can write files.  One is your /home/username directory; only you can write files there by default.  Everyone can write to /tmp; it will not survive a reboot.  Only root can write to places like /etc, /usr, and /var.

The file /etc/default/locale on my fairly vanilla US English Kubuntu contains LANG="en_US.UTF-8", appropriate for me, but probably not for you in New Zealand.

---

### Post by Dennis N on 2015-06-20
Hi Ray, 

Just this one final idea worthy of consideration: For my own music files, I have always separated playlist files into their own folder. That is really a better solution. If the paths to each music file are absolute (full path from / ), the playlists can be moved without having to modify them, and they will still work fine.

---

### Post by RayTomes on 2015-06-21
Thanks Dennis and Saiji.

I had earlier tried sudo but didnt get it right. This time it accepted the command that Seiji gave but it had no effect on the sort order. Or do I have to reboot?

The sort to file type was a good idea and makes it a lot easier. I hadn't mentioned that I had two sets of files one with "!!" and one with "!" so it mixed them up but otherwise all went to the front.

Unfortunately the pls files do not have directory info in them so I can't move to a separate folder.There are hundreds of them too.

---

### Post by vasa1 on 2015-06-21
Other than the leading "!!", how do the file names look? Perhaps you could provide the output of "ls"?

I feel it should be possible to do a mass rename of your pls files using "aaa" in place of "!!".

I've used perl pie to rename files in bulk. Depending on how messy the file names are, the command may resemble a "picket-fence". Fortunately, you can run perl pie in simulation mode before actually renaming your files.

---

### Post by vasa1 on 2015-06-21
And you maybe interested in reading about views on which characters to use (or not) while naming files (including folders). Here are a couple of links:
[http://stackoverflow.com/questions/2304221/what-character-sequence-should-i-not-allow-in-a-filename](http://stackoverflow.com/questions/2304221/what-character-sequence-should-i-not-allow-in-a-filename)
[http://www.mtu.edu/umc/services/web/cms/characters-avoid/](http://www.mtu.edu/umc/services/web/cms/characters-avoid/)

---

### Post by vasa1 on 2015-06-21
Re. the use of "locale", here's an answer that doesn't use sudo. I don't know if it's applicable to your situation. And, based on that answer, do try```
LC_ALL=C ls -l
```
For just a few files, I see this:```
10:46 PM ~/Desktop/ztemp/vtemp $ **ls -l**
total 0
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:38 aaatest.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:38 !!!test.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:38 !!test.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:37 !test.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:37 test.pls
10:46 PM ~/Desktop/ztemp/vtemp $ **LC_ALL=C ls -l**
total 0
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:38 !!!test.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:38 !!test.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:37 !test.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:38 aaatest.pls
-rw-rw-r-- 1 vasa1 vasa1 0 Jun 21 22:37 test.pls
10:46 PM ~/Desktop/ztemp/vtemp $ 

```

---

### Post by RayTomes on 2015-06-22
Thanks for suggestions folks. I think that I could rename files easily to aaa- and aab- from !! and ! and it would work.

But I also have other files using ! elsewhere. I commonly use it to make a file sort to the top, such as !readme.txt and so on. So it would be nive to solve the sort method which does seem to be possible.

---

### Post by vasa1 on 2015-06-22
> **RayTomes said:**
> Thanks for suggestions folks. I think that I could rename files easily to aaa- and aab- from !! and ! and it would work.

But I also have other files using ! elsewhere. I commonly use it to make a file sort to the top, such as !readme.txt and so on. So it would be nive to solve the sort method which does seem to be possible.

You should **stop using "!"** in filenames! Stick to a-z, A-Z, 0-9, and maybe -, _ and..

---

### Post by vasa1 on 2015-06-22
> **RayTomes said:**
> ... So it would be nive to solve the sort method which does seem to be possible.
Doesn't the code I gave, **LC_ALL=C ls -l**, work to get the files with ! or !! or !!! to the top?

---

### Post by RayTomes on 2015-06-23
> **vasa1 said:**
> Doesn't the code I gave, **LC_ALL=C ls -l**, work to get the files with ! or !! or !!! to the top?

Yes, But I want something that works permanently for files program. It is possible with the info on the two links I gave near the top. I just get lost with the sudo stuff.

---

### Post by RayTomes on 2015-06-23
> **vasa1 said:**
> You should **stop using "!"** in filenames! Stick to a-z, A-Z, 0-9, and maybe -, _ and..

That is all very well, but I made these files over a period of about 30 years when it worked OK on Windows. I have hundreds of thousands of files and I like what I did. Ubuntu should stop sorting files a silly way.

---

### Post by vasa1 on 2015-06-23
Try```
LC_ALL=C nautilus
```

I don't use nautilus aka Files and so don't know if it works but ```
LC_ALL=C pcmanfm
```works for me.

I guess you could make a .desktop file with that command.

---

### Post by vasa1 on 2015-06-23
> **RayTomes said:**
> That is all very well, but I made these files over a period of about 30 years when it worked OK on Windows. I have hundreds of thousands of files and I like what I did. **Ubuntu should stop sorting files a silly way.**
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

