---
title: "Display resolution too low"
date: 2009-08-29
forum: Desktop Environments
---

### Post by hmaseko on 2009-08-29
Just coming from Windows: How can I improve the resolution in my Ubuntu/GNOME installation? The one I am using now is too low and everything on my screen is really big and can't find in Preferences/Display a better res. In fact, there are only two options in there. Thanks in advance for your help.
hm

---

### Post by Richardarkless on 2009-08-29
this is one of the things you will need to learn if you want to get used to ubuntu, under system and administration then click on hardware drivers

if nothing comes up go under software sources, under administration and make sure proprietary drivers for devices is ticked after that we need to go to terminal which is under applications and accessories and type sudo apt-get update or if your scared of the terminal go under add/remove applications under applications and click reload when it says the sources is out of date

now restart

if something shows up then select the proprietary driver you want to install and click install 

if nothing comes up then it means that your hardware either isnt compatible or needs to compiled which I guess you dont want to do so early in learning ubuntu but as it involves the graphics card i am fairly certain that it will be supported

I dunno if you need to do it this way but whenever I need to install drivers after an install, this way always works

---

### Post by hmaseko on 2009-09-08
I want to apply the solution presented here but the problem is I keep getting this error message:
[B]
Could not download all repository indexes[/B]

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/main/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/main/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/main/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/main/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/restricted/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/restricted/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/universe/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/universe/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/universe/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/multiverse/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty/multiverse/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/main/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/main/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/restricted/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/universe/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/universe/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/main/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/main/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/restricted/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/restricted/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/universe/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/universe/source/Sources)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  403 Forbidden
Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://mirrors.cat.pdx.edu/ubuntu/dists/jaunty-security/multiverse/source/Sources)  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.

How can I get past it?

---

