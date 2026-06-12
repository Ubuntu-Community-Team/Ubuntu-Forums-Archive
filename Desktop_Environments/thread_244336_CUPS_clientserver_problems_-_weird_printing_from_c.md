---
title: "CUPS client/server problems - weird printing from clients"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Caveira2099 on 2006-08-26
Hello all!

I've found some guys who are facing the same problem tham I am with CUPS 1.2.2 (try this link [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg224752.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg224752.html) or Google for +CUPS "PCL3GUI").

Here's the problem: I have a HP PSC 1610 installed on a Ubuntu 6.06 fully updated. It is working great with cups and HPLIP locally, and was working well shared over my intranet with CUPS 1.2.2. Until last week, the clients (one with 6.06, the other with Fedora Core 5) could print perfectly over the intranet, directly. Since last update of CUPS (I don't know in ubuntu, in FC5 it was from 1.2.2-1.1 to 1.2.2-1.8 ) my clients can't print directly. CUPS installs them on the clients, but every document printing results in a sheet of paper with this text:

```
-12345X@PJL ENTER LANGUAGE=PCL3GUI
17H1-1M126Ao0M1-2Hg20WXX           XX
u600Dr4812Sr1Ap52Yb0Vb35W
``` 
I have checked every configuration on the clients and on the server and I couldn't figure anything out. I did try reinstalling the printer (on all computers) and nothing happened.

A special detail is that when connected directly to the printer, all of them printed perfectly. The only problem is printing from a client over the intranet.

If any of you guys have any ideas about this, or share the same problems, please post here.

Thanks!

P.S. If this post was misplaced, my appologies.

---

### Post by Caveira2099 on 2006-08-27
Ok guys, after 1 day and no answers, I'll post some things I've tried, but did not solve the issues.

1) I copied the PPD file from the server to the clients. The ubuntu client had the same file, the fedora core 5 client didn't have. So, I thought maybe it could make some new things on fc5. No way. I tried every combination, ipp and http adresses, and nothing.

2) Both FC5 and Ubuntu Dapper clients were able to print when direct plugin' the printer on them. Problem lies on the server or the client part of this new CUPS release I think.

I ask you who are facing the same or related issues to post here.

[ ]'s

---

### Post by mgmiller on 2006-08-27
If you are trying to use the Ubuntu machine as the cups server, try following the instructions on this link, it worked for me:

[HTML]https://help.ubuntu.com/community/HOWTO-enable-cups-browsing[/HTML]

---

### Post by mediocre on 2006-08-27
I've been having difficulties as well, and when I try the HOWTO above, I get:

```
nick@heracles:~$ sudo /usr/share/cups/enable_sharing 1
Error: cannot modify custom configuration
```

Same error for enable_browsing

N

---

### Post by Caveira2099 on 2006-08-28
Thank you people for the attention here!

I just wanted to add a test I did: I plugged the HP on a Windows XP machine, shared the printer, and both FC5 and Ubuntu 6.06 clients managed to print perfectly via smb shared printing--> obvious conclusion, there's something going on the cups server, the clients are OK.

mgmiller, I'll try that suggestion and post here the results.

Thanks!

---

### Post by Caveira2099 on 2006-08-28
Well,

mediocre: it seems you have already altered your "browse.conf" file and the script isn't recognizing what's there, for it is simply a file with "Browsing on" or "Browsing off" text.

mgmiller: I had already allowed sharing and browsing on Dapper server. It seems to be something else with the server, but I can't figure it out.

If I have news, I'll post here as soon as possible.

Thanks again!

---

### Post by centyx on 2006-09-02
I am experiencing almost the exact same problem here with an HP PSC 1510. 
My CUPS server is running on Ubuntu, and so are my clients. This setup was working fine until one day a month or more ago clients' jobs began producing the PCL3GUI output ( most likely an update to CUPS, but I'm not certain ). Looking forward to any progress you make.

---

### Post by centyx on 2006-09-02
I took a look at /var/cache/apt/archives ( I don't run apt-get clean very often ) and noticed that CUPS indeed had been upgraded August 3rd. 

It had been so long since I had run apt-get clean on the print server that I still had the CUPS debs from before that upgrade, which were version 1.2.1. I downgraded to those on both the client and server, and now remote printing is working properly again. 

This obviously isn't an acceptable solution, but it does verify that this is an issue w/ CUPS and at least I can print until things get straightened out.

---

### Post by centyx on 2006-09-02
From the CUPS changelong:

CHANGES IN CUPS V1.2b1
        - The HP-GL/2 filter could get in an infinite loop trying
          to convert HP-PCL files (STR #1415)

Could this be the problem?

---

### Post by harty83 on 2006-09-03
I have similar printouts when I try to print from OO through kprinter or xpp with 2 pages per sheet.  I only get it with OO though and not any other program.  Quite annoying and noone seems to know the answer to the problem.

---

### Post by Caveira2099 on 2006-09-06
centyx, thanks a lot! That was it then, the update...

Just asking, how did you perform the downgrade?

---

### Post by Caveira2099 on 2006-09-07
Ok guys, I've solved it. It was not a server problem, but a client problem with CUPS 1.2.2. Just upgraded the clients to CUPS 1.2.3 and the printer is back to work.

Tanks a lot people!

[ ]'s

---

### Post by centyx on 2006-11-20
Problem appears to be solved in edgy.

---

