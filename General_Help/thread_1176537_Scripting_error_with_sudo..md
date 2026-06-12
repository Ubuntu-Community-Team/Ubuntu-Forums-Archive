---
title: "Scripting error with sudo."
date: 2009-06-02
forum: General Help
---

### Post by EmanresuusernamE on 2009-06-02
I have a quick script that I wrote to help ease adding users to a dovecot password database:

```
#!/bin/sh -x
if [ "1" = "$1" ]
then {
  set pass=dovecotpw -u $1 -s CRAM-MD5
  echo $1:$pass >> /etc/cram-md5.pwd
}
fi
if [ "" = "$1" ]
then echo Error, username required.  Aborting.
fi

```

I just noticed that when I attempt to sudo echo anything into /etc/cram-md5.pwd I get a permission denied error for some reason now.  earlier I could do that but now I can't, even after I restart the machine.  I can edit it with pico just fine.  It's owned by root:root, and it has 600 permissions.  I deleted the file and recreated it, no dice.

Any suggestions?

---

### Post by blueridgedog on 2009-06-02
Do you get permission denied when you try to run the script or when you try to echo a line in with >>?

Can you do a simple test with:

```
sudo echo test >> /etc/cram-md5.pwd
```

The results are the same?

---

### Post by EmanresuusernamE on 2009-06-02
Yeah, I did that as a test already, same problem.  I could do it earlier, but now I can't.  I did a few copy and paste mistakes earlier on the terminal and did something like:
```
sudo echo $1: | dovecotpw -u username -s CRAM-MD5 >> /etc/cram-md5.pwd
```

But it didn't work.  I've tried changing the pipe to >, >> and stopped because I realized I was being a total newb and putting a file in my root's home directory called dovecotpw and overwriting it over and over again :oops:.  I also tried changing the pipe to a semicolon and then realized I need to work on my scripting. 

I looked at the man pages for echo and read that a -n might just be what I need to do this, but then I started to get the permission denied errors and got hung up.

I think this will work in my script, but even as root I'm getting permission errors............
```
echo -n $1: >> /ect/cram-md5.pwd
dovecot -u $1 -s CRAM-MD5 >> /etc/cram-md5.pwd
```
Or if that didn't work, I was also leaning towards:
```
set pass=dovecotpw -u $1 -s CRAM-MD5
echo $1:$pass >> /etc/cram-md5.pwd
```In my theory that will work, but then again I seem to be wrong on several issues so far here.  Also, I don't have a great deal of experience with the set command as I've only used it with DOS and Windows machines. Hmmm, perhaps a > instead of an = sign will do? :D 

Hehe, last time I had permission errors being root was on Suse 7.3 several years ago.......... Had that whole file system jacked up beyond my ability to repair.  Luckily it was all set to read-only and not unreadable.

---

### Post by EmanresuusernamE on 2009-06-03
Ok, I found out what was going on. sudo wasn't accessing the files as root for some reason.  I was able to have it update the file with this script.

```
#!/bin/sh
#Released to the public domain.
if [ "" != "$1" ]
then {
  sudo chown $USER:$USER /etc/cram-md5.pwd
  echo -n $1: >> /etc/cram-md5.pwd
  dovecotpw -s CRAM-MD5 >> /etc/cram-md5.pwd
  sudo chown root:root /etc/cram-md5.pwd
     }
fi
if [ "" = "$1" ]
then echo Error, username required.  Aborting.
fi
```

Also, in my earlier script, having: if [ "1" = "$1" ] and if [ "" = "$1" ] would always make it skip everything.

---

### Post by blueridgedog on 2009-06-03
I missed the "1" in the first pass.  I still find it odd that you can't sudo and echo into the file, but it looks like you found a work-around.

---

### Post by EmanresuusernamE on 2009-06-03
I think I found out why it wasn't allowing me to echo anything into the file using sudo.  Using sudo doesn't change you to root when using it, it just gives you access as if you were root.  Since I had the file attributes as root:root and 600, only root could read or write to the file.

If you do: "echo $USER" or "sudo echo $USER" you'll get the same result.  Since my account wasn't root, it wouldn't allow me to access it.  Which means everything is working the way it's supposed to........ technically.

:) In a nutshell, sudo is LIKE root, but it isn't root. :popcorn:

---

