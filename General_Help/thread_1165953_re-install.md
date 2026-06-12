---
title: "re-install"
date: 2009-05-21
forum: General Help
---

### Post by sevenearths on 2009-05-21
just a quick question about reinstalling.

My machine froze up during an update and it's never been the same since. Now some of the apps that I use regularly are acting weird so I have opt'ed for a re-install.

Has anyone got any advice for re-installing and keeping all your stuff?

[LIST=1]
[*]I know if I copy my /home directory to another location I'll be able to reuse it
[*]I know if I run a backup on my MySQL db I'll keep al my data (though I don't know if I'll keep all my users?!?)
[*]Will my /var/www still be there after a re-install
[*]does it matter if I don't do a reformat before a reinstall?
[*]if i'm doing php and python stuff with apache should I save my configs or just reinstall all my web stuff?
[*]how do I get a list of all the packages I have installed with 'apt-get install'?
[/LIST]

any other advice about re-installing and keeping your stuff would be greatly appreciated

---

### Post by blazemore on 2009-05-21
Back up /var/www and copy it back after
Yes, you should reformat
If you know where your configs are, back them up. If it won't take too long, just reconfigure your web stuff

---

### Post by sevenearths on 2009-05-31
I think your right. Cheers!

---

