---
title: "/var/cache/apt/archives/ PROBLEMS HELP ME"
date: 2009-01-12
forum: General Help
---

### Post by catoodubhagain on 2009-01-12
So I went into this directory in nautilus and deleted the files


"/var/cache/apt/archives/" 

well now i have problems everywhere


cato@cato-laptop:~$ sudo apt-get clean
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Unable to read /var/cache/apt/archives/partial/ - opendir (2 No such file or directory)


then i cannot install any software in synaptic either because of this 

AN ERROR OCCURRED 

The following details are provided: 

E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Unable to lock the download directory


how do i fix this?

Thanks
Cato

---

### Post by oldos2er on 2009-01-12
If you deleted them in Nautilus, then they're most likely in root's trash, and you should be able to restore them from there.

---

### Post by wolfen69 on 2009-01-12
```
sudo mkdir /var/cache/apt/archives/partial
``` will restore the directory.

---

### Post by cb34 on 2009-01-12
> **wolfen69 said:**
> ```
sudo mkdir /var/cache/apt/archives/partial
``` will restore the directory.i think he'll first have to create the archives dir, then make the partial dir.. no?
-----

edit-> sorry man, you're right. he didn't delete the archives dir just the partial dir inside.
i wasn't reading his problem correctly. my mistake.

---

### Post by WitchCraft on 2009-01-12
> **cb34 said:**
> i think he'll first have to create the archives dir, then make the partial dir.. no?

no, this will create the archive dir if it doesn't exist.

---

### Post by cb34 on 2009-01-12
but his problem is that is is looking for the /var/cache/apt/archives/partial dir

archives dir has to exist for partial to exist inside it. ??
-----

edit-> oh you're right, he does have the archives dir still in tact, thought he deleted the archives dir all together.. sorry.

---

### Post by iaculallad on 2009-01-12
Follow this steps:

To fix this error make sure you recreate the archives folder as well as the partial folder. open a console window and type


1.Change directory to your APT directory:

```
cd /var/cache/apt
```

2. Type the ls command to check if your archives folder exist, if it doesn't, create it:

```
sudo mkdir archives
```

3. Issue the commands below while on /var/cache/apt directory:

```
cd archives
sudo mkdir partial

```

4. Then, issue the command below to check if we got it working:

```
sudo apt-get autoclean
```

---

### Post by cb34 on 2009-01-12
what if he doesn't want to nuke the files in his archives dir. he didn't delete it from what i understand.. just deleted the partial dir.

---

### Post by iaculallad on 2009-01-12
> **cb34 said:**
> what if he doesn't want to nuke the files in his archives dir. he didn't delete it from what i understand.. just deleted the partial dir.

OP can just proceed to step number 3 from the post above.

The safest way to delete the content of your archive folder is to use the command:

```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by cb34 on 2009-01-12
i just think when telling someone those clean commands, it should be explained what they do in case they dont know.. because when i first started with ubuntu, someone told me that, and i cleaned my archives and i didn't want to, i was saving things so i dont waste my bandwidth that my isp rip me off capping the gigs. that's all i meant.

---

