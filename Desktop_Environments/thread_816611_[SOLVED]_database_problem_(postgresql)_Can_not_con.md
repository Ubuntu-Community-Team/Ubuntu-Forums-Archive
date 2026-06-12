---
title: "[SOLVED] database problem (postgresql): Can not connect to database"
date: 2008-06-02
forum: Desktop Environments
---

### Post by Valsodar on 2008-06-02
First of all specs:
Ubuntu 8.04 LTS on Dell1501

The problem:
Constantly getting "Can not connect to database" whenever i switch user (using su) or whenever I do sudo <command>.

I tried shutting both mysql and postgresql but I still get this error (and i made sure that the daemons for both are not started). I also stopped apache to make sure, but none of those resolved the issue. Additionally I had to update postgresql from 8.2 to 8.3. I checked the logs and this message does not appear there.

I am at a lost... any help appreciated.


-------------------------------------------------------------------------------------------------------------------------
So I managed to fix it and this was the problem proftpd (an ftp daemon that was install via gforge was wrongfully configured, actually I remember work around in order to install it) But yeah, after removing it, the error no longer happens. Sadly I removed apache, mysql, and postgresql, other sql, but I remembered to back up my config files and export mysql tables. So no biggie.

---

