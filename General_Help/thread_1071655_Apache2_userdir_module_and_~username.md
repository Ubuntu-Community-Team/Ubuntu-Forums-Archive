---
title: "Apache2 userdir module and /~username"
date: 2009-02-16
forum: General Help
---

### Post by Phlee on 2009-02-16
Hi all!
I've just enabled the Apache2 userdir module. I was wondering if anyone knew how to change the /~username to /username. I would like to get rid of the '~' as it won't fit my current needs. Any help would be greatly appricated as I've been all over the apache site as well as different forums. I'm running Ubuntu 8.10.

One solution is I've managed to add sym links to /var/www/username but I would like to steer clear of that if possible. 

Thanks in advance!

---

### Post by bodhi.zazen on 2009-02-16
Hard to tell what your issues is from the sketchy details.

the only thins that stands out is that you should, IMO, use the full path on servers / automated commands.

So:

~user == /home/user

NOT

~user != /user

/home/user is not the same as /user

The other problem could always be permissions apache needs to be able to read /home/user

---

### Post by Phlee on 2009-02-16
awww *Bump*

---

### Post by Phlee on 2009-02-16
Well I can't quite remember what all my conf files are.  I'll have to post snippets tomorrow when I get into work.  It's a straight forward install of Apache2 MySQL and PHP.  It's for our customers.

  In the past we have setup apache with the userdir mod to host customer webpages with [www.example.com/~customer](www.example.com/~customer).  Since then I've been wanting to deploy a better url theme so to speak.  I.E
users.example.com/customer.

  I've seen it done in the past many times.  The new versions of Apache2.conf are slimed down and I can't find the examples online.  The internal directory structure has "/home/user/public_html" Which translates to [www.example.com/~customer](www.example.com/~customer).  Hope that helps to clarify things;)  Thanks for the post BTW

---

### Post by bodhi.zazen on 2009-02-16
Ah, you mean on the browser, url not the server config ?

mod-re_write perhaps ?

I always specify the directory in Apache, but if you have multiple users it is more difficult to do that.

---

### Post by Phlee on 2009-02-16
> **bodhi.zazen said:**
> Ah, you mean on the browser, url not the server config ?

mod-re_write perhaps ?

I always specify the directory in Apache, but if you have multiple users it is more difficult to do that.

Indeed.  To be truthfully honest I wanted to keep both urls and Virtualize one side so customers had options for the new URL structure as well as the old ~/username option.  I started writing a perl script with adduser to create a symbolic link to /var/www/username and that did it.  Just didn't want someone to find a hole with sym links and now I have an exploit:)

---

### Post by Phlee on 2009-02-16
*bump*

---

### Post by Phlee on 2009-02-17
*Bump*  Anyone?:(

---

### Post by Phlee on 2009-02-17
Sheesh don't tell me I've stumped the community?:P

---

### Post by rrll1977 on 2009-05-18
Hi all,

Has anybody ever worked with mod_rewrite and mod_userdir on LAMPP?

It appears that mod_rewrite doesn't work with the user's websites (located on /home/user/public_html), although it appears to work fine with the home server websites (on /opt/lampp/htdocs)

Regards

---

