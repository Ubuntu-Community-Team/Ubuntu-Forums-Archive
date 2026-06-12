---
title: "Problem with installing packages"
date: 2005-06-26
forum: Desktop Environments
---

### Post by tekeo on 2005-06-26
Hello I installed Kubuntu for the first time today and I love the command apt-get. I want to install SuperKaramba but didn't find it on apt-get. So I downloaded source version and get the error:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

I googled it and found out I need xorg-devel but can't find that on apt-get either!
I don't know if I made something wrong (and yes I have 'sudo' in front).

I have used gentoo for a while before I changed to kubuntu and liked the command 'emerge'. U can use 'emerge -s' and then write a package name to search for I wounder also if there is an option like that included or where I can find a list of all packages.

Best regards
//Tekeo

---

### Post by Takis on 2005-06-26
Could you post the contents of '/etc/apt/sources.list'?

---

### Post by tekeo on 2005-06-26
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

I'm not sure how to open it tried ls aswell. I tried to install a few more packages that SHOULD work but only tells me that it doesn't exist :S.

//Tekeo

---

### Post by SGC on 2005-06-26
Superkaramba 0.35 is in the universe repositroy. to enable it, just remove the # in the begining of:
```

# deb http://se.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://se.archive.ubuntu.com/ubuntu hoary universe

```

For the latest version (0.36) you need , the backports repository , add this lines to the sources file:
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

After that you need to do **apt-get update** then **apt-get install superkaramba**


To search for packages use the following command:
```

apt-cache search KEYWORD

```

Example: apt-cache search karamba

To know more about a package:
```

apt-cache show PACKAGE_NAME

```

Example: apt-cache show superkaramba

---

### Post by tekeo on 2005-06-27
Thx lots now it works perfectly :D
//Tekeo

---

### Post by MetalHannes on 2005-09-04
Can somebody tell me why it wont work on my pc

Sources list: 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary universe
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

and done al the other stuff but the problem wont go away  ](*,)

---

### Post by Takis on 2005-09-04
[QUOTE=MetalHannes]Can somebody tell me why it wont work on my pc
[/QUOTE]
Could you be a bit more specific? What won't work - i.e. can you not install it or can you not run it?
What happens if you type
```
sudo apt-get install superkaramba
```?

---

