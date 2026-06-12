---
title: "[SOLVED] ntfs partion"
date: 2007-08-26
forum: Desktop Environments
---

### Post by tropcky on 2007-08-26
i have a biiiig proplim with that i cant control any fils  i have read only accese 
i tryed to install the 
sudo apt-get install ntfs-config 
and when i start 2 run it it gives me an eror msg sed that i havr to make it ro   or some thing like that   so plez  is any 1 have a way to make full accese read and writ  by mak it fat32  or any way els but plez without losing data i cat lose thes data 
( its the full albums for the best metal and hard rock bands ) so i cant lose it 
help plez 
thank u

---

### Post by jim_p on 2007-08-27
Except for ntfs-config, in order to gain access to ntfs drives, you need to have ntfs-3g installed

```
sudo apt-get install ntfs-3g
```

Do that and if the problem remains, get back here and tell us more.

---

### Post by Dark Star on 2007-08-27
Yep ninstalling NTFS 3g will fix the error but still I can't write in NTFS partition :?:?

---

### Post by tropcky on 2007-08-27
i did what u told me 2   and when i tray to run the ntfs-config agen  it gives me tha same eroe msg and here it is 

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/B610605D10602699': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

---

### Post by tropcky on 2007-08-27
by the way i heard that ther is a way to make the ntfs a fat32   with out losing ur data  so  u can read and write with linux
 do any 1 know about that

---

### Post by merlinus on 2007-08-27
If you are dual-booting with windows, start windows and run chdsk on that drive.

Then it should mount with write privileges in ubuntu.

-merlin

---

### Post by Dark Star on 2007-08-27
I have NTFS -3g installed but I can't copy files in NTFS driver ?:?

---

### Post by tropcky on 2007-08-27
i dont have windows  i only have ubuntu now thats the proplim

---

### Post by tropcky on 2007-08-27
come on guys plez its not over yet we still have thes proplim

---

### Post by tropcky on 2007-08-27
any one ??????????

---

### Post by jim_p on 2007-08-27
> **tropcky said:**
> ...
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista...


Install ntfs-tools and run ntfsfix as linux suggests

```

sudo apt-get install ntfs-tools
ntfsfix /dev/hda6
```

Just replace hda6 with your drive

---

### Post by tropcky on 2007-08-27
i trayed man but when i did  
E: Couldn't find package ntfs-tools

---

### Post by tropcky on 2007-08-27
ppl told me that i will get help here and i dont see that 
ppl plez i am not the only 1 i have thes proplim so plez help

---

### Post by stinger30au on 2007-08-27
this may help

[http://ubuntuforums.org/showthread.php?t=529838](http://ubuntuforums.org/showthread.php?t=529838)

---

### Post by tropcky on 2007-08-27
thank u man but it disnt help hes talkin about anther thing at all plez read the posts from the biging  so u can understant the deeeeeeep **** i am in

---

### Post by mtbsoft on 2007-08-27
tropcky, the error message you were given gives you all the information you need, it's just a matter of how to do it...

[LIST]
[*]Boot Windows and shutdown it cleanly.
[*]Run ntfsfix version 1.13.1 on Linux unless you have Vista.
[*]Mount the NTFS volume with the 'ro' option in read-only mode.
[/LIST]

So you must either use the ntfsfix tool to clean the outstanding issues with the partition or you need to chkdsk it from Windows - you might be able to boot your PC from a Windows cd and correct the problem from the command line or you will have to put the disk in/connect it to a Windows pc and correct it that way.  

I doubt you can convert it to FAT32 until you have resolved the outstanding issues so that's not an option.

Other than that, since you can read it, you could simply copy the data from the NTFS partition, then delete and recreate the partition and write the data back to it.

> **tropcky said:**
> ppl told me that i will get help here and i dont see that 
Oh, and don't be so ungrateful!  

I see people offering you plenty of help here, they cannot work miracles - you need do some of the work yourself.  If you cannot get the package ntfs-tools, you need to work out why and work toward solving that problem first - do a little of the leg work yourself.

---

### Post by tropcky on 2007-08-27
wow man thank u for helping 
and i sed that i didnt mean that ppl didnt help   no thay did  they did help me  
i really didnt mean that  i just mean that iam badly need help thats all 
and i really sick of the ntfs-config and ntfs-3g   all that stuf 
so i told what of my frends  that using win xp   that i will back up my data in hes pc 
and i will format my hard all over agen   but plez tell me what  thing is best 2 read and write without any proplim   is it fat 32 ?
thank u 
and sorry 4 what i sed  
really i am

---

### Post by mtbsoft on 2007-08-27
No worries, happy to help.

As for the partition type, if you're totally Ubuntu now then I'd use a Linux partition type e.g. ext3, I can't see any benefit in using FAT32 except for accessing the drive directly across multiple o/s.  Accessing the ext3 data from Windows across a network won't be an issue if you install/use SAMBA.

If, however, you think you might want to put the drive in a windows box any time, you need to keep it FAT32 so it can be read by both.

You do still need to discover why you cannot get the ntfs-tools package but that's an issue for another day.

Enjoy.

---

### Post by tropcky on 2007-08-27
thank u man really thank u wont blive what just happened  when i run the ntfs config from the root user  it gives the same eror msg but thes time it says to type some comand line to raper it 
and i did i repot the system and gess what now i  have full access to the ntfs read write delete
evrery thing man 
and u know what u made do that with ur words with tellin me that i have to my work by my self 
i  was never gonna make that 
so i dont know how much i have 2 thank 
and how much i am sory about the words i sed 
thank u so much

---

### Post by jim_p on 2007-08-28
> **tropcky said:**
> i trayed man but when i did  
E: Couldn't find package ntfs-tools

Excuse me for the big delay but I will be busy until tomorrow.
I made a HUGE mistake. It' NOT ntfs-tools, it's **ntfsprogs** and ntfstools is a transitional package as Synaptic says. I am really sorry :(

---

### Post by tropcky on 2007-08-28
noooooooooo man  dont worry no proplim 
thanks any way for help cuz u  helped me so u dont have 2 say sorry 
i  am th one who have 2 say thanks 
and i fix it thanks god now i can read and write on nfts 

thank for evry one who helped

---

