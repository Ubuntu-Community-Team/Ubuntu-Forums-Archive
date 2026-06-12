---
title: "Synaptic Trouble"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Natev2 on 2006-02-28
When I open up Synaptic I get an error message right away that states:
> Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
The list of sources could not be read.
Go to the repository dialog to correct the problem.

It fails to download any of the repository indexes and I get no package listings to come up. I then pushed the reload button and again it fails to download or show any repository package information and I get another error reading:
> E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
E: Unable to lock the list directory

I then went to check my repositories under settings --> repositories and I get the same error as when I tried the reload button.

After a reboot I still have the problem.

Any direct help or directions to a previous thread providing help would be greatly appreciated.

---

### Post by hod139 on 2006-02-28
Just wondering, if you open a console and type
```

ls /etc/apt/sources.list

```
does it return 
```
/etc/apt/sources.list
```
or 
```
/etc/apt/sources.list:  No such file or directory
```

I'm just checking if your sources.list file exists

---

### Post by bluevoodoo1 on 2006-02-28
[QUOTE=hod139]I'm just checking if your sources.list file exists[/QUOTE]

If it does exist, perhaps you could post it here. 

```
gedit /etc/apt/sources.list
```

---

### Post by Natev2 on 2006-02-28
nope no file
> ls /etc/apt/sources.list: No such file or directory

I wonder how i mangaged to deleted it

---

### Post by bluevoodoo1 on 2006-02-28
check out the bottom of this page for a listing of Breezy sources
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

```
sudo gedit /etc/apt/sources.list
```

paste in repositories, save. Then

```
sudo apt-get update
```

---

### Post by Natev2 on 2006-02-28
Thanks, that seems to have fixed things

---

