---
title: "DB2II and Ubuntu"
date: 2006-01-05
forum: General Help
---

### Post by Tom Stave on 2006-01-05
I am trying to evaluate DB2 on Ubuntu.  I am using trial versions of DB2 Universal Database Express; WebSphere MQ; and DB2 (WebSphere) Information Integrator.  I have been successful in installing and testing both the DB2 Universal Database (with its DB2 Fix Pak to upgrade to 8.2) and WebSphere MQ.   However, when I try to install DB2II I get the following message when running the installer './iisetup'.

"An unsupported edition or version of DB2 Universal Database was found on the system. You must install a supported edition or version of DB2 Universal Database before you install DB2 Information Integrator.

See the DB2 Information Integrator Installation Guide for a list of supported editions and versions of DB2 Universal Database."

I will continue to try and solve this on my own, but has anyone had any experience running DB2II on Ubuntu?  If so, do you have any pointers?

Thanks

---

### Post by KingBahamut on 2006-01-05
Not yet, though im working with getting Oracle Express to run at the moument. If your successful though, let me know.

---

### Post by Tom Stave on 2006-01-10
As a follow up to my earlier post.  I thought I would post my results.  I was able to get the following trial products to install and pass initial tests using Ubuntu:

IBM DB2 Express + FixPak 10
IBM DB2 Enterprise Server Edition + FixPak 10
WebSphere MQ

The main difficulties are that IBM uses RPM's exclusively and I had to modify each products setup script and perform manual installations.  This link was of great help to get me started:

[http://www.tldp.org/HOWTO/DB2-HOWTO/ubuntu504.html](http://www.tldp.org/HOWTO/DB2-HOWTO/ubuntu504.html)

I hit a brick wall when it came to installing Information Integrator which does not have manual installation scripts and seems to query for RPM installations from within the installation application.  I'm sure it can be done, I unfortunately don't have the time to figure it out.  IBM was very quick to respond to my questions and  they have my thanks.  I received the  response below when I asked about Installing Information Integrator on Ubuntu.  

“GMT 2006 First, let me state that the WebSphere Information Integrator trial is unsupported.
I presume you downloaded it from here:
[http://www-128.ibm.com/developerworks/downloads/ws/winin/index.html?S_TACT=105AGX28&S_CMP=DLMAIN](http://www-128.ibm.com/developerworks/downloads/ws/winin/index.html?S_TACT=105AGX28&S_CMP=DLMAIN)

If you click the support tab on that page, you will see that Information Integrator is not a supported trial product.

I did do some research in an effort to give you some ideas to explore.

1. The fact that Ubuntu is a supported Linux distribution for DB2 products  was a surprise to me. My standard support list does not list it. I did perform a google search which did indeed indicate that Ubuntu has been validated.

2. We have never tried installing Ubuntu , nor have we tried installing any products on it.
Therefore , I don't have any practical experience to report on it.

3. Please note that WebSphere Information Integrator is not the same product as DB2 Universal Database (DB2 UDB) which does have a Ubuntu  validation.   Therefore, you cannot conclude that Information Integrator is also supported on Ubuntu. Integrator is no longer branded as a DB2 product, which means it is marketed  by a different marketing team and will consequently have different marketing requirements.

This is the published list of supported Linux distributions:
[http://www-306.ibm.com/software/data/integration/db2ii/requirements.html](http://www-306.ibm.com/software/data/integration/db2ii/requirements.html)

Note that Ubuntu is not listed.   What are listed are RPM based products.
I suspect that the installer is trying to query whether you have UDB installed by doing a rpm -q command, and this is failing.

I would conclude that installation of Information Integrator on Ubuntu Linux  is not supposed to work.”

---

### Post by sanjai on 2006-09-08
Hi there,
         Well, i am actually a new kid in the block with respect to any experience with Ubuntu. From your post i came know that you had installed DB2,.. Well, could you please send me a detailed set of instructions to install softwares on Ubuntu..? 

Regards,
Sanjai

---

