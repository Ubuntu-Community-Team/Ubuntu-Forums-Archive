---
title: "Lost programme 'mscompress'"
date: 2005-10-14
forum: Desktop Environments
---

### Post by geofff on 2005-10-14
I need to decompress .exe files and have downloaded from Synaptic mscompress which according to synaptic includes 2 programmes, mscompress and msexpand. I don't know where they are. 

I have tried "find /home name 'mscompress*' -print" and "find /usr name 'mscompress*' -print" with no result. I don't know whether I'm looking in the wrong places, my use of find is at fault or the files I'm looking for are not called mscompress! 

I have also tried ./mscompress which comes up with no such file or directory.

I need to know where it is as, to open the .exe files, I am asked what should firefox do with them. When I ask for an alternative to the Archive Manager which can't handle .exe I am asked to choose the location of the Helper Application ](*,) 

(I've also looked on Add Applications and it doesn't seem to have appeared there despite me loading via synaptic and rebooting etc etc)

I'm sure the answer simple but its beyond me!!!!!#-o

---

### Post by geofff on 2005-10-15
I've now found mscompress and msexpand in /usr/bin/ 
However I still cannot find out how to expand an .exe file with them.
The window says 
"You have chosen to open T175-05j_00.exe which is a: ZIP archive
What should Firefox do with this file?
Open with Archive Manager (default)/other
Save to disc"

.exe is not supported by the Archive Manager and clicking 'open' with this gets nil response ie everything disappears. 

When I replace Archive manager with the bin file from /usr/bin/msextract and click open I get exactly the same.

I know this must be so simple to anyone who knows what they are doing?

---

### Post by PaganHippie on 2005-10-15
.exe files are not a compressed format, generally. Rather, they are the general M$ format for an executable file > 64 KB in size.

What, exactly, are you trying to do? If you're trying to run a M$DOS/Win program under Linux, you will almost certainly need either emulation software or something like Wine which translates Win APIs to Linux system calls.

---

### Post by geofff on 2005-10-15
I am being sent a files which have .exe extensions which I need to read and file. I don't want to do anything more than that. I am not sure whether I can ask for them to be sent with different extensions (eg zip) but as Ubuntu contains mscompress in the repos I thought using this would be the simple answer. However whatever I do I can't read them. Loading into OO doesn't work either.

Rereading the Synaptic notes on mscompress perhaps I've misunderstood? It says re msexpand: "which decompresses files compressed by the Microsoft compress.exe utility (eg Win 3x installation files)". I had assumed (as I was in a Linux environment) that the decompressed files would be readable in Linux. I think you're saying this isn't the case?

---

### Post by stoffe on 2005-10-15
Are these files by any chance self-extracting zip archives? Not sure if Archive Manager or unzip can handle those, although they should be able to. If they complain about file extension, maybe try renaming them zip and see what happens. 

Another way to do it might be to use wine to execute them and have them extract that way.

If they are just zip archives with the silly self-extract added, maybe you can have the files resent as plain zips? Self-extracting archives is a pain anyways and as it seems, mostly used for virus spreading anyways... :)

---

### Post by AndersAA on 2005-10-15
[QUOTE=geofff]Rereading the Synaptic notes on mscompress perhaps I've misunderstood? It says re msexpand: "which decompresses files compressed by the Microsoft compress.exe utility (eg Win 3x installation files)". I had assumed (as I was in a Linux environment) that the decompressed files would be readable in Linux. I think you're saying this isn't the case?[/QUOTE]

the microsoft compress.exe utility makes filename.ex_ files from filename.ext files.  So any asd.exe would be asd.ex_ compressed with that tool.

If it's a self extracting zip, either save it and rename it to .zip and open it with archive manager, or open a terminal (applications -> accessories) and write:
unzip filename 
(note, if filename has spaces in it, use "filename")

---

### Post by geofff on 2005-10-15
Yup. they are self-extracting zip files. If I save them, change the extension to zip and then use Archive Manager I can read them (although an attached gif file does not get loaded in the resulting document). 

Hope there aren't too many similar attachments in future files (this is feedback from my submissions re a course I'm doing). If I lose stuff I could well come back. In the meantime thanks for all the help.

---

