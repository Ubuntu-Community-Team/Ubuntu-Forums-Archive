---
title: "Rscript via php not working but works on terminal"
date: 2013-02-11
forum: Education &amp; Science
---

### Post by megamonk on 2013-02-11
Hi,

I have installed R on my server and have a problem with Rscript. basically when i use Rscript via terminal its working but the same exact code via php doesnt work.

on terminal:

*Rscript file.R > file.csv*

WORKS!

on php:

*shell_exec("Rscript file.R > five.csv");*

DOESNT work...

tried:

*shell_exec("Rscript file.R 2>&1");*

and shows:

*Rscript: command not found*

located Rscript directory at /usr/bin/Rscript

so i changed the code to:

*shell_exec("/usr/bin/Rscript file.R 2>&1");*

and got:

*sh: usr/bin/Rscript: No such file or directory*

made various variations to code thinking either i needed to make sure path to file is correct. tried both absolute and relative paths. nothing worked.

any ideas? please help me. THANKS

---

### Post by schragge on 2013-02-11
I guess the httpd (apache?) restricts what can be executed. Look in configuration settings for your web server.

---

### Post by megamonk on 2013-02-11
can you kindly point out what settings i should look for?

---

### Post by schragge on 2013-02-11
I don't know. That was only a wild guessing on my part. I could be very well wrong. Maybe there is someting in the *error_log* of your web server?

---

### Post by SlugSlug on 2013-02-11
has user www-data got access to 
[I]/usr/bin/Rscript  ?

[/I]In my exec scripts I use a ' not "  not sure if it matters[I]
& this 

[/I]
[I]sh: usr/bin/Rscript: No such file or directory

is not the same as 
[/I] *sh: **/**usr/bin/Rscript: No such file or directory*

Typo?

---

### Post by megamonk on 2013-02-11
how can i check if www-data got access to /usr/bin/Rscript? if they dont, how can i give it access?

i tried both:

echo "usr/bin/Rscript 2>&1";
print_r ( shell_exec('usr/bin/Rscript 2>&1'));
echo "<br />";

echo "/usr/bin/Rscript 2>&1";
print_r ( shell_exec('/usr/bin/Rscript 2>&1'));
echo "<br />";

and they give:

usr/bin/Rscript 2>&1 sh: usr/bin/Rscript: No such file or directory 
/usr/bin/Rscript 2>&1 sh: /usr/bin/Rscript: No such file or directory 

i really hope this can be resolved soon. thanks

---

### Post by SlugSlug on 2013-02-11
```
sudo chmod 755 /usr/bin/Rscript
```Does that error (unsure about capital R)

Unsure of php script but mine are along the lines of:
```
<?php
shell_exec('/usr/bin/Rscript 2>&1');
?>
```

---

### Post by schragge on 2013-02-11
> **megamonk said:**
> how can i check if www-data got access to /usr/bin/Rscript? if they dont, how can i give it access?I guess file permissions are ok, but there can be apparmor at play. If a confined process doesn't have access to a file, you'll get messages like
```

audit(1148420912.879:96): REJECTING x access to /bin/uname (sh(6646) profile /tmp/sh active /tmp/sh)

```
either in */var/log/audit/audit.log* or */var/log/messages*

---

### Post by megamonk on 2013-02-11
i have checked the permission of Rscript and its 0755.

i dont know if this helps but in my windows box i had to add the path to R directory to the environment variables to get it working on the local instance of my site.

on the ubuntu server.. i checked the $PATH (echo $PATH) when im using the terminal via ssh as:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

but on php:

using -> shell_exec('echo $PATH') outputs:
/sbin:/usr/sbin:/bin:/usr/bin 

in both paths, i can see that the directory /usr/bin is present. does this make a difference? or is their something wrong here?

about the capital "R", are you referring to the "Rscript" wording? if so i have checked using the terminal that using "rscript" (lowercase) doesnt work but "Rscript" works which suggest its case sensitive.

ex:

rscript blah.r <- doesnt work
Rscript blah.r <- works

---

### Post by megamonk on 2013-02-11
> **schragge said:**
> I guess file permissions are ok, but there can be apparmor at play. If a confined process doesn't have access to a file, you'll get messages like
```

audit(1148420912.879:96): REJECTING x access to /bin/uname (sh(6646) profile /tmp/sh active /tmp/sh)

```either in */var/log/audit/audit.log* or */var/log/messages*

checked /var/log but cant find "messages" or "audit". since i tested it today i checked the latest changed/updated log file and the only thing that changed is "auth.log". checked it and nothing remotely similar to the error log you gave within the time frame of my test.

---

### Post by megamonk on 2013-02-11
now that i think about it... maybe the reason my php page cant access the Rscript on /usr/bin/Rscript is the "directory jail". since:

shell_exec('/usr/bin/Rscript 2>&1')

results in:

/usr/bin/Rscript: No such file or directory

maybe it cant find the resource since its jailed to the "web directory". if this is the case, how can i give access to www-data to Rscript so that it can run it?

---

### Post by SeijiSensei on 2013-02-11
You can test out permissions by becoming the "www-data" user that Apache runs as like this:

```

you@something $ [COLOR="blue"]sudo su -[/COLOR]
[enter your password]
root@something # [COLOR="blue"]su www-data[/COLOR]
www-data@something $ [COLOR="Blue"]Rscript etc.[/COLOR]

```

Type the text in blue.

---

### Post by megamonk on 2013-02-11
> **SeijiSensei said:**
> You can test out permissions by becoming the "www-data" user that Apache runs as like this:

```

you@something $ [COLOR=blue]sudo su -[/COLOR]
[enter your password]
root@something # [COLOR=blue]su www-data[/COLOR]
www-data@something $ [COLOR=Blue]Rscript etc.[/COLOR]

```Type the text in blue.

tried it but encountered an error... 

me@somewhere:~$ sudo su -
root@somewhere:~# su jedoxweb
Cannot execute /sbin/nologin: No such file or directory
root@somewhere:~#

if it helps... im using an EC2 AWS server and have jedox installed thats why the user is 'jedoxweb' not 'www-data'

---

### Post by SeijiSensei on 2013-02-11
Edit as root the file /etc/passwd and change the /sbin/nologin entry for that username to /bin/bash, then try again.  Ubuntu's www-data user has shell privileges, but that "jedoxweb" user apparently does not.  When you have everything working, change the shell back to /sbin/nologin.

---

### Post by megamonk on 2013-02-13
Hi,

just an update. i found out why its not working on my linux box. basically, im not using a regular lamp stack from ubuntu. im using jedox which in itself already has apache and php included. it also seems that to make jedox work on linux they run it by 'virtualizing' (dunno how to properly describe it) it. i realized this because the directory structure of jedox has etc, usr, home folders which we usually see in the root directory. also i found out that to make jedox work its chrooted so /urs/bin on command line is not the same as usr/bin when ran via php shell_exec() which causes those errors.

now the question is there any way  to work around this? make or allow the php shell_exec to work out of its chrooted environment for Rscript to work.

thanks

---

### Post by SeijiSensei on 2013-02-13
You need to make copies of every binary and its associated libraries and configuration files in the chrooted environment. I presume for you that means R and Rscript and anything associated with them.

You can use dpkg to list all the files in a package to see which ones you need to copy.  You might also consider installing packages to the chrooted environment with the "instdir" option to dpkg pointing to the top of chroot tree.

---

### Post by megamonk on 2013-02-13
> **SeijiSensei said:**
> You need to make copies of every binary and its associated libraries and configuration files in the chrooted environment. I presume for you that means R and Rscript and anything associated with them.

You can use dpkg to list all the files in a package to see which ones you need to copy.  You might also consider installing packages to the chrooted environment with the "instdir" option to dpkg pointing to the top of chroot tree.

can you kindly guide me on how to do this? not really that well versed yet. im interested in the "instdir". how do i do that? thanks

---

### Post by SeijiSensei on 2013-02-13
You need the .deb files for the applications you are using.  Take a look in /var/cache/apt/archives; anything you installed recently from the repositories should be there.  

Now read "man dpkg".  You'll see a mention of the "--instdir" option.  The default is the root of the filesystem, /.  You need to specify the top of the chroot tree instead.  Then instead of installing a binary to /usr/bin, it will be installed to instdir/usr/bin.

I think this should work, but it's not something I've done myself.  

As an aside, is there some reason you've chosen to use this jedoxweb thing rather than a standard web server like Apache?  Running in a chrooted jail is one way to improve security, but Apache itself is already pretty robust without any of that.  I've run Apache servers for over fifteen years and only had one security issue a decade ago when I failed to upgrade after a fix was released for a security flaw.  Even then all that happened was someone dropped a binary into /tmp that he used as a IRC repeater to attack another IRC site.

---

