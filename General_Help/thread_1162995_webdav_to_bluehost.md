---
title: "webdav to bluehost"
date: 2009-05-18
forum: General Help
---

### Post by MorayJ on 2009-05-18
Hi,

I can't really tell whether this is a bug or not as there doesn't seem to be much fuss about it, though it is mentioned from time to time in a google search, but with no answer.

I have webdav access offered by Bluehost. I couldn't connect with Nautilus so I gave up and followed a guide that allowed me to mount it from the command line:

```
sudo mount -t davfs -o uid=me,gid=users [https://myserver.org:2078](https://myserver.org:2078) /media/webdrive/
```

This mounts it and I have access. I can create a new folder. But if I try and copy a file there, I get 

```
cannot touch `me': Input/output error
```

Also, if I try and connect with Cadaver I get the following error

```
 Could not access / (not WebDAV-enabled?):
Did not find a collection resource.
```

Anyone with any ideas?

Cheers
MorayJ

---

### Post by MisterM on 2009-06-12
Hi, MorayJ,

I have the exact same problem, but with a different WebDAV server. Have you found a solution?

---

### Post by tuggy on 2009-07-04
bump

---

### Post by MorayJ on 2009-07-14
Hi, sorry, missed your post.

I've actually moved onto using ssh as they allow that, so I didn't really find a solution.

Cadaver, which is command line, worked for me if I used the "-t" switch (if memory serves correctly). 

This means 'tolerant' and I think it indicates that our WebDav hosts are maybe not using a standard setup. I don't know any more than that though.

Hopefully someone else will jump in and advise..?

---

### Post by DizzyCoder on 2010-05-21
Late in game, I know, but maybe this will help others as I got here in my search, but as of now, you can connect to webdavs through nautilus (in 9.10 or 10.04) as my experience indicates.

Under "Places": Connect to server
Choose secure webdav
enter just the hostname in the server box
2078 is the port for SSL
I left the folder and username blank
it then asked me for my webdav user/password (I used my main account name so I could have full access, you could/should use a different user mapped to a specific folder)
then it asked me for my CPanel webdisk password which was different than my webdav user password... don't know why/where/how that is set, but it *did* work for me.

Cheers

---

