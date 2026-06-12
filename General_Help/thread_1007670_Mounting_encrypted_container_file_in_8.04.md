---
title: "Mounting encrypted container file in 8.04?"
date: 2008-12-10
forum: General Help
---

### Post by cbraxton on 2008-12-10
I recently moved (finally!) from 6.06 Dapper to 8.04 Hardy. I have some encrypted container files that previously would be mounted using cryptoloop with losetup, something like:

  losetup -e encryption_type /dev/loopN /path/to/container/file
  mount -t filesystem_type /dev/loopN /mount/path

This does not seem to work in Hardy. I could not find cryptoloop in Synaptic, and losetup just returns the error:

   LOOP_SET_STATUS invalid argument

How can I access my encrypted container files under Hardy?

---

### Post by albinootje on 2008-12-10
According to this message you need loop-aes-utils :
[http://lists.debian.org/debian-user-german/2005/09/msg02757.html](http://lists.debian.org/debian-user-german/2005/09/msg02757.html)
[http://packages.ubuntu.com/search?keywords=loop-aes-utils](http://packages.ubuntu.com/search?keywords=loop-aes-utils)

---

### Post by cbraxton on 2008-12-10
> **albinootje said:**
> According to this message you need loop-aes-utils :
[http://lists.debian.org/debian-user-german/2005/09/msg02757.html](http://lists.debian.org/debian-user-german/2005/09/msg02757.html)
[http://packages.ubuntu.com/search?keywords=loop-aes-utils](http://packages.ubuntu.com/search?keywords=loop-aes-utils)

Thanks, that got me a little further - but now losetup complains that the password is less than 20 characters. (This was not a problem with Dapper.) I checked the losetup man page but did not see a way to get it to accept my shorter password.  Now you can argue that the shorter password is not secure enough, and you would probably be right, but it's already embedded in an existing container file.

This seems like a pretty nasty limitation, maybe even a bug. I can understand not being able to create new containers using short passwords, but to apply this limitation to a pre-existing password effectively locks the user out of his or her own data.

So do I have to go back to Dapper temporarily to decrypt my data, and redo the encryption with long passwords, or is there a hidden losetup option someplace? (It's because of surprises like this that I tend not to update the OS very often!!)

---

