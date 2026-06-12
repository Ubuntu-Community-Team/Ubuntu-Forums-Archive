---
title: "[SOLVED] Bash: /usr/bin/amazonmp3 no such file, but the file is there!"
date: 2008-12-13
forum: General Help
---

### Post by jamesrl on 2008-12-13
I have installed amazonmp3 in the past.  Today I tried to use it, but firefox wouldn't let me (it said error when opening it).  I then tried to launch amazonmp3 manually, and it wouldn't launch.

The key confusing part being:
```

computername:~/install$ /usr/bin/amazonmp3 
bash: /usr/bin/amazonmp3: No such file or directory
computername:~/install$ ls -l /usr/bin/amazonmp3
-rwxr-xr-x 1 root root 668208 2008-03-01 13:19 /usr/bin/amazonmp3
computername:~/install$ file /usr/bin/amazonmp3
/usr/bin/amazonmp3: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped

```
The file is there, and has information in it (as seen by file, or say 'strings /usr/bin/amazonmp3' and isn't a link or hard-link.  I can uninstall amazonmp3, it goes away, and then reinstall it and it comes back, but I still get "bash: /usr/bin/amazonmp3: No such file or directory".

I should add that I am using 64 bit (x86_64) ubuntu 8.10, so installing is a little more complicated then normal.  My first thought was to try uninstalling everything related, and reinstalling it again.   I then uninstalled (dpkg --purge) both amazonmp3, getlibs and ia32-libs (and associated 32 bit libraries), and tried reinstalling from scratch, following the procedure outlined elsewhere (e.g., [here]("http://ubuntuforums.org/showpost.php?p=5522318&postcount=1"), [here]("http://liltux.wordpress.com/2008/05/29/how-to-install-amazonmp3-on-a-64-bit-xubuntu/")) for installing amazonmp3 in 64 bit ubuntu.  Installation seems to work fine, but the application won't launch as bash claims it can't find the executable.  

Here's detailed explanation of what what I did to reinstall.
First, take the ubuntu 7.04 version from amazon.com (I am running 8.10 but that shouldn't make a difference).
Second, use the getlibs script: 
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs)
to install the dependencies:
```


computername:~/install$ sudo dpkg -i --force-architecture amazonmp3.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package amazonmp3.
(Reading database ... 179939 files and directories currently installed.)
Unpacking amazonmp3 (from amazonmp3.deb) ...
Setting up amazonmp3 (1.0.3-1) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

computername:~/install$ file /usr/bin/amazonmp3
/usr/bin/amazonmp3: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
computername:~/install$ /usr/bin/amazonmp3 
bash: /usr/bin/amazonmp3: No such file or directory
computername:~/install$ which amazonmp3
/usr/bin/amazonmp3
computername:~/install$ amazonmp3 
bash: /usr/bin/amazonmp3: No such file or directory
computername:~/install$ sudo getlibs /usr/bin/amazonmp3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32asound2 lib32ncurses5 lib32z1
The following NEW packages will be installed:
  ia32-libs lib32asound2 lib32ncurses5 lib32z1
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 395kB/23.8MB of archives.
After this operation, 109MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ubuntu.media.mit.edu intrepid/main lib32z1 1:1.2.3.3.dfsg-12ubuntu1 [75.6kB]
Get:2 http://ubuntu.media.mit.edu intrepid/main lib32asound2 1.0.17a-0ubuntu4 [320kB]
Fetched 395kB in 1s (258kB/s)        
Selecting previously deselected package lib32z1.
(Reading database ... 179952 files and directories currently installed.)
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3.3.dfsg-12ubuntu1_amd64.deb) ...
Selecting previously deselected package lib32asound2.
Unpacking lib32asound2 (from .../lib32asound2_1.0.17a-0ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.6+20071124-1ubuntu2_amd64.deb) ...
Selecting previously deselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu18_amd64.deb) ...
Setting up lib32z1 (1:1.2.3.3.dfsg-12ubuntu1) ...

Setting up lib32asound2 (1.0.17a-0ubuntu4) ...

Setting up lib32ncurses5 (5.6+20071124-1ubuntu2) ...

Setting up ia32-libs (2.2ubuntu18) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
This application isn't missing any dependencies

computername:~/install$ /usr/bin/amazonmp3 
bash: /usr/bin/amazonmp3: No such file or directory
computername:~/install$ ls -l /usr/bin/amazonmp3
-rwxr-xr-x 1 root root 668208 2008-03-01 13:19 /usr/bin/amazonmp3

```
I then installed it on another 64 bit computer (my laptop) where it installed on the first try with no problems, and was able to send myself to link to download the album I bought.  But it still bothers me ...

Also for anyone who thinks this is a bash problem (like I have an alias somewhere), (da)sh can't find the file either.
```

computername:~$ sh
$ amazonmp3
sh: amazonmp3: not found
$ /usr/bin/amazonmp3
sh: /usr/bin/amazonmp3: not found
$ cd /usr/bin
$ ls -l amazonmp3
-rwxr-xr-x 1 root root 668208 2008-03-01 13:19 amazonmp3
$ /usr/bin/amazonmp3
sh: /usr/bin/amazonmp3: not found
$ file /usr/bin/amazonmp3
/usr/bin/amazonmp3: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
$ 

```

---

### Post by aigulf on 2008-12-17
I'm having a similar problem with an m2ts file I'm trying to convert.  m2tstoavi complains that the file (00001.m2ts) is not present, but it shows up in ls, and will even play in XBMC.

```
$ m2tstoavi 00001.m2ts 
using:
./xporthdmv
./ldecod
/usr/bin/ffmpeg
/usr/local/bin/m2tstoavi Starting.
 
file 00001.m2ts not found

```

I've determined that the problem with me is that the file is failing a csh existence check

```
if(! -f $file) then
    echo file $file not found
    exit
endif
```

But, what I don't know is why it returns FALSE for -f $file.  Can anyone explain this?

jamesrl, can you run the following script on your file, and let me know if it fails the same check as mine?
```
#!/bin/sh

set files=($*)

foreach file ($files)
    if( -f $file) then
        echo file $file found
    else
        echo file $file not found
    endif
end
```

---

### Post by Bulletbeast on 2008-12-17
You're lucky, guys. Same thing happens to me with /sbin/init at startup.

---

### Post by jamesrl on 2008-12-20
Your script didn't work as written but a small modification:

```
#!/bin/sh

for file; do
  if [ -e $file ]; then
      echo "file $file found"
  else
      echo "file $file not found"
  fi
  if [ -f $file ]; then
     echo "file $file is a regular file"
  fi
  if [ -x $file ]; then
      echo "file $file is an executable"
  fi
  if [ -s $file ]; then
      echo "file $file has a non-zero length
  fi
done

```
So test.sh /usr/bin/amazonmp3 gives me:
```

comp-name:~$ sh filetest.sh /usr/bin/amazonmp3 
file /usr/bin/amazonmp3 found
file /usr/bin/amazonmp3 is a regular file
file /usr/bin/amazonmp3 is an executable
file /usr/bin/amazonmp3 has a non-zero length
comp-name:~$ amazonmp3 
bash: /usr/bin/amazonmp3: No such file or directory
comp-name:~$ bash filetest.sh /usr/bin/amazonmp3 
file /usr/bin/amazonmp3 found
file /usr/bin/amazonmp3 is a regular file
file /usr/bin/amazonmp3 is an executable
file /usr/bin/amazonmp3 has a non-zero length

```

The -f expression fails (as it should), since it is not a 'regular' file.  From man sh:
```
            -b file       True if file exists and is a block special file.

            -c file       True if file exists and is a character special file.

            -d file       True if file exists and is a directory.

            -e file       True if file exists (regardless of type).

            -f file       True if file exists and is a regular file.

            -g file       True if file exists and its set group ID flag is
                          set.

            -h file       True if file exists and is a symbolic link.

            -k file       True if file exists and its sticky bit is set.

            -n string     True if the length of string is nonzero.

            -p file       True if file is a named pipe (FIFO).

            -r file       True if file exists and is readable.

            -s file       True if file exists and has a size greater than
                          zero.

            -t file_descriptor
                          True if the file whose file descriptor number is
                          file_descriptor is open and is associated with a
                          terminal.

            -u file       True if file exists and its set user ID flag is set.

            -w file       True if file exists and is writable.  True indicates
                          only that the write flag is on.  The file is not
                          writable on a read-only file system even if this
                          test indicates true.

            -x file       True if file exists and is executable.  True indi&#8208;
                          cates only that the execute flag is on.  If file is
                          a directory, true indicates that file can be
                          searched.

            -z string     True if the length of string is zero.


```

---

### Post by jamesrl on 2008-12-20
I believe my problem is related to running 32 bit executables in 64 bit architecture (x86-64), and the proper libraries not being able to be found when I attempt to execute it.  However, I believe all the proper libraries are installed ... as a nearly identical setup (according to synaptic) on my laptop (also x86-64) works.  

I should also add that other 32 bit applications are failing on me as well.  For example, wine and acroread don't work lead me to the potential problem.

On further inspection:
```
computer:~$ wine
bash: /usr/bin/wine: No such file or directory
computer:~$ which wine
/usr/bin/wine
computer:~$ acroread 
exec: 572: /lib/ld-linux.so.2: not found

```

Comparing my desktop to my laptop shows that I am is missing /lib/ld-linux.so.2 (which according to my laptop should be a link to /lib32/ld-linux.so.2 which is also missing on my desktop.)

---

### Post by jamesrl on 2008-12-20
Ok, /lib/ld-linux.so.2 should be in libc6-i386 which according to synaptic was properly installed.  I just reinstalled the package within synaptic and now everything (wine/amazonmp3/acroread) is working again.

---

### Post by chappel on 2009-01-26
I had the exact same issue running the 'unlocker' program necessary to access my IronKey USB flash drive.  It works fine on my AMD64 system running 8.1, but not on a Dell precision 490 or 470 running 8.1.  I installed 'libc6-i386' as suggested (even though it says it's intended for AMD64 and I'm running intel), but it gave me this error:

root@BYV1DH1:/media/IronKey/linux# ./ironkey
./ironkey: error while loading shared libraries: libgcc_s.so.1: cannot open shared object file: No such file or directory

I didn't find any useful info regarding libgcc_s.so.1, but on a whim I installed 'lib32gcc1', and that fixed it.

Thanks a lot for posting all the helpful suggestions.  :KS

---

