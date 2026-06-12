---
title: "rm -r emergency"
date: 2005-10-15
forum: Desktop Environments
---

### Post by escobar on 2005-10-15
I was half sleep, and I just wanted to remove the 'hdb1' folder within /media/. I did not want to delete the sub-directories. Long story short I ran the above command and trashed it all. I'm going to remain calm because there is was to bring it back, right? Please tell me this is possible.

If it helps this is a fat32 drive. Anyone think a Windows restore app will help? Also, I found this command for Solaris by Googling:

ufsrestore 0f /dev/rmt/0 

Does anyone know if fat32restore of /media/hdb1 will work? I actually don't want to do anything unless I know it will work. 

Thanks for any help. I'll keep searching.

---

### Post by daller on 2005-12-01
Since you question seems quite urgent, I assume you have this sorted out!

(Just to have one unanswered question less)

---

### Post by escobar on 2005-12-05
[QUOTE=daller]Since you question seems quite urgent, I assume you have this sorted out!

(Just to have one unanswered question less)[/QUOTE]


I had to boot into windows and run a restore app on my machine. Took more hours than I cared to count but I recovered the majority of what I lost. Thanks though.

---

### Post by guice on 2005-12-05
woohoo! I linux forum is NEVER complete w/out a mistaken rm -r command! Way to go. Welcome to the world of linux where when it's gone, it's gone. :twisted:

Reminds me of the good ol' days when a co-worker did rm -rf * in /etc when he thought he was in his home directory. And a manager that did rm -rf * in his home directory where he thought he was in a directory he was trying to blow away.

Moral of the story, don't use rm -r unless you're *absolutely sure* you know what you're doing. ;)

---

### Post by chaumurky on 2005-12-05
Maybe these scripts may help in future...
 
[http://www.intuitive.com/wicked/showscript.cgi?015-newrm.sh]("http://www.intuitive.com/wicked/showscript.cgi?015-newrm.sh")
 
and
 
[http://www.intuitive.com/wicked/showscript.cgi?016-unrm.sh]("http://www.intuitive.com/wicked/showscript.cgi?016-unrm.sh")
 
;-)

---

