---
title: "Global Adress List in Evolution"
date: 2009-05-21
forum: General Help
---

### Post by hirolau on 2009-05-21
Hi. I am trying to get my school mail to work at home with Evolution.

I a able to sync everything except the GAL (Global Address List)

It does not matter what i do, i get this message:

[I]
Error loading address book.

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.[/I]

I booted my virtual XP and installer outlook 2003, from there i can easily connect and search the GAL. I checked to make sure the URL is right, and so the user name, and the password is the same.

From Outlook 2003 the GAL connects to mail11.stu.***.com with the user name STUDENT\studentnr

I get the error above even if i do have the same URL and user name. One thing I might thing is wrong is that in Outlook 2003 there is a field called: *The directory hierarchy folder path for this container is: \Global Address List * This might be some subfolder or something, but i cant seem to find the same thing in Evolution. I have tried mail11.stu.***.com\Global Address List and mail11.stu.***.com\Global%20Address%20List but i cant get it to work.

Anyone who is able to access An exchange server from bot evolution and outlook 2003 that can check how to set it up?

---

### Post by hlygrail on 2009-06-02
I have the same problem.  Any help would be appreciated.
> This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

---

### Post by Loyd Gravitt on 2009-06-04
Same problem here.  Any help would be most welcome.  This is one of the last big steps to making ubuntu my main box at work.

---

### Post by Loyd Gravitt on 2009-06-04
Ok, found the solution, at least for my box.  It was related to not having a Fully Qualified Domain Name for my Active Directory domain controller specified in the setup for my evolution email account.  A summary of the problem and its solution can be found at:

[http://www.bauer-power.net/2009/06/i-finally-got-global-address-to-work-in.html](http://www.bauer-power.net/2009/06/i-finally-got-global-address-to-work-in.html)

For me, the biggest problem was in finding the name of my domain controller, but one of our system administrators was finally able to get that information for me.

---

