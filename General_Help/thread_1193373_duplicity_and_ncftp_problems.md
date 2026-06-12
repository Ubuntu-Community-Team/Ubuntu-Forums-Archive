---
title: "duplicity and ncftp problems"
date: 2009-06-21
forum: General Help
---

### Post by chetancrasta on 2009-06-21
I'm trying to use duplicity (0.5.09-0ubuntu2) on Ubuntu 9.04 to backup files to my godaddy.com web space using FTP but it fails to complete because of an error with ncftp (2:3.2.1-1).
When I run the commands (not my real passphrase, login and web site name):
```
export PASSPHRASE=123456789
export FTP_PASSWORD=mypassword
duplicity /home/myname/Documents ftp://mylogin@mysite.com/
```
Duplicity successfully connects to my web server and uploads the files and then I get this error message:
```
Running 'ncftp -u mylogin mysite.com' failed (attempt #1)
Running 'ncftp -u mylogin mysite.com' failed (attempt #2)
Running 'ncftp -u mylogin mysite.com' failed (attempt #3)
Running 'ncftp -u mylogin mysite.com' failed (attempt #4)
Running 'ncftp -u mylogin mysite.com' failed (attempt #5)
Giving up trying to execute 'ncftp -u mylogin mysite.com' after 5 attempts
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 582, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 576, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 566, in main
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 235, in full_backup
    bytes_written = write_multivol("full", tarblock_iter, globals.backend)
  File "/usr/bin/duplicity", line 162, in write_multivol
    (tdp, dest_filename)))
  File "/usr/lib/python2.6/dist-packages/duplicity/asyncscheduler.py", line 148, in schedule_task
    return self.__run_synchronously(fn, params)
  File "/usr/lib/python2.6/dist-packages/duplicity/asyncscheduler.py", line 174, in __run_synchronously
    ret = fn(*params)
  File "/usr/bin/duplicity", line 161, in <lambda>
    async_waiters.append(io_scheduler.schedule_task(lambda tdp, dest_filename: put(tdp, dest_filename),
  File "/usr/bin/duplicity", line 115, in put
    backend.put(tdp, dest_filename)
  File "/usr/lib/python2.6/dist-packages/duplicity/backends/ftpbackend.py", line 171, in put
    res = self.run_ftp_command_list(commands)
  File "/usr/lib/python2.6/dist-packages/duplicity/backends/ftpbackend.py", line 166, in run_ftp_command_list
    raise BackendException("Error running '%s'" % self.commandline)
BackendException: Error running 'ncftp -u mylogin mysite.com'
```

However, I am able to connect to my FTP account if I run 'ncftp -u mylogin mysite.com' in a terminal window separately -- I am asked to enter my password and after I do, I successfully connect.

Anyone knows what's going on? Is ncftp incompatible with duplicity in Jaunty?

---

### Post by HowdyDo on 2009-07-17
Hello,

I ran across your post searching for a solution to the same behavior.  I don't know if the following applies to you, but I experienced exactly the same behavior you described.  In my case at least, the problem was due to the fact that I had an "@" embedded in my ftp username.  The "@" is beyond my control, but fortunately the changelog at [http://duplicity.nongnu.org/](http://duplicity.nongnu.org/) includes:
> New in v0.5.11 (2009/03/08)
---------------------------
bug #25787: Usernames with @-sign are not handled properly
[https://savannah.nongnu.org/bugs/?25787](https://savannah.nongnu.org/bugs/?25787)Note the version available through the repos (at the time of writing) is 0.5.09 (pre bug fix).  So I built from the latest stable version, 0.5.18, and it works just fine.

One note, though.  The download link for the latest stable tarball is broken.  You need to replace 'trunk' with 'stable' in the URL for it to work.  Here is the working link:
[http://code.launchpad.net/duplicity/stable/0.5.18/+download/duplicity-0.5.18.tar.gz](http://code.launchpad.net/duplicity/stable/0.5.18/+download/duplicity-0.5.18.tar.gz)

Perhaps that will help.  Even if your issue isn't the "@", you might parse the changelog and see if something jumps out.  Good luck.

---

