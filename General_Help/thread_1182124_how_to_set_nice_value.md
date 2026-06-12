---
title: "how to set nice value"
date: 2009-06-08
forum: General Help
---

### Post by luke0927 on 2009-06-08
OK i figured out how to open a program with higher nice value but it does not save it and then the program runs and saves files to the root account and not the default path.  How can i permanently set the nice value so every time I open that program i don't have to specify the nice I would be setting it below 0.


Thanks

---

### Post by sisco311 on 2009-06-09
Only a privileged user may run a process with lower ([-20,-1]) niceness.

Add this line to the /etc/security/limits.conf file:
```
yourusername        -        nice        -10
```

(Log out and log back in!)

Then run the process as your regular(non-root) user:
```
/usr/bin/nice -n -10  *command*
```

---

### Post by luke0927 on 2009-06-09
I added the line below, but after logging back in it still would not allow me to change the value unless i used sudo when trying to run a program at -10 any idea on what i did wrong?

(copying and pasting it messed up the tabs in the file its spaced correctly)



#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
[COLOR="Red"]Luke		 -        nice        -10[/COLOR]
# End of file

Edit

After reading it on here I had a capital L.  im still thinking windows! changed it to lowercase and it works 

thanks!

---

