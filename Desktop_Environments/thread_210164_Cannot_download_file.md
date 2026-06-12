---
title: "Cannot download file"
date: 2006-07-06
forum: Desktop Environments
---

### Post by mishranurag on 2006-07-06
Whenevr, I try to download some file, firefox says it cannot, beacuse there is not enough space on /tmp/(some_random_folder). I have root partition of more than 8 Gb. Can anybody tell me what's going on? How can I free the space? Which files should I delete?

Anurag

---

### Post by atoponce on 2006-07-06
Anything in /tmp is safe to delete.  If I were you, I would delete everything in there.

---

### Post by taurus on 2006-07-06
Then why not have firefox save files to your home directory.  Create a temp and save everything to it...
```

mkdir ~/temp

```

---

### Post by mishranurag on 2006-07-06
Does that mean /tmp and consequently root paritition is full? I have 8 Gb of / partition.

---

### Post by taurus on 2006-07-06
Depending how much stuff you install or download, it could be full...  What is the output of this command, from a terminal?
```

df -h

```

---

### Post by mishranurag on 2006-07-07
> **taurus said:**
> Depending how much stuff you install or download, it could be full...  What is the output of this command, from a terminal?
```

df -h

```
I wanted to do that today but the system is not letting me log in. When I entered my username, password and pressed enter, it gave me following error. 

"XSession: warning: unable to write to /tmp. Xsession may exit with an error". I went to terminal by pressing Ctrl+Alt+F1 and removed couple of directories in /tmp, but its still not letting me log in. I am right now using Windows partition :(.

What's happening?

Anurag

---

### Post by atoponce on 2006-07-07
You can't log in graphically, but you can get in the terminal?  Delete everything in /tmp.  You don't need anything in there.

```
sudo rm -rf /tmp/*
``` 
Finally, check the permissions of your ~/.ICEauthority file.  It should be readable and writeable by you only (-rw-------).  Use

```
chmod 600 ~/.ICEauthority
``` 
if needed.

---

### Post by mishranurag on 2006-07-07
I did delete some files when logged in as terminal. The system did not let me login even after that. I will delete all the files the next time I try!

---

