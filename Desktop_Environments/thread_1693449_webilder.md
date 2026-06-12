---
title: "webilder"
date: 2011-02-22
forum: Desktop Environments
---

### Post by degarb on 2011-02-22
Does webilder just keep growing the collection?  Or does it ever get rid of old photos?

It seems to me an ideal webilder I could set max 100k, it would delete oldest photos to make room for new.  

Or, like flickrwall (windows), it would just pull one flickr photo per hour, over writing last photo.

---

### Post by thesamet on 2011-02-23
> **degarb said:**
> Does webilder just keep growing the collection?  Or does it ever get rid of old photos?

It seems to me an ideal webilder I could set max 100k, it would delete oldest photos to make room for new.  

Or, like flickrwall (windows), it would just pull one flickr photo per hour, over writing last photo.

Webilder does not remove old files. If you wish, you can easily set up a cron job that will remove the old files. Run 'crontab -e' and add the following line:

0  * * * *   find /home/yourusername/.webilder/Collection -mtime +20 -type f -exec rm {} \;

This will delete everyday files that are more than 20 days old.

---

