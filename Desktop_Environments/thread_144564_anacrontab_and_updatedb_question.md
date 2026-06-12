---
title: "anacrontab and updatedb question"
date: 2006-03-14
forum: Desktop Environments
---

### Post by dpm on 2006-03-14
Hi,

I had a problem where I could never do a search from root (/) with the gnome-search-tool. That is, I tried to search for a file from 'Places>Search For Files...' and when 'Look in Folder' was set to 'Filesystem', it always returned 0 results, although the file was there.

It was not until today that I realised (after searching in the forums) that updatedb needs to be run before doing a search from root:

```
$sudo updatedb
``` 
That worked fine, but after some more research, it is my understanding that updatedb should be run as an anacron job in Breezy per default. Therefore, I shouldn't have had to run updatedb manually in the first place. However, the slocate database does not seem to get updated automatically on my system, although AFAIK anacron is run at startup and the slocate script (which executes updatedb) is in /etc/cron.daily. 

Any suggestions? Is there a way I can tell whether updatedb is being run automatically or not?

Thanks.

---

