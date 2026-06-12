---
title: "Erase/Shred  File Completely"
date: 2006-03-28
forum: Desktop Environments
---

### Post by granny4linux on 2006-03-28
I want to completely erase a few files from my hard drive rather than just delete them. Does anyone know of a program like this?

---

### Post by art on 2006-03-28
on the command line
shred filename

---

### Post by NESFreak on 2006-03-28
synaptic
applications-->install aplication the (simpelest way)
is you wanna see all apps then choose file-->advanced

---

### Post by granny4linux on 2006-03-28
Art, you're the man, thank you. This could not have been more obvious, except to a Newbie who is still learning the command line.

---

### Post by granny4linux on 2006-03-28
[QUOTE=art]on the command line
shred filename[/QUOTE]

Now that I've learned the "shred" command exists, I wanted to know more so I went to help for shred and this is what I'm now wondering about:
"CAUTION: Note that shred relies on a very important assumption:
that the filesystem overwrites data in place.  This is the traditional
way to do things, but many modern filesystem designs do not satisfy this
assumption.  The following are examples of filesystems on which shred is
not effective:

* log-structured or journaled filesystems, such as those supplied with
  AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)"

The files I am trying to erase completely are on an EXT 3 partition; according to the help file the shred command won't delete them. Any other suggestions?

---

### Post by VonMarschall on 2006-03-28
Does shred do a forensic wipe of the file?  If so, what standard does it use?
 
Gutmann?
US DoD 3 Pass?
US DoD 7 Pass?
Pseudorandom Data 1 Pass?

I use a program called "Wipe" that is capable of all of the above, but if Shred does it, I may just use that.  The goal is permanent erasure of files without the potential of recovery by any means.

Thanks!

---

### Post by engla on 2006-03-28
**Addition:** Yeah, I'm kind of late. :)
Note that the shred manual page says
>        CAUTION:  Note  that  shred relies on a very important assumption: that
       the filesystem overwrites data in place.  This is the  traditional  way
       to  do  things,  but many modern filesystem designs do not satisfy this
       assumption.  The following are examples of filesystems on  which  shred
       is not effective:

       * log-structured or journaled filesystems, such as those supplied with

              AIX and Solaris (and JFS, ReiserFS, XFS, **Ext3,** etc.)


Ext3 is the default filesystem with Ubuntu, so there is no guarantee that this will work for forensic-class purposes or perhaps even simpler recovery means.

---

### Post by VonMarschall on 2006-03-28
Here is the link to Wipe.  Check it out.

[http://wipe.sourceforge.net/](http://wipe.sourceforge.net/)

Enjoy!

---

### Post by engla on 2006-03-28
[QUOTE=VonMarschall]Does shred do a forensic wipe of the file?  If so, what standard does it use?
 
Gutmann?
US DoD 3 Pass?
US DoD 7 Pass?
Pseudorandom Data 1 Pass?

I use a program called "Wipe" that is capable of all of the above, but if Shred does it, I may just use that.  The goal is permanent erasure of files without the potential of recovery by any means.

Thanks![/QUOTE]
What I know it doesn't claim to use any standard. Here is a test run with --verbose and --zero
```
$ shred --zero --verbose test
shred: test: pass 1/26 (random)...
shred: test: pass 2/26 (db6db6)...
shred: test: pass 3/26 (eeeeee)...
shred: test: pass 4/26 (666666)...
shred: test: pass 5/26 (444444)...
shred: test: pass 6/26 (888888)...
shred: test: pass 7/26 (cccccc)...
shred: test: pass 8/26 (000000)...
shred: test: pass 9/26 (222222)...
shred: test: pass 10/26 (777777)...
shred: test: pass 11/26 (aaaaaa)...
shred: test: pass 12/26 (b6db6d)...
shred: test: pass 13/26 (random)...
shred: test: pass 14/26 (333333)...
shred: test: pass 15/26 (111111)...
shred: test: pass 16/26 (dddddd)...
shred: test: pass 17/26 (ffffff)...
shred: test: pass 18/26 (999999)...
shred: test: pass 19/26 (6db6db)...
shred: test: pass 20/26 (bbbbbb)...
shred: test: pass 21/26 (249249)...
shred: test: pass 22/26 (924924)...
shred: test: pass 23/26 (555555)...
shred: test: pass 24/26 (492492)...
shred: test: pass 25/26 (random)...
shred: test: pass 26/26 (000000)...

```
It overwrites the file with the patterns above in turn (some of the patterns are random). It also zeroes the file on the last run since I asked it to *--zero*

You can also specify the number of times, if 25 is not enough.

---

### Post by VonMarschall on 2006-03-28
25 passes should be plenty!  3 is actually enough, and some drive recovery companies won't even attempt to recover a drive that has been wiped with one pass.  My security guy can't recover a one pass drive with encase.  (Little fun test we did)

---

### Post by engla on 2006-03-28
There is also [THC's SecureDelete release]("http://www.thc.org/releases.php?s=8&q=&o=") with several tools like srm. Not much information on the site though, but there are claims it's better than wipe in the README :)

---

### Post by art on 2006-03-28
the thing with shred is that it may not delete the backups the file had, so it is perfect when wiping partition, but for a single file maybe wipe, or there is even a secure-delete
[http://www.thc.org/download.php?t=r&f=secure_delete-3.1.tar.gz](http://www.thc.org/download.php?t=r&f=secure_delete-3.1.tar.gz)
will do the job better. I am not sure if these delete the backups too.

---

### Post by elamericano on 2006-03-28
Wipe doesn't work for individual files when "you're wiping a file in a log structured file system" - in other words Ext3. As far as I know Secure Delete shares this limitation as well. It may be that journaling filesystems haven't taken this functionality into account, which would explain why there appear to be no programs that can do it.

I'd using Ext2 and shred, or stick to wiping entire partitions.

-EA

---

### Post by engla on 2006-03-28
[QUOTE=elamericano]Wipe doesn't work for individual files when "you're wiping a file in a log structured file system" - in other words Ext3. As far as I know Secure Delete shares this limitation as well. It may be that journaling filesystems haven't taken this functionality into account, which would explain why there appear to be no programs that can do it.

I'd using Ext2 and shred, or stick to wiping entire partitions.

-EA[/QUOTE]
I found a claim that you could unmount an ext3 partition and remount it as ext2 when you want to shred files. That should be possible but I don't know if the journal would be damaged.

Otherwise, there must be some kind of kernel hook for this to get around the journaling.

---

### Post by art on 2006-03-28
After some reading it appears to me that there is NO way to completely wipe a file in a journalled file system, so shred or wipe or secure-delete are all the same to some extent... One can always wipe a partition though...

---

### Post by engla on 2006-03-28
[QUOTE=art]After some reading it appears to me that there is NO way to completely wipe a file in a journalled file system, so shred or wipe or secure-delete are all the same to some extent... One can always wipe a partition though...[/QUOTE]
There must be a way for the kernel to do it. For example, you can put swapfiles (not partitions) on a journalled filesystem. The kernel then makes sure that the journal ignores the swapfile (for performance reasons). In the same way, the kernel could "exempt" a file from journaling during the time of the shredding.

---

### Post by mandragor on 2006-11-18
According to this link it should still work:
[http://www.slac.stanford.edu/comp/unix/secure-erase.html](http://www.slac.stanford.edu/comp/unix/secure-erase.html)

The reasoning is that ext3 only contains metadata about the file,
so no real content will be revealed by the journaling filesystem.
Also, check out the "scrub"-program that enables secure wiping of
free space.

---

