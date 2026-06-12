---
title: "Mysql 5"
date: 2005-10-23
forum: Deferred/Invalid Requests
---

### Post by jqshenker on 2005-10-23
(I posted this in another forum a couple days ago... I didn't realize it was in the wrong place. Nor did I see it posted anywhere else.)

Many developers (including myself) are developing on Mysql 5, and a package would be much appreciated. 5.0.13rc is stable enough that some people are using in it *production* (let alone development), and an officially stable release is coming in November. Ubuntu is great as a no-muss-no-fuss developers' distro, but some updated packages might make it even better.

Thanks,
Jacob

---

### Post by KLineD on 2005-10-24
I second that. I was waiting for mysql 5 to become final and now it has. A deb package of this would be great.

---

### Post by traherom on 2005-10-24
I third it. I don't want to use the generic or alien on an RPM because the server is too important... can't wait for a deb.

---

### Post by jqshenker on 2005-10-25
Ok, the real deal is out. We need a package asap people!

---

### Post by dudus on 2005-10-25
mysql 5.0.15 is out and I'm waiting here. This one has to go into the repos soon.

---

### Post by jqshenker on 2005-10-26
Yeah. Soon as in RIGHT NOW! ;)

---

### Post by KLineD on 2005-10-26
I'm amazed as how so few people is requesting this...
:???:

---

### Post by ember on 2005-10-26
Well, if you like stored procedures, triggers and so on, you could as well use Postgres, which is available in the repositories. No need to rush MySQL 5 in.

---

### Post by Velvet Elvis on 2005-10-26
If you read the ubuntu-devel mailing list archive at lists.ubuntu.org you will see the mantra repeated over and over "enterprise users want stability above all else."

Since Dapper is to be the "enterprise ready" release that will be supported for five years, I seriously doubt there will ever be a Mysql 5 in Dapper to backport.

It will have to be in extras, if anywhere.  It would doubtlessly break enough dependencies that it's unlikely to show up for a while though.  I'd be surprised to see it until after Dapper is out.

---

### Post by jqshenker on 2005-10-26
Stable != enterprise-ready != ancient

Mysql 5 has been ready and has been used in production for a while now. On Monday they just announced it as stable. Mysql 5 brings it much closer to Postgres and commercial databases in terms of nested queries, clustering, stored procedures (yuck), etc...; features which are very important to enterprise users.

How about... *providing* mysql 5 and those who want it can have it, those who don't can use another version. The mysql 5 *client* is backwards-compatible, so everything compiled against it would work on any mysql version. Also, the 4.1 client often works with 5.0 anyway (in my experience, at least).

I'm actually a postgres guy, but I need to use Mysql 5 for a project that demands it. 

I'm also suprised that so few are responding. Oh well.

---

### Post by ember on 2005-10-26
I guess it will be in dapper - but it is unlikely to be the default database. Yet I guess it will take some time for it to be backported - let's face it, there are actually not very many people that do need MySQL 5.

---

### Post by C38a7r1zvl on 2005-10-26
Well, I need it, so I compile it myself. Been using it for months now. A ready to go Ubuntu package would be handy though, no doubt about it.

---

### Post by jqshenker on 2005-10-27
Yeah. I've never had any experience with the Debian packaging system, being a Gentoo/FreeBSD guy. Can anyone who is skilled with package creation whip us up a package, pretty pretty please? I'll compile it from scratch, sure... but packages are *a lot* nicer to deal with especially because Mysql 5 is going to have frequent bugfix updates because it's so new.

---

### Post by jqshenker on 2005-10-27
Actually, I just got Mysql 5 installed from .debs and it's working like a champ! I'd still love a package and I think it'd be an important improvement to Dapper--but for now the alternative isn't bad at all.

---

### Post by C38a7r1zvl on 2005-10-27
A few months ago I wrote a little PHP script to ease updates for me. Usage is as follows: "./mysql.php version [all|get|compile|build]". It fetches the specified version from a given mirror, unpacks, configures and compiles it and creates a debian package. 

Originally I didn't intend to make this script public so it is pretty much designed for my own needs (e.g. the install path is /usr/local/mysql while data is stored in /var/mysql, which might not be everybody's desire) however it can be easily customized or at least be a starting point for the creation of your own packages.

---

### Post by KLineD on 2005-10-28
[QUOTE=dePOLL]A few months ago I wrote a little PHP script to ease updates for me. Usage is as follows: "./mysql.php version [all|get|compile|build]". It fetches the specified version from a given mirror, unpacks, configures and compiles it and creates a debian package. 

Originally I didn't intend to make this script public so it is pretty much designed for my own needs (e.g. the install path is /usr/local/mysql while data is stored in /var/mysql, which might not be everybody's desire) however it can be easily customized or at least be a starting point for the creation of your own packages.[/QUOTE]

Ok I'll try this when I get home, I'm anxious... :smile:

---

### Post by smeg4brains on 2005-10-31
OK, I'll be one of the much missed "more people" requesting this add.

I too would like to switch to devoloping with mysql5, and I don't really want to do with compiling it up myself. Package management is the way to go!

I've been using mysql for years, and I've nevers seen any real stability problems even using their alpha release products. I trust mysql enough that I'm going to move our production systems to using mysql 5 immediately now that they've stated that their release is stable.

-Jeff

---

### Post by Lapeth on 2005-11-01
#17: I completely agree.
Not only would I like to get the new version of MySQL up & running, but I also need some of the new features for my university database project, so I hope it won't be too long. Otherwise I'll need to compile it myself, but I tend to prefer the pre-built packages whenever they're available.

---

### Post by horus on 2005-11-01
Add me to the list. I'm currently building a new server; we're planning to put MySQL 5 on it, as we need views, and I was hoping (hah!) for once to install everything not ColdFusion or written by us as packages.

Looks like MySQL will be going on from source again.

---

### Post by Pr0phet on 2005-11-01
I'll chime in on this one.  There's a good many businesses who are already cycling to MySQL 5 for R&D and future production development.  Of the clients that I have, all of them are taking a long, hard look at MySQL 5.  Having something is better than nothing, particularly when you can default a dummy "mysql" package to MySQL 4.1, and give the option for 5 should the user specifically choose that series of packages.

I've not read anywhere that you can connect a MySQL 4 client lib to a 5 server (I know I can't do it), so I would consider it in the best interest of a future release (and a backport, hopefully) to maintain with the more cutting edge of professional and personal users.

---

### Post by Txukie on 2005-11-03
It will be nice to have it as a possibility

---

### Post by iluminate on 2005-11-06
Hi,

Is there a guide somewhere how to install it from the deb-package?
Also do I need to uninstall the previous MysqlServer installation ? v.4.0.24 before 
I install Mysql5 ?

---

### Post by akurashy on 2005-11-06
Umm, after installing mysql 5, this is something i thought, well woudln't it need a apache2-lib to work in apache?

---

### Post by iluminate on 2005-11-06
[QUOTE=akurashy]Umm, after installing mysql 5, this is something i thought, well woudln't it need a apache2-lib to work in apache?[/QUOTE]
How did you manage to install Mysql5?
Have tried numerous of times but without sucess.
Any help or guide would be very much appreicated.

Cheers

---

### Post by akurashy on 2005-11-07
[quote=iluminate]How did you manage to install Mysql5?
Have tried numerous of times but without sucess.
Any help or guide would be very much appreicated.

Cheers[/quote]

oh i haven't i must he said something wrong :(. well im going to compile it tommorrow to check *or try to*

---

### Post by iluminate on 2005-11-07
Is someone getting the same error message as I do?
I have followed the install instructions found here - [http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html](http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html)
But when I type in "scripts/mysql_install_db --user=mysql" I recieve an error saying "
Could not find help file 'fill_help_tables.sql' in ./support-files or inside /usr."

Do I have to set the correct PATH to /usr/local/mysql/bin/ ? or
any help would be much appreciated.

Cheers

---

### Post by jdong on 2005-11-09
Because of the cloud of potential security backporting work around MySQL not to mention its enterprise platform stability issues...

In short, MySQL is not a good backports candidate.

---

### Post by pecanov on 2005-11-13
[QUOTE=jdong]Because of the cloud of potential security backporting work around MySQL not to mention its enterprise platform stability issues...

In short, MySQL is not a good backports candidate.[/QUOTE]

That's just pure nonsense.
Most of the software distributors still ignore ubuntu in their packaging. And the chances are it is going to stay that way.
So we depend on installing from source or doing a "roulette" with static binaries. Backports should come in handy here.

**Especially with MySQL.**
"Somehow" Ubuntu developers made the perfectly satisfying 4.1.12 a 4.1.12-ubuntu3 version - a nightmare for any java developer (see the issue on prepared statements: they don't work!).

---

### Post by jdong on 2005-11-13
I simply do not have the resources to keep up with MySQL patches and security fixes at the source code level, nor does the Backports project have the authority to modify Dapper sources in that fashion. The maintainership burden gets placed on the Backports project in that case, and the security of the distribution is potentially compromised.

While providing one person a MySQL upgrade to 5 helps you out, it harms many others who do not wish to get a new MySQL. 

If you really want it, may I suggest building yourself a backport using ubp-build.py or apt-source?

---

### Post by pecanov on 2005-11-13
That was my point exactly.
If the metter was to solve a problem that is relevant only to me, I would find a way to solve it. I still have a spare machine with Mandrake :)
However, many look up to backport as an alternative way to incriase their systems capatibility.

For example: We have an Ubuntu hoary installed on a clients server. It has a small but annoying issue with mysql (again) 4.0.20. Actions that this client would approve involve only clean upgrades of the system, which is logical since they less time, are supposed to be more reliable, and provide them with a sense of security. 
However, the only choice I have is to upgrade to badger and have them use 4.1.12-ubuntu3 which renders the point of further upgrading inept since it's uncompatible with future flows of development of mysql related technology (the server, jdbc drivers, etc).
Another example is that the current software that we are developing, althought not strictly bound to any database (or database at all), makes Ubuntu breezy a veery unrecommended choice for installing it since the environment would easilly be ratted as "hostile" by the system evaluators (outdated java, problematic mysql etc). I keep mentioning mysql since, in my experience, it is the choice of many companies for this kind of software that relly on the open source software branch.
I guess all I want to say is that it wouldn't hurt anyone to have a more choices. Not many, but definatelly more. And backports might be the only thing to look up to, at the moment being.

---

### Post by C38a7r1zvl on 2005-11-13
Why not create mysql-server-5.0? People wouldn't be "forced" to upgrade to it as there wouldn't be any automatic updates when invoking apt-get upgrade. The "potentially buggy" argument is really a pureley theoretical one as there were tons of alpha, beta, gamma and rc releases before marking it as production stable.

---

### Post by jdong on 2005-11-13
Well, I don't have slotted packages for MySQL 5, nor do I have the capacity to make it according to Debian standards.

---

### Post by C38a7r1zvl on 2005-11-13
Sorry, forgot we were in the backports forums. Was meant as a suggestion for dapper so that afterwards you can backport ;)

---

### Post by jdong on 2005-11-13
hehe, oops :)

May I suggest using the mailing lists or IRC channels, or even e-mailing the maintainer of the current MySQL package. Your chances of reaching masses of developers over here is pretty slim :-/

---

### Post by C38a7r1zvl on 2005-11-13
Will do that. And while I'm at it, rant about the lack of php5-mysqli, php5-mcrypt & co :)

btw: Thanks for your work regarding the backports. I'm happy you got eventually endorsed by the Ubuntu developers.

---

### Post by jdong on 2005-11-13
Thanks, and good luck!

---

### Post by pecanov on 2005-11-13
[QUOTE=dePOLL]Why not create mysql-server-5.0? People wouldn't be "forced" to upgrade to it as there wouldn't be any automatic updates when invoking apt-get upgrade. The "potentially buggy" argument is really a pureley theoretical one as there were tons of alpha, beta, gamma and rc releases before marking it as production stable.[/QUOTE]

There's noting theoretical about bugs in the breezy included mysql. It's real and present.

---

### Post by jdong on 2005-11-13
MySQL is in **main**, an officially supported package. Any bugs/issues with it should be brought to Ubuntu developers, not me.

---

### Post by pecanov on 2005-11-14
It's obviously to late for that.

---

### Post by jdong on 2005-11-14
No, it's not too late to get MySQL problems fixed... that's what **breezy-updates** is for :)

---

### Post by agalligani on 2005-11-16
I second/third . . .  tenth the motion for MySQL 5 in breezy. It's hard to get developers to use Mysql 4 when you can't create a view in it. 

They want to keep using MSSQL!

Noooooooooooooo!!!!!!!!!!! #-o 

MS = :evil: 

Incidentally, why are MySQL 5 commands (see CREATE USER) in the \h utility if you can't load MySQL 5??!?! . . .  confusing.

Otherwise - Breezy kicks ass!!!!

---

### Post by dudus on 2005-11-17
Even with Mysql AB telling us that mysql5 is the stable and recomended verssion the masters of universse seems relutant in adopting it. In fact the verssion 4.1 is optional as the 4.0 is the recomended for ubuntu!!!!

Nota that mysql 4.0 is listed as obsolet by mysql ab

The only way to get it working is either compiling it yourself or trying not official deb packages as the ones in  [http://packages.dotdeb.org]("http://packages.dotdeb.org").

---

### Post by dudus on 2005-11-22
Ok I compilled mysql5 and that was a pain in the a** since I'm not a very compilling boy. But i did it and it was fine.

But then I noticied that php5 in ubuntu doesn't support mysqli. So I had to compila php5 either and uninstall the repo version.

Since I had compiled both and I was becoming a compiling boy I compilled apache2 either 'cause the ubuntu one act weird processing php files... maybe I couldn't get it rigth. 

Since the verssion of Mysql Administrator and Query Browser are are very old in the repos I compilled them too... :razz: 

So after compilling all of the I'm very happy with the results, and I'll probably compile more things from now one.

I'll be here if you need help compilling them. And maybe write a HOW TO or something like these just to keep track of the tricky parts.

Sorry for the bad english

---

### Post by Robgould on 2005-11-22
dudus,

I don't know how to compile, but I want MySql 5.0 so I guess I will learn.  What do I need to do?

---

### Post by dudus on 2005-11-22
[QUOTE=Robgould]dudus,

I don't know how to compile, but I want MySql 5.0 so I guess I will learn.  What do I need to do?[/QUOTE]

I posted a 'how to compile mysql5' in ubuntu forums today. Try this. And let me know if something goes wrong.

[http://ubuntuforums.org/showthread.php?t=93725](http://ubuntuforums.org/showthread.php?t=93725)

---

### Post by ZylGadis on 2005-12-06
I am also one of the people who would like a package for mysql5.

---

### Post by JLTB on 2006-01-13
And your wish is granted!

```

elected package libmysqlclient15.
(Reading database ... 92071 files and directories currently installed.)
Unpacking libmysqlclient15 (from .../libmysqlclient15_5.0.18-4_i386.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.50-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0002-2_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.18-4_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.18-4_i386.deb) ...

```

A snap shot of what apt is writing to my terminal right now!

(on my Dapper box with all universe, multiverse, etc.. repos accessible)

---

### Post by PlatinumPlus on 2006-01-13
Can I update it on BreezyB? I need MySQL5 latest too :cool:

---

### Post by ikarus9999 on 2006-01-26
I've upgraded today from the dapper repo and it worked like a charm.
I had to upgrade gcc and a few other libraries but sofar no problem.

---

### Post by rcpettit on 2006-01-28
I found a mysql 5.0 deb at this site.  Worked right off the bat.

[http://www.linuxcompatible.org/PHP_5.1.2_MySQL_5.0.18_for_Debian_s61988.html]("http://www.linuxcompatible.org/PHP_5.1.2_MySQL_5.0.18_for_Debian_s61988.html")

you do need to edit /etc/mysql/my.cnf and comment out skip-network and then restart mysql.

;)

---

### Post by delirii on 2006-03-16
[QUOTE=dudus]
I'll be here if you need help compilling them. And maybe write a HOW TO or something like these just to keep track of the tricky parts.
[/QUOTE]

It could be useful to provide instructions about the compilation of the 3.
I also have a problem with mysqli and will need to compile php5... Any help will be appreciated, like your experience ! :-)

---

### Post by dudus on 2006-03-16
[QUOTE=delirii]It could be useful to provide instructions about the compilation of the 3.
I also have a problem with mysqli and will need to compile php5... Any help will be appreciated, like your experience ! :-)[/QUOTE]

As the repos don't contain mysql5 it's mandatory to compile.:( 

Php5 is in the repos but it doesn't have support for mysqli so it's fairly useless.:( 

Apache is in the repos and is ok, but he depends on php5 wich we don't want to use the provided one.:( 

It seems that the stars don't want us to do that!:-k 

Maybe there's a more simple way, but i just compiled everything.

Apache should be easy and the web is full of tutorials on this. Just keep in mind that you need php5 support (you may want it trough mod-php5).

Php is easy as well, very documented, just try to compile all the libs you'll need with it. here's my configure options if you need an exemple 

```
'./configure' '--prefix=/usr/local/php5' \
'--with-apxs2=/usr/local/apache2/bin/apxs' \
'--with-libxml-dir=/usr/local/lib' \
'--with-zlib' '--with-zlib-dir=/usr/local/lib' \
'--with-mysqli=/usr/local/mysql/bin/mysql_config' \
'--with-mysql=/usr/local/mysql' '--with-mysql-sock=/tmp/mysql.sock' \
'--with-gd' '--enable-soap' '--enable-sockets'
```

Chances are that you'll need zlib and libxml support (you realy should compile them into php5). But this extensions don't come bundled in php5. Just download each in it's own site, compile it, and use the option above to link it.
Don't forget to add the '--with-mysqli=PATH_TO_mysqli_config' flag so you have mysqli support. There are many tutorials on web and it should be easy to get the job done.

Mysqli5 in the trickiest. Mysqli documentation on compiling is poor, there's some tutorials out there, but they're all missing something. So you're free to ask here.

Remember that this tutorial would see some improvements I never had time to test and update. But they're all discussed in this thread.:-D 

Good luck

---

### Post by AdonisV on 2006-10-25
why not use the recomended method by mysql.com? :confused: 

[http://dev.mysql.com/downloads/mysql/5.0.html](http://dev.mysql.com/downloads/mysql/5.0.html) 

find Ubuntu 6.06 LTS (Dapper Drake) downloads
where a list of files are open for downloads. 
This note from MySQL :
"We recommend Ubuntu users to get MySQL, via the apt-get tool. Simply running sudo apt-get install mysql-server will get you MySQL 5.0."

also read this article
'MySQL Launches MySQL Forge Web Site & Announces Support for Ubuntu'
ref : [http://www.mysql.com/news-and-events/press-release/release_2006_22.html](http://www.mysql.com/news-and-events/press-release/release_2006_22.html) :KS

---

### Post by dudus on 2006-10-26
> **AdonisV said:**
> why not use the recomended method by mysql.com? :confused: 

[http://dev.mysql.com/downloads/mysql/5.0.html](http://dev.mysql.com/downloads/mysql/5.0.html) 

find Ubuntu 6.06 LTS (Dapper Drake) downloads
where a list of files are open for downloads. 
This note from MySQL :
"We recommend Ubuntu users to get MySQL, via the apt-get tool. Simply running sudo apt-get install mysql-server will get you MySQL 5.0."

also read this article
'MySQL Launches MySQL Forge Web Site & Announces Support for Ubuntu'
ref : [http://www.mysql.com/news-and-events/press-release/release_2006_22.html](http://www.mysql.com/news-and-events/press-release/release_2006_22.html) :KS
This is a very old topic. more than a year, Breezy time.
At that time there were not mysql5 packages and ubuntu was not supported by mysql ab

---

