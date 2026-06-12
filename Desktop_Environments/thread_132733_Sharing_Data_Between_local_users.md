---
title: "Sharing Data Between local users"
date: 2006-02-18
forum: Desktop Environments
---

### Post by kelloggsx on 2006-02-18
First, most be honest! I been getting alot of help in this transition from M$ to the world of linux-ubuntu.. for that I thank everyone one.

Now to my next problem

In my window enviroment:
My wife and i share a win2k pc ( work/mp3s/movies/junk)
We have different users name (accounts) on the pc.
In order for us to have access to the same data on the pc regarless of the user, we save our information into a local directory (ex.  C:\OurData ).

Now in ubuntu:
How do i replicate that?  So far, i haven't be able to figure out how to create a directory under the "filesystem" ( i am assuming that is the C:\ ")  not sure why. or if that's even do-able.

Whenever i open Places-->Computer-->SystemFile    I am not able to right-click and create a forder there.

Any suggestion?

---

### Post by Mikecore on 2006-02-18
There is two ways for doing this.

1) from inside of the file manager just open up your / directory and created a a new folder ( maybe called "share" ) and after that right click on that folder go to "properties" and set your permissions so every body can read write to that folder.

2) you can use the shell like 

```



 cd /
sudo mkdir share
sudo chmod +rwx share


```

that should work everybody will be able to use that folder/directory

---

### Post by kelloggsx on 2006-02-18
I did step 2 and created a directory in my " / "  but i am unable to creat sub directorys or move files into it.

when i right click on the directory to see properties.. it said that i am not the ower or  have no rights ove it.

---

### Post by professor_chaos on 2006-02-18
#this command recursively changes the owner of the directory to you
sudo chown -R yourusername /share
#this recursively changes the permissions to rwx
chmod -R 777 /share

---

