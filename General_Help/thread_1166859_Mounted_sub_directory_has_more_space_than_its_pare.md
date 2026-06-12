---
title: "Mounted sub directory has more space than its parent... conflict"
date: 2009-05-22
forum: General Help
---

### Post by RavUn on 2009-05-22
At work we have /var allocated to 2 gigs and the IT dept mounted 6 gigs of space for us to use in /var/www/html.  The problem is that the files for /var/www/html are being counted as space used in /var.  What should happen to correct this issue?  I filed an issue and the IT guy said it's working the way "it's designed to".  This "design" is the issue, though!  

Any suggestions?  Should they just make /var the 6gigs or mount the 6 gigs somewhere else and use that location as the web server directory?  Or, is it possible to have more space in the sub-directory somehow?  I don't know if it'd be possible to mount the space somewhere else and have a pointer to that location from inside /var/www/html and if we did that would the files still count towards used space in /var?

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/VolGroup00-LogVol00
                       7935392   3120844   4404948  42% /
/dev/mapper/VolGroup00-LogVol02
                       1967952     42608   1823764   3% /home
/dev/mapper/VolGroup00-LogVol03
                       2063164     68788   1887880   4% /tmp
/dev/mapper/VolGroup00-LogVol04
                       2190096   2078176         0 100% /var
/dev/sda1               101086     18657     77210  20% /boot
tmpfs                  1029908         0   1029908   0% /dev/shm
/dev/sdb1              6190664   1316172   4560024  23% /var/www/html

```

---

