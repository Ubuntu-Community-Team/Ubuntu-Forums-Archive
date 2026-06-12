---
title: "partition setup?"
date: 2009-05-11
forum: General Help
---

### Post by tenmilez on 2009-05-11
I have a 250gb and a 1tb hard drive in a computer that will be running ubuntu server. It will have subversion, tomcat, mysql, transmission, and maybe a few other things running on it. I'm curious what the best way would be to set up the partitions so that I have a backup partition for the important things (a fairly small amount of data) and a partition that would be reusable if I were to reinstall the OS (like what some people do with /home) for the database and whatnot.

---

### Post by mb_webguy on 2009-05-11
Well, if you're running MySQL, it wouldn't be a bad idea to put /var on a separate partition, since that's where the database directory is located by default.  I'm not sure about Tomcat, but I know the default web directory for Apache is in /var also.  And of course your log files are also in /var, so separating it out is usually a good idea for a server.

Putting /home on a separate partition would also probably be a good idea, to keep your data (such as downloaded torrents) separate from your system files.

If these two directories are separate, the root directory only needs to be about 6GB.  I'd put this on the 250GB drive, and use the rest of the drive and the 1TB drive for the /home and /var directories, depending one which I expected to need the greater amount of storage.

You could put some of the other directories on separate partitions as well, but those are the important ones for the setup you described, IMO.  And really, separate partitions on the same drive don't really serve much purpose other than separation and limitation of data -- you don't want your data to fill up the partition containing your system files, since that can bork your system.

---

