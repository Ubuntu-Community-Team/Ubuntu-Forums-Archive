---
title: "firefox question"
date: 2005-01-11
forum: Desktop Environments
---

### Post by danip on 2005-01-11
Why is firefox 1.0 not available for installation via apt-get.  It says I am still running .93.  This seems a little old to me.

---

### Post by wallijonn on 2005-01-11
Becasue when Warty was put together FF0.93 was the latest version. Now that Hoary is using FF1.0, a year from now when people install Hoary they will be asking why it isn't at FF2.3, etc. In the Windows world you have to remove the old FF and install the new FF. The same applies here, there are ways to use the Hoary backports to update FF0.93 to FF1.0.

---

### Post by byourg on 2005-01-11
download version 1.0 from the mozilla.org website, install it in your home folder, create a launcher on your desktop to the new firefox file and away you go. It picks up all your settings from your previous version.

---

### Post by ra1 on 2005-01-11
You can download it from mozilla.org like byourg said or you can use backports from
 [http://ubuntu-bp.sourceforge.net/]("http://ubuntu-bp.sourceforge.net/")

---

### Post by danip on 2005-01-11
I added that backport but when i search for firefox i still just get .93 am i doing something wrong?

---

### Post by ra1 on 2005-01-12
You need to do  ```
apt-get update
``` first.

---

### Post by barbarian on 2005-01-12
What I did:
added hoary repository to my etc/apt/ sources.list
then

*sudo apt-get update*

then

*sudo apt-get install mozilla-firefox*

then 

*uncomment hoary repository by# sign*

that's it;)

---

### Post by jdong on 2005-01-12
That's really not smart to do. Installing packages like that definitely will break stuff. Don't do it!


As others have mentioned, I do have firefox 1.0 packaged specifically for Warty, in Backports.

make sure you do **apt-get update; apt-get dist-upgrade** after adding the Warty Backports section to /etc/apt/sources.list.

You should also get many other updates too.

---

### Post by barbarian on 2005-01-13
So, if I'm running warty,
supose to be, that I should replace hoary firefox with the warty to avoid crashes,  isn't it?

---

### Post by Stefan Koopmanschap on 2005-01-13
thanks for that backports repository, I'm now running a wonderful recent version of firefox :)

---

### Post by jdodson on 2005-01-13
[QUOTE=wallijonn]Now that Hoary is using FF1.0, a year from now when people install Hoary they will be asking why it isn't at FF2.3, etc.[/QUOTE]

you mean a few months right?  hoary is going to be released in april:  [http://www.ubuntulinux.org/wiki/HoaryReleaseSchedule](http://www.ubuntulinux.org/wiki/HoaryReleaseSchedule)

---

### Post by clparker on 2005-01-14
Thanks again.

---

### Post by mattack on 2005-01-14
[QUOTE=jdong]That's really not smart to do. Installing packages like that definitely will break stuff. Don't do it!


As others have mentioned, I do have firefox 1.0 packaged specifically for Warty, in Backports.

make sure you do **apt-get update; apt-get dist-upgrade** after adding the Warty Backports section to /etc/apt/sources.list.

You should also get many other updates too.[/QUOTE]

Thanks for this advice. I just installed Ubuntu and am looking to get Firefox and THunderbird up to date and use my old profiles from the Windows versions I was using...

Is there a package for Thunderbird 1.0 somewhere?

---

### Post by mattack on 2005-01-14
[QUOTE=mattack]Is there a package for Thunderbird 1.0 somewhere?[/QUOTE]


Nevermind...   found it.
Now if I can just figure out where the old profiles go.

---

