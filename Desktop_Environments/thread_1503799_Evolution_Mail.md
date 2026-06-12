---
title: "Evolution Mail"
date: 2010-06-07
forum: Desktop Environments
---

### Post by Nozy on 2010-06-07
Hi Guys 

This is driving me nuts not even sure how or when it started
I think may be after a update ? but not sure.

[IMG]http://nozy.mozysswamp.org/07062010/key.png[/IMG]

so from what you can see the hot key to send a email is X now
like "Liun." email sent

What I'm using is Ubuntu 9.04 - the Jaunty Jackalope
hoping someone may help....

---

### Post by crowderd on 2010-06-07
Which version of Evolution are you using. I know 2.28 was real buggy I downloaded 2.30 and everything is great now.

---

### Post by Nozy on 2010-06-08
> **crowderd said:**
> Which version of Evolution are you using. I know 2.28 was real buggy I downloaded 2.30 and everything is great now.

Hi Crowderd 

hmmmm I have Evolution 2.26.1! How hard was it to update to 2.30 ?

Nozy

---

### Post by crowderd on 2010-06-08
Quite simple actually I have Lucid so I am not 100% certain it will work but here is what I did
Add the PPA: [FONT=monospace]
[/FONT]sudo add-apt-repository ppa:jacob/evo230 && sudo apt-get update[FONT=monospace]
[/FONT]and Install: 
sudo apt-get install evolution

Let me know how it goes and if it works. If not I would recommend to uninstall and reinstall evolution.

---

### Post by Nozy on 2010-06-08
> **crowderd said:**
> Quite simple actually I have Lucid so I am not 100% certain it will work but here is what I did
Add the PPA: [FONT=monospace]
[/FONT]sudo add-apt-repository ppa:jacob/evo230 && sudo apt-get update[FONT=monospace]
[/FONT]and Install: 
sudo apt-get install evolution

Let me know how it goes and if it works. If not I would recommend to uninstall and reinstall evolution.

Hi Crowderd, 

have 9.04 and this does not have "add-apt-repository" but I'm sure I can work that in to 9.04 ( looking it up now )

Nozy

Let you know how it goes

---

### Post by crowderd on 2010-06-09
Ahh yes I forgot. I havent used 9.04 in quite some time but If i remember you can just add **ppa:jacob/evo230  **to your software sources (SYSTEM --> ADMIN --> Software Sources. then click other software then add and copy and paste).  Im pretty sure this will work but again I try to update with beta additions so it has been some time since I have used 9.04 as always let me know!!

---

### Post by Nozy on 2010-06-09
Hi Corowded 

Making notes here so if someone find this thread he/she will work it out too

Ok under 9.04 System --> Administration --> Software Sources

with 9.04 its under Third-Party Software --> click on +add 

this need to have the full url 

deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main

But can't find the gpg key.

on update 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

we are all most done just not sure how to find the key :)

Nozy

> **crowderd said:**
> Ahh yes I forgot. I havent used 9.04 in quite some time but If i remember you can just add **ppa:jacob/evo230  **to your software sources (SYSTEM --> ADMIN --> Software Sources. then click other software then add and copy and paste).  Im pretty sure this will work but again I try to update with beta additions so it has been some time since I have used 9.04 as always let me know!!

---

### Post by crowderd on 2010-06-09
Nozy,
        This seems to be a lil more complicated than I expected. I dont know where you would find the key. Have you tried to add the source to /etc/apt/sources.list. Also Im not for sure where you got that particular url but try "http://ppa.launchpad.net/jacob/evo230/ubuntu jaunty main". I tried this on a friends Jaunty machine and it worked without problems, hopefully this will work for you.

---

### Post by Nozy on 2010-06-11
Hi Crowderd 

Did this and now we are getting.

---
W: Failed to fetch [http://ppa.launchpad.net/jacob/evo230/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/jacob/evo230/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
--

this part is no longer on this server  jaunty/main/binary-i386 ?

# apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


> **crowderd said:**
> Nozy,
        This seems to be a lil more complicated than I expected. I dont know where you would find the key. Have you tried to add the source to /etc/apt/sources.list. Also Im not for sure where you got that particular url but try "http://ppa.launchpad.net/jacob/evo230/ubuntu jaunty main". I tried this on a friends Jaunty machine and it worked without problems, hopefully this will work for you.

---

### Post by crowderd on 2010-06-13
Nozy,
         This is getting to me... I have tried everything and now I cant get a successful install on Jaunty either. I am not very good at compiling source code but I know you can get the source from here:
[http://ftp.gnome.org/pub/GNOME/sources/evolution/2.30/](http://ftp.gnome.org/pub/GNOME/sources/evolution/2.30/)
I am not good at compiling but hope this helps.

---

### Post by Nozy on 2010-06-16
Thats ok Crowderd If I recall I had this with 7 then moved to 8 and it was fixed 

Thanks for your help 

NoZy 

> **crowderd said:**
> Nozy,
         This is getting to me... I have tried everything and now I cant get a successful install on Jaunty either. I am not very good at compiling source code but I know you can get the source from here:
[http://ftp.gnome.org/pub/GNOME/sources/evolution/2.30/](http://ftp.gnome.org/pub/GNOME/sources/evolution/2.30/)
I am not good at compiling but hope this helps.

---

### Post by crowderd on 2010-06-16
Nozy,
  Good luck. You still might want to try reinstalling your version. I wish I could of gotten this one fixed for you.

---

### Post by Nozy on 2010-06-16
Yep I would do it now but I have to do a full reinstall 

Why you ask ( or not =-) ):popcorn::popcorn:

have a /boot folder that to small 
say good buy to my vista install only booted it 5 times in 3 years
and I have the /home under xfs
and I need fill disk crypt too.



> **crowderd said:**
> Nozy,
  Good luck. You still might want to try reinstalling your version. I wish I could of gotten this one fixed for you.

---

