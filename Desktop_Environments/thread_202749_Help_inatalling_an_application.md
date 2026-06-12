---
title: "Help inatalling an application"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Isoss on 2006-06-24
I have downloaded an arabic dictionary called qamoose from [arabeyes.org]("http://www.arabeyes.org/project.php?proj=QaMoose")
I extracted the file and now I have a folder which contains a bunch of files and a README one. I opened it with gedit and here is the installation steps listed:

```

-------------------
Basic Instructions:
-------------------

+ Download the package to you local machine

+ Modify dict_header.pl
   - Inspect and modify file with YOUR info (username/password/domain, etc)
   - Insure $embed's value is 0 (unless you're embedding this code into
     your site and would like to extend the look-n-feel of the package
     NOTE: setting this to 1 will require some customization work on your
     end as well on dict_main, dict_admin and dict_lib)

+ Insure availability of mySQL on your local machine - if a different
  database is used, make appropriate modification in dict_header.pl

+ Run `dict_create.pl'

+ Invoke (click-on) dict_admin.cgi within your browser

+ Login by entering your Super admin email and password

+ Click on 'Account:Password' to change Super admin's password
  NOTE: Once Password is changed the entry in dict_lib.pl is irrelevant.
  NOTE: All passwords are stored in the mySQL db in encrypted form.

+ Logout and now the package is ready for usage

+ Invoke (click-on) dict_main.cgi within your browser - MAIN start point

+ In order to access the DICT abilities, either start one on your machine
  or point to an available server on the 'net.

```
ok ... I am not sure of some parts espetially the invoking part (clicking-on) I don't know what this does, I did a one click on dict_admin.cgi and the icon changed but nothing happened. I double-clicked on it and it prompts this error:
```

**Cannot open dict_admin.cgi**
The filename "dict_admin.cgi" indicates that this file is of type "CGI script". The contents of the file indicate that the file is of type "Perl script". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Perl script", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

```
I am not sure of what's happening! I modified dict_header.pl as said ("I am familiar with these scripts for I am a php programmer) ... So I hope somebody has an answer cuz this is complicated. I dunno why all packages are just the same in linux, like in windows they're all EXEs! Why RPMs and DEBs and the ones that need configure, make and make install???

Thanks.

---

### Post by amohanty on 2006-06-24
NOTE: I have never installed this app, and my advise is pretty much based on what you have posted here. 

> + Invoke (click-on) dict_admin.cgi within your browser

When you have a file with an extension .cgi, it is typically meant to be hosted off of a web server that supports cgi (for e.g. apache). I am not sure if > + Run `dict_create.pl'
this step sets up the web server for you (most likely not). 

Basically:
1. you will have to install apache on your machine (the default setup has cgi enabled)
2. Copy the dict_admin.cgi file to the cgi-bin folder in the apache root (look at  the apache docs to find out where it is by default - I cant seem to remember ot offhand)
3. Restart apache and then go to the following url:
[http://localhost/cgi-bin/dict_admin.cgi](http://localhost/cgi-bin/dict_admin.cgi)

If everything went smoothly you should see the login page.

> I dunno why all packages are just the same in linux, like in windows they're all EXEs! Why RPMs and DEBs and the ones that need configure, make and make install???
Because [linux is not windows]("http://www.ubuntuforums.org/showthread.php?t=58017")

HTH
AM

---

### Post by Isoss on 2006-06-24
[QUOTE=amohanty]NOTE: I have never installed this app, and my advise is pretty much based on what you have posted here. 



When you have a file with an extension .cgi, it is typically meant to be hosted off of a web server that supports cgi (for e.g. apache). I am not sure if 
this step sets up the web server for you (most likely not). 

Basically:
1. you will have to install apache on your machine (the default setup has cgi enabled)
2. Copy the dict_admin.cgi file to the cgi-bin folder in the apache root (look at  the apache docs to find out where it is by default - I cant seem to remember ot offhand)
3. Restart apache and then go to the following url:
[http://localhost/cgi-bin/dict_admin.cgi](http://localhost/cgi-bin/dict_admin.cgi)

If everything went smoothly you should see the login page.
[/QUOTE]
Thanks. I have apache server and I am running my websites with localhost but have never seen the cgi-bin folder any where!? cuz according to the URL [http://localhost/cgi-bin](http://localhost/cgi-bin) it means that the folder must be put in /var/www . Are u sure that the cgi file must be copied to such a folder? But anyway I'll have a look at the docs and see where it is.
[QUOTE=amohanty]
Because [linux is not windows]("http://www.ubuntuforums.org/showthread.php?t=58017")
[/QUOTE]
I KNOW THAT'S WHY I LOVE LINUX!!!
I know it's not windows, I've been using it for 4 months now and I strongly believe that it has nothing to do with windows. when ppl see it they say: what kinda windows you are using? I say THIS IS NOT WINDOWS:mrgreen:  it's just that I was thinking: isn't it better to have ONE extension and only ONE way to install application than all these debs, rpms, bins and  other ways? well ... these are easy but compressed applications that require ./configure, make, and make install have never worked for me although I've tried and read and asked alot about it! they always give me errors. That's why I prefere to deal with only one installation method.

---

### Post by amohanty on 2006-06-26
> according to the URL [http://localhost/cgi-bin](http://localhost/cgi-bin) it means that the folder must be put in /var/www . Are u sure that the cgi file must be copied to such a folder? But anyway I'll have a look at the docs and see where it is.

Look at the docs here:
[http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)

> these are easy but compressed applications that require ./configure, make, and make install have never worked for me although I've tried and read and asked alot about it! they always give me errors. That's why I prefere to deal with only one installation method.

What you are saying does make sense, but (to oversimplify it greatly) linux/foss is about scratching your own itch and distro philosophies. As a result what works for one may not work for others and hence you end up with a lot of choice, which IMO is a good thing.

If  you would like the single installer option stick to the standard repos in synaptic. If the app you want to be in the same format (ie deb/rpm/etc) try dropping an email to the developer and asking him nicely :) - it doesnt alway work, but there's no harm in trying.

HTH
AM

---

