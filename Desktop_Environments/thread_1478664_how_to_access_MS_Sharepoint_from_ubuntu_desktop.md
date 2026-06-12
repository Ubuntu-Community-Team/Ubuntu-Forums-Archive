---
title: "how to access MS Sharepoint from ubuntu desktop??"
date: 2010-05-10
forum: Desktop Environments
---

### Post by rockercya on 2010-05-10
HI
 
i have installed ubuntu desktop 9.10 and added the pc to a windows server 2003 domain, now i can log on to the ubuntu desktop wint domain user accounts and passwords,
 
in the domain there is a sharepoint server where all the company documents are shared among employees, 
 
my problem is i tried to access the sharepoint server from the web browser in the ubuntu desktop, but im unable to access,
 
how can i access the sharepoint site from ubuntu desktop??
 
help please
 
thanks
 
chamara

---

### Post by st0nes on 2010-07-06
I'd like to know, too, but judging by the number of replies it's probably impossible.

---

### Post by rockercya on 2010-07-19
yes i think so too :(

---

### Post by bvanaerde on 2010-07-19
> **rockercya said:**
> my problem is i tried to access the sharepoint server from the web browser in the ubuntu desktop, but im unable to access

What exactly is the error message?

Sharepoint is normally using domain credentials which are fetched by Internet Explorer. When using Firefox (in Windows), you have to manually enter your domain user and password. My guess is this will be the same when using Ubuntu.

---

### Post by rockercya on 2010-10-27
hi guys
 
i tried accessing the sharepoint site with the fully qualified domain name of the windows 2003 sharepoint server and i was able to access the root pageafter providing my domain credentials  , 
 
but everytime i click and try to access a page in the share point site i have to type the fully qualified domain name of the server otherwise it replies with a page cannot find error , is there a solution for this issue ?? is thr a way to access all the pages by clicking their link and not providing fully qualified domain name ?? 
 
thanx

---

### Post by themtx on 2010-10-27
Surprisingly (because I don't think this used to work) I'm able to authenticate and browse MOSS2007 sites in Chromium.  If I supply the url of one of our MOSS2007 boxes in FQDN format, I auth once and am able to click away - and things actually work...  I'm unfortunately the admin of our various Sharepoint instances, and even tried functions like adding users to sites via the PeoplePicker web part / object, and even that worked.  I checked Firefox and was able to mostly browse, but some other functions failed.  My xubuntu box is NOT joined to our domain, so perhaps the pre-auth through the browser, depending upon your settings, is what's breaking the url when you navigate the site(s).  Try removing the MOSS server's credentials from your cache, then not saving them when you auth the next time.

---

### Post by abexman on 2013-01-22
> **themtx said:**
> Surprisingly (because I don't think this used to work) I'm able to authenticate and browse MOSS2007 sites in Chromium.  If I supply the url of one of our MOSS2007 boxes in FQDN format, I auth once and am able to click away - and things actually work...  I'm unfortunately the admin of our various Sharepoint instances, and even tried functions like adding users to sites via the PeoplePicker web part / object, and even that worked.  I checked Firefox and was able to mostly browse, but some other functions failed.  My xubuntu box is NOT joined to our domain, so perhaps the pre-auth through the browser, depending upon your settings, is what's breaking the url when you navigate the site(s).  Try removing the MOSS server's credentials from your cache, then not saving them when you auth the next time.

Does this still work for folks? Best in Chromium but not Firefox in Ubuntu? It sounds like I may try clearing the browser cache and maybe cookies too, each time I am accessing?

---

### Post by howefield on 2013-01-22
Old thread closed.

Please feel free to create a fresh one.

---

