---
title: "How To: Bugzilla"
date: 2006-07-26
forum: Desktop Environments
---

### Post by thoolihan on 2006-07-26
I had some problems installing the bugzilla package on Dapper.  I got it to work by installing the perl modules and apache with apt and then installing bugzilla by hand. Here's a quick summary of how:

```

sudo apt-get install \
apache \
apache-common \
apache-doc \
apache-perl \
apache-ssl \
libapache-mod-perl \
libdbd-mysql-perl \
libdbi-perl \
libhtml-parser-perl \
libhtml-tagset-perl \
libhtml-tree-perl \
liblocale-gettext-perl \
libnet-daemon-perl \
libperl5.8 \
libplrpc-perl \
libtext-charwidth-perl \
libtext-iconv-perl \
libtext-wrapi18n-perl \
libunicode-string-perl \
liburi-perl \
libwww-perl \
perl \
perl-base \
perl-modules \

wget http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-2.22.tar.gz

cd /var/www
sudo tar xvzf ~/bugzilla-2.22.tar.gz

sudo ln -sf /var/www/bugzilla-2.22 /var/www/bugzilla
cd /var/www/buzilla
sudo ./checksetup.pl
sudo [your fav editor here] localconfig

```
While in your editor, set the parameters to use your mysql server.

Also, change your apache group to 'www-data'

```

sudo ./checksetup.pl   # yes, again

```

Then edit /etc/apache/httpd.conf and make sure you have something like the following:
```

<Directory /var/www/bugzilla>
        AddHandler cgi-script .cgi
        Options +Indexes +ExecCGI
        DirectoryIndex index.cgi
        AllowOverride Limit
</Directory>

```

Then restart apache:
```

sudo /etc/init.d/apache restart

```

and take your browser to [http://127.0.0.1/bugzilla/](http://127.0.0.1/bugzilla/)

---

