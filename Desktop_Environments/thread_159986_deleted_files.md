---
title: "deleted files"
date: 2006-04-13
forum: Desktop Environments
---

### Post by mjunior on 2006-04-13
Hi guys, my doubt this time is regarding deleted files. I had two .ods files that desapeared yesterday..they were in a shared folder ( I have another user on the same pc), so I presume it was her who deleted those files.
I already logged in using her username but those files aren't on the trash box anymore (not even on recent files list).
Is there a way to recover it?

Thanks in advance.

---

### Post by cilynx on 2006-04-13
If you --really-- need the files back, look into 'unrm'.  It's a pretty mean program not for beginner use, but it does get the job done for data recovery.  If you're going this route, do it as soon as possible.  The less disk activity between delete and recovery, the better your chances.

---

### Post by mjunior on 2006-04-14
No luck..
Couldn't find the urnm on aptitude search..
I found this link on how to use: [http://staff.washington.edu/dittrich/talks/blackhat/tct/man/man1/unrm.1.html](http://staff.washington.edu/dittrich/talks/blackhat/tct/man/man1/unrm.1.html)

I tried the undelete on aptitude search then and installed the gtkrecover.. but running it, there's an error:"segmentation fail"

Any tip?](*,)

---

### Post by cilynx on 2006-04-14
'unrm' is part of the 'tct' forensic tools package.  You also may want to look into 'recover'.  Be careful as a lot of file recovery tools are exclusive to ext2 as opposed to working with ext3 (ubuntu default).  If you read the docs on 'recover', it gives you some hints for dealing with ext3.

---

### Post by mjunior on 2006-04-14
[QUOTE=cilynx]'unrm' is part of the 'tct' forensic tools package.  You also may want to look into 'recover'.  Be careful as a lot of file recovery tools are exclusive to ext2 as opposed to working with ext3 (ubuntu default).  If you read the docs on 'recover', it gives you some hints for dealing with ext3.[/QUOTE]


Humm..that quite explains the error I got with gtkrecover previously...
I found this tool on a web search..it covers ext2 and 3 and says guarantee for Debian, but is paid: [http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm)
Do you know some similar for free?

Thanks so far for your tips...

---

### Post by mjunior on 2006-04-14
Althogh the software I posted on last reply says recover ext3 guarantee, I found this Faq that says it's not possible for safety reasons to recover anything from ext3 but from ext2...it seems final: ([http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html))
Q: How can I recover (undelete) deleted files from my ext3 partition?
A:Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.

---

### Post by cilynx on 2006-04-14
It does kinda sound like w/ ext3 you're pretty much SOL.

See [http://recover.sourceforge.net/unix/]("http://recover.sourceforge.net/unix/") for what looks to be the only light

---

### Post by mjunior on 2006-04-16
I'm givin up..seems like the lfile literaly not exist anymore..

marcelojunior@mjunior:~$ sudo grep -f "divida" /dev/hda1
grep: divida: Arquivo ou diretório não encontrado
marcelojunior@mjunior:~$


Thanks for your help anyway.

---

### Post by cilynx on 2006-04-16
Sorry to hear that.  I hope your future adventures go better.

---

