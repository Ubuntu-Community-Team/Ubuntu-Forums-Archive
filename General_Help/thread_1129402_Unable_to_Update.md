---
title: "Unable to Update"
date: 2009-04-18
forum: General Help
---

### Post by ollieblake on 2009-04-18
Hello,

I have recently installed Ubuntu 8.10 on to my Dell Inspiron 640m, I have a strange question to ask.

I set up the computer at work and set the proxy to the straight through line to the unrestricted internet so I could set things up quicker, I THINK I have removed all traces of the proxy that I used in work from all network places but when I go to update it says:


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dash/dash_0.5.4-9ubuntu1.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dash/dash_0.5.4-9ubuntu1.1_i386.deb)
  Unable to connect to 172.16.1.201 80:




My home network is 192.1.0.0 though, I cant possibly see in any settings within the Update Manager properties or any other properties where 172.16.1.201 is being used?

I have even set the default gateway as my home network in terminal and it says it already exists, having a hard time here!

Thank you in advance,

Ollie Blake

---

### Post by Alterax on 2009-04-18
Ollie:

I'd be glad to help you, but PLEASE trim down the post above.  The bulk of it can be replaced with one instance of the error, rather than the same exact error for 100+ files.  Pain to scroll through it all every time.

Not to worry, though, like I said, I will help.  It looks like you can't resolve the location of your files.  I'm assuming that you've tried different mirrors.  Post the contents of your resolv.conf file and let's have a looksie at your DNS servers.

Also the contents of /etc/network/interfaces would help in resolving this.

Make sure your gateway and netmask are set appropriately for your network, and that you can surf the web from that machine.  If not, that could be the source of your problem, as the updating service uses the HTTP protocol to pull these packages.

If you can, then the next logical step would be to try a different mirror.  Look in SOFTWARE SOURCES, under your ADMINISTRATION tab.  You should be able to use it to detect (and set up) a mirror that works best for your location.

Keep me posted.  I'll run some diagnostics from here, based on what you have posted.

---

### Post by Alterax on 2009-04-18
Interesting...it appears that your DNS server is giving out the 172.whatever range address for the mirror.  Meaning when you are looking up the mirror in DNS (like a telephone book, really), you get that number.

Problem is that number is a reserved block that doesn't go anywhere.

Try changing your DNS server to 208.67.222.222 (which is the address for the OpenDNS server I use) and running it again.  

If that doesn't do it, try changing it back and going to [http://172.16.1.201](http://172.16.1.201) in firefox--this may be a case of your proxy server intercepting the stream and either requesting that you log in (in which case you log in on Firefox and do your updates while the window is open) or telling you flat-out "NO" (in which case you talk to your proxy's administrator and ask them nicely to add *.ubuntu.com to the list of accepted sites or sites that do not require authentication, on the grounds that it is used to distribute critical security updates for your OS)

Let me know!

-Alterax

---

### Post by ollieblake on 2009-04-18
> **Alterax said:**
> Interesting...it appears that your DNS server is giving out the 172.whatever range address for the mirror.  Meaning when you are looking up the mirror in DNS (like a telephone book, really), you get that number.

Problem is that number is a reserved block that doesn't go anywhere.

Try changing your DNS server to 208.67.222.222 (which is the address for the OpenDNS server I use) and running it again.  

If that doesn't do it, try changing it back and going to [http://172.16.1.201](http://172.16.1.201) in firefox--this may be a case of your proxy server intercepting the stream and either requesting that you log in (in which case you log in on Firefox and do your updates while the window is open) or telling you flat-out "NO" (in which case you talk to your proxy's administrator and ask them nicely to add *.ubuntu.com to the list of accepted sites or sites that do not require authentication, on the grounds that it is used to distribute critical security updates for your OS)

Let me know!

-Alterax


Perfect, it works! Thank you ever so much to you both for your help, its greatly appreciated!


Thanks again,

Ollie Blake

---

