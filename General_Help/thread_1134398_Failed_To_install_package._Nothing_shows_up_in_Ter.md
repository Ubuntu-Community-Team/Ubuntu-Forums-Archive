---
title: "Failed To install package. Nothing shows up in Terminal"
date: 2009-04-23
forum: General Help
---

### Post by errormessage on 2009-04-23
I have a problem, every time I try to install a package, even with add/remove apps I get the error "Failed to install package" But when I go to Terminal, NOTHING shows up. No messages, nothing. 

        And when I go to Add/Remove Applications, It fails to download the package(s), Ive tried multiple programs and it still Fails to download packages. And yes, I am connected to the Internet. I'm typing this on ubuntu.

Thanks!

---

### Post by Peter09 on 2009-04-23
Try in a terminal

```
sudo apt-get install <the name of the application>
```

what error messages do you get

---

### Post by paradigm2 on 2009-04-23
> **errormessage said:**
> I have a problem, every time I try to install a package, even with add/remove apps I get the error "Failed to install package" But when I go to Terminal, NOTHING shows up. No messages, nothing. 

        And when I go to Add/Remove Applications, It fails to download the package(s), Ive tried multiple programs and it still Fails to download packages. And yes, I am connected to the Internet. I'm typing this on ubuntu.

Thanks!

The repositories are being hammered right now due to the new release.  Maybe wait a day or so if you can.

---

### Post by michy99 on 2009-04-23
The servers are clogged because so many people are updating/upgrading to the new version which was officially released today. All you can do is try again later.

---

### Post by errormessage on 2009-04-23
Thanks guys for the responses, I did what Peter09 done and got this error
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package AbiWord (Just a test, don't really need the program)

NOTE: It is not that the servers are clogged, I have the file on my desktop .DEB file (Its avast! antivirus)

I also get the error with EVERY other .DEB file I try to install.

Thanks!

---

### Post by michy99 on 2009-04-23
Now I'm confused. If you got the package from Add/Remove Applications, it would not be on your desktop. You must have downloaded it from somewhere else.

If you have the DEB package, you can install it with dpkg. Or (I think) just double-click on it.

---

### Post by errormessage on 2009-04-23
No, I downloaded a .DEB file from a website (avast.com) and saved it to my desktop, I then tried to install it when It failed. 

Then, I went to add/remove apps to install something eles (WINE) and got a error when downloading a file.

So yea, it doesn't work ether way.

---

### Post by michy99 on 2009-04-23
What happens if you double click the .DEB file?

---

### Post by paradigm2 on 2009-04-23
> **errormessage said:**
> No, I downloaded a .DEB file from a website (avast.com) and saved it to my desktop, I then tried to install it when It failed. 

Then, I went to add/remove apps to install something eles (WINE) and got a error when downloading a file.

So yea, it doesn't work ether way.

If you have the .deb file and are sure you want to install it.

Go to Terminal.
Go to the directory the .deb file is in.

```

sudo dpkg -i nameoffile.deb

```

(replace nameoffile.deb with the actually name of the *.deb file)

This will install it.

---

### Post by errormessage on 2009-04-23
> **michy99 said:**
> What happens if you double click the .DEB file?

Okay, this is Exactly what happends after double clicking
Package installer pops up with details of the file and what not.
I click "install package"
I type in my password for security reasons
it comes up saying "Failed to install package"
Nothing shows up in the Terminal EXCEPT for a little rectangle located in the very top left corner. 


This Happends to EVERY .DEB file I try to install.
Hope that helped.
Thanks

---

### Post by paradigm2 on 2009-04-23
If you use the command I showed above, check it again.  I forgot to tell you to use 'sudo' in front of it. :(

---

### Post by errormessage on 2009-04-23
Well guys, after looking up the problem many times I THINK I have the solution.
The solution is to type this in Terminal

sudo apt-get install -f

BUT when I type that in, I get this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 204 package `foomatic-db':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

Please help, I think I might go back to windows if this continues =(

---

### Post by errormessage on 2009-04-23
> **paradigm2 said:**
> If you use the command I showed above, check it again.  I forgot to tell you to use 'sudo' in front of it. :(
Still got the same error =(
Oh yea, just got done d/l the new ubuntu 9.04 from bittorrent! Went to install it and got a error (forgot to copy/paste it)
but it said "Source" file could not be read or something

---

### Post by errormessage on 2009-05-01
> **errormessage said:**
> Still got the same error =(
Oh yea, just got done d/l the new ubuntu 9.04 from bittorrent! Went to install it and got a error (forgot to copy/paste it)
but it said "Source" file could not be read or something

EDIT: I have came back to windows XP, which crashed on me a few days ago. Due to this reason, I had to re-install my  whole OP.

I guess I have 0 luck with any operating system

---

