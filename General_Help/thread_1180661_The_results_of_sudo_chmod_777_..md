---
title: "The results of sudo chmod 777 /.*"
date: 2009-06-07
forum: General Help
---

### Post by oof on 2009-06-07
Hi,


I CD to specific directory on the Desktop and mistakenly typed:

sudo chmod 777 /.*

Instead of 

sudo chmod 777 ./*

The results are catastrophic: Ubuntu cannot restart, and I do not know how to restore it to its the previous phase.
 

Maybe you have any idea

Thanks,
Oof

---

### Post by _Purple_ on 2009-06-07
You can use a live CD to backup your work somewhere else and then reinstall.

---

### Post by DeMus on 2009-06-07
> **_Purple_ said:**
> You can use a live CD to backup your work somewhere else and then reinstall.

I second that since I think you are in deep ****. Changing folder and file properties of system files is a terrible thing to do and results, as you have seen, in a not working system.
Backup your important stuff (don't forget the hidden files and folders) and start all over.

---

### Post by Phasmagon on 2009-06-07
Actually then only thing you can do is what is mentioned above. There no way to restore the file permission to what the were before. At least not on all files and you 're better off reinstalling the system. Then coping the files you own, to reset the permissions on them too. But I can't help myself on commenting.

You used SUDO to change permissions on a folder you OWN.
Please don't do that.
That's why Ubuntu does not allow you (by default) to log in as root.

---

### Post by ActiveFrost on 2009-06-07
You can't fix it ! The one and only choice is to backup your data and reinstall Ubuntu.
Good luck ;)

---

### Post by sisco311 on 2009-06-07
> **oof said:**
> Hi,

...

The results are catastrophic: Ubuntu cannot restart, and I do not know how to restore it to its the previous phase.
 

Maybe you have any idea

Thanks,
Oof

Try to boot in recovery mode and restore the permissions:
```
chmod 0755 /
chmod 0755 /*
chmod 1777 /tmp
chmod 0750 /root
chmod 0700 /lost+found

```

If you can boot in recovery mode, then boot a liveCD, mount the root partition and restore the permissions.

---

### Post by theozzlives on 2009-06-07
When you re-install, make a seperate /home partition by selecting: Manual.

---

### Post by oof on 2009-06-07
> **sisco311 said:**
> Try to boot in recovery mode and restore the permissions:
```
chmod 0755 /
chmod 0755 /*
chmod 1777 /tmp
chmod 0750 /root
chmod 0700 /lost+found

```If you can boot in recovery mode, then boot a liveCD, mount the root partition and restore the permissions.

I'll try this option before doing anything too drastic.  It is not clear to me: does the command "chmod ... /.*" change also sub-directories, or it is restricted only to the directories on the root. 



Thanks all for the help,
Oof

---

### Post by sisco311 on 2009-06-07
> **_Purple_ said:**
> You can use a live CD to backup your work somewhere else and then reinstall.

> **DeMus said:**
> I second that ...

> **Phasmagon said:**
> Actually then only thing you can do is what is mentioned above. ...

> **ActiveFrost said:**
> You can't fix it ! The one and only choice is to backup your data and reinstall Ubuntu.
Good luck ;)

> **theozzlives said:**
> When you re-install, make a seperate /home partition by selecting: Manual.

The chmod command is NOT recursive by default. 

/.* means all the files (and directories) in the root ("/") directory including the hidden files/directories ( . = current directory and .. = parent directory) but NOT the sub-directories. 

The OP only needs to restore the permissions on the above mentioned directories. So there is NO need for a re-install.

---

### Post by sisco311 on 2009-06-07
> **oof said:**
> I'll try this option before doing anything too drastic.  It is not clear to me: does the command "chmod ... /.*" change also sub-directories, or it is restricted only to the directories on the root. 



Thanks all for the help,
Oof

It's restricted only to the directories.

---

### Post by oof on 2009-06-10
0> **sisco311 said:**
> Try to boot in recovery mode and restore the permissions:
```
chmod 0755 /
chmod 0755 /*
chmod 1777 /tmp
chmod 0750 /root
chmod 0700 /lost+found

```If you can boot in recovery mode, then boot a liveCD, mount the root partition and restore the permissions.


sisco311, 


It seems that ubuntu works exactly as before after I changed the root permission according to your advice in the recovery mode (is there anythings else I need to do now to be sure ubuntu is  fully restored?). 
So thank you, and thanks all the other for trying to help (and I also want to thank god I was not listening to their advice ;))


What other dangers should I be aware of in this respect, and does ubuntu have any option of restoring itself (In my case, I must sudo many times in different ways, and it is impossible not to make simple misprints sometimes)

---

### Post by Lucky75 on 2009-06-10
LOL, this is why you always get a second (or sometimes, sixth) opinion.

I think you should be okay now, since you essentially undid what you did in the first place and just set the permissions back. Just watch for anything unusual, and check if permissions are the problem if something else breaks.

---

### Post by danger89 on 2010-03-03
Uhm, I did this stupid thing also mistakenly...
Should Ubuntu to make a confirm messange for only the input arg '/'?

---

### Post by derrick81787 on 2010-03-03
> **danger89 said:**
> Uhm, I did this stupid thing also mistakenly...
Should Ubuntu to make a confirm messange for only the input arg '/'?

Well, there are two problems with what you and the original poster did.  First of all, if you own the directory, you shouldn't use sudo.  Just doing chmod without sudo would have worked just fine.

Second of all, there is no reason to run
```
chmod 777 ./*
```
You can run
```
chmod 777 *
```
and it will give you the exact same results, but there is practically no chance that you will accidentally change your root directory's permissions.

Putting a warning message might not really hurt anything, but there are a million commands that someone can run to screw up their system, and it would be difficult and annoying to have confirmation messages for them all.

- Derrick

---

