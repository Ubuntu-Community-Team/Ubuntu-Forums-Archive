---
title: "CIFS VFS: Server Not Responding on Shutdown"
date: 2009-06-25
forum: General Help
---

### Post by measekite on 2009-06-25
**Jaunty 9.04**

I finally go fstab to work and auto mount my network shares on my Win2K server.  I have 2 issues.

1.  I cannot unmount them.  The error dialog says only root can unmount them.  This did not happen under Feisty but Jaunty is a different animal.

2.  The bigger issue is when I do a shut down I get an error like:

1529.004048  CIFS VFS: Server Not Responding and it takes about 30 to 40 more seconds to shut down the machine.

What is funny is that the file system in my fstab describes it as smbfs.

**Does anybody know what is happening?**

---

### Post by jt_04 on 2009-07-14
I have the same error on shutdown in Jaunty.  Have you come across any solutions yet?

---

### Post by measekite on 2009-07-15
> **jt_04 said:**
> I have the same error on shutdown in Jaunty.  Have you come across any solutions yet?

Yes.

I wrote a script that called dismount.sh and placed it in my Script folder
/home/username/Scripts.  [COLOR=Blue]Make sure you change the permissions to executable![/COLOR]

```
umount /media/yourdrivename
```Then place the full path name prefaced by sudo in
[COLOR=Red]**/etc/gdm/PostSession/Default**[/COLOR]
```

#!/bin/sh
sudo /home/username/scripts/dismount.sh

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```

---

### Post by ubradford on 2009-12-06
I found a fix for this problem on Karmic. I posted it here:
[http://ubuntuforums.org/showthread.php?t=1347340](http://ubuntuforums.org/showthread.php?t=1347340)

---

