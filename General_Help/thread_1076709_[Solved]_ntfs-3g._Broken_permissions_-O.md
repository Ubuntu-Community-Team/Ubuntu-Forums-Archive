---
title: "[Solved] ntfs-3g. Broken permissions :-O"
date: 2009-02-21
forum: General Help
---

### Post by _exn_ on 2009-02-21
Hello.

  Today i try to mount ntfs partitions in ubuntu, and got big problem about permissions.

  I try to mount partition as 
    ```

      /dev/sda5 /mnt/sda5 ntfs-3g defaults 0 0

      ls -l /mnt/
      total 52
       drwxrwxrwx 1 root root      8192 2009-02-21 23:42 sda5
    
```

  Ok, this is right, i know.

   ```

      /dev/sda5 /mnt/sda5 ntfs-3g umask=002,gid=1002,uid=1002 0 0

      ls -l /mnt/
       total 52
       drwxrwxr-x 1 uploader uploader  8192 2009-02-21 23:42 sda5
   
```
     
  Yeah, this is right too.

   ```

       su admin1
       $ id
        uid=1001(admin1) gid=1001(admin1) groups=115(admin),1001(admin1)
      
    $ mkdir /mnt/sda5/test
    $ ls -ld /mnt/sda5/test
drwxrwxr-x 1 uploader uploader 0 2009-02-22 00:14 /mnt/sda5/test

  
```

 WTF!!!!?? Why ??? 

 Any, any ideas please.

---

### Post by _exn_ on 2009-02-21
Sorry :redface:
 After apt-get upgrade all works fine. Just update and be happy :)

---

### Post by bodhi.zazen on 2009-02-21
Glad it is solved. Moved to general help and FYI I do not see what the problem was in the first place, everything in your first post seemed perfectly normal ;)

---

### Post by _exn_ on 2009-02-22
And one little note.
  Don't use ntfs-3g from ubuntu repositories. It is does not works.

 Allways compile that from source. 

  [This is tested  version ;)]("http://pagesperso-orange.fr/b.andre/download-tarball.html#ntfs-3g-2009.2.1AR.1.tgz")

---

