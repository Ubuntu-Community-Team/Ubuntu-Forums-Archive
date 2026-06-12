---
title: "how to see htm &amp; html files"
date: 2005-12-10
forum: Desktop Environments
---

### Post by ShirishAg75 on 2005-12-10
Hi there, 
          this is in reference to the thread started by me, [here]("http://ubuntuforums.org/showthread.php?t=100653") but didn't quite make it. I tried to do the following things :-

Firstly tried running the code given
```
cd /
sudo chmod -x `find . -name '*.htm'`
sudo chmod -x `find . -name '*.html'`
```
This gave me a permission denied error, this prompted me to give an 
```
sudo su
``` command & saw that I became root. Then tried running the same command & got two errors first time it was argument is too short, then argument is too long, both by bash. Of course both the times 'sudo' was not used now, another thing is it necessary to run the updatedb command regularly, for just to make sure also did that but no difference. Can anybody help me?

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=shirishag75]Hi there, 
          this is in reference to the thread started by me, [here]("http://ubuntuforums.org/showthread.php?t=100653") but didn't quite make it. I tried to do the following things :-

Firstly tried running the code given
```
cd /
sudo chmod -x `find . -name '*.htm'`
sudo chmod -x `find . -name '*.html'`
```
This gave me a permission denied error, this prompted me to give an 
```
sudo su
``` command & saw that I became root. Then tried running the same command & got two errors first time it was argument is too short, then argument is too long, both by bash. Of course both the times 'sudo' was not used now, another thing is it necessary to run the updatedb command regularly, for just to make sure also did that but no difference. Can anybody help me?[/QUOTE]
A couple of points:
1) There should not be any executable HTML files in your system directories, so you should probably just run your script in your home directory.  That way you won't run into permission problems.
2) If you still get errors, can you print out the exact messages?  It sounds like you might need to use xargs, but I can't be sure without knowing exactly what went wrong.

---

### Post by ShirishAg75 on 2005-12-10
the thing is all the htm & html files are in windows parition. Now I wanna look at them. Without going the whole copy & paste routine. As far as the exact error is concerned after doing sudo su the error is/was
```
bash::chmod the argument is too long
``` I haven't written it down exactly but that's the closest I can come to it.

---

### Post by stuporglue on 2005-12-10
I think that means it found too many files to run the command on. Try running that command inside each sub directory, instead of just in your home directory.

---

### Post by ShirishAg75 on 2005-12-10
yup, it was argument list too long, o.k. will do thnx, btw do I need to run updatedb daily & if yes, then how to change the time to do something like in the afternoon or something, any ideas?

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=shirishag75]yup, it was argument list too long, o.k. will do thnx, btw do I need to run updatedb daily & if yes, then how to change the time to do something like in the afternoon or something, any ideas?[/QUOTE]
You could change it in /etc/crontab.  There is a line that looks like this:
```

25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily

```
That is running all the scripts in /etc/cron.daily at 6:25 AM, I think.  The /etc/cron.daily/slocate script is probably updating your file location DB.

---

