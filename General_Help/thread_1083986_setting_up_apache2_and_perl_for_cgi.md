---
title: "setting up apache2 and perl for cgi"
date: 2009-03-01
forum: General Help
---

### Post by pdj on 2009-03-01
Hi All,

I was wondering if anyone could help. I've been trying to set up apache2 to run cgi scripts using perl. 

I followed the instructions in this tutorial: [http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html) (but skipped the php stuff)

So I installed modperl and added the following to my apache2.conf:

    ScriptAlias /cgi-bin/ /var/www/cgi-bin/

    <Directory /home/www/cgi-bin/>
    Options ExecCGI
    AddHandler cgi-script cgi pl
    </Directory>

But I still just get an Internal Server Error when I try to access a perl script.

Where am I going wrong?

Cheers,

PDJ.

---

### Post by albinootje on 2009-03-01
> **pdj said:**
>  But I still just get an Internal Server Error when I try to access a perl script.

Did you restart apache after making those changes ?
And what about the cache of the web browser ? Sometimes Firefox keeps errors in the cache annoyingly long. I usually try a few other web browsers (Galeon,Konqueror) in such cases.

And is there anything interesting in the apache logs about this ?

---

### Post by Rallg on 2009-03-01
I no longer have apache with perl cgi configured, but when I did, it took great effort to get it to work correctly (it was easier on Windows). As I recall, the how-to instructions were missing some information. Possibilities:

Does your config have +Includes
Does your config tell apache to parse html and htm (not just shtml) for cgi
Is your perl cgi file where apache thinks it should be
Can the folder (entire path) be accessed, that is, does it have correct permissions
Within the cgi file, does the "shebang" show the correct path to perl

As I say, I forgot what I had to do, but did eventually get it working. I believe the last three suggestions are where to start, since you wouldn't get the error message if either of the first two were wrong.

---

### Post by pdj on 2009-03-02
Hi guys,

Thanks for the suggestions, I think firefox was showing me the cached version. I had restarted apache after I made the changes, so that wasn't it, but I've cleared my browser history and tried it again and it works!!

So thanks for the help guys!

PDJ.

---

