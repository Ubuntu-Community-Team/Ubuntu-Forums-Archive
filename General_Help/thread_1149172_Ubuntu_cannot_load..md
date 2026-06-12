---
title: "Ubuntu cannot load."
date: 2009-05-05
forum: General Help
---

### Post by Reyes1986 on 2009-05-05
Hi, I am EXTREMELY new to Ubuntu and I was messing around with files and then my OS froze, I went to restart it and now it says the following:

> 
LOADING MANUAL DEVICES...

modprobe: WARNING: /etc/modprobe.d/alsa-base.conf.save Line 5: Ignorning b...starting with "^x"

Can somebody please help me? I just installed Ubuntu too

Thanks

---

### Post by paradigm2 on 2009-05-05
> **Reyes1986 said:**
> Hi, I am EXTREMELY new to Ubuntu and I was messing around with files and then my OS froze, I went to restart it and now it says the following:


Can somebody please help me? I just installed Ubuntu too

Thanks

Hmmm.  Are you getting dumped into a terminal or is it still freezing entirely?

If you can get a terminal maybe try:

```

sudo alsaconf

```

This will try to reconfigure alsa which appears to be the problem.

If you cannot even get to a terminal, see:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

and try the above command once you can.

---

### Post by gamblor01 on 2009-05-05
It looks like you just accidentally inserted a bad character into your /etc/modprobe.d/alsa-base.conf.save

If you can get to a terminal you might just try to edit that file and see if you can remove the offending character(s).  The ^ character usually implies ctrl in the terminal.  So it looks like line 5 has a ctrl+x character in the beginning of it.  modprobe (a program that adds/removes modules from the kernel) seems to be choking on that line....in theory that should only prevent your sound from working properly.

---

### Post by Reyes1986 on 2009-05-05
I am at the recovery par t what command I type to fix it ??

---

### Post by paradigm2 on 2009-05-05
> **Reyes1986 said:**
> I am at the recovery par t what command I type to fix it ??

I would probably in your case try 

```

sudo alsaconf

```

---

### Post by Reyes1986 on 2009-05-05
Sorry but it says command not found :(

---

### Post by paradigm2 on 2009-05-05
> **Reyes1986 said:**
> Sorry but it says command not found :(

Darn. :(

In that case maybe just:

EDITED: Actually don't do this part I edited.

instead just:

```

rm /etc/modprobe.d/alsa-base.conf.save

```

then

```

shutdown -r now

```

Explanation:

That *.save file was automatically created and it is trying to load that because it is in /etc/modprobe.d and this is messing things up.  There probably is a alsa-base.conf there which will work already.

---

### Post by Reyes1986 on 2009-05-05
Still can't find it? Cannot remove "" read-only file

---

### Post by paradigm2 on 2009-05-05
> **Reyes1986 said:**
> Still can't find it?

What did you type exactly and what error did it give you exactly?

I edited the post but I think I was too late.

try

```

rm /etc/modprobe.d/alsa-base.conf.save

```

and if you did the other things I edited out already (Sorry, we're gettign rid of the files we just created), also do:

```

rm /etc/modprobe.d/backup-alsa-base.conf.save

```


```

rm /etc/modprobe.d/backup-alsa-base.conf

```

Finally

```

shutdown -r now

```

---

### Post by Reyes1986 on 2009-05-05
Your goi g to kill mr it's saying that cannot remove read only file and the last twosays no such file..

---

### Post by paradigm2 on 2009-05-05
> **Reyes1986 said:**
> Your goi g to kill mr it's saying that cannot remove read only file and the last twosays no such file..

Progress.

See what happened is the "/etc/modprobe.d" directory which works with modules for the kernel.  EVERY file in there, no matter what extension, is automatically loaded.  When you were editing this before it crashed and created a *.save file whichit is tryign to load.  That is screwing things up.

We have to get rid of that file "/etc/modprobe.d/alsa-base.conf.save"


Try this

```

chmod ugo+rw /etc/modprobe.d/alsa-base.conf.save

```

then

```

rm /etc/modprobe.d/alsa-base.conf.save

```

finally (if it all worked)

```

shutdown -r now

```


** If you get an error about operation not permitted, let me know.

---

### Post by Reyes1986 on 2009-05-05
Thank u I appreciate the help I will try again tomorrow i'm exhausted I will keep you updated

---

### Post by paradigm2 on 2009-05-05
> **Reyes1986 said:**
> Thank u I appreciate the help I will try again tomorrow i'm exhausted I will keep you updated

You're welcome. It was late for me as well and I didn;t realize what directory we were in... I should have caught that far earlier...

Hope it works...

---

### Post by gamblor01 on 2009-05-05
> **paradigm2 said:**
> What did you type exactly and what error did it give you exactly?

I edited the post but I think I was too late.

try

```

rm /etc/modprobe.d/alsa-base.conf.save

```and if you did the other things I edited out already (Sorry, we're gettign rid of the files we just created), also do:

```

rm /etc/modprobe.d/backup-alsa-base.conf.save

``````

rm /etc/modprobe.d/backup-alsa-base.conf

```Finally

```

shutdown -r now

```


That first command isn't going to work.  You're trying to edit a file in /etc/modprobe.d as a regular user.  Thus you get the error about not being able to edit a read only file:

> 
it's saying that cannot remove read only file and the last twosays no such file..
You need to prefix the command with sudo so that you temporarily elevate yourself to root privileges.  I wouldn't just flat out remove the file without first checking to see that the original one does indeed exist however.

You can the use command

```

ls -l /etc/modprobe.d/alsa-base.conf*

```It should show (along with a bunch of details about the file such as permissions, owner, group, etc.) at least 2 files there.  You can also use the cat command to list the contents of the file:

```

cat /etc/modprobe.d/alsa-base.conf

```I would run that and make sure it looks reasonable.  If you want to do a diff on the files to see where they are different then:

```

cd /etc/modprobe.d
diff alsa-base.conf alsa-base.conf.save

```According to your error output earlier, they should differ on line 5.  Assuming the alsa-base.conf file looks reasonable then I would just run:

```

sudo rm /etc/modprobe.d/alsa-base.conf.save
sudo shutdown -r now

```Apparently neither of those backup* files exist so you shouldn't need to worry about them.  Just run the two commands above and it should remove the file and then reboot immediately.

---

### Post by Reyes1986 on 2009-05-05
Everything works _however_ it won't let me delete it via sudo b/c it's a read only file?

Edit: origional file alsa-base does exsit when I did dir in terminal to view files alsa-base.conf.save is --rw

---

### Post by Reyes1986 on 2009-05-05
Anybody else out there? I really want to take advantage of ubuntu and learn it's awesome features!

---

### Post by paradigm2 on 2009-05-05
> **Reyes1986 said:**
> Anybody else out there? I really want to take advantage of ubuntu and learn it's awesome features!

```

sudo chmod ugo+rw /etc/modprobe.d/alsa-base.conf.save

```

```

sudo rm /etc/modprobe.d/alsa-base.conf.save

```

---

### Post by Reyes1986 on 2009-05-05
okay , but wasn't this same script as before?i will try it now and reposit with edit

Edit: cannot remove "" read-only file system
Edit#2: I've tried sudo rm -i -f "filename" still no avail

---

### Post by Reyes1986 on 2009-05-05
Okay guys, to make a long story short, I just reinstalled it (after hours of thinking on what to do next)

thank you all

---

