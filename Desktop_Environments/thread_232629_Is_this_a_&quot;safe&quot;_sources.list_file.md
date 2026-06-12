---
title: "Is this a &quot;safe&quot; sources.list file?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by JohnJSal on 2006-08-09
I used the file from the DapperGuide, but commented out a few extra things. My main questions are:

1. Is there anything here that could either harm my system or prevent me from getting needed updates or security patches?

2. Can you put comments in the middle of a line, like I did with the updates and security links, or must they start at the beginning of a line?

3. My original sources.list file also had this line:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

Is this necessary? The guide I used didn't mention this line.

So here is my file:

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted #universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted #universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted #universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted #universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted #universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted #universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
#deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

Edit: I'm noticing that some links in my original file have the us. prefix in the URL, and some don't. Can I assume that I'm still getting the proper versions for my system even if I don't specify the country?

---

### Post by computergroove on 2006-08-09
Your only safe sources.list file is the one that comes with the installation of ubuntu. If you are worried about it then dont add new repositories to your sources.list file. Instead install anything you need from source files manually downloaded from developers websites. 

BTW - Ive never had a repository screw up any part of my install.

---

### Post by cantormath on 2006-08-09
Any sources.list can be safe. Yours looks pretty safe.  There is nothing wrong with the repos you have listed there.  What you might want to be careful of is updating your system with 
```

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted #universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted #universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

The universe, backports and PLF have new packages or versions of packages that have not been as tested on ubuntu.  This may be a risk to your stability, depending on what you are doing.  Just my opinion.

good luck.

---

### Post by JohnJSal on 2006-08-09
> **cantormath said:**
> Any sources.list can be safe. Yours looks pretty safe.  There is nothing wrong with the repos you have listed there.  What you might want to be careful of is updating your system with 

<snip code>

The universe, backports and PLF have new packages or versions of packages that have not been as tested on ubuntu.  This may be a risk to your stability, depending on what you are doing.  Just my opinion.

good luck.

I don't understand what you mean. Haven't I commented out all those things you mentioned, so they won't be a part of the installation?

---

### Post by John.Michael.Kane on 2006-08-09
JohnJSal you can also make your own using [**[COLOR="Red"]source-o-matic[/COLOR]**]("http://www.ubuntulinux.nl/source-o-matic").

---

### Post by Ramses de Norre on 2006-08-09
Man you are really limiting yourself if you ask me.. there is nothing unsafe about universe or multiverse, those packages are just made by mainly debian devs and not by ubuntu devs. But hey they work in 99% of the cases!
And you can be pretty sure things in backports wont be trojans or rootkits neither, all those packages are made by people from the ubuntu comunity.

---

### Post by JohnJSal on 2006-08-09
Thanks for the advice. I think I will turn universe and multiverse back on like you say. But what are 'backports'? How do they differ from the universe and multiverse programs that are in the other ubuntu links?

---

### Post by Ramses de Norre on 2006-08-09
That are packages for programs with outdated versions in the repos, on release the versions of packages in the repos are locked. They only upgrade packages for security reasons. But when a package gets a new version with a great functionality raise the backports team will see whether it's possible to create a deb for the newer package without breaking dependencies and if that's possible the newer package gets in the backports repo.
It's possible that in a couple of months several edgy packages will hit the backports repo.

---

### Post by cantormath on 2006-08-11
> **JohnJSal said:**
> I don't understand what you mean. Haven't I commented out all those things you mentioned, so they won't be a part of the installation?

yes, you did, thats why I said it looks pretty safe, I was just noteing that one would want to be careful of updating with those, just in case you uncommented them in the future.

sorry for the confusion.

---

### Post by cantormath on 2006-08-11
> **Ramses de Norre said:**
> Man you are really limiting yourself if you ask me.. there is nothing unsafe about universe or multiverse, those packages are just made by mainly debian devs and not by ubuntu devs. But hey they work in 99% of the cases!
And you can be pretty sure things in backports wont be trojans or rootkits neither, all those packages are made by people from the ubuntu comunity.


Its not that the packages might not be safe its just that they have not been as tested on ubuntu, from what I understand, and I have had a few minor issues with a few of the packages in universe/multiverse, small things.  I only make that comment because Im not sure what kind of system or setup one is using....  I would hate for something bad to happen.

---

