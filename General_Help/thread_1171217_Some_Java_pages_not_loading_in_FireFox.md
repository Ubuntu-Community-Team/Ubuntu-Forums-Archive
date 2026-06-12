---
title: "Some Java pages not loading in FireFox"
date: 2009-05-27
forum: General Help
---

### Post by marshmugger on 2009-05-27
I have this problem on my Acer Aspire One since Linpus. I hacked Linpus to death and have done a fresh install of Ubuntu 9.04, it's much better than Linpus but the problem remains.

My online banking sites has these hardware requirements:
OS Windows or Mac
Browser IE v6+, Firefox v2+ or Safari v2
Screen Resolution 800x600 or greater

The bank site works fine on two different Windows PCs.

When I try and load the logon page with my Linux machine, first I get a warning about browser compatibility, then the .jsp page loads verrry slowly and nothing much happens after login.

I have done a fresh install of Ubuntu, ran the Update Manager, installed updates and then I installed Sun Java 6 browser plugin with Add/Remove Applications. I haven't installed anything else yet.

Firefox reports v3.0.10
Java reports Java 6 update 13 here [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

I think my system is capable. Has anyone experienced problems like this? How might I fix it?

It's important that I can access my bank online because I want to take my netbook on the road.

Stephen.

---

### Post by wetsocksmell on 2009-05-27
I also have the same problem with other java based sites i feel jour pain :-( if i find a solution i'll send you a post.

---

### Post by mike555 on 2009-05-27
try the add-on for firefox called "user agent switcher" , it works for some sites ..... I think it's something about Firefox in Ubuntu reporting the browser as "Ubuntu" instead of Firefox.

---

### Post by jamesstansell on 2009-05-27
Yes, there have been similar problems reported in the launchpad bugs.  The less specific they are the harder they are to see if the problems are the same.

What is the URL of the site that has problems?  Others who use it might have had similiar issues and found out how to address them.

Java 6 for x86 starting with update 10 (6u10) includes two plugins.  The old one has oji in the name.  The new one is called npjp2.  Only one can be used at a time but some sites don't run properly with the new one.  (Yeah, that's a bit sad.)  In Firefox 3 select Tools -> Add-ons from the menu and let us know which version shows up.

Explaining how to switch between them is a little more than I can get into right now, but there are some other threads here that discuss it.  If a site works with the old plugin but doesn't work with the new one then it would be ideal to report the problem both to the webmaster and to Sun (or by proxy through launchpad.)

Regards,

-james.

P.S.  JSP is a server-side use of java so it really isn't related to your apparent client-side issue.

P.P.S. The windows edition of the java plugin should also include two plugin versions starting with 6u10.  I believe they can also be switched out, but I've never tried there.  (BTW, the npjp2 version uses the newer plugin API so it doesn't work with Firefox 2.)

---

### Post by Sum Guy on 2009-05-29
I have now got access to 3 computers with Ubuntu:
Vaio UX
Aspire One
Eee PC

Now all 3 can access the net, but the Aspire can't seem to do anything with Java script (don't know about Java itself), not even being able to use Ubuntu's Google mirror (default homepage). Could this be a similar problem? Note the others are fine.

---

### Post by marshmugger on 2009-05-30
Thanks everyone, I hope I get this sorted.

I have libnpjp2.so plugin.
The url is [http://www.nab.com.au/](http://www.nab.com.au/) Click on the login button.

I'm going to try and get the user agent switcher plugin.

---

### Post by Sum Guy on 2009-05-30
fyi, found the problem with mine too, ubuntu's recommended partitioning didn't give it enough space or swap. 170 mb swap is not enough.:-x

---

### Post by ajgreeny on 2009-05-30
I am having similar problems here with a compaq laptop.  It has all the same installed java apps as my desktop, and shows the same info in about:config, (libnpjp2.so shows if I use the filter "javaplugin") but certain java applets refuse to work on the laptop.

---

### Post by marshmugger on 2009-06-18
I still haven't solved the problem.
The pages load speedily on two Windows PCs but on my laptop they slow down at about 2/3 progress. I could login but gave up waiting for the next page. I have increased my SWAP to 1GB.

---

### Post by marshmugger on 2009-06-28
Umm, don't ask me how but the problem has solved itself or maybe it's the regular updates I've been installing. I am happy now.

---

