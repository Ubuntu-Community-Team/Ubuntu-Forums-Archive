---
title: "Looking for a good backup Tools"
date: 2009-05-19
forum: General Help
---

### Post by Ioky on 2009-05-19
Appealingly , Linux is a very stable system. I almost don't need to any re-installation of the OS, except for upgrade, and change Distro.

SO I have a very head sketching problem, that is find out a good way to back up my data. Back into the day, while using windows, that is not a problem because before my date goes up to 4GBs, I will eventually need to re-install my OS for various reason, except for one time, that it actually goes up to 60GB for some reason, before something funny happen. 

I guess I only really need one function from whatever the backup tool might be, is that I want it backup one folder, and all the it's sub-*. And have it check once a week, to see if any new stuff got into the folder, or any file that got modify. save the new stuff in whatever they should be, and save an extra copy of the modified file, into my ext-harddrive. 

I know that might be a silly question, but really, I usually just burn DVD / CD for back up, with take forever and ever. but I guess now, I should take advantage of my ext-harddrive. It would be even better, if the software will check my ext-harddrive, and let me know when it is about die or something start going wrong. So I can do my part to save my data.

Thanks........

---

### Post by Jive Turkey on 2009-05-19
the program rsync (CLI version) is what I use for backing up my data.  There is a GUI version called grsync in the repositories too.  You could read up how to set up cron jobs to schedule an rsync command to be run at certain intervals.  

I'm not sure what kind of disk checking you have in mind but if you run the command:
```
apropos disk
``` you will get lots of hints toward programs that do stuff with disk.
then if one looks like it might do what you need then type ```
man <nameofprogram>
``` you will get a man page telling you how it works

---

### Post by HermanAB on 2009-05-19
Rsync is your friend.  

The standard way is to add a two line script to /etc/cron.daily so it will run every morning at 4 am.

The trick is to include say /home and then exclude the directories/files you *don't* want transferred, so that the script doesn't need any maintenance.  Then you can forget about it and let it do its thing.

There is also a similar things called rbackup and rsnapshot, but they are hard to find with Google due to a plethora of commercial offerings.  Google isn't what it used to be - guess it is time for a competitor to come to the fore.

---

### Post by kpkeerthi on 2009-05-19
+1 for rsync. Checkout [grsync]("http://www.opbyte.it/grsync/screenshot.html") if you need a GUI.

```
rsync -a /home/Data /media/Backup
```

---

