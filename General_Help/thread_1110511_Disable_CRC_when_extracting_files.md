---
title: "Disable CRC when extracting files?"
date: 2009-03-29
forum: General Help
---

### Post by AllRadioisDead on 2009-03-29
Hi, I have a bit of an interesting problem. My friend got a nasty trojan on windoze, and used a backup program (nero backitup) to back up all his data on his external drive. It created these (.nba) files which are compressed files. When he tries to restore his data with nero backitup, he can only select one file at a time to restore, and since the (.nba) files all contain parts of files, it fails. However, on linux, Ubuntu recognises the .nba files as compressed, and attempts to extract them. It sucessfully extracted the first one, but when it tries to do the second one, it completes, but at the very end it gives an error saying the files failed to pass a CRC check, and removes the folder it extracted to. Is there any way to stop it from doing this? I know Ubuntu didn't cause the problem, but it may be the solution. 
-Thanks

---

### Post by 3Miro on 2009-03-29
If there is a CRC error, then either the file was corrupt or it was incompatible with the Ubuntu archiver. I guess Nero could have put something in the file to make it unusable by other archiver programs. If that is the case, disabling the CRC wouldn't help.

For disabling, I don't know if it is possible, but try calling tar or some other archive program from the command line and see if there is a command line option to use.

---

### Post by AllRadioisDead on 2009-03-29
> **3Miro said:**
> If there is a CRC error, then either the file was corrupt or it was incompatible with the Ubuntu archiver. I guess Nero could have put something in the file to make it unusable by other archiver programs. If that is the case, disabling the CRC wouldn't help.

For disabling, I don't know if it is possible, but try calling tar or some other archive program from the command line and see if there is a command line option to use.
Ubuntu extract's the file though, at the end, it brings up the crc error and deletes the folder it extracted. Could you elaborate more on the command line? I'm not sure what you mean, thanks for the reply.

---

### Post by 3Miro on 2009-03-29
> **ihermit said:**
> Ubuntu extract's the file though, at the end, it brings up the crc error and deletes the folder it extracted. Could you elaborate more on the command line? I'm not sure what you mean, thanks for the reply.

Yea, sorry, I will try to be more clear.

Applications -> Accessories -> Terminal, gets you to the command line. From here you can do everything (if you know the right command) and you can do things the graphical interface wouldn't allow you (including dangerous things that can damage your system). For almost any command you can type
```
man command
```
and you will get list of possible options.



Yea, sorry, I will try to be more clear.

You can create an archive with a command like:
```
tar -cvvf foo.tar foo/
```
This will use the tar command to create archive foo.tar from folder foo/

tar is the main Linux archiving tool, but there seems to be nothing the man pages about CRC. Do you know what kind of archive Nero is using?

BTW, the file that you see being created, might have never been extracted. Tar might be just creating the file and then filling it with data from the archive, but due to the CRC, nothing gets populated. The file might not be extracted at all.

---

### Post by AllRadioisDead on 2009-03-29
> **3Miro said:**
> Yea, sorry, I will try to be more clear.

Applications -> Accessories -> Terminal, gets you to the command line. From here you can do everything (if you know the right command) and you can do things the graphical interface wouldn't allow you (including dangerous things that can damage your system). For almost any command you can type
```
man command
```and you will get list of possible options.



Yea, sorry, I will try to be more clear.

You can create an archive with a command like:
```
tar -cvvf foo.tar foo/
```This will use the tar command to create archive foo.tar from folder foo/

tar is the main Linux archiving tool, but there seems to be nothing the man pages about CRC. Do you know what kind of archive Nero is using?

BTW, the file that you see being created, might have never been extracted. Tar might be just creating the file and then filling it with data from the archive, but due to the CRC, nothing gets populated. The file might not be extracted at all.
Thanks for the reply. I read a bit of the nero documentation and it appears to be  zipped. These are pretty big files (about 2gb each) so it takes a bit of time to extract them. While they're extracting, I can view the files inside the folder it creates (music, pictures, documents), but when it's finished, the crc error causes the folder to be deleted.

---

### Post by 3Miro on 2009-03-29
> **ihermit said:**
> Thanks for the reply. I read a bit of the nero documentation and it appears to be  zipped. These are pretty big files (about 2gb each) so it takes a bit of time to extract them. While they're extracting, I can view the files inside the folder it creates (music, pictures, documents), but when it's finished, the crc error causes the folder to be deleted.

Hm, can you open the files?

---

### Post by 3Miro on 2009-03-29
To unzip a file, the command is
```
unzip file
```

```
man unzip
```
gives a lot of options, but nothing about removing CRC.

Does the archive have a password, sometimes the graphical archive programs would mess up on passwords and command line ones wold work. Give it a try.

---

### Post by AllRadioisDead on 2009-03-29
> **3Miro said:**
> To unzip a file, the command is
```
unzip file
``````
man unzip
```gives a lot of options, but nothing about removing CRC.

Does the archive have a password, sometimes the graphical archive programs would mess up on passwords and command line ones wold work. Give it a try.
My friend's gone to sleep. I'll give this a try tomorrow and I'll let you know, thanks for the help and this looks like it could work. Opening the files is also a good idea, we'll give that a try.

Update: Thanks for the help. it was a bug with the original nero software and he fixed it by selecting the last package for extraction in nero.

---

