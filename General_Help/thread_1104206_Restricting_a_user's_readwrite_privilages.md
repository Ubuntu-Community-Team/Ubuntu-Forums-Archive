---
title: "Restricting a user's read/write privilages"
date: 2009-03-23
forum: General Help
---

### Post by malfist on 2009-03-23
I have a user called winLogger, and I want him to have read write access to /home/winLogger/Logs _only_. I've already make it so winLogger and root are the only two users who can read or write to /home/winLogger/Logs. But I want to restrict it further. 

Some things I'd like to do: 
[LIST]
[*]Prevent winLogger from writing anywhere but /home/winLogger/Logs
[*]Prevent winLogger from creating subdirectories (i.e. prevent access to mkdir)
[*]Prevent winLogger from writing files over the size of X megabytes
[*]Restrict the size of /home/winLogger/Logs to X gigabytes
[/LIST]

If you know how to do them, please show me or point me in the right direction. Thanks!

---

### Post by malfist on 2009-03-23
Found one, restricted user's max file size

[http://www.cyberciti.biz/faq/file-size-limit-exceeded-error-under-linux-and-solution/](http://www.cyberciti.biz/faq/file-size-limit-exceeded-error-under-linux-and-solution/)

---

### Post by bodhi.zazen on 2009-03-23
Well, unless the users is accessing the system remotely, and even then, you will need to give some access to system files, usually read only.

IMO, i fyou are using Ubuntu, I think this is a perfect use of Apparmor.

Alternates would be SELinux or acl.

---

### Post by malfist on 2009-03-23
i'm using an ubuntu 8.04 server, I want the user to have a few privilages as possible. The only thing this user is for is transfering log files from windows servers to the monitoring ubuntu server via scp.

I think if I set the home folder max size to like 5GB it would be good enough. The user has an insanly complex and long password, but it's stored in a program, which can easily be decompiled or someone can watch it's memory. I seriously doubt anyone will try anything, but if they do I want to limit the damage they can do. The user is part of no groups, and is the only one that can read and write to the log folder, besides root.

---

### Post by bodhi.zazen on 2009-03-23
Make the user use a key with ssh (scp)

You can the set the key to run scp and deny access otherwise.

Then generate and apparmor profile for scp (if you use scp fo rother things, then make a "fake" scp with a hard link, link scp to /usr/local/jailscp and make an apprmor profile for /usr/local/jailscp ).

For an overview of the keys, see this blog : 

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

Tha blog is on svn, but still, just look at the key setup.

---

### Post by malfist on 2009-03-23
How would that prevent a user from loging in otherwise. They'd be able to use the key for an ssh login.

---

### Post by bodhi.zazen on 2009-03-23
no, they will only be able to use the key for scp.

I do not get the impression you read the blog, but basically using a key allows you to specify a command to be run at login (in this case scp) and the additional options prevent things such as obtaining a terminal, using port forwarding, or running commands.

I will PM you with a key and the password, see what you can do to my server.

---

### Post by apmcd47 on 2009-03-23
You could also look at using the restricted version of bash ([see this link]("http://www.gnu.org/software/bash/manual/bashref.html#The-Restricted-Shell")) for this user. Put "**cd Logs**" into the *.bash_profile* file. The restricted version of bash will not allow changing the directory or reading from or writing to files with / in the name.

Andrew

---

### Post by bodhi.zazen on 2009-03-23
rbash is "ok" but it is easy to break out, heck I can break out of rbash in under 5 seconds.

apparmor is really a better option.

---

