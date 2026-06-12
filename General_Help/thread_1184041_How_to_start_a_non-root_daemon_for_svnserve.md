---
title: "How to start a non-root daemon for svnserve"
date: 2009-06-10
forum: General Help
---

### Post by r.stiltskin on 2009-06-10
I'm trying to set up an svn repository/server for a small group, using plain-vanilla svnserve.  The svnbook recommends "create a single svn user on your system and run the server process as that user. Be sure to make the repository directory wholly owned by the svn user as well. From a security point of view, this keeps the repository data nicely siloed and protected by operating system filesystem permissions, changeable by only the Subversion server process itself."  That sounds very sensible, but how is that done?

Obviously I know how to create a user and setting the ownership and permissions to /var/svn is no problem.  Starting the daemon is also simple:
```
svnserve -d
``` and there's a -r option that limits access to a specific path.

But how can I set it up so that this non-root user's daemon starts every time the system boots up, without having to manually log-in the user & run that command?

---

### Post by blueridgedog on 2009-06-10
Take a look at this page:

[http://weblogs.java.net/blog/evanx/archive/2007/07/trip_and_tick_s.html](http://weblogs.java.net/blog/evanx/archive/2007/07/trip_and_tick_s.html)

It appears the path they took was to creat an xinetd entry to run it as a specific user.  You may need to install xinetd if that is the route you want to go.

---

### Post by r.stiltskin on 2009-06-11
Thanks for that link -- it's wonderful.  There were still a few stupid hurdles to get over (at first neither svnserve nor xinetd would work) but I finally figured out that

1 - svnserve doesn't allow blank spaces at the beginning of lines in svnserve.conf, e.g. in the sample configuration file that is written in the new repository when you run "svnadmin create", on the line ```
# auth-access = write

```you have to delete not only "#" but "# ".

and

2 - xinetd wouldn't start svnserve when my /etc/xinetd.d/svn file was formatted as in the blog, e.g. ```
service svn {
  port = 3690
  socket_type = stream
  ...
```
So I moved the "{" to the beginning of the 2nd line and deleted all leading blank spaces so it now looks like```
service svn
{
port = 3690
socket_type = stream
...
```

After sorting out that nonsense, it seems to work perfectly.

---

### Post by blueridgedog on 2009-06-11
Well done!

---

