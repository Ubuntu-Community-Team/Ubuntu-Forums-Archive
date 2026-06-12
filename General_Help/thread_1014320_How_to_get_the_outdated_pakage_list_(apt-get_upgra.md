---
title: "How to get the outdated pakage list (apt-get upgrade list)"
date: 2008-12-17
forum: General Help
---

### Post by Elv13 on 2008-12-17
Hi, here is a simple question, how can I get a list of package that need to be upgraded. I want to use it in a cron script so It have to just list package, not interact with a shell.

Thanks!

---

### Post by albinootje on 2008-12-17
> **Elv13 said:**
> Hi, here is a simple question, how can I get a list of package that need to be upgraded. I want to use it in a cron script so It have to just list package, not interact with a shell.

Thanks!

Do you want to do automatic updates every night ?
There's the package called cron-apt amongst others (I've used it for a while), but maybe you want : apticron

---

### Post by Elv13 on 2008-12-17
No, I want to do it myself, it is why I need a packages list. Diong an automiatic update is not hard at all, it look like

apt-get update
apt-get upgrade --force-yes

but I want to use a for loop like

apt-get update
for i in (the command) 
   my script
done

---

### Post by albinootje on 2008-12-17
> **Elv13 said:**
> 
but I want to use a for loop like

apt-get update
for i in (the command) 
   my script
done

If you use the command "sudo apt-get -d dist-upgrade" you can see which packages are marked to be upgraded, and perhaps you can grab that information to run your script.

---

### Post by Elv13 on 2008-12-17
Yes, but it still ask the [Y/N] question, I need to disable it if I want to get the packae list, thats my problem here.

---

### Post by albinootje on 2008-12-17
> **Elv13 said:**
> Yes, but it still ask the [Y/N] question, I need to disable it if I want to get the packae list, thats my problem here.

Okay, but if you run one script which nightly does :
sudo apt-get -d dist-upgrade > /tmp/output.txt
then you can work in another script while extracting the text in /tmp/output.txt and use both in a cronjob.
Think of tools like awk and sed.
Perhaps this idea is too difficult to achieve, but it's an idea.

---

### Post by Elv13 on 2008-12-17
Not dificult, just not practicable, it is a hack and is really cheap, this is for production, so even having to deal with the header and end of page feel cheap for a production script. I am sure there is a way somehow. After all how many apps have that list, I don't think they parsed apt-get.

---

### Post by cdtech on 2008-12-17
Install:
```
sudo apt-get install apt-show-versions
```
Then run:
```
$ apt-show-versions -u
login/intrepid-security upgradeable from 1:4.1.1-1ubuntu1.1 to 1:4.1.1-1ubuntu1.2
passwd/intrepid-security upgradeable from 1:4.1.1-1ubuntu1.1 to 1:4.1.1-1ubuntu1.2

```
Shows what packages in your system may be updated. The -u option displays a list of upgradeable packages.

---

### Post by Elv13 on 2008-12-17
Thanks! It work perfectly

---

