---
title: "Impossible to stop svnserve?"
date: 2008-11-06
forum: Desktop Environments
---

### Post by greg.harvey on 2008-11-06
We have a really weird problem. We have a normal Ubuntu desktop, v8.04, acting as a temporary development and Subversion server. It runs fine, but we are moving our SVN repository to somewhere more sensible (a proper RedHat server on our company back-up systems and in a server room, rather than beside my toes).

At first the new repository could not be used, because we could not commit, so having initially taken down SVN on the Ubuntu desktop machine, I started it up again:

```
killall svnserve
```
```
svnserve -d
```

So, a few weeks pass, IT resolve the commit issue on the RedHat machine, and we relocate again to the new repository location. To avoid mistakes and confusion, I want to switch off the old repository completely:

```
killall svnserve
```

I can still access the repository... Okaaaaay...

```
killall svnserve
svnserve: no process killed

```

D'oh! Repository still up! Ok, well for now I'll at least make it so it's read only:

```
chmod -R 444 /svn
```

Nope, I can *still* commit. Time to get nasty! 106 days of up time. Reboot the machine - that'll fix it. It's overdue a reboot anyway.

Nope! SVN is still there, even after a restart, still serving the repository, still allowing me to commit! Try to kill it again:

```
killall svnserve
svnserve: no process killed

```

No joy. Edit the svnserve.conf file, just in case, making sure all anon-access is off. Restart Ubuntu again. SVN *still* there!

For now we have just renamed the repository directory:

```
mv /svn/ /svn-old/
```

So people can't use it on the old URL, but if you use a repository browser and type in the new directory you can still access the old SVN repository.

We've given up!

Anyone seen this before? It seems impossible to stop svnserve. This whole box is on the brink of being formatted and Ubuntu replaced with CentOS (since our UAT, stage and production servers are all RedHat that makes sense anyway). =(

---

### Post by nickleus on 2008-11-06
what does this say:
```
ps aux|grep svnserve
```on my box i get:
> myuser   7362  0.0  0.1  10016   764 ?        Ss   13:50   0:00 svnserve --listen-port=3692 -d -r /srv/svn/repos/
if this doesn't work (as you say it doesn't):
```
sudo killall svnserve
```(although technically you didn't write "sudo" in your thread)
then try this:
```
sudo kill -9 7362
```where 7362 is the PID number from your output

---

