---
title: "Folder Permissions"
date: 2009-01-05
forum: General Help
---

### Post by optimistique1 on 2009-01-05
Hi All

In my home folder I have another folder called 'Examples' which I want to delete.

However, the permissions are for 'root' and it will not let me delete or move.

Can someone please advise 'HOW' I change the permissions on this folder?

Many thanks

Garry

---

### Post by notquiterite on 2009-01-05
do you want to delete it or do you want to change the owner on it?

to delete it type
```
sudo rm -r /home/username/Examples 
```  

username would obviously be replaed with whatever your user name is. If you want to change the permissions on it you can do either of the following. remember... replace username with YOUR username

this will allow anyone to delete the folder

```
 sudo chmod 777 /home/username/Examples
```

this will make you the owner

```
 sudo chown username /home/username/Examples
```

---

### Post by jerome1232 on 2009-01-05
Just a note I believe that "folder" is actually a symlink to /usr/share/example-content.

You can simply remove the symlink rather than deleting recursvly. You don't even need root privileges. (at least I didn't)

```
rm ~/Examples
# or if it gave you permission denied.
sudo rm ~/Examples
```

---

