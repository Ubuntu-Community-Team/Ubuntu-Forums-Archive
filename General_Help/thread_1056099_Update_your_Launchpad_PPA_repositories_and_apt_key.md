---
title: "Update your Launchpad PPA repositories and apt keys"
date: 2009-01-31
forum: General Help
---

### Post by forger on 2009-01-31
> Your Launchpad PPA: three important changes
--------------------------------------------

We have three important items of news regarding your Launchpad 
Personal Package Archive(s):

 * your PPA now has its own key and packages are now signed
 * your PPA URLs and upload paths are going to change
 * we are going to start removing deleted/superseded packages 
   from our servers.
   
These changes affect PPAs owned both by individuals and teams.

Full email here: [http://paste.ubuntu.com/112078/](http://paste.ubuntu.com/112078/)

I made a perl script that:
- Can detect and fix any launchpad PPA link from apt .list files
- Backs up the original source list (e.g. /etc/apt/sources.list as 
  /etc/apt/sources.list.backup)
- Imports GPG keys for the links detected apt .list files

**[size=150]Requirements:[/size]**
- Administrative privileges
- Perl
- Internet connection
- HTML::Parser IO::Socket::SSL
```
sudo apt-get install libhtml-parser-perl libio-socket-ssl-perl
```

**How to use it:**
```
wget http://savvas.radevic.com/launchpad/launchpad-ppa-fix.tar.gz -O launchpad-ppa-fix.tar.gz
tar xzvf launchpad-ppa-fix.tar.gz
perl launchpad-ppa-fix.pl
sudo apt-get update
rm launchpad-ppa-fix.tar.gz launchpad-ppa-fix.pl

```

**Fallback plan:**
If anything goes wrong, I guess the only important thing changed are the .list files.
The script creates a backup for each .list file, for example /etc/apt/sources.list.d/test.list 
is backed up as /etc/apt/sources.list.d/test.list.backup

You can see the output and restore whichever file required.

**Code**
bazaar: bzr branch lp:~medigeek/+junk/launchpad-ppa-fix

**Updates:**
> # UPDATES:
# 1.6:
#    * Added support for new format in edge.launchpad.net server.
#    * No longer adding $key to your username's gpg (using apt-key adv)
# 1.5:
#    * Added support when 2+ PPAs exist from the same user/team.
# 1.4:
#    * Fixed wrong check between @lpusers and $ENV{'http_proxy'}
# 1.3:
#    * Enlists errors (contacting the Launchpad site)
#    * Adds suggestions for proxy if errors found
#    * Using glob("$sourceparts/*.list") instead of regex \.list$ check
#    * Using LWP::UserAgent instead of LWP::Simple
#    * Using environment *_proxy fields
# 1.2:
#    * Added md5sum check for sources.list
#    * Added support for /etc/apt/sources.list.d/*.list
# 1.1:
#    * Added support for key format in edge.launchpad.net server.
#    * Needs IO::Socket::SSL


-

---

### Post by jpeddicord on 2009-01-31
I've moved this to General Help from Tutorials & Tips. My reasoning is that this is really just a script that does everything for you. Scripts updating repositories especially are generally discouraged, because if it fails then the user is left with an unusable system save for the backup list.

You are free to resubmit your tutorial, but please make sure that it details **how** a user can update their sources and add GPG keys, don't just do it for them with a script.

---

### Post by forger on 2009-02-01
> I've moved this to General Help from Tutorials & Tips. My reasoning is that this is really just a script that does everything for you.
Ah ok :)

> You are free to resubmit your tutorial, but please make sure that it details how a user can update their sources and add GPG keys, don't just do it for them with a script. 
That is already explained here:
[http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by forger on 2009-02-13
I've added support for /etc/apt/sources.list.d/*.list :)

---

### Post by binbash on 2009-02-16
Helped me a lot! Works like a charm thanks

---

### Post by forger on 2009-02-16
Thanks for the comment! :)
I've added support for http_proxy environment fields, should be able to handle requests behind proxy servers.

---

### Post by boehr on 2009-02-21
Script and instructions worked great! Thanks.

---

### Post by Derspankster on 2009-02-23
Thank you! Worked.  Nice job!

---

### Post by kneewax on 2009-02-26
Thank yoU!  I have been trting to work out to fix my ppa keys issues for ages, with so many repos to update, your script really reall helped.

Thanks.

---

### Post by Julian David Pitt on 2009-02-27
Thanks a lot Forger, worked a treat many thanks again.

---

### Post by ukblacknight on 2009-02-28
Thanks for this! Works like a charm

I think the process of adding repo's and keys is a bit of a complicated process if you don't know what is going on. Isn't there a way we could have a 'one-click-add' like you can with apt:// links to install software?

---

### Post by ultrageeky on 2009-02-28
Will this work in Kubuntu or is it specific to Gnome?

---

### Post by forger on 2009-02-28
> 
I think the process of adding repo's and keys is a bit of a complicated process if you don't know what is going on. Isn't there a way we could have a 'one-click-add' like you can with apt:// links to install software?
Support solution #5 at:
[http://brainstorm.ubuntu.com/idea/17692/](http://brainstorm.ubuntu.com/idea/17692/)

> 
Will this work in Kubuntu or is it specific to Gnome?
ultrageeky, it's run through the terminal/konsole and it's a perl script.
I think it will run fine on any debian-based/ubuntu operating system that uses ubuntu ppa archives (and of course, the packages required). :)

---

### Post by ukblacknight on 2009-02-28
> **forger said:**
> Support solution #5 at:
[http://brainstorm.ubuntu.com/idea/17692/](http://brainstorm.ubuntu.com/idea/17692/)


Done :)

In envisage it as that a software website, such as say Banshee for example, would have a button on its website.  This button would automatically add the ppa to the software sources and the GPG key.  All that would be needed is for the user to enter their password.

---

### Post by forger on 2009-03-02
Great, let's hope that someone will realise it. :)

---

### Post by kitajoy on 2009-03-02
Worked Great!!! Thanks!:popcorn:

---

### Post by Lews on 2009-03-06
I tried it but it gives me this error:

> 
Release: intrepid
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory


What can i do?

---

### Post by forger on 2009-03-06
are you sure it's this script? I don't use cat :)
you're using blackgr's script probably.

Try mine at the top of this topic:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by cooltd825 on 2009-03-15
genius.  thanks!

---

### Post by AlexenderReez on 2009-03-21
i got this error when i want to install...please help :(

```
[ reez @ alexendeRReez : /home/reez/Desktop ] perl '/home/reez/Desktop/launchpad-ppa-fix.pl' 
Can't locate IO/Socket/SSL.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/reez/Desktop/launchpad-ppa-fix.pl line 43.
BEGIN failed--compilation aborted at /home/reez/Desktop/launchpad-ppa-fix.pl line 43.

```

what is exact package i need to install?

---

### Post by forger on 2009-03-23
read the first thread post please:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by KhaaL on 2009-03-30
you saved me a lot of hassle man, great job!

one question though, is it possible to back these gpg keys up? where are they stored in that case?

---

### Post by forger on 2009-03-31
```

gpg --list-keys "Launchpad PPA"
gpg --list-keys "Launchpad PPA" | tr -s ' ' | grep ^pub | cut -d' ' -f 2

``` :)

---

### Post by har02052 on 2009-04-03
Would it be possible to have the script scan all sources and then the ones that don't have keys ask the user if they know the location of the key?  I have a couple of sources (non-launchpad) that don't have a key added yet but I know the location of the key and I could just copy and paste it into the terminal if it asked me.

---

### Post by forger on 2009-04-03
That goes beyond the purpose of the script :)

But you can use something like:
```

list="B5140445 62E44DBB"
for i in $list; do sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com $i; done
```

It will insert keys B5140445 and 62E44DBB directly into apt-key. :)

---

### Post by qhaz on 2009-04-07
Thanks for fix!

---

### Post by en23 on 2009-04-08
Great. I allways had these two or three missing keys. Thanks.
I had an error first (some problems with libio-socket-ssl-perl). I think something like libnet-ssleay-perl was missing.

---

### Post by forger on 2009-04-08
You didn't read the first page then :)
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by Crowchild on 2009-04-08
I am still having issues. I have checked and I do have the right permissions for /home/adam/.gnupg/gpg.conf. I don't know why it's telling me that I don't.

> adam@adam-laptop:~$ perl launchpad-ppa-fix.pl
Found apt source list files:
  /etc/apt/sources.list.d/medibuntu.list
  /etc/apt/sources.list

Checking file /etc/apt/sources.list.d/medibuntu.list
No change for /etc/apt/sources.list.d/medibuntu.list

Checking file /etc/apt/sources.list
Detected/Fixed: deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main
Detected/Fixed: deb [http://ppa.launchpad.net/jef-norbit/ppa/ubuntu](http://ppa.launchpad.net/jef-norbit/ppa/ubuntu) intrepid main
Detected/Fixed: deb [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) intrepid main
Detected/Fixed: deb-src [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) intrepid main
Detected differences between /tmp/lp_change.list and /etc/apt/sources.list
Moving temporary file as /etc/apt/sources.list
INFO: Enter your administrator password if asked


Will retrieve keys for: openoffice-pkgs jef-norbit psyke83
Attempting to get Launchpad key for openoffice-pkgs: [http://launchpad.net/~openoffice-pkgs/+archive/ppa](http://launchpad.net/~openoffice-pkgs/+archive/ppa)
Found key: 247D1CFF
Adding 247D1CFF to your username's gpg
gpg: WARNING: unsafe permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
system gpg --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF failed: 512
Adding key to apt
INFO: Enter your administrator password if asked

gpg: WARNING: unsafe permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: nothing exported
[sudo] password for adam: 
gpg: no valid OpenPGP data found.

Attempting to get Launchpad key for jef-norbit: [http://launchpad.net/~jef-norbit/+archive/ppa](http://launchpad.net/~jef-norbit/+archive/ppa)
Found key: 389C663C
Adding 389C663C to your username's gpg
gpg: WARNING: unsafe permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
system gpg --keyserver keyserver.ubuntu.com --recv-keys 389C663C failed: 512
Adding key to apt
INFO: Enter your administrator password if asked

gpg: WARNING: unsafe permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

Attempting to get Launchpad key for psyke83: [http://launchpad.net/~psyke83/+archive/ppa](http://launchpad.net/~psyke83/+archive/ppa)
Found key: 16AE4E77
Adding 16AE4E77 to your username's gpg
gpg: WARNING: unsafe permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
system gpg --keyserver keyserver.ubuntu.com --recv-keys 16AE4E77 failed: 512
Adding key to apt
INFO: Enter your administrator password if asked

gpg: WARNING: unsafe permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/adam/.gnupg/gpg.conf'
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.


All done.

---

### Post by forger on 2009-04-10
That means that your file owner has changed:
```
sudo ls -l /home/adam/.gnupg/gpg.conf
```
I'd just do:
```
sudo chown -R $USER:$USER /home/adam/.gnupg/
```

Then log out and log back in

---

### Post by forger on 2009-04-11
New version, 1.5:
* Added support when 2+ PPAs exist from the same user/team.

---

### Post by N_Nick on 2009-04-11
Worked like a charm, thank you very much :)

---

### Post by Zoot7 on 2009-04-11
I'm getting an error that it can't connect behind the proxy I'm sitting behind. Here's what I get:

```
mark@mark-laptop:~/Downloads/key_update$ perl launchpad-ppa-fix.pl
Found apt source list files:
  /etc/apt/sources.list.d/hardy-partner.list
  /etc/apt/sources.list.d/medibuntu.list
  /etc/apt/sources.list

Checking file /etc/apt/sources.list.d/hardy-partner.list
No change for /etc/apt/sources.list.d/hardy-partner.list

Checking file /etc/apt/sources.list.d/medibuntu.list
No change for /etc/apt/sources.list.d/medibuntu.list

Checking file /etc/apt/sources.list
openoffice-pkgs/ppa
Detected/Correct: deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
openoffice-pkgs/+archive/ppa
awn-testing/ppa
Detected/Correct: deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu hardy main
awn-testing/+archive/ppa
awn-testing/ppa
Detected/Correct: deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu hardy main
awn-testing/+archive/ppa
project-neon/ppa
Detected/Correct: deb http://ppa.launchpad.net/project-neon/ppa/ubuntu hardy main
project-neon/+archive/ppa
openoffice-pkgs/ppa
Detected/Correct: deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
openoffice-pkgs/+archive/ppa
openoffice-pkgs/ppa
Detected/Correct: deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
openoffice-pkgs/+archive/ppa
No change for /etc/apt/sources.list

Detected http proxy: http://10.51.255.250	:8080/
Will retrieve keys for: openoffice-pkgs/+archive/ppa awn-testing/+archive/ppa project-neon/+archive/ppa
Attempting to get Launchpad key for openoffice-pkgs/+archive/ppa: http://launchpad.net/~openoffice-pkgs/+archive/ppa
ERROR: 500 Can't connect to launchpad.net:443 (connect: Network is unreachable)
Attempting to get Launchpad key for awn-testing/+archive/ppa: http://launchpad.net/~awn-testing/+archive/ppa
ERROR: 500 Can't connect to launchpad.net:443 (connect: Network is unreachable)
Attempting to get Launchpad key for project-neon/+archive/ppa: http://launchpad.net/~project-neon/+archive/ppa
ERROR: 500 Can't connect to launchpad.net:443 (connect: Network is unreachable)
3 errors detected while checking the Launchpad site.
Are you behind a proxy? Read these links:
    - http://www.gnu.org/software/wget/manual/html_node/Proxies.html
    - http://web.archive.org/www.fedoraforum.org/forum/printthread.php?t=742

All done.
```

Any Ideas?

---

### Post by forger on 2009-04-11
hm..
```
Detected http proxy: http://10.51.255.250	:8080/
```

you have one tab character between your proxy and its port, try without it:
```
http_proxy="http://10.51.255.250:8080/" perl launchpad-ppa-fix.pl
```

---

### Post by Zoot7 on 2009-04-11
Thanks for replying. I'm getting the same problem again though:
```
Detected http proxy: http://10.51.255.250:8080/
Will retrieve keys for: openoffice-pkgs/+archive/ppa awn-testing/+archive/ppa project-neon/+archive/ppa
Attempting to get Launchpad key for openoffice-pkgs/+archive/ppa: http://launchpad.net/~openoffice-pkgs/+archive/ppa
ERROR: 500 Can't connect to launchpad.net:443 (connect: Network is unreachable)
Attempting to get Launchpad key for awn-testing/+archive/ppa: http://launchpad.net/~awn-testing/+archive/ppa
ERROR: 500 Can't connect to launchpad.net:443 (connect: Network is unreachable)
Attempting to get Launchpad key for project-neon/+archive/ppa: http://launchpad.net/~project-neon/+archive/ppa
ERROR: 500 Can't connect to launchpad.net:443 (connect: Network is unreachable)
3 errors detected while checking the Launchpad site.
Are you behind a proxy? Read these links:
    - http://www.gnu.org/software/wget/manual/html_node/Proxies.html
    - http://web.archive.org/www.fedoraforum.org/forum/printthread.php?t=742

All done.
```

---

### Post by forger on 2009-04-11
Try these:
```

http_proxy="http://10.51.255.250:8080/" ping -c 5 www.google.com
http_proxy="http://10.51.255.250:8080/" wget www.google.com -O /tmp/testgoogle
http_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad
https_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad2

```

If none works, then I don't know, probably something is wrong with your proxy setup?
If launchpad is the only one that fails, it could be the fact that it uses https ? Just guessing though. :)

---

### Post by Zoot7 on 2009-04-12
Here's what I get for typing those into the terminal:

```
mark@mark-laptop:~$ http_proxy="http://10.51.255.250:8080/" ping -c 5 www.google.com
connect: Network is unreachable
```

```
mark@mark-laptop:~$ http_proxy="http://10.51.255.250:8080/" wget www.google.com -O /tmp/testgoogle
--11:19:12--  http://www.google.com/
           => `/tmp/testgoogle'
Connecting to 10.51.255.250:8080... connected.
Proxy request sent, awaiting response... 302 Moved Temporarily
Location: http://www.google.ie/ [following]
--11:19:17--  http://www.google.ie/
           => `/tmp/testgoogle'
Connecting to 10.51.255.250:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 5,393         --.--K/s             

11:19:24 (2.41 MB/s) - `/tmp/testgoogle' saved [5393]
```

```
mark@mark-laptop:~$ http_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad
--11:20:13--  https://launchpad.net/~project-neon/+archive/ppa
           => `/tmp/testlaunchpad'
Resolving launchpad.net... 91.189.90.211
Connecting to launchpad.net|91.189.90.211|:443... failed: Network is unreachable.
```

```
mark@mark-laptop:~$ https_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad2
--11:20:58--  https://launchpad.net/~project-neon/+archive/ppa
           => `/tmp/testlaunchpad2'
Connecting to 10.51.255.250:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: 49,813 (49K) [text/html]

100%[====================================>] 49,813       134.90K/s             

11:20:58 (134.75 KB/s) - `/tmp/testlaunchpad2' saved [49813/49813]
```

Strange, considering running apt-get update has always been fine, but yet I get "network is unreachable" with some of those commands.
Anyway, thanks for you're help forger, and I'll ask around. And thanks for that script too. :)

---

### Post by forger on 2009-04-12
Final shot:
```
https_proxy="http://10.51.255.250:8080/" http_proxy="http://10.51.255.250:8080/" perl launchpad-ppa-fix.pl
```
Sorry if I can't be of any more assistance, I don't use a proxy unfortunately :)

---

### Post by Zoot7 on 2009-04-13
Hmmm... I still get this:

```
Detected http proxy: http://10.51.255.250:8080/
Will retrieve keys for: openoffice-pkgs/+archive/ppa awn-testing/+archive/ppa project-neon/+archive/ppa
Attempting to get Launchpad key for openoffice-pkgs/+archive/ppa: http://launchpad.net/~openoffice-pkgs/+archive/ppa
ERROR: 501 Not Implemented
Attempting to get Launchpad key for awn-testing/+archive/ppa: http://launchpad.net/~awn-testing/+archive/ppa
ERROR: 501 Not Implemented
Attempting to get Launchpad key for project-neon/+archive/ppa: http://launchpad.net/~project-neon/+archive/ppa
ERROR: 501 Not Implemented
3 errors detected while checking the Launchpad site.
Are you behind a proxy? Read these links:
    - http://www.gnu.org/software/wget/manual/html_node/Proxies.html
    - http://web.archive.org/www.fedoraforum.org/forum/printthread.php?t=742

All done.

```

No worries anyway, I fixed the outdated keys using these for both of them:
```
gpg --keyserver subkeys.pgp.net --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add
```

[QUOTE=forger]I don't use a proxy unfortunately :)[/QUOTE]
Sometimes I wish I didn't too, but in this backwards country (as regards telecommunications in general :rolleyes: ) considering my connection is 20Mb upload and download having to contend with a proxy is a small price to pay. :)

---

### Post by Siggma on 2009-04-29
Perfect, Thank you. I love it when people take the time to write airtight scripts!

:)

---

### Post by jfg69 on 2009-04-30
Worked perfectly for me. Thank you!

---

### Post by ubuntubrian on 2009-05-06
Fixed my PPA woes! Thanks
:guitar:

---

### Post by Mushed on 2009-05-16
I still get this error:

W: GPG error: [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I've tried to do this:

```
gpg --keyserver keyserver.ubuntu.com --recv BADSIG 40976EAF437D05B5
```

This seemed to work fine it skipped BADSIG and spat out:

```
gpg: "BADSIG" not a key ID: skipping
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
```

so then I tried:

 ```
gpg --export --armor 437D05B5 | sudo apt-key add
```

but then it only gives me:

 ```
can't open `': No such file or directory
```

can anyone help me, please?? 
I really don't know what I'm doing here I'm just trying things that found through googleing ([http://ubuntuforums.org/archive/index.php/t-1054906.html](http://ubuntuforums.org/archive/index.php/t-1054906.html)) 

Thanks in advance!

---

### Post by forger on 2009-05-16
> **Mushed said:**
> I still get this error:

W: GPG error: [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


Mushed: You should make a new topic about it. This script is not for the purpose you want it. :)

A suggestion would be to go from menu System > Administration > Software sources > Download from: "Main server"
Click "Close" and "Reload".

---

### Post by steve_steve on 2009-05-19
Many thanks, Foger.  Yes, it probably would've been better if I'd read the tutorial & figured it all out  But it's late.  I'm tired.  But now I'm tired and grateful.

---

### Post by TheExplorer on 2009-05-19
Sorry if I misunderstood anything. I'm comparatively new to all this. Does it affect Ubuntu Swat [**x-updates**]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")  from the PPA? Well, you know what I mean.
Thank you in advance.

---

### Post by forger on 2009-05-19
TheExplorer, what do you mean? You can use it for that PPA.

It works here as far as I can see:
```

Attempting to get Launchpad key for ubuntu-x-swat/+archive/x-updates: http://launchpad.net/~ubuntu-x-swat/+archive/x-updates
Found key: AF1CDFA9
Adding AF1CDFA9 to your username's gpg
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Adding key to apt
INFO: Enter your administrator password if asked

OK
```

---

### Post by TheExplorer on 2009-05-22
OK, thank you. Just checked :)

---

### Post by forger on 2009-06-25
Version 1.6 :KS
 * Added support for new format in edge.launchpad.net server.
 * No longer adding $key to your username's gpg (using apt-key adv)

---

### Post by davim on 2009-07-02
this script should be integrated into ubuntu-tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by forger on 2009-07-02
> **davim said:**
> this script should be integrated into ubuntu-tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Tweak is written in python, maybe someone would want to rewrite the whole thing in python. ;)

---

### Post by davim on 2009-07-06
Or just call your script from tweak :P

os.system(launchpad-ppa-fix.pl)

---

### Post by rasmith3530 on 2009-07-06
I just came across this post while searching for a way to correct an error I receive when updating my system. You Perl script worked like a charm Forger, thank you very much!

):P

---

### Post by pitirolo on 2009-08-21
Thank a lot. my sources.list is working again !!! :-)))

---

### Post by Syntax. on 2009-09-01
Thanks!

---

### Post by scholzilla on 2009-10-04
didn't work for me, unfortunately. All seemed to go smoothly, but apt-get update still gives me:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems

---

### Post by rospo84 on 2009-10-09
> **scholzilla said:**
> didn't work for me, unfortunately. All seemed to go smoothly, but apt-get update still gives me:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems

it's the same for me....

```
W: Errore GPG: http://ppa.launchpad.net jaunty Release: Le seguenti firme non sono state verificate perché la chiave pubblica non è disponibile: NO_PUBKEY 2ABD4DE1E855A72E
W: Errore GPG: http://ppa.launchpad.net jaunty Release: Le seguenti firme non sono state verificate perché la chiave pubblica non è disponibile: NO_PUBKEY EF50D13CAA832887
W: Errore GPG: http://ppa.launchpad.net jaunty Release: Le seguenti firme non sono state verificate perché la chiave pubblica non è disponibile: NO_PUBKEY D739676F7613768D
W: Errore GPG: http://ppa.launchpad.net jaunty Release: Le seguenti firme non sono state verificate perché la chiave pubblica non è disponibile: NO_PUBKEY 2E183FA1E260F5B0

```

---

### Post by roffik on 2010-01-11
@[#43]("http://ubuntuforums.org/showpost.php?p=7288470&postcount=43"):
You're missing ```
" -"
``` (without quotes) after ```
"sudo apt-key add"
```

---

### Post by SaintDanBert on 2010-03-18
I continue to get apt-get authentication errors during
```

user@host:path$ sudo apt-get update
...
Get...
Hit...
...
Fetched 86.2kB in 1s (51.9kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
W: You may want to run apt-get update to correct these problems


```

I have not idea which package is the offender or how to discover which package has a missing key.

Cannot see what is likely obvious to those who know,
~~~ 0;-Dan

---

### Post by forger on 2010-03-27
Does anyone use this script? :popcorn:
I mean... with "sudo add-apt-repository" in ubuntu 9.10+ I think I'll dub this script obsolete soon. :)

---

### Post by SaintDanBert on 2010-03-30
> **forger said:**
> Does anyone use this script? :popcorn:
I mean... with "sudo add-apt-repository" in ubuntu 9.10+ I think I'll dub this script obsolete soon. :)

That presumes that most folks deploy the update...

I cannot go v9.10 or later because too many changes torpedo my "tablet-pc" workings in various ways. I continue to get a complaint
about a missing launchpad key [see elsewhere in this thread] without
any resolution. It seems I'm cursed to have dents and scratches, rumbles
and rattles in an otherwise useful Ubuntu deployment.

~~~ 8d;-/ Dan

---

### Post by wesleybishop on 2010-06-10
THANKS!!! YOU :guitar:!!!

---

### Post by afrodeity on 2010-07-18
I'm looking for a script which will check ppa address and keys and _resolve the correct distribution available for your installation irrespective of which distribution is installed._ 

For example: some ppas are only available as Karmic but you on Lucid. There is no real difference iin architecture if its just game etc.

The official ubuntu upgrade utility changes all ppas to LUCID for eg, without bothering to check if they ppa has Lucid.

---

### Post by dino99 on 2010-07-18
never had issue when adding ppa path to synaptic repo tab (copy/paste from ppa url)

---

### Post by AHOHA on 2010-09-01
hi   **forger**

i got a strange error after apply script 

```

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

```

how to fix it 

thanx

---

