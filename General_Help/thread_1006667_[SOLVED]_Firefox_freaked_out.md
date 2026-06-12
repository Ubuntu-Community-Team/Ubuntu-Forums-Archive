---
title: "[SOLVED] Firefox freaked out"
date: 2008-12-09
forum: General Help
---

### Post by Kissell on 2008-12-09
This isn't the first time this has happened to me on the same machine, both times running Hardy v8.04 (2.6.24-22-server).  Last time it was fixed after reformatting.  I'd really like to avoid that if possible.

Symptoms: Firefox works just great until one day inexplicably when it's opened it no longer lets me use the back button, and doesn't display the current website in the address bar.  instead the address bar just displays the last address I typed in it, no matter what tab or page i'm on.

I've tried "apt-get purge firefox" but when I reinstall the same problem persists...  Once this occurs the only way I've been able to get rid of it is to reformat the PC, then it works fine, even after installing all my plugins and all the OS updates, but then for some reason one day it seemingly resorts to this behavior again.

---

### Post by Benbow on 2008-12-09
Unfortunately I can't help but I can offer sympathy. Mine  has done a similar thing since an update last night. So many problems that I cant list them but firefox is completely non functional. (64 bit system)

---

### Post by Kissell on 2008-12-09
mine's a 32-bit system, but it is extremely frustrating to use internet this way.  

if i go into the other room my 64-bit machine works just fine with firefox :)  but this is ridiculously frustrating using internet without being able to see the address of the page your on or being able to go back to the page you've been.

i know that if i just reformat it'll fix it, but i've done that before and the problem reappeared...  so i'd really like a fix.

---

### Post by kellemes on 2008-12-09
> **Kissell said:**
> This isn't the first time this has happened to me on the same machine, both times running Hardy v8.04 (2.6.24-22-server).  Last time it was fixed after reformatting.  I'd really like to avoid that if possible.

Symptoms: Firefox works just great until one day inexplicably when it's opened it no longer lets me use the back button, and doesn't display the current website in the address bar.  instead the address bar just displays the last address I typed in it, no matter what tab or page i'm on.

I've tried "apt-get purge firefox" but when I reinstall the same problem persists...  Once this occurs the only way I've been able to get rid of it is to reformat the PC, then it works fine, even after installing all my plugins and all the OS updates, but then for some reason one day it seemingly resorts to this behavior again.

Have you tried using a different profile?
From terminal..
```
firefox -ProfileManager
```

Click on 'Create Profile...' Click 'Next' and enter a name for the new profile. Click Finish to have Firefox create the new profile. Select new profile and start firefox.

You can go back to your own profile by starting Firefox using the command firefox -ProfileManager again, selecting your own profile, and clicking on 'Start Firefox'.

---

### Post by Kissell on 2008-12-09
No, I hadn't tried "firefox -ProfileManager"

That seems to have fixed it.  

Phew!  thanks so much, that will save me so much time and frustration.

But, any idea why I had to do that?  Somehow my default profile got corrupted?  hmmm...  I'd still like to pursue the cause a little, but this satisfied me 95% of the way.  So much better, thanks again!

---

### Post by Kissell on 2008-12-09
and that begs the question, why when i purge firefox does it not purge my firefox profile?  

):P

---

### Post by karlr42 on 2008-12-09
Well, as far as I know, apt-get purge won't remove your configuration files, which are in your home directory. That might explain why the problem persisted until you reinstalled, deleting those files in the process.

---

### Post by ajgreeny on 2008-12-09
There have been several instances of similar situations with FF going bonkers on people, and always a new profile seems to do the job.  It is easiest to start by renaming the old hidden .**mozilla** folder in ~ as .**mozillaold** and then restarting FF, which will make a new .mozilla folder.  You can then copy back the files and sub folders one by one until it you find the cause.  In this way you can at least keep your old bookmarks and extensions, but be aware that it often is extensions that cause problems with FF, so just be carefull.

And, No, purge will not get rid of the .mozilla nor .mozilla-thunderbird folders in ~, which is very good news as that is where a lot of your personal info, eg emails etcf etc is stored.  In fact I don't think purge removes any configurations in ~, just those in /etc and other system folders.

---

### Post by kellemes on 2008-12-10
> **ajgreeny said:**
>  And, No, purge will not get rid of the .mozilla nor .mozilla-thunderbird folders in ~, which is very good news as that is where a lot of your personal info, eg emails etcf etc is stored.  In fact I don't think purge removes any configurations in ~, just those in /etc and other system folders.

Indeed. Uninstalling an application shouldn't remove personal data.
In general, uninstalling will only remove data generated at install.

Following will explain how to import old profile to new profile..
[http://kb.mozillazine.org/Profile_Manager#Creating_a_new_profile]("http://kb.mozillazine.org/Profile_Manager#Creating_a_new_profile")

As to why your profile got corrupted.. I'm afraid I don't know.
It could be some plugin that's screwing with your profile, or maybe it's just a bug.

Obviously you can always consider using another browser, [Opera]("http://www.opera.com/") is on my recommendation list.

---

