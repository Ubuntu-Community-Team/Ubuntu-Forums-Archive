---
title: "rm -rf'ed my /usr/local directory"
date: 2009-05-28
forum: General Help
---

### Post by mrfnuts on 2009-05-28
I thought I was in another directory...long story...

It seems I have no 'undelete' option for ext3 file system....

So, my question, is, how do I 're-install' the native stuff that should be there when one installs Ubuntu?  (v 9.04 if it matters).

---

### Post by kpkeerthi on 2009-05-28
Do you have a backup?

---

### Post by x33a on 2009-05-28
you are lucky as it is not a very important directory.

at least in my case, there are no files under /usr/local.

in the future, be careful.

and there is no undelete option for rm. if you delete stuff from nautilus, then it goes to the recycle bin, though.

---

### Post by mrfnuts on 2009-05-31
Unfortunately no backup.

I had installed my 32-bit firefox there, which I have hence  re-installed.

But, I was wondering what other stuff should be there (i.e. if I just went and ran a fresh install of Ubuntu, what would end up in that directory?)

---

### Post by kaibob on 2009-05-31
> **mrfnuts said:**
> ...But, I was wondering what other stuff should be there (i.e. if I just went and ran a fresh install of Ubuntu, what would end up in that directory?)

I checked the /usr/local directory, and it contained a lot of subdirectories but only one file (mimeinfo.cache).

```
$ find /usr/local -type f
/usr/local/share/applications/mimeinfo.cache
```

---

### Post by asmoore82 on 2009-05-31
My /usr/local in 9.04 Jaunty, pretty bare:

```
**ls -RAl /usr/local**
/usr/local:
total 32
drwxr-xr-x  2 root root 4096 2009-03-23 19:55 bin
drwxr-xr-x  2 root root 4096 2009-03-23 19:55 etc
drwxr-xr-x  2 root root 4096 2009-03-23 19:55 games
drwxr-xr-x  2 root root 4096 2009-03-23 19:55 include
drwxr-xr-x  5 root root 4096 2009-05-14 08:30 lib
lrwxrwxrwx  1 root root    9 2009-05-09 02:22 man -> share/man
drwxr-xr-x  2 root root 4096 2009-03-23 19:55 sbin
drwxr-xr-x 11 root root 4096 2009-05-09 23:45 share
drwxr-xr-x  2 root root 4096 2009-03-23 19:55 src

/usr/local/bin:
total 0

/usr/local/etc:
total 0

/usr/local/games:
total 0

/usr/local/include:
total 0

/usr/local/lib:
total 12
drwxrwsr-x 3 root staff 4096 2009-05-14 08:30 python2.5
drwxrwsr-x 4 root staff 4096 2009-05-09 23:38 python2.6
drwxr-xr-x 3 root root  4096 2009-05-11 00:24 site_ruby

/usr/local/lib/python2.5:
total 4
drwxrwsr-x 2 root staff 4096 2009-05-14 08:30 site-packages

/usr/local/lib/python2.5/site-packages:
total 0

/usr/local/lib/python2.6:
total 8
drwxrwsr-x 2 root staff 4096 2009-03-23 19:56 dist-packages
drwxrwsr-x 2 root staff 4096 2009-05-09 23:38 site-packages

/usr/local/lib/python2.6/dist-packages:
total 0

/usr/local/lib/python2.6/site-packages:
total 0

/usr/local/lib/site_ruby:
total 4
drwxr-xr-x 3 root root 4096 2009-05-11 00:24 1.8

/usr/local/lib/site_ruby/1.8:
total 4
drwxrwsr-x 2 root staff 4096 2009-05-11 00:24 i486-linux

/usr/local/lib/site_ruby/1.8/i486-linux:
total 0

/usr/local/sbin:
total 0

/usr/local/share:
total 36
drwxr-xr-x 2 root root  4096 2009-05-29 09:33 applications
drwxr-xr-x 2 root root  4096 2009-03-23 20:12 desktop-directories
drwxrwsr-x 2 root staff 4096 2009-03-23 20:03 fonts
drwxr-xr-x 3 root root  4096 2009-03-23 20:12 icons
drwxr-xr-x 2 root root  4096 2009-03-23 19:55 man
drwxr-xr-x 3 root root  4096 2009-03-23 20:12 mime
drwxrwsr-x 2 root staff 4096 2009-05-09 23:45 ppd
drwxrwsr-x 7 root staff 4096 2009-03-23 20:02 sgml
drwxrwsr-x 6 root staff 4096 2009-03-23 20:02 xml

/usr/local/share/applications:
total 4
-rw-r--r-- 1 root root 13 2009-05-29 09:33 mimeinfo.cache

/usr/local/share/desktop-directories:
total 0

/usr/local/share/fonts:
total 0

/usr/local/share/icons:
total 4
drwxr-xr-x 2 root root 4096 2009-03-23 20:12 hicolor

/usr/local/share/icons/hicolor:
total 0

/usr/local/share/man:
total 0

/usr/local/share/mime:
total 4
drwxr-xr-x 2 root root 4096 2009-03-23 20:12 packages

/usr/local/share/mime/packages:
total 0

/usr/local/share/ppd:
total 0

/usr/local/share/sgml:
total 20
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 declaration
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 dtd
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 entities
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 misc
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 stylesheet

/usr/local/share/sgml/declaration:
total 0

/usr/local/share/sgml/dtd:
total 0

/usr/local/share/sgml/entities:
total 0

/usr/local/share/sgml/misc:
total 0

/usr/local/share/sgml/stylesheet:
total 0

/usr/local/share/xml:
total 16
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 declaration
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 entities
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 misc
drwxrwsr-x 2 root staff 4096 2009-03-23 20:02 schema

/usr/local/share/xml/declaration:
total 0

/usr/local/share/xml/entities:
total 0

/usr/local/share/xml/misc:
total 0

/usr/local/share/xml/schema:
total 0

/usr/local/src:
total 0
```

---

### Post by asmoore82 on 2009-05-31
here(attached) is a tar archive of my bare /usr/local

you could restore yours with the proper ownerships/permissions like this:
```
sudo tar xzvf usr.local.tar.gz -C /usr/local
```

---

