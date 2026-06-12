---
title: "Tool To Format File Names for Windows Naming Rules?"
date: 2009-03-27
forum: General Help
---

### Post by irregardlessly on 2009-03-27
Hi everyone.  I am unfortunately in that boat where I use Ubuntu primarily (yay) but still need to use Windows (boo) for work.  Anyway, I have a large external hard drive in NTFS format which I access from both Ubuntu (Hardy at the moment) and Windows XP.  I am mostly writing data to it from the Ubuntu side, and reading from the Windows side.  I have a lot of files which came from the linux side which I can't read from Windows because of invalid file names.  I am pretty sure Ubuntu is letting me write files with characters that are not allowed in Windows file names.

I could, through trial and error or looking for docu, figure out which characters are bad, find/write some kind of script to strip them out and rename from the linux side.  But I was wondering if this problem is already solved and anyone knows of a util to do this automatically.  I see a lot of mass renamers but nothing smart enough to format correctly for Windows.

Thanks.

---

### Post by irregardlessly on 2009-06-21
I know this is probably elementary for most people on here but I will explain the process I'm going through for the benefit of any n00bs like myself.  (Not new to linux, just new to scripting and command line stuff more complex than equivalents of DOS operations.)

Looks like the windows forbidden characters are:
\ / : * ? " < > |
(Thanks [http://www.xvsxp.com/files/forbidden.php]("http://www.xvsxp.com/files/forbidden.php"))

I haven't written this script yet, but I have gotten good results at least identifying problematic files by doing stuff like this.  From the directory you want to start searching...

```

ls -R | grep \>

```

So this will find all files or directories containing a >.  You need the \ to escape it else it will think you are redirecting your output.  I was able to search for all of the characters above doing stuff like this except for \ itself.. I get an error from grep when using \\.  Also note that since *nix uses / as the directory separator I don't think you can have file names containing it... I certainly don't... so I wasn't worried about that one.  Also : is not very helpful because you get the top of every directory listing.  It's a start though.

---

