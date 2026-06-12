---
title: "Issue with init.d script in cronjob"
date: 2009-02-03
forum: General Help
---

### Post by ZiaTioN on 2009-02-03
I am trying to call one of my init.d script from a cronjob and it seems to be failing.  here is the cronjob entry (in root's crontab).

**15 */3 * * * /usr/bin/service script restart >>/tmp/script_crontab.txt 2>&1**

I redirected the output to this tmp file to try and catch any errors that may be thrown and low and behold I get this.

**env: invoke-rc.d: No such file or directory**

Can the system not find invoke-rc.d?  I have had env issues with crontab before due to the fact that cronjobs are executed outside of any shell environment but I used to run this very cronjob on Fedora systems for years.

Any idea on how I can alleviate this issue?

---

### Post by ZiaTioN on 2009-02-03
bump...

---

### Post by dcstar on 2009-02-03
> **ZiaTioN said:**
> I am trying to call one of my init.d script from a cronjob and it seems to be failing.  here is the cronjob entry (in root's crontab).

**15 */3 * * * [B]/usr/bin/service** script restart >>/tmp/script_crontab.txt 2>&1[/B]

I redirected the output to this tmp file to try and catch any errors that may be thrown and low and behold I get this.

**env: invoke-rc.d: No such file or directory**

Can the system not find invoke-rc.d?  I have had env issues with crontab before due to the fact that cronjobs are executed outside of any shell environment but I used to run this very cronjob on **Fedora **systems for years.

Any idea on how I can alleviate this issue?

Ubuntu is not Fedora, it does not have that service binary.

---

### Post by ZiaTioN on 2009-02-04
> **dcstar said:**
> Ubuntu is not Fedora, it does not have that service binary.

```

root@Freedom:# cat /etc/issue
Ubuntu 8.10 \n \l

root@Freedom:# whereis service
service: /usr/bin/service /usr/share/man/man1/service.8.gz

root@Freedom:# ll /usr/bin/service
-rwxr-xr-x 1 root root 3250 2008-10-14 08:02 /usr/bin/service

```

Sure looks like it does to me.  The crontab command works fine when I run it from a shell env manually, it is an issue with cron.

---

### Post by ZiaTioN on 2009-02-04
bump...

---

### Post by ZiaTioN on 2009-02-04
sorry but I have to keep bumping to try and catch the right person I guess.

---

### Post by liquidpele on 2009-02-04
Your error is this:

env: invoke-rc.d: No such file or directory

"env" refers to environmental variables.  If it works when you run it manually, but not when cron runs it, the issue is probably that cron does not have some env variables set that your user does.

You can type "env" in the command line and hit enter to have it print a list of your user's variables, then see what you need to set for the cron script to run correctly. 

how to set env varibles:
[http://www.codecoffee.com/tipsforlinux/articles/030.html](http://www.codecoffee.com/tipsforlinux/articles/030.html)

---

### Post by ZiaTioN on 2009-02-05
Yes thank you but I stated that I already knew that this was the problem in my original post.  My concern was not that it was having a problem running my init script but that it was having a problem running one of it's own system binaries. I should not have to tell it how to find one of it's own apps.

cron path: PATH=/usr/bin:/bin
bash path: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

According to what cron has access to via it's PATH env variable, it should be able to access /usr/bin/service because /usr/bin is in it's path but it is still unable to find it.  This was my question.  In the end what it turned out to be was that it was able to run the service binary but this service binary calls the invoke-rc.d binary which is in a path that is NOT in cron's env.

```

root@Freedom:# whereis invoke-rc.d
invoke-rc: /usr/sbin/invoke-rc.d

```

I could do sudo -s in the cronjob to invoke the users shell env before running the job but this just seems like a hack 1. because it would prompt for my password thus killing the automated nature of cron and 2. it is just a lame thing to have to do :-). I was looking for a more permanent, viable solution.  Is there a way to permanently update crons env?

---

### Post by liquidpele on 2009-02-05
To permanently set env variables:

[http://www.cyberciti.biz/faq/environment-variable-change-on-linux-freebsd-unix-bash/](http://www.cyberciti.biz/faq/environment-variable-change-on-linux-freebsd-unix-bash/)

---

### Post by dcstar on 2009-02-05
> **ZiaTioN said:**
> ```

root@Freedom:# cat /etc/issue
Ubuntu 8.10 \n \l

root@Freedom:# whereis service
service: /usr/bin/service /usr/share/man/man1/service.8.gz

root@Freedom:# ll /usr/bin/service
-rwxr-xr-x 1 root root 3250 2008-10-14 08:02 /usr/bin/service

```

Sure looks like it does to me.  The crontab command works fine when I run it from a shell env manually, it is an issue with cron.

Sorry, my 8.04 version does not have it - which is why people should specify the version they are actually using when posting questions.

And as you have discovered, cron runs in its own environment. The /etc/crontab file has an example of how the system crontab sets things up.

---

