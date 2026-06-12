---
title: "[SOLVED] Can someone take a look at this...."
date: 2008-05-25
forum: Gaming &amp; Leisure
---

### Post by SteveNorman on 2008-05-25
I am trying to download fighter ace for linux, but it aint working,,

Im to noob to figure out why. Any help? Th instructions are in the link below,,I am trying the tarball method but get this when I try to unpack it:

$ tar -jxvf PATH_TO/FighterAce-3.x-112.i386.tbz2
tar: PATH_TO/FighterAce-3.x-112.i386.tbz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors




the link to the instructions:

[http://linux.ketsujin.com/index.php?option=com_content&task=view&id=19&Itemid=35](http://linux.ketsujin.com/index.php?option=com_content&task=view&id=19&Itemid=35)

---

### Post by acoustibop on 2008-05-25
Are there any spaces or illegal characters in your path, SteveNorman?

---

### Post by Grishka on 2008-05-25
> **SteveNorman said:**
> I am trying to download fighter ace for linux, but it aint working,,

Im to noob to figure out why. Any help? Th instructions are in the link below,,I am trying the tarball method but get this when I try to unpack it:

$ tar -jxvf PATH_TO/FighterAce-3.x-112.i386.tbz2
tar: PATH_TO/FighterAce-3.x-112.i386.tbz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors




the link to the instructions:

[http://linux.ketsujin.com/index.php?option=com_content&task=view&id=19&Itemid=35](http://linux.ketsujin.com/index.php?option=com_content&task=view&id=19&Itemid=35)

man, put the true path to your file in place of "PATH_TO". you can cd to the directory with the file then enter
$ tar -jxvf ./FighterAce-3.x-112.i386.tbz2
but it would be most convenient to simply open the archive with a graphical archive manager. just double click the file to open it.

---

### Post by unutbu on 2008-05-25
Change PATH_TO to the path to the file FighterAce-3.x-112.i386.tbz2.
For example, if FighterAce-3.x-112.i386.tbz2 is in your home directory, type

```
tar -jxvf ~/FighterAce-3.x-112.i386.tbz2
```

If FighterAce-3.x-112.i386.tbz2 is saved in /tmp, then

```
tar -jxvf /tmp/FighterAce-3.x-112.i386.tbz2
```

---

### Post by SteveNorman on 2008-05-25
Well I got it to extract,,but I cant get the inlinks or the permissions to change.


I extracted it to ~, ls shows it there. It extracted as opt, which is also there under ls

the next set of instructions are:

    # rm -f /opt/Ketsujin/FighterAce/.FAStart.version
    # rm -f /opt/Ketsujin/FighterAceBeta/.FAStart.version
    # unlink /usr/local/bin/FAStart
    # unlink /usr/local/bin/FABeta
    # chmod -R oag+rwx /opt/Ketsujin
    # chown -R root:root /opt/Ketsujin
    # ln -s /opt/Ketsujin/FighterAce/FAStart /usr/local/bin/FAStart
    # ln -s /opt/Ketsujin/FighterAce/FABeta /usr/local/bin/FABeta
    # cp -fa /opt/Ketsujin/FighterAce/fighterace.desktop  /usr/share/applications/fighterace.desktop
    # cp -fa /opt/Ketsujin/FighterAce/fighterace.png /usr/share/pixmaps/fighterace.png
    # cp -fa /opt/Ketsujin/FighterAce/fighteracebeta.desktop /usr/share/applications/fighteracebeta.desktop
    # cp -fa /opt/Ketsujin/FighterAce/fighteracebeta.png /usr/share/pixmaps/fighteracebeta.png
 

The instructions to remove files work,, but the unlinks give me no such file errors, as do the chmods..

I tried this in ~ and after cd opt with the same results. Stuck again...

---

### Post by keb0x80 on 2008-05-25
It seems like you extracted the archive to your home directory (~) though the commands specify paths as if the archive was extracted to the root directory (/) instead.

Inserting ~ at the beginning of the paths would probably help you.

You could also decide to extract the archive directly to the root directory instead...

---

### Post by SteveNorman on 2008-05-25
would that be like

unlink ~/usr/local/bin/FAStart
 vs
unlink /usr/local/bin/FAStart?

I tried both and got the same thing no such file or dir mesg,,

So I extracted it to ~

It extracted as opt

should I be in opt or ~ to do the rest?

---

### Post by SteveNorman on 2008-05-25
Actually I get a lot of it to work,, just not the /usr/local/bin stuff


any ideas? is that path different in ubuntu? All I see is . and .. when I ls -a it

---

### Post by unutbu on 2008-05-25
Check that the files in /opt/Ketsujin/FighterAce/
are in place:

```
ls -lR /opt/Ketsujin/FighterAce/
```

You should see quite a few files; it's not necessary to post, just make sure they are there.

If it looks right to you, then make symbolic links with
```
ln -s /opt/Ketsujin/FighterAce/FAStart /usr/local/bin/FAStart
ln -s /opt/Ketsujin/FighterAce/FABeta /usr/local/bin/FABeta
```

Have you already done this?

To check that the symbolic links have been made, type
```

ls -l /usr/local/bin/
```

You should see a line for FAStart and one for FABeta.

---

### Post by SteveNorman on 2008-05-26
heres where I am

~$ ls -lR opt/Ketsujin/FighterAce/
opt/Ketsujin/FighterAce/:
total 964
-rwxrwxrwx 1 steve steve    338 2007-07-16 09:50 FABeta
-rwxrwxrwx 1 steve steve    766 2006-04-12 15:44 FA.ico
-rwxrwxrwx 1 steve steve    308 2007-07-16 09:50 FAStart
-rwxrwxrwx 1 steve steve 910399 2007-12-11 07:24 FAStart.jar
-rwxrwxrwx 1 steve steve    215 2007-02-02 07:39 fighteracebeta.desktop
-rwxrwxrwx 1 steve steve   5366 2007-12-11 07:24 fighteracebeta.png
-rwxrwxrwx 1 steve steve    203 2006-04-12 15:44 fighterace.desktop
-rwxrwxrwx 1 steve steve   5043 2007-12-11 07:24 fighterace.png
-rwxrwxrwx 1 steve steve    300 2006-04-12 15:44 Messages.TEMPLATE.txt
-rwxrwxrwx 1 steve steve    105 2006-04-12 15:44 quiet.TEMPLATE.txt
-rwxrwxrwx 1 steve steve   6129 2006-04-12 15:44 ReadMe_EN.txt
-rwxrwxrwx 1 steve steve   6093 2006-04-12 15:44 ReadMe_JP.txt
-rwxrwxrwx 1 steve steve   6129 2005-04-22 06:46 Readme.txt
steve@teampeanut-desktop:~$ ln -s opt/Ketsujin/FighterAce/FAStart /usr/local/bin/FAStart
ln: creating symbolic link `/usr/local/bin/FAStart' to `opt/Ketsujin/FighterAce/FAStart': Permission denied


I did opt/Ket...
vrs /opt/Kets and got to the above


Also on this line:
$ chown -R root:root ~/opt/Ketsujin
I get "change ownership not permitted. Man I dont know how to do anything,,,pretty sad

-For :ln -s /opt/Ketsujin/FighterAce/FAStart /usr/local/bin/FAStart

steve@teampeanut-desktop:~$ ln -s ~/opt/Ketsujin/FighterAce/FAStart /usr/local/bin/FAStart
ln: creating symbolic link `/usr/local/bin/FAStart' to `/home/steve/opt/Ketsujin/FighterAce/FAStart': Permission denied
steve@teampeanut-desktop:~$

---

### Post by Cappy on 2008-05-26
You have to sudo (superuser do) if you want to interact (add files, change permissions, change user:group ownership, etc.) with a directory owned by root.
```
sudo ln -s opt/Ketsujin/FighterAce/FAStart /usr/local/bin/FAStart
```

---

### Post by SteveNorman on 2008-05-26
Thanks guys,,learned a lot about paths in this one. Now I gotta figure out how to start the game lol..

---

### Post by SteveNorman on 2008-05-26
so I found out it should have been opened in root,,is there an easy way to delete the previous download? since its not a package I dont have to worry about dependencies etc? I am thinking 
cd ~ 
rm -r opt
should do it, but I am worried about the links I made,,can anyone see a problem doing this before I try?

After I remove it I will unpack the tarball in root and do it all again.

Thanks

---

### Post by unutbu on 2008-05-26
This should be ok.
```
cd              # change to home directory
rm -rf ~/opt    # remove everything in opt (including opt)
cd /            # change to the / directory
sudo -s         # become root
rm /usr/local/bin/FAStart    # remove old symlink
rm /usr/local/bin/FABeta     # remove old symlink

```
then just follow the instructions on the download page.

---

### Post by SteveNorman on 2008-05-27
I got it loaded,,and was able to log in and get into the game.
Just need to get the game to see my joystick, and be able to log in fullscreen,since I believe this is a wine issue,, I will mark this solved and post my other problems there. Thank you guys very much,, I learned quite a bit doing this.

---

