---
title: "Ipod Shuffle (1st gen.) still dead even after Amarok update."
date: 2008-10-28
forum: Desktop Environments
---

### Post by marcthenarc on 2008-10-28
After an upgrade in the middle of this summer my iPod Shuffle (1st gen.) so I used my iBook w/ OS X instead all summer.  I've upgraded to the latest Amarok on Kubuntu (1.4.9.1, build date Oct. 20 2008 with libgpod3 0.6.0-3ubuntu3) hoping that it would fix my problem but it still doesn't.  And though I read complaints about it lately, I still don't have a comprehensive fix to hold on to.

Does anyone have similar problems ?

---

### Post by lunarcloud on 2008-10-28
Is the shuffle windows (fat32) format or macintosh (hfs+) format?

I've never gotten the hfs+ formatted ipods to work.

---

### Post by tgalati4 on 2008-10-28
hfs+ ipods do work, but you have to disable journaling.  This can be done on the mac using the terminal command:

>diskutil disableJournal disk#s#

Where your disk may be called disk1s1 or similar.  Use the following command with your shuffle plugged into the mac:

>df -h

Note the disk names for your mac system boot drive and your shuffle.  Don't turn off journaling on your mac.  It's really needed.  It's not needed for the shuffle.

Here's a link that describes some other things to try:

[http://simplyubuntu.wordpress.com/2006/07/29/ubupod/](http://simplyubuntu.wordpress.com/2006/07/29/ubupod/)

---

### Post by marcthenarc on 2008-10-28
It's fat32.

I don't understand it. The whole thing beautifully until the Amarok updates this summer. I did not need to reformat in HFS or disable some doo-hickey before that.

---

