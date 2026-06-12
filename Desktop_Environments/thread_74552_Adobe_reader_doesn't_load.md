---
title: "Adobe reader doesn't load"
date: 2005-10-12
forum: Desktop Environments
---

### Post by catskin on 2005-10-12
hey people,

just asking if anyone uses acrobat reader for linux.

I installed mine on the default locations, and when I typed acroread to start it, it shows me the splash screen and then exits. Not even an error message. Does anyone know how to fix that? environment variable perhaps?

thanks!

---

### Post by xaverx on 2005-10-12
Use rather evince, is's more fast and stable.

```
sudo apt-get install evince
```

---

### Post by 23meg on 2005-10-12
and if that doesn't work, use xpdf :)

if you must use adobe reader for some reason though, did you try typing acroread in the terminal window? if not, try and see what error message it gives there, if any.

---

### Post by catskin on 2005-10-12
no error message at all.

---

### Post by 23meg on 2005-10-12
weird; did you install it from the ubuntu repositories? if so, try a reinstall. but it's best to stick with evince as a viewer.

---

### Post by 23meg on 2005-10-12
also try installing the package acroread-debian-files.

---

### Post by Alexander Kirillov on 2005-10-12
[QUOTE=catskin]hey people,

just asking if anyone uses acrobat reader for linux.

I installed mine on the default locations, and when I typed acroread to start it, it shows me the splash screen and then exits. Not even an error message. Does anyone know how to fix that? environment variable perhaps?

thanks![/QUOTE]
Which version of acroread? did you get the .deb package from one of the repositories or downloaded the tar.gz file from adobe web site?  how exactly did you install it?

---

### Post by rsankuratri on 2005-10-12
I am also having the same problem.  I installed the latest version from the adobe website, which is version 7 on my laptop (running breezy release candidate. :-) ).  Followed the installation instructions in the provided README file and when I execute the acroread shell script it just flashes the splash screen and vanishes.  No error messages and nothing in the terminal window either when you run it from the terminal.

Could it be a permissions issue?  I did do a chmod 777 on the entire contents of the adobe folder :???: 

I want to use Acrobat Reader so that I can fill in the editable data fields in the pdf files.

Any ideas or alternatives? :???: 

Thanks for your help

---

### Post by HermanAB on 2005-10-12
Just a thought:  
Sometimes when an application has crashed, a new instance won't run, since it will look around at startup and sense that it is already running, then exit.  This is done to prevent multiple copies from running when you clicked too many times.

So, do 'ps -e' and see if there is a crapped out Adobe reader stuck in memory  and if so, do a 'kill -9 PID' on it.  After that, Adobe may work again.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by catskin on 2005-10-12
[QUOTE=Alexander Kirillov]Which version of acroread? did you get the .deb package from one of the repositories or downloaded the tar.gz file from adobe web site?  how exactly did you install it?[/QUOTE]

Newest version from Adobe web site. Untar, change to root, then install. Default directories-> /usr/local/Adobe...

---

### Post by catskin on 2005-10-12
observation though:

on earlier Linux boxes I have used, I set this little variable called LC_CTYPE to "ISO8859-1", and then it will work.

Trying this now with Breezy and Reader 7.0.1 results in a message "Locale not supported, reverting to C locale". Any ideas?

---

### Post by dongdongdog on 2005-10-13
I have the same issue on my computer. When I typed "acroread" in the console, nothing happened next. There is no error message at all. I used synaptic to install acroread.

---

### Post by zuoliang on 2005-10-14
I also have this issue since 5.10 RC.

---

### Post by wq7278 on 2005-10-21
Hi, 
I had the same problem.
Download acrobat reader 7 form acrobat website.:AdbeRdr701_linux_enu.tar.gz
unzip this gz file to /etc/acrobate
the open a console. 
: su root
: sh INSTALL  
it asked to accept a agreement. then tell me it intall it to: /usr/local/.. something. I used this default. 
then it copyed and say:

"
Adobe and Reader are either registered trademarks or trademarks of Adobe Systems Incorporated in the United States and/or other countries.

Reader_WWEULA-en_US-20040915_1630


Please type "accept" to accept the terms and conditions of license agreement; Type "decline" to exit.  accept

This installation requires 94 MB of free disk space.

Enter installation directory for Adobe Reader 7.0.1 [/usr/local/Adobe/Acrobat7.0]
/usr/local/Adobe/Acrobat7.0

Installing platform independent files ... Done

Installing platform dependent files ... Done

root@ubuntuLaptop:/etc/AdobeReader#
"

then I went ot the dir it told me and run:
cd /usr/local/Adobe/Acrobat7.0/bin
sh acroread

the acorbat picture show up and then it dispear...without any error message.

Any idea why?

---

### Post by jb.tux on 2005-10-22
I am having the same problems, sh acroread does next to nothing. I got a bit of output from mine though. Maybe this will help.

```
$:/usr/bin/Adobe/Acrobat7.0/bin$ sh acroread
acroread: line 304: /usr/bin/Adobe/Acrobat7.0/Reader/intellinux/bin/acroread: cannot execute binary file
acroread: line 304: /usr/bin/Adobe/Acrobat7.0/Reader/intellinux/bin/acroread: Success
```

I too need to fill in forms for work. I installed to /usr/bin, is that an ok place to install? I figured most of the other program files I use are there too. Would uninstalling and reinstalling to a different directory solve the issues? I'm on Breezy 5.10.

---

### Post by akaihola on 2005-10-22
On a breezy default installation with acroread installed by Automatix 2.10, acroread works fine.

On my laptop it doesn't. I removed ~/.adobe and ~/.acrobat, purged acroread, re-installed it and run it in the terminal. The splash screen flashes, acroread quits and there is no output on the terminal.

There must be a conflict with some other package. I checked that I have libstdc++5 and gcc-3.3-base on both computers.

I need acroread for filling in forms and to be able to check that PDFs I generate open successfully on Win/Mac computers.

---

### Post by kevinz on 2005-10-23
so i also have this problem and find this post.. is it still hanging?

---

### Post by short4lif2 on 2005-10-24
I simply performed the installation and it worked fine but i do not have an acroread command in the console

---

### Post by KidKat on 2005-11-06
[QUOTE=catskin]hey people,

just asking if anyone uses acrobat reader for linux.

I installed mine on the default locations, and when I typed acroread to start it, it shows me the splash screen and then exits. Not even an error message. Does anyone know how to fix that? environment variable perhaps?

thanks![/QUOTE]
I fixed this by running
ubuntu@ubuntu:~$ sudo apt-get install libstc++5

---

### Post by t3g on 2005-11-08
For information, this problem occured the same time qgo stopped working issuing a segmentation fault. Might be linked to the same libs (on qgo forums, s.o. suggested qt libraries compiled with styles not enabled).

They worked on a clean breezy install. The package that broke them was scim.

---

### Post by imoas83 on 2005-11-15
Ok.. I had the same problem and I resolved it by installing libstdc++5 with this command:

sudo apt-get install libstdc++5

then I wrote in the console:

/usr/local/Adobe/Acrobat7.0/bin/acroread

and it started!!!! ;)

P.S. Sorry for my english!!

---

### Post by t3g on 2005-11-15
To everybody

acroread not starting is a known bug. It happens on Breezy when you have scim-gtk2-immodule installed cause this package asks for libstdc++6 and thus makes 3rd parties software compiled against libstdc++5 crash.

ATM, there is no other solution than remove scim-gtk2-immodule. If you need both scim input and acroread, there is a trick to configure scim so you don't need to have scim-gtk2-immodule installed, but you'll have to look for it yourselves (I didn't try it), possibly on launchpad (look for acroread or scim bug reports).

I'm just writing what I've read elsewhere, so I might not have explained it correctly, but I can confirm that removing scim-gtk2-immodule allow acroread to work. However, to me scim was far more important than acroread, so I'll just wait till scim is fixed.
Man, Evince sure shows ugly .pdf. Wish they add antialiasing soon.

---

### Post by cwmccabe on 2005-12-19
A quick-fix I found was to append the following two lines to the beginning of the */usr/bin/acroread* file, just after the *#!/bin/sh*:

*GTK_IM_MODULE=xim*

*export GTK_IM_MODULE*

Now acroread, in and out of Mozilla, works just fine for me.

---

### Post by danielinffm on 2007-05-04
> **cwmccabe said:**
> A quick-fix I found was to append the following two lines to the beginning of the */usr/bin/acroread* file, just after the *#!/bin/sh*:

*GTK_IM_MODULE=xim*

*export GTK_IM_MODULE*

Now acroread, in and out of Mozilla, works just fine for me.

it's been a long time someone has written to this thread... but... this work's fine for me, too. thx!

---

