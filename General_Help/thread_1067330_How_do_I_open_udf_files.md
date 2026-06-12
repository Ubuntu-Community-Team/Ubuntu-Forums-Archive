---
title: "How do I open udf files?"
date: 2009-02-11
forum: General Help
---

### Post by ozguitarplayer on 2009-02-11
Not knowing the rules I have added a post to this solved thread (1 Attachment(s) [ubuntu] [SOLVED] can't read udf cd (Multi-page thread 1 2)
ejv) in Absolute Beginner Talk where there are instructions on how to open udf files and I pasted the results of my efforts in terminal, I include them here again in case they are ignored in the other post since it's says solved.

My question is; can anytell me why I would get so many error messages?

nigel@Master:~$ cd ~/Downloads
nigel@Master:~/Downloads$ wget -O udf-filesystem-2.5.tar.gz [http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057](http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057)
[1] 6812                                                                                                                          
nigel@Master:~/Downloads$ --2009-02-12 10:09:29--  [http://ubuntuforums.org/attachment.php?attachmentid=61993](http://ubuntuforums.org/attachment.php?attachmentid=61993)                      
Resolving ubuntuforums.org... 91.189.94.12                                                                                        
Connecting to ubuntuforums.org|91.189.94.12|:80... connected.                                                                     
HTTP request sent, awaiting response... 200 OK                                                                                    
Length: 84633 (83K) [unknown/unknown]                                                                                             
Saving to: `udf-filesystem-2.5.tar.gz'                                                                                            

100%[===================================================================================================>] 84,633      42.5K/s   in 1.9s    

2009-02-12 10:09:32 (42.5 KB/s) - `udf-filesystem-2.5.tar.gz' saved [84633/84633]

tar -xvzf udf-filesystem-2.5.tar.gz
udf-filesystem-2.5/                
udf-filesystem-2.5/Kbuild          
udf-filesystem-2.5/COPYING         
udf-filesystem-2.5/Makefile        
udf-filesystem-2.5/src/            
udf-filesystem-2.5/src/super.c     
udf-filesystem-2.5/src/udftime.c   
udf-filesystem-2.5/src/inode.c     
udf-filesystem-2.5/src/namei.c     
udf-filesystem-2.5/src/udf_fs_sb.h 
udf-filesystem-2.5/src/osta_udf.h  
udf-filesystem-2.5/src/partition.c 
udf-filesystem-2.5/src/fsync.c     
udf-filesystem-2.5/src/udfdecl.h   
udf-filesystem-2.5/src/UDF_2.50-linux-2.6.24.patch
udf-filesystem-2.5/src/dir.c                      
udf-filesystem-2.5/src/udf_i.h                    
udf-filesystem-2.5/src/misc.c                     
udf-filesystem-2.5/src/ecma_167.h                 
udf-filesystem-2.5/src/unicode.c                  
udf-filesystem-2.5/src/symlink.c                  
udf-filesystem-2.5/src/ialloc.c                   
udf-filesystem-2.5/src/udfend.h                   
udf-filesystem-2.5/src/lowlevel.c                 
udf-filesystem-2.5/src/file.c                     
udf-filesystem-2.5/src/udf_fs.h                   
udf-filesystem-2.5/src/udf_sb.h                   
udf-filesystem-2.5/src/truncate.c                 
udf-filesystem-2.5/src/directory.c                
udf-filesystem-2.5/src/crc.c                      
udf-filesystem-2.5/src/balloc.c                   
udf-filesystem-2.5/src/Makefile                   
udf-filesystem-2.5/src/.tmp_versions/
[1]+  Done                    wget -O udf-filesystem-2.5.tar.gz [http://ubuntuforums.org/attachment.php?attachmentid=61993](http://ubuntuforums.org/attachment.php?attachmentid=61993)
nigel@Master:~/Downloads$ cd udf-filesystem-2.5 && ls
COPYING  Kbuild  Makefile  src
nigel@Master:~/Downloads/udf-filesystem-2.5$ echo "1150a1151" > tinypatch.patch
nigel@Master:~/Downloads/udf-filesystem-2.5$ echo "> (le16_to_cpu(((__le16 *)upm2->partIdent.identSuffix)[0]) == 0x0201) ||" >> tinypatch.patch
nigel@Master:~/Downloads/udf-filesystem-2.5$ patch src/super.c < tinypatch.patch
patching file src/super.c
nigel@Master:~/Downloads/udf-filesystem-2.5$ make
make -C /lib/modules/2.6.27-11-generic/build M=/home/nigel/Downloads/udf-filesystem-2.5 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/nigel/Downloads/udf-filesystem-2.5/src/balloc.o
In file included from /home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:22:
/home/nigel/Downloads/udf-filesystem-2.5/src/udfdecl.h:4:26: error: linux/udf_fs.h: No such file or directory
In file included from /home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:28:
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h: In function ‘UDF_I’:
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: warning: initialization from incompatible pointer type
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: error: invalid use of undefined type ‘struct udf_inode_info’
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function ‘__load_block_bitmap’:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:109: error: implicit declaration of function ‘udf_debug’
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function ‘udf_table_free_blocks’:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:446: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:512: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:514: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:543: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:556: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:557: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:569: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:597: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function ‘udf_table_prealloc_blocks’:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:633: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:635: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:642: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function ‘udf_table_new_block’:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:698: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:700: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:715: error: dereferencing pointer to incomplete type
make[3]: *** [/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.o] Error 1
make[2]: *** [/home/nigel/Downloads/udf-filesystem-2.5/src] Error 2
make[1]: *** [_module_/home/nigel/Downloads/udf-filesystem-2.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2
nigel@Master:~/Downloads/udf-filesystem-2.5$

---

### Post by mc4man on 2009-02-11
That patch is for the kernel hardy uses, 2.6.24, not the kernel in intrepid.
Intrepid supports UDF 2.5, but doesn't support the UDF version used by vista for disc's formatted as "live system"

When that patch is used in hardy then all UDF up to 2.5 (maybe even 2.6) are supported including the Vista "live system" version.

---

### Post by ozguitarplayer on 2009-02-11
thanks mc4man,
Just to be sure....does this mean that I cannot open any UDF in Intrepid?
Also...I'm new to Ubuntu however I've noticed that there are some things that Intrepid can't do that Hardy can do. As I understand it Hardy is older than Intrepid...is Hardy considered better or is it one of those..it's a matter of opinion issues...basically I need the most userfreindly and most compatable with other systems Linux distro..any suggestions or do I just wait for bug fixes with Intrepid?

---

### Post by mc4man on 2009-02-11
> does this mean that I cannot open any UDF in Intrepid?

No, just dvd's burned with vista's 'live system' format.

I think it's a matter of opinion mainly.

Edit: 'opinion' can also be taken to include usage and hardware compatibility.

I actually have both in a dual boot, I think hardy's great, Intrepid does have some advantages in area's that corncern me, mainly it's a bit easier to integrate the latest AV codecs and libs.



On the other hand I've had no issues doing what i want on hardy and it will be supported for a yr. longer than Intrepid.

So you could go either way.

My intrepid install is really a 'base' of intrepid with the bulk of the multimedia stuff installed and updated from debian-multimedia, (sid and experimental), with some jaunty packages thrown in. 

If it wasn't for it's ability be 'adapted' that way I wouldn't have bothered with it, hardy is extremely 'malleable' and easy to modify to suit. More of an experiment that I've come to like.

---

### Post by ozguitarplayer on 2009-02-11
thanks again mc4man,
I will try Hardy as a dual boot....and if I may..
How then do I open non dvd udf files like mp3's? I have followed most leads and suggestions without success..

---

### Post by mc4man on 2009-02-11
> How then do I open non dvd udf files like mp3's
It's usually better to start a new thread on different topics.
And also a little more specific goes a long way.
Like, I have some mp3's <here> and want to play them on <this player>  or I want to do <this> with them.
Usually you only need to install mp3 support in the form of a package or 2 depending on usage.

If your on kubuntu then going in a konsole

```
sudo apt-get install libxine1-ffmpeg
```

will prove to be very useful for kaffeine and amarok

---

### Post by ozguitarplayer on 2009-02-11
you're right I'll start a new thread...thanks for all the tips mc4man....

---

### Post by drpjkurian on 2009-04-30
Hi 

Can i have step by step instruction to install some programme so as to read udf file.

I am using ubunti hardy in dell vostro A860

With regards
Dr Kurian

---

