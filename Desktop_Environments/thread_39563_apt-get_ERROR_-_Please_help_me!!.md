---
title: "apt-get ERROR - Please help me!!"
date: 2005-06-05
forum: Desktop Environments
---

### Post by cusco on 2005-06-05
hi.. I messd arround with armagetronad.. then I wanted to remove it and I got this error:

```
cusco@Portatil:~$ sudo apt-get remove armagetronad
Reading package lists... Done
Building dependency tree... Done
E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.
cusco@Portatil:~$
```

then I open synaptic and it says...

E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.



now everytime I want to use apt-get for anything I can't:

```
cusco@Portatil:~$ sudo apt-get install supertux
Reading package lists... Done
Building dependency tree... Done
E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.
cusco@Portatil:~$
```


Please help me

---

### Post by shof2k on 2005-06-06
Erm not sure if this will help but if it's complaining about cache, try clearing out your apt cache folder (I think it's in /var/apt/cache but I can't check because I'm at work).  Then check your sources.list file, then run **sudo apt-get update**, to refresh your cache.

let me know how you get on.

---

### Post by nilus on 2005-06-06
It's similar to an error that I had...
I remember I resolved with dpkg... but I can't remember how I did, sorry. Hope that this, in any case, helps.

---

### Post by az on 2005-06-06
sudo dpkg --clear-avail

---

### Post by iamkmaniam on 2005-06-06
If none of the above work try 
sudo apt-get clean 
this may solve your problem

---

### Post by jobezone on 2005-06-06
Also try:

```
sudo apt-get -f install
```

This just might be what you want! This is what the apt-get manual says about the -f option:
> -f, --fix-broken,
              Fix;  attempt  to  correct  a system with broken dependencies in
              place. This option, when used with install/remove, can omit  any
              packages  to permit APT to deduce a likely solution. Any Package
              that are specified must completely correct the problem. The  op&#8208;
              tion is sometimes necessary when running APT for the first time;
              APT itself does not allow broken package dependencies  to  exist
              on a system. It is possible that a system’s dependency structure
              can be so corrupt as to require manual intervention (which  usu&#8208;
              ally  means  using dselect(8) or dpkg --remove to eliminate some
              of the offending packages). Use of this option together with  -m
              may  produce  an  error  in some situations. Configuration Item:
              APT::Get::Fix-Broken.


---

### Post by Ramaddan on 2006-05-30
Hi,
I don't know if anyone replied to this problem, or if anyone needs help with it, but I figured how to fix such a problem without having to re-install Ubuntu again.

I ran into the same problem, and saw some other people run into it,
but I did not find a solution, so I kept following through the original files,
and I figured how to fix the problem.

First the problem occured for me when I tried to use "alien" to change
files from rpm to deb files.

So after fooling around with all the apt-get commands, and dpkg commands,
to no avail, I finally decided to try my luck manually.

1. I opened up the deb files with Archive Manager, to have an idea of where
the files install, and followed through and saw where all the files are,
and uninstalled them.

2. Also make sure you read the files in the control zip file within the deb package with gedit (or other editor), and find out where the files where
installed.

3. Make sure all installed files and folders are deleted.
Some files will require root pass, so be careful you don't delete other files
and folders.

4. After making sure that all files and folders are deleted.

- Check "/var/packages" to see if there are any related folders
and delete them.

5. The most important:
- In order to remove package info from system,
go into "/var/lib/dpkg/info", and delete all files associated with package
and delete them.

6. Now go into a terminal and type:
- sudo dpkg -r  --force-remove-reinstreq <package name> (without brackets)

- Then, sudo dpkg --purge <package name> (without brackets)

7. Update repositories with: sudo apt-get update

And hope that you're done, and it works.

This thread is a bit old, but I did not find a reply anywhere,
so I thought to myself that this might help some people.

---

### Post by Jucato on 2006-06-07
@ramaddan: I have to thank you. your solution worked greatly for me. Thanks! :D

---

### Post by Ramaddan on 2006-06-09
Hi Fenyx,

I'm just happy it helped. Even though this is an old post, and most people
may have already stopped using Hoary, I thought to myself it could be left,
and someone might just google it up or something, and it could help.

The solution is still applicable to later versions, or maybe even other distros.

So I'm glad that the post is fulfilling its purpose.

---

### Post by Jucato on 2006-06-09
Btw, I was using your method in Dapper. So it works across releases. Thanks again!

---

### Post by msak007 on 2006-06-21
Than you Ramaddan! Your post helped me too...I foolishly tried to install a Lexmark Z65 driver RPM using alien and it hosed everything. Needless to say I'm never using alien again (or if I do and mess up I'll know how to fix it :)). Thanks again, it also worked for me in Dapper.

---

### Post by Ramaddan on 2006-06-22
Hi msak007,

You're welcome. :-)

---

### Post by GOTAO on 2006-07-29
I worked it out by using this:
```
dpkg --remove --force-depends --force-remove-reinstreq <package name>
```
I'm not sure how badly it would break dependencies, but so far so good with mine.

---

### Post by baracuda227 on 2006-07-30
Ramaddan  you are genius my friend - - no super genius. Had the same problem, worked like charm. Thank you very much! Ken

---

### Post by cro.smiley on 2006-08-04
Ramaddan you are my hero :)
You really saved my Ubuntu and my nerves!

---

### Post by nephish on 2006-08-08
whoa nelly !

just used your fix that saved a re-install of my os. 
thanks for this bunches.

works in dapper.

---

### Post by taner on 2006-08-11
thanx Ramaddan :-({|=

---

### Post by mwpo on 2006-08-26
> **Ramaddan said:**
> Hi,
I don't know if anyone replied to this problem, or if anyone needs help with it, but I figured how to fix such a problem without having to re-install Ubuntu again.

I ran into the same problem, and saw some other people run into it,
but I did not find a solution, so I kept following through the original files,
and I figured how to fix the problem.

First the problem occured for me when I tried to use "alien" to change
files from rpm to deb files.

So after fooling around with all the apt-get commands, and dpkg commands,
to no avail, I finally decided to try my luck manually.

1. I opened up the deb files with Archive Manager, to have an idea of where
the files install, and followed through and saw where all the files are,
and uninstalled them.

2. Also make sure you read the files in the control zip file within the deb package with gedit (or other editor), and find out where the files where
installed.

3. Make sure all installed files and folders are deleted.
Some files will require root pass, so be careful you don't delete other files
and folders.

4. After making sure that all files and folders are deleted.

- Check "/var/packages" to see if there are any related folders
and delete them.

5. The most important:
- In order to remove package info from system,
go into "/var/lib/dpkg/info", and delete all files associated with package
and delete them.

6. Now go into a terminal and type:
- sudo dpkg -r  --force-remove-reinstreq <package name> (without brackets)

- Then, sudo dpkg --purge <package name> (without brackets)

7. Update repositories with: sudo apt-get update

And hope that you're done, and it works.

This thread is a bit old, but I did not find a reply anywhere,
so I thought to myself that this might help some people.

I got this error when I try to install jedit using apt from [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit).

E: the package jedit needs to be reinstalled but I can't find an archive for it. When I go to update I get the same error plus I get 
E: Internal error opening cache(1).

I have the follow in my sources.list

##jedit
deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./


I resolve in this way:

# cd /var/lib/apt/lists

remove the file(s) dl.sourceforge.net_sourceforge_jedit_._Packages and dl.sourceforge.net_sourceforge_jedit_._Sources

# rm -fr dl.sourceforge.net_sourceforge_jedit_._*

then 

# cd /var/lib/aptitude

open the file **pkgstates** and delete any related lines to the packages jedit

finally

# cd /var/lib/dpkg

open the file **status** and lete any related lines to the packages jedit


# sudo apt-get clean
# sudo apt-get update

Now I'm able to use apt-get or synaptic to install/remove/update packages !!!
Thanks to ramaddan for help me to find the right way.

---

### Post by urbanus on 2006-08-26
GREAT! Finally an answer to this IRRITATING problem :confused: #-o :mad: 
;) ;) ;) ;) ;)

---

### Post by dean703 on 2006-09-18
I also solved this problem using your method in Dapper. Thank you.

---

### Post by Ramaddan on 2006-09-18
Hi,

Everyone is welcome!

---

### Post by think13 on 2006-09-28
Thank you!

---

### Post by wirah on 2008-02-06
I just used this method in Gutsy! Fantastic howto, worked a treat- thanks.

Ubuntu guys - this 'last resort' functionality really needs to go into apt/aptitude. I was stuck for nearly 2 days with a package which wouldn't install, reinstall, or remove!!

---

