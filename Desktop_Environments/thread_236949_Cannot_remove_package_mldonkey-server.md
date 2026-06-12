---
title: "Cannot remove package mldonkey-server"
date: 2006-08-15
forum: Desktop Environments
---

### Post by agrabah on 2006-08-15
Hello!

I'm sporting Kubuntu dapper for a few months now, and am very content with it. There are a few quirks that are bothering me, but I'm getting slowly around to eliminating them.

Now here is one that won't go away no matter what I do (with my humble knowledge of linux, that is).

I installed mldonkey-server package (via adept) version 2.7.1-2ubuntu2. Adept told me at that time that he could not run some post-install scripts that package provided. I didn't bother much at that time, as mldonkey worked. But then adept started crashing almost every time I installed something, telling me he couldn't finish installing mldonkey-server. I had to do dpkg --configure -a every time I installed something.
But it really became a nuisance yesterday when I tried to remove mldonkey-server. Neither adept nor apt-get or dpkg could remove the package. This is the console output of apt-get:
tine@durumba:/etc/init.d$ sudo apt-get remove mldonkey-server
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mldonkey-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 8151kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing mldonkey-server (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
tine@durumba:/etc/init.d$ Errors were encountered while processing:
 mldonkey-server

When I try to do a reinstall:

tine@durumba:/etc/init.d$ sudo apt-get install --reinstall mldonkey-server
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2970kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mldonkey-server.
(Reading database ... 88840 files and directories currently installed.)
Preparing to replace mldonkey-server 2.7.1-2ubuntu2 (using .../mldonkey-server_2.7.1-2ubuntu2_i386.deb) ...
Stopping MLDonkey: mlnetNo process in pidfile `/var/run/mlnet.pid' found running; none killed.
invoke-rc.d: initscript mldonkey-server, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping MLDonkey: mlnetNo process in pidfile `/var/run/mlnet.pid' found running; none killed.
invoke-rc.d: initscript mldonkey-server, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mldonkey-server_2.7.1-2ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting MLDonkey: mlnetinstall: invalid option -- f
Try `install --help' for more information.
invoke-rc.d: initscript mldonkey-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mldonkey-server_2.7.1-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I get similar messages from dpkg. I would really like to get rid of this package. 
Any ideas?

Thanks,
   
    Tine

---

### Post by agrabah on 2006-08-15
Ok, I resolved the situation (with a little help from my friends...).
I found a post stating the same issues:

[http://www.ubuntuforums.org/showthread.php?t=232680&highlight=mldonkey](http://www.ubuntuforums.org/showthread.php?t=232680&highlight=mldonkey)

the solution was simple: I followed the instrucions in this post and found another thing: mlnet MUST be running before one tries to uninstall it.

Oh, and sorry for double posting... I guess I will have to do my homework better before I post.

Tine

---

