---
title: "how to make hard drive active"
date: 2009-05-08
forum: General Help
---

### Post by icivilion on 2009-05-08
hi all... i have purchased a new hard drive ... i formatted it using gparted in ext3... but i am not able to copy any thing into my external hard drive.... hard drive get mounted and there only one folder inside by lost+found... how to activate my partion...??????  i know this is very easy task for you guys... thanks in advance...

---

### Post by Bindsa on 2009-05-08
First make sure that you checked the whole drive. Secondly, is there a mount point on that partition?

---

### Post by dubhear on 2009-05-08
> chown --help you need to change permissions, permissions are probably root, is that so?

---

### Post by icivilion on 2009-05-08
and if i go to permissions it says that permissions couldn be determined....

total 8
lrwxrwxrwx 1 root root    6 2009-05-06 14:33 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-05-06 14:33 cdrom0
drwxr-xr-x 3 root root 4096 2009-05-09 16:21 ext3 indu

hi this was the output ....... m bit new to linux,,,, m bit confused with permission and checking... but can follow what you say..:)


and for chown help this was the output....

Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...
  or:  chown [OPTION]... --reference=RFILE FILE...
Change the owner and/or group of each FILE to OWNER and/or GROUP.
With --reference, change the owner and group of each FILE to those of RFILE.

  -c, --changes          like verbose but report only when a change is made
      --dereference      affect the referent of each symbolic link (this is
                         the default), rather than the symbolic link itself
  -h, --no-dereference   affect each symbolic link instead of any referenced
                         file (useful only on systems that can change the
                         ownership of a symlink)
      --from=CURRENT_OWNER:CURRENT_GROUP
                         change the owner and/or group of each file only if
                         its current owner and/or group match those specified
                         here.  Either may be omitted, in which case a match
                         is not required for the omitted attribute.
      --no-preserve-root  do not treat `/' specially (the default)
      --preserve-root    fail to operate recursively on `/'
  -f, --silent, --quiet  suppress most error messages
      --reference=RFILE  use RFILE's owner and group rather than
                         specifying OWNER:GROUP values
  -R, --recursive        operate on files and directories recursively
  -v, --verbose          output a diagnostic for every file processed

The following options modify how a hierarchy is traversed when the -R
option is also specified.  If more than one is specified, only the final
one takes effect.

  -H                     if a command line argument is a symbolic link
                         to a directory, traverse it
  -L                     traverse every symbolic link to a directory
                         encountered
  -P                     do not traverse any symbolic links (default)

      --help     display this help and exit
      --version  output version information and exit

Owner is unchanged if missing.  Group is unchanged if missing, but changed
to login group if implied by a `:' following a symbolic OWNER.
OWNER and GROUP may be numeric as well as symbolic.

Examples:
  chown root /u        Change the owner of /u to "root".
  chown root:staff /u  Likewise, but also change its group to "staff".
  chown -hR root /u    Change the owner of /u and subfiles to "root".

Report bugs to <bug-coreutils@gnu.org>.

---

### Post by haired on 2009-05-08
You can try the following:

Open a terminal and run:

```
cd /path/to/your/drive
```

Next, recommended permissions for now I'd say are 755, so:

```
sudo chmod 755 */*
```

It's been a while since I have, you may need to:

```
sudo chmod 755 /path/to/your/drive
```


Hope this helps. ;p

---

### Post by icivilion on 2009-05-08
hi please dont mind... i am bit new... my mounted new hard drive is on desktop only.. when i open it i get this path..
/media/ext3 indu, but when i run in terminal it says  indu@Kina:~$ cd /media/ext3 indu
bash: cd: /media/ext3: No such file or directory..... can you tell me where i have gone wrong??????
the problem is i can open my new drive but couldnt copy anything into it.... is there anything to do with flags??? please help...

---

### Post by haired on 2009-05-08
If there is a space in filename you'll need "s around the path,

```
cd "/media/ext3 indu"
```

also be sure your have the correct case, Linux is case sensitive.

---

### Post by icivilion on 2009-05-08
command did woked but nothing happened....means command got through terminal... but still i cant copy or paste anything in the hard drive... in my hard drive by default there is only one folder that is lost+found.... 

Is this is anything to do with flags or mount points i have not given anything....  or logical drive or extended so?..... i formatted using gparted for default...  do help

---

### Post by haired on 2009-05-08
You could try 777 permissions in place of 755, though anybody with access to computer can read/write then.

```
sudo chmod 777 "/media/ext3 indu"
```

Also you could test your drive by running the following:

```
 sudo mkdir "/media/ext3 indu/test_dir"
```

---

### Post by icivilion on 2009-05-08
thanks a lot dude... it worked..... can you explain me what was the problem.... thaks agian..!!!!!!!:P:P:P any idea... where to close the thread

---

### Post by haired on 2009-05-08
I'd hazard a guess that since GParted works under root, any modifications are set as such.

Don't quote me on it. ;p

Also 777 permissions allow all users to read/write in full, might wanna consider switching those around. 755 allows read (and I thought write, was wrong) to 'users' and 'others'.

Glad you sorted it though. :D

---

