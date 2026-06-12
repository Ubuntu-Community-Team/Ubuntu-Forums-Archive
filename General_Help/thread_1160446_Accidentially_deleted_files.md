---
title: "Accidentially deleted files"
date: 2009-05-15
forum: General Help
---

### Post by Brasker on 2009-05-15
Hey, I was wondering how I would go about recovering deleted files? or if there is a way, I accidentially deleted some system files

---

### Post by prem1er on 2009-05-15
How did you delete them? With the rm command?

---

### Post by Brasker on 2009-05-15
yea i used sudo rm

---

### Post by sailthesea on 2009-05-15
What happened?
 You could restore system files from disc or with some terminal commands (not sure which) Or they may be in the Trash!
 It can't be that bad or you would have downed the computer :) Edit : Ooops!

---

### Post by Brasker on 2009-05-15
The files I deleted are ssh_host_dsa_key.pub  ssh_host_rsa_key.pub ssh_config ssh_host_dsa_key  ssh_host_rsa_key. I tried purging the installation of ssh, and reinstalling, and that didn't work, I also tried the lsof command, but nothing happened. EDIT: also checked the trash, no there

---

### Post by kanikilu on 2009-05-15
I don't think there's an easy way to recover those. I know people recommend utilities like testdisk (package is in the repos.), but I've never used it, so you might want to search around.

Also, to prevent future mistakes, you might want to look into the **trash-cli** package...

---

### Post by sailthesea on 2009-05-15
You should be able to sudo get the missing files
 Am not too sure of the exact commands I'm only just learning to use Terminal it can be very obvious sometimes and very hard others

---

### Post by unutbu on 2009-05-15
ssh is merely a metapackage. Try reinstalling openssh-client:
```

sudo apt-get --reinstall install openssh-client
```

---

### Post by Brasker on 2009-05-15
No dice, did not work unutbu, or sailthesea, and I am unsure of how to restore from the disk

---

### Post by unutbu on 2009-05-15
Oops. I think these files are generated when openssh-server is installed. (See [http://ubuntuforums.org/showthread.php?t=732860](http://ubuntuforums.org/showthread.php?t=732860)).
So perhaps try
```

sudo apt-get --reinstall install openssh-server
```

---

### Post by Brasker on 2009-05-15
AH HA! Great success! I like! thank you very much sir.

---

