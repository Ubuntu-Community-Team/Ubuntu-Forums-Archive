---
title: "Can't access my wordpress"
date: 2011-04-08
forum: Desktop Environments
---

### Post by Codemagnet on 2011-04-08
Hi all.

Let me start by saying Ubuntu rocks and Ubuntu Forums is a lifesaver!! I'm currently running 32bit Natty, I've used windows mainly in the past but have dabbled with linux distros on the sideline always.  However, since I've started coding again, mainly doing wordpress theme development, using Linux was a no brainer.

I installed LAMP, phpmyadmin and wordpress fine.  To start with I couldnt access my themes but I discovered that the problem was related to permissions in the 'var/www' folder, so i used "chmod -R o+rxw '/var/www/' " to resolve this and all seemed ok.  However, a couple of days later, i tried accessing my site and nothing, just a blank page.  I can't even access my wordpress admin panel. I'm 90% sure its not a wordpress issue as I haven't changed any critical code within wordpress, but as with all things, I may be wrong. my apache server is running and working, I have my wordpress in a seperate folder and I can access localhost and files within there but not within my wordpress folder.

Apologies if this is in the wrong place, perhaps I should have gone to the wordpress site but I'm almost certain theres something within ubuntu causing this. I've just upgraded to Natty recently but the problem was there even in Maverick.  I can't go back to developing in Windows again, that would just be sad, and wrong and, well..... sad.

So, what gives??

Thanks all for the help.

---

### Post by Codemagnet on 2011-04-08
I eventually dropped my database using phpmyadmin, deleted the files within the folder and reinstalled wordpress. ran chmod again to make sure all files within that folder had permissions and everything is working fine.  Didnt want to resort to that, seems like a bit of a runaway resolution, I would have liked to get to the root of the problem but needs must.

---

