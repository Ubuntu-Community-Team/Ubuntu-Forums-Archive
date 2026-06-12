---
title: "Backup SVN using Bash script and TAR"
date: 2009-03-18
forum: General Help
---

### Post by Buggin1965 on 2009-03-18
I thought this was going to be easy. I want to automatically backup my subversion repository using a simple script that cron will run once a week.

```

#!/bin/bash
date=`date +%Y%m%d`
svnadmin dump /home/svn/bmu | tar cvfn /home/svn/backup/$date.bmu.svn.dump.tgz
svnadmin dump /home/svn/bmu2 | tar cvfn /home/svn/backup/$date.bmu2.svn.dump.tgz

```

I keep getting an error message that says that the pipe is broken.

I can successfully dump the repository with this command:
```
svnadmin dump /home/svn/bmu2 > bmu2.svn.dump
```

But I want to be able to direct where the output file is created and I also want to compress the dump.

Is there an easier way? Or Do you know what I am doing wrong?

Thank you.

---

### Post by Buggin1965 on 2009-03-24
I am still having problems with this script.  If this is not the right area to ask for help, can someone please point me in the right direction.

Should I simply use two lines instead of one?

I am new to linux and scripting in bash.

I have done google searches for information on how to use the pipe properly, but I can't find a basic explanation that I understand. 

Also what is this character "~" called and how do you use it in the command line?

Thank you.

---

### Post by Slim Odds on 2009-03-24
> **Buggin1965 said:**
> But I want to be able to direct where the output file is created and I also want to compress the dump.

Is there an easier way? Or Do you know what I am doing wrong?
 

Well, for starters, tar wants a list of file not just some data.

You might want to just pipe to gzip or bzip2

the "~" is equal to /home/<your user name>

---

### Post by merlin_rbs on 2009-04-07
You could try something like:

svnadmin dump /path/to/svn/repos > /path/to/tmp/svn_repos.dump; tar -jcf /path/to/backup/repos-`date +%d%m%y`-rev`svnlook youngest /path/to/svn/repos`.tar.bz2 /path/to/tmp/svn_repos.dump

---

