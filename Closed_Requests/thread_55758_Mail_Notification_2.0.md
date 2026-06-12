---
title: "Mail Notification 2.0"
date: 2005-08-10
forum: Closed Requests
---

### Post by dexae on 2005-08-10
Gmail support has been fixed, and Evolution support has been added. Several issues have been fixed, and the user interface has been improved.

[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

---

### Post by infinito on 2005-08-10
I've packaged mail-notification 2.0 for me, and it works great. 
You can grab it from here:
[http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb](http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb)

Some considerations:
* Gmail accounts work again.
* Consider at least 2 minutes between checks for Gmail accounts.
* Disabled SSL support (debian/ubuntu licenses issues)
* Disabled Evolution folders support (didn't want to dl evo sources)

Cheers!

---

### Post by ssck on 2005-08-10
[QUOTE=infinito]I've packaged mail-notification 2.0 for me, and it works great. 
You can grab it from here:
[http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb](http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb)

Some considerations:
* Gmail accounts work again.
* Consider at least 2 minutes between checks for Gmail accounts.
* Disabled SSL support (debian/ubuntu licenses issues)
* Disabled Evolution folders support (didn't want to dl evo sources)

Cheers![/QUOTE]

great job ... just what i need .... thanks

---

### Post by dexae on 2005-08-10
thanks now it works great  :smile:

---

### Post by rjr1049 on 2005-08-10
Thanks.  It works very well.  Great job!

Bob

---

### Post by krusbjorn on 2005-08-10
Many thanks for this!

---

### Post by bored2k on 2005-08-10
[QUOTE=infinito]I've packaged mail-notification 2.0 for me, and it works great. 
You can grab it from here:
[http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb](http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb)

Some considerations:
* Gmail accounts work again.
* Consider at least 2 minutes between checks for Gmail accounts.
* Disabled SSL support (debian/ubuntu licenses issues)
* Disabled Evolution folders support (didn't want to dl evo sources)

Cheers![/QUOTE]
 Thank you mate !

---

### Post by cstudent on 2005-08-11
Ahhhh. I'm glad to get mail-notification back. Thanks for creating the deb package. It would be nice to see backports get updated with the 2.0 version.

What exactly does the new Evolution support do? I know you disabled it in your package. I'm just curious.

---

### Post by acascianelli on 2005-08-12
The 2.0 package works perfect for me too, how about putting this in the repository :D

---

### Post by vvlist on 2005-08-12
Thanks for the .deb! \\:D/

---

### Post by manicka on 2005-08-28
I get this error message when running mail-notification-2.0

 Unable to find include file: ".gtkrc-2.0-scrollbar_cog

then it just hangs

---

### Post by basvg on 2005-09-02
[QUOTE=infinito]I've packaged mail-notification 2.0 for me, and it works great. 
You can grab it from here:
[http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb](http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb)

Some considerations:
* Gmail accounts work again.
Cheers![/QUOTE]


Hi,

I just grabbed it and tried to install it. Unfortunately it *didn't* work for me. The error I'm getting is "unable to retrieve feed: Invalid URI". Any clues on how to fix this?

  Bas

---

### Post by rawler on 2005-09-23
[QUOTE=infinito]I've packaged mail-notification 2.0 for me, and it works great. 
You can grab it from here:
[http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb](http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb)

Some considerations:
* Gmail accounts work again.
* Consider at least 2 minutes between checks for Gmail accounts.
* Disabled SSL support (debian/ubuntu licenses issues)
* Disabled Evolution folders support (didn't want to dl evo sources)

Cheers![/QUOTE]
 Hey,

Where can I find the deb-src, so I can rebuild myself WITH evo-support?

(Need Evo for the damn company Exchange-filth.)

---

### Post by keen3tix on 2005-09-28
I downloaded it with apt-get. How can I add it to the panel. It doesn't appear on the "Add to panel" menue.

---

### Post by manicka on 2005-09-28
Applications--> Internet--> 

Right Clcik on Gmail-notify and choose 'Add this launcher to panel'

Edit: ignore this, wrong package, sorry

---

### Post by Jingo on 2005-10-11
[QUOTE=infinito]I've packaged mail-notification 2.0 for me, and it works great. 
You can grab it from here:
[http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb](http://infinito.f2o.org/downloads/mail-notification_2.0-1~inf1_i386.deb)

Some considerations:
* Gmail accounts work again.
* Consider at least 2 minutes between checks for Gmail accounts.
* Disabled SSL support (debian/ubuntu licenses issues)
* Disabled Evolution folders support (didn't want to dl evo sources)

Cheers![/QUOTE]

What are the licensing problem for using SSL ?
How can I build it with SSL support ?
I won't be sending my password cleartext over the network when my pop3 server supports ssl encryption.
And these days europe discusses if law should be created for ISP's to collect and store all emails for later investigation!! At least make it hard for them we can.

---

### Post by mustang on 2005-10-11
[QUOTE=Jingo]What are the licensing problem for using SSL ?
How can I build it with SSL support ?
I won't be sending my password cleartext over the network when my pop3 server supports ssl encryption.
And these days europe discusses if law should be created for ISP's to collect and store all emails for later investigation!! At least make it hard for them we can.[/QUOTE]

I ran into the same problem. My school imap server requires SSL encryption so I just use this

[http://gnubiff.sourceforge.net/](http://gnubiff.sourceforge.net/)

hope it helps.

```
sudo apt-get install gnubiff 
```

---

### Post by ernstp on 2005-10-12
I built the debian package for breezy!
It's avaliable at here: (not online 24/7)
[http://zapp.no-ip.com/breezy/mail-notification_2.0-1_i386.deb](http://zapp.no-ip.com/breezy/mail-notification_2.0-1_i386.deb)

---

### Post by chanders on 2005-10-15
Hey thanks for the .deb file....  I am pretty sure a lot of people will be looking for this soon ;)

---

### Post by skirkpatrick on 2005-10-15
I built it with all options.  Is there any way for one of us to get it into the repositories?  Or does it require someone on the Ubuntu team to put stuff into the repos?

---

### Post by kiddo on 2005-10-15
um, could someone share their deb on a 24/7 server? :) or I could share it after downloading it, however my DSL is pretty slow this week and I would not guarantee the speed

---

### Post by skirkpatrick on 2005-10-16
Can somebody point me to where I can find out how to make it into a .deb?

---

### Post by kiddo on 2005-10-16
the only easy way I know is

./configure
make
sudo checkinstall -D make install


Take note that it does not handle dependencies :(

---

### Post by humina on 2005-10-17
bump on adding this package to the repositories.

---

### Post by idn on 2005-10-18
Yeah another bump, I think this is a really handy application, it would be good to get the latest version

---

### Post by Jingo on 2005-10-19
[QUOTE=mustang]I ran into the same problem. My school imap server requires SSL encryption so I just use this

[http://gnubiff.sourceforge.net/](http://gnubiff.sourceforge.net/)

hope it helps.

```
sudo apt-get install gnubiff 
```[/QUOTE]

Thank you. It is in the repositories and working great.

---

### Post by cwhitmore75 on 2005-10-25
Is there a way to add this to the notification area so it acts like the gmail checker?  

So far I can only get it to sit on the desktop.  I'm probably missing something.

Thanks in advance.

---

### Post by patrick295767 on 2005-10-25
Hi, 

I wished to know whether it was possible to get some sound when an email has been received with gmail-notification ??

thank you

best regards, 

Patrick

---

### Post by dcstar on 2005-11-04
[QUOTE=ernstp]I built the debian package for breezy!
It's avaliable at here: (not online 24/7)
[http://zapp.no-ip.com/breezy/mail-notification_2.0-1_i386.deb](http://zapp.no-ip.com/breezy/mail-notification_2.0-1_i386.deb)[/QUOTE]
I just tried to download this and ended up with a zero length file!

---

### Post by dcstar on 2005-11-07
[QUOTE=dcstar]I just tried to download this and ended up with a zero length file![/QUOTE]
Hurrah, now I've got it!

---

### Post by jdong on 2005-11-09
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=mail-notification](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=mail-notification)

Not in Dapper yet --- reopen request once this hits Dapper.

---

### Post by jasplund on 2005-11-10
Mail Notification 2.0 is in dapper now

---

### Post by jdong on 2005-11-10
Alright, approved :)

---

### Post by Technoviking on 2005-11-10
[QUOTE=jdong]Alright, approved :)[/QUOTE]
I have one built for backports, testing now.

Mike

---

### Post by jdong on 2005-11-10
Queued into build system.

---

### Post by gnol on 2005-11-15
Ummm, does anyone have one with evolution support???  Or am I missing something.

Do I need to build myself?   
Better yet, is there a reason it seems to have been left out?

---

### Post by infinito on 2005-11-15
[QUOTE=gnol]Ummm, does anyone have one with evolution support???  Or am I missing something.

Do I need to build myself?   
Better yet, is there a reason  seems to have been left out?[/QUOTE]
The problem with the hoary version was that the evolution-dev didn't include some files which where mandatory for evo support on mail-notification. But now, in breezy, those files are there, so i think the backported one will have evo support (if it's enabled in dapper ;)

---

### Post by gnol on 2005-11-15
Sorry, I should have mentioned I'm using Dapper and the .deb for Dapper dosen't list evo when I do 'mail-notification --list-features'  :(

---

### Post by eetu on 2005-11-23
Since Breezy has evolution 2.4.1 it would probably make more sense to have mail notification 2.0 built with the patch which makes it work with evo 2.4.X. This way users could just use their evolution mail accounts in mail notification instead of adding the same accounts there...

---

### Post by humina on 2005-11-27
I cannot seem to connect to my gmail account using the backports version of this program.  I keep getting the error:

unable to transfer data: (null)

Is there anything else I need to install for gmail support to work?

---

### Post by jdong on 2005-11-27
heh, weird... gmail works fine here.

---

### Post by cjamesjust on 2005-11-30
I'm fairly new to Ubuntu and have been able to manage most installs with apt-get and synaptic, but the deb files still mess me up.  I've downloaded the Mail Notification 2.0 to my desktop, but now am stuck.  There's reference in some of the text files to an INSTALL file, but there isn't one anywhere in the folders so I'm lost on how and where to install the deb file.  I know I have to dpkg it, but don't know where.  Is there either an INSTALL file that someone has or can someone assist by posting it?

Cheers.

---

### Post by Bou on 2005-11-30
[QUOTE=eetu]Since Breezy has evolution 2.4.1 it would probably make more sense to have mail notification 2.0 built with the patch which makes it work with evo 2.4.X. This way users could just use their evolution mail accounts in mail notification instead of adding the same accounts there...[/QUOTE]

Sorry, but how can I apply that patch to Mail Notification?

---

### Post by Yoda_Oz on 2005-11-30
id like to know how to do that too...

does evolution need to be open for mail-notification to work?

how does mail notification work anyway?

---

### Post by Artis on 2006-01-10
Any ideas how to get evolution to bring up the existing window instead of opening a new one?

---

### Post by adamkprice on 2006-01-18
I am on breezy and cant get the deb to load it keeps complaining that I need libgnome-menu0. The current version that comes with breezy is libgnome-menu2. Do I have to get 0 as well or can I get it to work with 2?

Thanks

---

### Post by uptimebox on 2006-01-24
Breezy .deb with Evolution support:

[http://rolevikov.net/debian/mail-notification_2.0-1~uptimebox_i386.deb](http://rolevikov.net/debian/mail-notification_2.0-1~uptimebox_i386.deb)

---

### Post by uptimebox on 2006-01-26
Dapper .deb with Evolution 2.6 support:

[http://rolevikov.net/debian/mail-notification_2.0.dfsg.1-2uptimebox1_i386.deb]("http://rolevikov.net/debian/mail-notification_2.0.dfsg.1-2uptimebox1_i386.deb")

Had to patch the patch ;) There's no official support for Evolution 2.6.

---

### Post by dpm on 2006-01-26
[quote=uptimebox]Breezy .deb with Evolution support:

[http://rolevikov.net/debian/mail-notification_2.0-1~uptimebox_i386.deb]("http://rolevikov.net/debian/mail-notification_2.0-1%7Euptimebox_i386.deb")[/quote]

Since uptimebox has provided us with a nice package with Evolution support enabled, could we have it uploaded on the backports repository?

As it's been noted before on this thread, the currently backported version does not have support for Evolution folders. Since Evolution is nowadays an integral part of the GNOME desktop and this little app seems to blend in so well with Evo and GNOME, I think it would make sense to enable it.

Another thing is SSL support, I've read a bit about the licensing issues of the OpenSSL library (which mail-notify uses if it is present on the system and the option was enabled at compile-time), but since I'm not an expert on this, I leave commenting on it to any GPL or Debian gurus out there. Here's some info in case anyone is interested:

 Licensing issues: GPL + OpenSSL 
    [http://www.gnome.org/~markmc/openssl-and-the-gpl.html]("http://www.gnome.org/%7Emarkmc/openssl-and-the-gpl.html") 
    [http://www.openssl.org/support/faq.html]("http://www.openssl.org/support/faq.html") 
    [http://lists.debian.org/debian-legal/2002/10/msg00113.html]("http://lists.debian.org/debian-legal/2002/10/msg00113.html") 
    
Anyway, regardless whether SSL support is enabled or not, I think that having the possibility of using mail-notification with Evolution folders would just be nice.

Thanks.

---

### Post by uptimebox on 2006-02-11
OpenSSL support is NOT enabled in my build.

---

### Post by Super King on 2006-02-24
Hey all, I've tried installing this from the .deb provided in the thread and also from source, but it says 

```
dpkg: dependency problems prevent configuration of mail-notification:
 mail-notification depends on libgnome-menu0; however:
  Package libgnome-menu0 is not installed.

```

I see libgnome-menu2 in Synaptic, but not 0, which I assume is the older version. I really want this to work as the 1.1whatever in Synaptic has issues connecting to my Gmail account. Anyone else have this problem, or any suggestions?

---

### Post by lyly on 2006-02-24
[QUOTE=desp]
Another thing is SSL support, I've read a bit about the licensing issues of the OpenSSL library (which mail-notify uses if it is present on the system and the option was enabled at compile-time), but since I'm not an expert on this, I leave commenting on it to any GPL or Debian gurus out there. Here's some info in case anyone is interested:

 Licensing issues: GPL + OpenSSL 
    [http://www.gnome.org/~markmc/openssl-and-the-gpl.html]("http://www.gnome.org/%7Emarkmc/openssl-and-the-gpl.html") 
[http://www.openssl.org/support/faq.html]("http://www.openssl.org/support/faq.html")     [http://lists.debian.org/debian-legal/2002/10/msg00113.html]("http://lists.debian.org/debian-legal/2002/10/msg00113.html") 
Thanks.[/QUOTE]

So why gnubiff has an SSL support and not mail-notify? Both depend on libssl0.9.7 ... Is it a zeal excess from mail-notify package manager? It is really a pity to have to repackage it each time a new version is out! And on security I wont make any compromise...

---

### Post by dpm on 2006-02-25
[quote=Super King]Hey all, I've tried installing this from the .deb provided in the thread and also from source, but it says 

```
dpkg: dependency problems prevent configuration of mail-notification:
 mail-notification depends on libgnome-menu0; however:
  Package libgnome-menu0 is not installed.

``` 
I see libgnome-menu2 in Synaptic, but not 0, which I assume is the older version. I really want this to work as the 1.1whatever in Synaptic has issues connecting to my Gmail account. Anyone else have this problem, or any suggestions?[/quote] 
FYI, I've got libgnome-menu2 installed and *not* libgnome-menu0, which, as you said, is not in the repos. I guess you'll just have to try and install libgnome-menu2 and see if it works. It should be safe.

And if you want to use *mail-notify* only for checking mail on a gmail account and are not woorried about its integration with the GNOME desktop, you may also want to try the *gmail-notify* package available from the repositories, which is also a nice application  for gmail accounts. 

Out of interest, I've tried both the package provided in this thread and also compiling from source, and both of them show the following strange behaviour, so I was just wondering whether anyone else has experienced the same:

If *mail-notification* is started without *Evolution* being started, *bonobo* crashes after some time, and after that any applications that depend on bonobo (i.e *nautilus,* *epiphany...* etc.) fail to start complaining about some *bonobo* server error -I cannot reproduce the exact error right now, since I now always start Evolution automatically with my gnome session. 

After a restart, everything is fine (as long as *mail-notification* is not running standalone, that is, without *Evolution* being run).  Please note that I'm only using *mail-notification* for my *Evolution* Inbox, and on my system it is not set up to check for mail from any other external accounts. So it seems to be an issue with mail-notification and Evolution folders only. It is a pity that mail-notification has not got a bug-tracking system, otherwise I'd just post this as a bug.

Other than that, I find it a great little app. 

BTW, I'm running *Evolution* 2.4.1, the one that is shipped per default with Breezy.

---

### Post by nads on 2006-02-25
i am also having trouble running the client. when i first installed it i was able to configure my gmail account properly, but now when i try to run the program and it automatically tries to check for mail it gets stuck....

any idea of how i solve this?

or better yet, where does it save the config files so i can erase them?

thanks

EDIT: turns out that it only gets stuck when theres new mail...

---

### Post by bender unit on 2006-02-26
Greetings folks.

The mail server at my university won't work without SSL (which I find a very sensible thing), so I need a version of mail-notification with SSL support. Now how do I make my own .deb for this program that includes OpenSSL support?

---

### Post by uptimebox on 2006-02-27
[QUOTE=bender unit]Greetings folks.

The mail server at my university won't work without SSL (which I find a very sensible thing), so I need a version of mail-notification with SSL support. Now how do I make my own .deb for this program that includes OpenSSL support?[/QUOTE]
If you need this only for your own use, you'd better simply build from sources.

---

### Post by bender unit on 2006-02-27
[QUOTE=uptimebox]If you need this only for your own use, you'd better simply build from sources.[/QUOTE]

Well, I'm sure I'm not the only one who needs this (just look at post #52). It's really a pity that such a licensing issue should compromise security. I guess the original author of mail-notify didn't even think about that problem when he released his program under the GPL, and probably would've thought about that twice if he knew about it. And to repeat lyly's question, why the hell then is the gnubiff in the repositories OpenSSL-enabled when mail-notify isn't? Can't we just stick an SSL-enabled version of the program in some "unfree" repository and let people themself decide whether they have a problem with such issues? 

It's really disappointing to have such a nice distro and powerful package management system, but whenever you need something specific you still have to compile it yourself (and that means you loose all of the advantages of apt and just get all the disadvantages). Guess I should've stuck to Gentoo after all...

---

### Post by uptimebox on 2006-02-28
[QUOTE=bender unit]Guess I should've stuck to Gentoo after all...[/QUOTE]
Good luck.

When I tried to switch from Debian to Gentoo on my work PC, I found myself wasting 30% of time "supporting" and "upgrading" my own machine. 

Debian. When you have work to do.

---

### Post by uptimebox on 2006-02-28
[QUOTE=bender unit]Well, I'm sure I'm not the only one who needs this (just look at post #52).[/QUOTE]
Do you need evolution support in the package? If not, I'll build a .deb for you.

---

### Post by bender unit on 2006-02-28
[QUOTE=uptimebox]Good luck.

When I tried to switch from Debian to Gentoo on my work PC, I found myself wasting 30% of time "supporting" and "upgrading" my own machine. 

Debian. When you have work to do.[/QUOTE]

Well, just guess why I'm using Ubuntu now instead of Gentoo... ;) 

Don't want to cause another distro battle here, but back when I was using Debian, I had at least the same amount of "supporting and upgrading" to do in order to keep my machine useful. I'll just say hardware support (I really like that about Ubuntu, I installed it and just about everything worked without me ever having to think about it).

I think Gentoo's main advantage is that you just don't have problems like those we're talking about right now. Because everything is built from source and automatically configured to your needs, based on your selection of USE flags and other installed packages. Therefore you don't have to worry about strange decisions a package maintainer might have done for you, like disabling SSL support. 

Now don't get me wrong, I find Ubuntu a very good distro, actually the first since about three years that could really make me switch permamently from Gentoo (because, mainly, I'm sick of how long updates take or, for example, "just trying out some new app"). But things as the disabled SSL support and no "official" pacakge available really bug me. I know from Gentoo that most linux programs can be configured quite a bit at compile time, which can change their functionality quite drastically, so I'm also aware that for binary packages, there will never be a "one size fits all" version of a particular app available in the repositories. But then I'm missing an easy way to just keep a mixed system of "official" packages and and source-built software. 

The problem is (correct me if I'm wrong), that once I decide to build a certain package on Ubuntu (or Debian) myself, I loose all the advantages of apt, meaning no automatic upgrades and dependency management. If a new version of that program came out, I would have to fetch the sources myself and build it again by hand, passing the right configure arguments and whatnot. 

I really wish there would be some kind of hybrid distro which combined the strenghts of Debian's and Gentoo's package managament systems. So if there's some app that's not available as a binary package or if I don't like the way some binary package has been configured, I can just type something like an "emerge app" and that's it. No hassling around with getting the sourcecode, configuring it and building it by hand, no loose of automatic upgrades once a new version comes out, etc. 

Regarding you offer of building a .deb for me: thanks, I appreciate that. But I don't want to be a burden for you. Anyways, what's the Evolution support do? Maybe I do need it after all, since I just switched from Thunderbird to Evolution since it can also manage my appointments and sync them with my mobile.

Greetings
Christoph

---

### Post by uptimebox on 2006-02-28
[QUOTE=bender unit]The problem is (correct me if I'm wrong), that once I decide to build a certain package on Ubuntu (or Debian) myself, I loose all the advantages of apt, meaning no automatic upgrades and dependency management. If a new version of that program came out, I would have to fetch the sources myself and build it again by hand, passing the right configure arguments and whatnot.[/QUOTE]
You are wrong. Things like source upgrade are more than possible. And don't forget about apt pinning. [APT Howto]("http://www.debian.org/doc/manuals/apt-howto/index.en.html") is your friend.

---

### Post by lyly on 2006-02-28
[QUOTE=uptimebox]You are wrong. Things like source upgrade are more than possible. And don't forget about apt pinning. [APT Howto]("http://www.debian.org/doc/manuals/apt-howto/index.en.html") is your friend.[/QUOTE]

But you still will need to install all the dev packages, which is not very conveniant for normal users...

---

### Post by bender unit on 2006-02-28
[QUOTE=uptimebox]You are wrong. Things like source upgrade are more than possible. And don't forget about apt pinning. [APT Howto]("http://www.debian.org/doc/manuals/apt-howto/index.en.html") is your friend.[/QUOTE]

Thanks for link, guess I'll read through that document before complaining about apt and/or dpkg again. But that pinning stuff is something I already didn't understand back when I was using (or rather, trying to use) Debian. Seems too complicated for me. What's the use of say, preference settings between 100 and ~900, if special behaviours only occur on certain levels? For keeping a mixed stable/unstable system, something like Gentoo's package keywords and mask/unmask really does the job well enough, IMHO. No need to play with obscure preference levels, just put unstable packages in /etc/portage/package.keywords and you're done. Why can't it be that easy in Ubuntu/Debian?

Anyways, regarding the original topic: apart from this APT HOWTO, is there a nice guide somewhere that I've missed that explains just what I wanted to know (i.e., specifically, how to have a certain package automatically built from source using definable ./configure settings instead of using the available binary package and upgrading that package using these settings whenever a new version becomes available)?

---

### Post by uptimebox on 2006-03-01
[QUOTE=bender unit]Anyways, regarding the original topic: apart from this APT HOWTO, is there a nice guide somewhere that I've missed that explains just what I wanted to know (i.e., specifically, how to have a certain package automatically built from source using definable ./configure settings instead of using the available binary package and upgrading that package using these settings whenever a new version becomes available)?[/QUOTE]
[http://packages.debian.org/stable/devel/apt-build.html](http://packages.debian.org/stable/devel/apt-build.html)

---

### Post by manicka on 2006-03-01
[QUOTE=uptimebox][http://packages.debian.org/stable/devel/apt-build.html](http://packages.debian.org/stable/devel/apt-build.html)[/QUOTE]

apt-build is available in the Universe repos. There's no need to use a Debian package.

---

### Post by ngms27 on 2006-03-01
Right, this works like a charm. However I cannot get a sound to play when new mail arrives.

I've added mplayer mynewmail.wav with full path to the the wav in a shell script that works manually, but doesn't work via mail notifcation.

Any ideas?

---

### Post by ngms27 on 2006-03-01
Sorry fixed it!

Needed full path to my shell script!

---

### Post by bender unit on 2006-03-02
Ok, well I have installed apt-build now and tried building an SSL-enabled version of mail-notification myself. Read the article at [http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html) and got to work. Figured I had to run "sudo apt-build source mail-notification" first in order to get the sources because maybe I'd have to change the config (if it has hard-disabled SSL). But everything I got was "Missing package name for source_by_package()."

So that didn't work. Well, I wanted to find out if apt-build worked at all so I tried "sudo apt-build install mail-notification". This looked better. First it installed a whole bunch of *-dev Packages which are supposedly needed to compile mail-notification myself. Then it download the sources and went to work. But that didn't go far either. It aborted just a few seconds after that with an error. Scanning through all the stuff it had output before, I found that while running the configure script, the following error occured:

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Ok. Fine. What's that mean now? First off, the config.log file it didn't exist, at least not where I supposed to find it (/var/cache/apt-build/build/mail-notification-2.0, i.e. the build directory of apt-build). Then I searched to forum for the "compiler cannot create executables" problem and every posting that I found said "you have to install the build-essential package". Well, it's already installed, so that can't be the problem. Regarding the compiler, "dpkg -l gcc*" tells me that I got gcc versions 4.0.1, 3.4.4 and 3.3.6 installed, dunno why I'd need all three of them, but heck, could have been installed while running Automatix or following one or  two HOWTOS from the Wiki. 

Anyways, I changed into the build directory of mail-notification and wanted to see if I at least could run ./configure by hand. Ran it using sudo because I figured my normal user didn't have write access there and apt-build was also run using sudo. Surprisingly, the script went trough everything without any problems! Not a word about the compiler not being able to create executables! Just in case, I tried the apt-build command again, but nothing had changed, there.

So what is wrong now? BTW, sorry I'm still posting in this thread although it's already quite offtopic, but I'm not quite sure where else to post it. Besides, this thread is like the only place in the forum where my posts ever got answered.

---

### Post by uptimebox on 2006-03-03
As far as I could investigate, there are broken dependencies in Breezy backports. Probably this is the reason of your failure.

[size=1]```

# apt-get install libeel2-dev Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libeel2-dev: Depends: libgnomevfs2-dev (>= 2.9.1) but it is not going to be installed
               Depends: libgnomeui-dev (>= 2.6.0) but it is not going to be installed
               Depends: libgnome-desktop-dev (>= 2.1.4) but it is not going to be installed
E: Broken packages

```[/size]

---

### Post by dpm on 2006-03-03
[quote=bender unit]
Anyways, I changed into the build directory of mail-notification and wanted to see if I at least could run ./configure by hand. Ran it using sudo because I figured my normal user didn't have write access there and apt-build was also run using sudo. [/quote] 
I cannot help on the rest, but I can tell you that you do not need to run configure with sudo. You only need root privileges when installing the binaries with 'make install', since then, amongst other things the binaries get copied to /usr/bin (or whichever bin directory a particular app gets installed to), where generally only the root account has write access.

Just as extra info, once you've managed to resolve the dependencies, you could try

```
sudo checkinstall
``` 
instead of the usual 'make install'. That will create a .deb package from the compiled sources for you. You then only have to type

```
dpkg -i mail-notification.deb
``` 
where mail-notification.deb is the name you've given to your package with checkinstall (it could be something else, of course). Also note that you obviously have to install the checkinstall package, which is available from the breezy repositories. Of course checkinstall is not a perfect replacement for a properly built debian package, so one of the disadvantages of using it is that it does not generate its dependencies.

BTW, I remember that I had to install the **gnome-devel**, **openssl** and **libssl-dev** packages when I compiled mail-notification from source. If you want evolution support, you'll have to install **evolution-dev** and maybe also **evolution-data-server-dev**.

Maybe you've already had a look, but the homepage of mail-notification

[http://www.nongnu.org/mailnotify/]("http://www.nongnu.org/mailnotify/")

instructs you to apply the appropriate patches before running configure.

If I remember correctly, after resolving all dependencies and applying the patches, I ran

```
  LDFLAGS=-Wl,--export-dynamic
  ./configure --with-evolution-source-dir=/usr/include/evolution-2.4
``` 
to compile the sources. 

That worked for me. I was running my custom-made .deb of mail-notification until I found uptimebox's package, which is what I'm using right now (I personally don't need SSL, only Evolution folders support). Also have a look at the INSTALL script in the source tree for extra info.

And finally, since the package is already out there, could someone from the backports team not upload it to the repos? I understand that the available version can not have SSL enabled for licensing reasons, but I'll just say it again: having evolution support would be nice!

Just my 2 cts.

---

### Post by bender unit on 2006-03-13
Ok, I finally managed to get a working SSL-enabled version of mail-notification. apt-build wasn't such a great helper though. Well, anyways, the problem with apt-build was that the breezy version (0.12.9) seems to be somehow broken. Found another thread here in the forums that said something like that. So I installed 0.12.17 (which is probably from dapper, but I don't know just found it by browsing the pool directory on an ubuntu mirror). 

So, with this version, the "compiler cannot create executables" problem seems to be gone, at least I could do "sudo apt-build install mail-notification", which fetched the sources, built the package and installed it. Of course, without SSL support, because in the whole process, there's a patch applied that does this. But after editing the debian/rules file in apt-build's build directory and running apt-build again with --reinstall, it finally worked and got me an SSL enabled version. Well, that would have probably been easier by and using checkinstall. Now I'm wondering, what's apt-build good for (except compiling some packages with "better" optimization)? Guess if a new version comes out I'd have to do the whole process again (or might as well install a new self-built version by hand). Looks like apt-build could do with a little more features, like editable configure flags...

---

### Post by mikkel_robin on 2006-04-23
[QUOTE=uptimebox]Dapper .deb with Evolution 2.6 support:

[http://rolevikov.net/debian/mail-notification_2.0.dfsg.1-2uptimebox1_i386.deb]("http://rolevikov.net/debian/mail-notification_2.0.dfsg.1-2uptimebox1_i386.deb")

Had to patch the patch ;) There's no official support for Evolution 2.6.[/QUOTE]


I cant get the evolution support to work ( running [http://rolevikov.net/debian/mail-notification_2.0.dfsg.1-2uptimebox1_i386.deb](http://rolevikov.net/debian/mail-notification_2.0.dfsg.1-2uptimebox1_i386.deb) and Dapper). 

Im getting this message:
Mail Notification can not contact Evolution-
Make sure that Evolution is running and taht the
Evolution Mail Notification plugin is loaded

"Evolution Mail Notification plugin" means "New Mail Notification" or am i missing somthing?


Can anyone help me?

/Mikkel

---

### Post by uptimebox on 2006-04-24
[attach]8704[/attach]

---

### Post by nocturn on 2006-04-24
[QUOTE=uptimebox][attach]8704[/attach][/QUOTE]

If I'm not mistaken that is the Evolution plugin that generates a dbus message if a new mail arrives.

What it is sorely lacking is a listening part to actually display a notification when a message comes in.

---

### Post by dpm on 2006-04-30
First of all, thanks again for the Dapper .deb. I installed that and it worked perfectly.

I've got only a question: I had tried to recompile mail-notification before for Evo 2.6 support (I had only to patch the patch also :) ). After that, I configured the sources successfully (all options were enabled, no errors or warnings), compiled and installed with no trouble, logged out and in (as recommended in the tarball README file), and when I started mail-notification, I got the dreaded "The application mail-notification has quit unexpectedly" message. 

As I say, now I've got mail-notification working in Dapper with uptimebox's package, but I just don't understand why my self-compiled version did not work. Uptimebox: did you compile the package with a different gcc version than the one in Dapper?

---

### Post by uptimebox on 2006-05-02
> **desp]First of all, thanks again for the Dapper .deb. I installed that and it worked perfectly.
[/QUOTE]
It's my pleasure  said:**
> 
As I say, now I've got mail-notification working in Dapper with uptimebox's package, but I just don't understand why my self-compiled version did not work. Uptimebox: did you compile the package with a different gcc version than the one in Dapper?


I've compiled this package last January, with the current Dapper version of gcc. Don't know if it was changed since.

May be your optimization flags are too high?

---

### Post by Whoopie on 2006-05-11
Hi,

when somebody has problems with mail-notification with enabled evolution support, you shoud look at [https://launchpad.net/bugs/44078](https://launchpad.net/bugs/44078)
There's a patch for bonobo.

Best regards,
Whoopie

---

### Post by psweetma on 2006-06-14
Hi, I'm trying to build mail-notification from source in Dapper to turn on SSL.  I did an "apt-get source mail-notification", but when I run "./configure" I get an error saying:

checking for GTK+ - version >= 2.6.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: unable to find the GTK+ library

I thought Dapper ran GTK 2.8.xx, am I missing something obvious...?

Paul

---

### Post by uptimebox on 2006-06-14
[QUOTE=psweetma]
I thought Dapper ran GTK 2.8.xx, am I missing something obvious...?
[/QUOTE]

Obviously, you do ;) 

[LIST=1]
[*]You don't need to run ./configure script. Please, read apt-src documentation. 
[*]You need to have GTK dev package (at least) to be installed, because it contains headers.
[/LIST]

---

### Post by dpm on 2006-06-15
[quote=psweetma]Hi, I'm trying to build mail-notification from source in Dapper to turn on SSL.  I did an "apt-get source mail-notification", but when I run "./configure" I get an error saying:

checking for GTK+ - version >= 2.6.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: unable to find the GTK+ library

I thought Dapper ran GTK 2.8.xx, am I missing something obvious...?

Paul[/quote] 
As uptimebox said, you need the development packages every time you compile something. And If you are recompiling a debian package from source, you do not need to  run ./configure. There are debian tools that will recompile the package, repackage it and install it for you.

Here's how you can do it:

1. **sudo apt-get install fakeroot**
Necessary to run the debian scripts that you will use later pretending you are root.

2. **apt-get source mail-notification**
Get the sources for the debian mail-notification package

3. **sudo apt-get build-dep mail-notification**
Get all the development packages necessary to compile the mail-notification package (that includes the gtk dev packages)

4. **sudo apt-get install libssl-dev**
Get the development package necessary to compile mail-notification with SSL support. IIRC, mail-notification will enable all available features at compile time if it finds the development packages for it, e.g., it is not necessary to enable the feature explicitly as a compialation flag if the appropriate -dev package is installed.

5. Edit the **debian/rules** file in the mail-notification source tree in order to add SSL support (IIRC deleting the "DEB_CONFIGURE_EXTRA_FLAGS = --disable-ssl" line should do)

6. Run '**dch -n**' and change the package version number to something sensible (e.g. append .0.0.<your-name>.0 to the package version).
This step is important in order to make sure that the package version is higher than the one you've got installed but also to make sure that (in case you want it) newer versions in the repository will be able to be installed. Please read the debian new maintainers guide for more information about packaging .deb's. Also write something sensible in the changelog so you know what this package is about.

7. **fakeroot dpkg-buildpackage -b -uc -us -d**
That will compile the sources, build the package for you and install it. Please read the man page of dpkg-buildpackage in order to get to know more about the options.

8. Run '**mail-notification --list-features**' in order to confirm that SSL support is now enabled.

9. You're all set. You may have to log out and log back in in order to get mail-notification to see the new features. I think I read somewhere that this was necessary due to a bug in some gnome library that mail-notification uses.

Note that I'm writing this off the top of my head. I did something similar some time ago and it worked, but I haven't tested it this time. I think I didn't forget anything. Please let me know if this worked for you or if there is something missing in this steps and I'll update the post accordingly.

I hope this helps.

Cheers.

---

### Post by dpm on 2006-06-15
And while you're at it, and in case you are interested, you can **unpack and copy** the attached patch to the **debian/patches** folder after **step 5** (call it 5a, if you like) of my previous post.

04-mail-notification-2.0-evolution-2.6.diff-> This patch adds Evolution 2.6 folder support. Read bug [https://launchpad.net/distros/ubuntu/+source/mail-notification/+bug/37474](https://launchpad.net/distros/ubuntu/+source/mail-notification/+bug/37474) in Malone for issues related to this.

Cheers.

---

### Post by psweetma on 2006-06-15
Desp(and Uptimebox), thank you very much for your help, following your instructions I managed to build the package first time and it's working a treat.  You certainly saved me a lot of time - it was a case of not knowing what it was that I didn't know, if you follow my drift, but I'll feel a lot more confident about building my next Unbuntu / Debian package from source.

Paul

---

### Post by dpm on 2006-06-15
[quote=psweetma]Desp(and Uptimebox), thank you very much for your help, following your instructions I managed to build the package first time and it's working a treat.  You certainly saved me a lot of time - it was a case of not knowing what it was that I didn't know, if you follow my drift, but I'll feel a lot more confident about building my next Unbuntu / Debian package from source.

Paul[/quote]

Glad to hear that, you're welcome.

---

### Post by uptimebox on 2006-06-16
[QUOTE=psweetma]Desp(and Uptimebox), thank you very much for your help, following your instructions I managed to build the package first time and it's working a treat.  You certainly saved me a lot of time - it was a case of not knowing what it was that I didn't know, if you follow my drift, but I'll feel a lot more confident about building my next Unbuntu / Debian package from source.

Paul[/QUOTE]

Not at all. And another good advice. Read APT documentation. APT - is the hiden power of any Debian based OS.

[http://www.debian.org/doc/user-manuals#apt-howto](http://www.debian.org/doc/user-manuals#apt-howto)

---

### Post by Briquet on 2006-06-24
Mail Notification 3.0 was released June 14, 2006

Please anybody could create the .deb package?
Thanks

---

### Post by uptimebox on 2006-07-05
[QUOTE=Briquet]Mail Notification 3.0 was released June 14, 2006

Please anybody could create the .deb package?
Thanks[/QUOTE]
[http://rolevikov.net/debian/mail-notification_3.0.uptimebox.1_i386.deb](http://rolevikov.net/debian/mail-notification_3.0.uptimebox.1_i386.deb)

---

### Post by uptimebox on 2006-07-05
Started new thread about Mail Notification 3.0:

[http://ubuntuforums.org/showthread.php?t=209361](http://ubuntuforums.org/showthread.php?t=209361)

---

### Post by Briquet on 2006-07-08
Good job! and thanks

---

### Post by republicson on 2007-02-27
You had me until step 5. I cannot find the debian/rules file. any help?

---

