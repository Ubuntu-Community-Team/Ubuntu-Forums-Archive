---
title: "How to empty root's Trash contents?"
date: 2009-04-11
forum: General Help
---

### Post by dodle on 2009-04-11
I learned the command to empty root's Trash, but I can only do it as root (su).  Is there a way I can use this same command as a sudoer (sudo)?

This is the command I am using: (**WARNING:** Only use this command if you know what you are doing!)
```
rm -r /root/.local/share/Trash/files/* /root/.local/share/Trash/info/*
```If I try it as a sudoer, I get the following output:
```
rm: cannot remove `/root/.local/share/Trash/files/*': No such file or directory
rm: cannot remove `/root/.local/share/Trash/info/*': No such file or directory

```

---

### Post by quazi on 2009-04-11
You could restore the trash and then, as a sudoer, remove the files.

---

### Post by dodle on 2009-04-11
> **quazi said:**
> You could restore the trash and then, as a sudoer, remove the files.

I'm not sure what you mean, the Trash does not need restored.  It's a permission issue.  I have to be logged in as root to empty root's Trash.

---

### Post by ibuclaw on 2009-04-11
Why would you even have Trash in the root trash folder if you don't (supposedly) login as root?

```
ls /root/.local/share
```
If the directory doesn't exist, **the directory doesn't exist**. :)

Also, do you have a separate home partition?
If so, the root's Trash contents would be instead stored in:
> /home/.0-Trash
Try:
```
ls -A /home
```
and see what output it shows.

Regards
Iain

---

### Post by snova on 2009-04-11
> **tinivole said:**
> ```
ls /root/.local/share
```
If the directory doesn't exist, **the directory doesn't exist**. :)

Unless, of course, Bash wasn't globbing the files in there because it couldn't read /root/.local/.

I don't know how to get around it; except by running a shell as sudo:

```
sudo "sh rm /root/.local/share/Trash/{files,info}/*"
```

But that's far from an elegant solution.

---

### Post by dodle on 2009-04-11
> **tinivole said:**
> Why would you even have Trash in the root trash folder if you don't (supposedly) login as root?

```
ls /root/.local/share
```
If the directory doesn't exist, **the directory doesn't exist**. :)

The directory does exist.  Items go into root's Trash folder if they have been deleted using nautilus started with gksu.

> **snova said:**
> I don't know how to get around it; except by running a shell as sudo:

```
sudo "sh rm /root/.local/share/Trash/{files,info}/*"
```

But that's far from an elegant solution.It's not working for me.  I get the following error:```
command not found
```

---

### Post by snova on 2009-04-11
> **dodle said:**
> The directory does exist.  Items go into root's Trash folder if they have been deleted using nautilus started with gksu.

It's not working for me.  I get the following error:```
command not found
```

Silly me.

```
sudo bash -c "exec rm /root/.local/share/Trash/{files,info}/*
```

Really ugly, but I don't know of better way to do the globbing...

---

### Post by dodle on 2009-04-11
> **snova said:**
> ```
sudo bash -c "exec rm /root/.local/share/Trash/{files,info}/*
```I still get "no such file or directory".

I'm not going to worry about too much.  I've created a script:```
#! /bin/bash

sudo rm -r ~/.local/share/Trash/{files,info}/*
```I just have to log in as **su** to empty the root's trash.  That's good enough for now.

Thanks snova for showing me how to use {files,info}.

---

### Post by snova on 2009-04-11
> **dodle said:**
> I still get "no such file or directory".

If there are no files in there, Bash will leave the glob as it is, and "*" presumably doesn't exist in there either. :)

---

### Post by dodle on 2009-04-11
No, I made sure that were files in root's Trash.

```
$ sudo bash -c "exec rm -r /root/.local/share/Trash/{files,info}/*"
rm: cannot remove `/root/.local/share/Trash/files/*': No such file or directory
rm: cannot remove `/root/.local/share/Trash/info/*': No such file or directory

```

---

### Post by dodle on 2009-04-11
Sorry, it's working.  I was doing something wrong.  Apparently it worked when I thought it didn't and the next time I tried it the directory was empty.  Thanks snova, this is exactly what I wanted.

```
sudo bash -c "exec rm -r /root/.local/share/Trash/{files,info}/*"

```

---

### Post by mc4man on 2009-04-11
If you are sure about deleting files when in gksudo nautilus then there is a 'delete' option  the same as is available for nautilus (file management -> behavior

To access run 
```
gksudo nautilus-file-management-properties
```

I would strongly suggest not changing anything else in there

---

### Post by quazi on 2009-04-12
> **dodle said:**
> I'm not sure what you mean, the Trash does not need restored.  It's a permission issue.  I have to be logged in as root to empty root's Trash.

What I mean, is that in order to delete the files permanently, it might be easier to restore them first and then just delete them from the command line:
```
sudo rm whatever
```

---

### Post by Elep.Repu on 2009-08-11
I deleted a bunch of files, but I don't have a .local on /root/

---

### Post by michy99 on 2009-08-11
Any file or directory that starts with a dot (.) is hidden. To see it in nautilus, press Ctrl+H or show hidden files under View menu. To see it in terminal, enter```
ls -a
```

---

### Post by Elep.Repu on 2009-08-11
> **michy99 said:**
> Any file or directory that starts with a dot (.) is hidden. To see it in nautilus, press Ctrl+H or show hidden files under View menu. To see it in terminal, enter```
ls -a
```

I did, sir.

---

### Post by sblunix on 2009-08-13
.

---

