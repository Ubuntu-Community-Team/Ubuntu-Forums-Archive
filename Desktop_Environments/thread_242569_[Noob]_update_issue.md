---
title: "[Noob] update issue"
date: 2006-08-23
forum: Desktop Environments
---

### Post by homie_budy_dude on 2006-08-23
When installing 6.06 LTS I get the following errors.
Also tried running the "apt-get update" and "aptitude upadate" in terminal but I get connection failed too.

I can load page [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) from machine fine.

This may have something to do with Authentication as it shows trying to download these updates "Not Authenticated"

But I have no idea what that means.

Any help would be great!! Thanks in advanced


Here are a couple of the errors that I recieved...119 errors in all.

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)
  Connection failed


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb)
  Connection failed

---

### Post by Paul41 on 2006-08-23
> Also tried running the "apt-get update" and "aptitude upadate" in terminal but I get connection failed too.

For apt-get you need to use sudo, so it would be:
```
sudo apt-get update
```

---

### Post by homie_budy_dude on 2006-08-23
Yes sorry I did use the "sudo apt-get update"

Same errors but in the terminal window

---

### Post by homie_budy_dude on 2006-08-24
UPdate:

Also tried fix in post
[http://www.ubuntuforums.org/showthread.php?t=238349&highlight=Archive+automatic+signing+key](http://www.ubuntuforums.org/showthread.php?t=238349&highlight=Archive+automatic+signing+key)

Didn't help.

Also removed the "ca." as indicated in post
[http://www.ubuntuforums.org/showthread.php?t=128684&highlight=ca.archive](http://www.ubuntuforums.org/showthread.php?t=128684&highlight=ca.archive)

Anyone with any idea??
Please help ](*,)

---

### Post by asplode on 2006-08-24
You might try editing your /etc/apt/sources.list file, cutting everything out, saving it (leave the window open), run a sudo apt-get update, then put all the repos back in the sources.list file.  Then update again and try again (There's sometimes a bug in apt)

---

### Post by homie_budy_dude on 2006-08-24
> **asplode said:**
> You might try editing your /etc/apt/sources.list file, cutting everything out, saving it (leave the window open), run a sudo apt-get update, then put all the repos back in the sources.list file.  Then update again and try again (There's sometimes a bug in apt)

Lets make sure i did this right
Edit /etc/apt/sources.list to be blank
save it (leaving open in gedit)
Run "sudo apt-get update"
Put back all the info into /etc/apt/sources.list
Run "sudo apt-get update"

That didn't fix it.

I'm kinda leaning more towards this being a Key issue...but any help would be great!!

---

### Post by homie_budy_dude on 2006-08-24
Anyone think my issue may be related to the Xserver update issue.

I did have Ubuntu 6.06 installed before without any issues but had to put Windows on for a few days for testing some software.

Then when trying to install now I'm running into all these issues.

---

### Post by FuriousLettuce on 2006-08-24
This may seem silly, but can you get the update if you ping first?

```
ping ca.archive.ubuntu.com
```

Then try

```
sudo apt-get update
```

If you get the resolution as 1.0.0.0 or 0.0.0.1 [or anything along those lines] it might be worth disabling IPv6 [it's unlikely you're using it anyway]. There are many tutorials on disabling it, just search the forums.

---

### Post by homie_budy_dude on 2006-08-24
> **FuriousLettuce said:**
> This may seem silly, but can you get the update if you ping first?

```
ping ca.archive.ubuntu.com
```

Then try

```
sudo apt-get update
```

If you get the resolution as 1.0.0.0 or 0.0.0.1 [or anything along those lines] it might be worth disabling IPv6 [it's unlikely you're using it anyway]. There are many tutorials on disabling it, just search the forums.


No luck there either
It does resolve to 82.211.81.182

I can also take any of the addresses and load them fine in firefox.

More info for anyone that can help.
This is a fresh install...well I'm at work and I did it just before I left home so 7-8 hours ago.

During install it couldn't download the security packages.

BTW thanks to all for the help!!! Any other sugestions are apreciated!

---

### Post by FuriousLettuce on 2006-08-24
What happens if you just use wget to directly fetch one of the files?

---

### Post by homie_budy_dude on 2006-08-24
> **FuriousLettuce said:**
> What happens if you just use wget to directly fetch one of the files?

I can download them fine

Where should I download them to tho would be my next question.

---

### Post by homie_budy_dude on 2006-08-26
So....this is still not working.
I've done a new install and same results.
I've redone all the fixes...still not working...any ideas out there from some of the masters?

Here is a copy of my /etc/apt/sources.list incase that helps anyone.

```


deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu dapper universe
# deb-src http://archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by mrvw0169 on 2006-08-26
This is weird - I'm having the same problems as well and can't do aptitude upgrade due to all connection errors (but I can still ping, type the URLs in Firefox, and still browse the packages)... Seems to be a problem with apt/get/itude? Everything was working fine last night... I'm using [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) and got rid of the us and even replaced it with ca but no luck at all...

EDIT: Ok, further searching got it working for me - I just disabled "block keywords" on my router during the update and turn it back on afterwards -- apparently you may also have success by port forwarding port 80 to the Ubuntu computer...

---

### Post by homie_budy_dude on 2006-08-26
> **mrvw0169 said:**
> This is weird - I'm having the same problems as well and can't do aptitude upgrade due to all connection errors (but I can still ping, type the URLs in Firefox, and still browse the packages)... Seems to be a problem with apt/get/itude? Everything was working fine last night... I'm using [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) and got rid of the us and even replaced it with ca but no luck at all...

EDIT: Ok, further searching got it working for me - I just disabled "block keywords" on my router during the update and turn it back on afterwards -- apparently you may also have success by port forwarding port 80 to the Ubuntu computer...

That is crazy...this has been an ongoing thing for me...I had Dapper insalled once on this box and was working fine...had to install windows for some testing then back to dapper and this is happening!!

I was almost wondering if it could be an athentication issue...there are keys that are assigned but I don't know how to get a new one.

And yes I can browse to them and do wget for all of the URL's that I've tried.

If you do find out what is up give me a halla!!

Cheers,
Chris

---

### Post by homie_budy_dude on 2006-08-26
> **mrvw0169 said:**
> 
EDIT: Ok, further searching got it working for me - I just disabled "block keywords" on my router during the update and turn it back on afterwards -- apparently you may also have success by port forwarding port 80 to the Ubuntu computer...

YOUR NOW MY HERO!!!

I didn't even know I had block words setup in my router...been there from some testing I did a long time ago!!

THANK YOU SOOO MUCH

I'm back to loving Ubuntu again!!!

---

