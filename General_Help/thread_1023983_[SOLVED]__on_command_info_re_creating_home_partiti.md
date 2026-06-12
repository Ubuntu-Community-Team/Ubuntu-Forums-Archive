---
title: "[SOLVED] ? on command info re creating /home partition from another post"
date: 2008-12-28
forum: General Help
---

### Post by hawkhock on 2008-12-28
[COLOR="Red"]Part of post by caljohnsmith on 11/19/2008:
Just as a side note, I think a simpler way than the tutorial's method is:
Code:

sudo mkdir /old /new
sudo mount /dev/sda1 /old
sudo mount /dev/sda3 /new
sudo cp -ax /old/home/* /new

The above steps accomplish the same thing so that all permissions/users/groups etc are all preserved on all the files/directories that you copy over, and I've used it myself with success.[/COLOR]

Noobie -- would like to add partition for /home on hard drive.  Very uneasy about doing this.  Would like to confirm sequence of events. Current partitions:
/dev/sda1        ext3       71.43G
/dev/sda2        extended    3G
  /dev/sda5      linux swap  3G

1) Use the psychocats tutorial (Live CD & GPartEd)
-- Resize sda1 to 41G
-- Unallocated becomes 30G - format as /ext3 - 
-- Leave sda2 and sda5 as is

2) Close GPartEd and exit Live CD.  Boot into regular system.  Open terminal -- here is where I get confused.  I think that "sudo" = "root user".  To use caljohnsmith's commands do I copy the commands as is OR do I need to log on as root?  

3) I found instructions on how to log as root.  The final command to do this is "root@name:~#".  Is this where I type in caljohnsmith's sudo commands?

5) Do I then return to the psychocats tutorial to modify the /etc/stab file by adding the last command line?

OR does the caljohnsmith command block take care of everything at once?

Georgi in UT

---

