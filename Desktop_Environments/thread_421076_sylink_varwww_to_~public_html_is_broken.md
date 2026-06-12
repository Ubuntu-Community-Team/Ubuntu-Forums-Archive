---
title: "sylink /var/www/ to ~/public_html is broken"
date: 2007-04-24
forum: Desktop Environments
---

### Post by jammodotnet on 2007-04-24
Just upgraded from Edgy Eft 6.10 to the Feisty Fawn 7.04.
All is well, except ... 

everything was installed manually over a month ago via the tutorial here: 
i have php 5.2.1 + mysql 5.0.38 + apache 2 installed.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Since my update to Feisty Fawn, my localhost is not properly responding.
what i mean is, i know that **/var/www** = root for my localhost.
**/home/jammo/public_html** = where i have all my files.

Previously, I had some link connecting the two.
Now, the link has been broken, and I've tried every variation I know of to reconnect the two.

ie: i want to save files at **/home/jammo/public_html** and have them available at:
[http://localhost/jammo/](http://localhost/jammo/) which = **/var/www/jammo**

But everytime I run:
$ ln -s /home/jammo/public_html /var/www/jammo
I get a /public_html folder inSIDE /var/www/jammo ... i dont want that.

what i need is for /var/www/jammo to equal the contents of /home/jammo/public_html

Am I dense?
I must have overlooked something here tonight.
:(
Forgive me for overlooking the obvious.

---

### Post by lloyd_b on 2007-04-24
Try this:

```
rm /var/www/jammo
ln -s /home/jammo/public_html /var/www/jammo
```

(note: you may need "sudo" in front of the commands - it depends on the permissions settings for "/var/www").

Lloyd B.

---

### Post by jammodotnet on 2007-04-24
> **lloyd_b said:**
> Try this:

```
rm /var/www/jammo
ln -s /home/jammo/public_html /var/www/jammo
```

(note: you may need "sudo" in front of the commands - it depends on the permissions settings for "/var/www").

Lloyd B.tried that.
it gives me a :

```
**Forbidden**
You don't have permission to access /jammo on this server.
```

error.

---

### Post by mlind on 2007-04-24
btw. why don't you use apache2 userdir module (which should be enabled by default). Your public_html is automatically aliased as [http://localhost/~jammo/](http://localhost/~jammo/)

---

### Post by jammodotnet on 2007-04-24
> **mlind said:**
> btw. why don't you use apache2 userdir module (which should be enabled by default). Your public_html is automatically aliased as [http://localhost/~jammo/](http://localhost/~jammo/)

i dont know about the module thingie.
if its enabled by default.

i went to [http://localhost/~jammo/](http://localhost/~jammo/) only to get the same error. :(

---

### Post by mlind on 2007-04-24
Try this
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 force-reload

```

I think your ~/public_html must be "word executable"
```

chmod +x ~/public_html

```

You should remove the symlink you created manually.

---

### Post by jammodotnet on 2007-04-24
> **mlind said:**
> Try this
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 force-reload

```

I think your ~/public_html must be "word executable"
```

chmod +x ~/public_html

```

You should remove the symlink you created manually.

i do:
```
sudo a2enmod userdir
```
i get:
```
This module is already enabled!
```

i also did:
```
chmod +x ~/public_html
```

[http://localhost/~jammo/](http://localhost/~jammo/) = 403
[http://localhost/jammo/](http://localhost/jammo/) = 404

---

### Post by mlind on 2007-04-24
~/public_html must be be "world readable" too
```

chmod +r ~/public_html

```

/edit
I forgot the important part, you home directory must be "world executable"
```

chmod +x ~/

```

---

### Post by jammodotnet on 2007-04-24
> **mlind said:**
> ~/public_html must be be "world readable" too
```

chmod +r ~/public_html

```

arrggh, captain.
this is frustrating.
everything else works after updating to feisty fawn. im excited to get the new Tomboy Notes.

this is my only issue right now.
cant get it to work.
:(

---

### Post by mlind on 2007-04-24
> **jammodotnet said:**
> arrggh, captain.
this is frustrating.
everything else works after updating to feisty fawn. im excited to get the new Tomboy Notes.

this is my only issue right now.
cant get it to work.
:(

Yeah I know :mrgreen:
Setting your home directory "world executable" should do it though, did you try it yet (I edited my last post) ?

---

### Post by jammodotnet on 2007-04-24
> **mlind said:**
> 
Setting your home directory "world executable" should do it though, did you try it yet (I edited my last post) ?

yes sir.
i did:
```

chmod +r ~/public_html
chmod +x ~/public_html

```
how bout this.

to avoid any confusion, we/i start over?

i remove /var/www/jammo
i got a terminal open.

:(
now what?

---

### Post by mlind on 2007-04-24
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 restart
mkdir -p ~/public_html
chmod +rx ~/public_html
chmod +x ~/
firefox http://localhost/~$USER

```

?

---

### Post by jammodotnet on 2007-04-24
The weirdest thing happen?!?!?!

it works.
sorta ... (arrggh yet again!)

I got one folder that is still inaccessible. but i think i learned enough today to be able to chmod it properly.
its giving me a 500 error.

THANK YOU tremendously mlind!!!

---

### Post by mlind on 2007-04-24
> **jammodotnet said:**
> The weirdest thing happen?!?!?!

it works.
sorta ... (arrggh yet again!)

I got one folder that is still inaccessible. but i think i learned enough today to be able to chmod it properly.
its giving me a 500 error.

THANK YOU tremendously mlind!!!

no problem. You should be able to resolve error 500 by looking log files in /var/log/apache2/

---

### Post by TACtech on 2007-04-29
hi guys 

I does not work for me. 
I get 404 NOT FOUND error when trying to access [http://localhost/~myusername](http://localhost/~myusername).

I've tried enabling userdir module that was already enabled,
 reloaded apache2 and recreated public_html folder with permission set mention earlier in the posts.
I also created another system user with new public_html folder with the same results 404 NOT FOUND.

Any Ideas how to fix this?

My apache2 has these modules enabled

 *Apache/2.2.3 (Ubuntu) DAV/2 PHP/5.2.1 mod_ruby/1.2.6 Ruby/1.8.5(2006-08-25) Server*

---

### Post by mlind on 2007-04-29
does using 127.0.0.1 instead of localhost result the same?

---

### Post by TACtech on 2007-04-29
Yes


[http://127.0.0.1/~tac](http://127.0.0.1/~tac)

Not Found

The requested URL /~tac was not found on this server.

---

### Post by mlind on 2007-04-29
Then either you don't have user named **tac** or you don't have **public_html** directory in your $HOME folder. You can refer to apache2 userdir module documentation [http://httpd.apache.org/docs/2.0/mod/mod_userdir.html](http://httpd.apache.org/docs/2.0/mod/mod_userdir.html)

---

### Post by TACtech on 2007-04-29
I do have both and that is the strangest thing  that userdir mod  is not working correctly.
As I mentioned earlier I created another system user test and logged in as one then created public_html.
tried to access public_html under test account thru [http://127.0.0.1/~test](http://127.0.0.1/~test) with the same results 404 NOT FOUND.

---

### Post by RichGuk on 2007-04-30
What does,

tail /var/log/apache2/error.log

give you?

---

### Post by TACtech on 2007-04-30
[Mon Apr 30 08:12:55 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac
[Mon Apr 30 08:12:58 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac
[Mon Apr 30 08:13:07 2007] [error] [client 127.0.0.1] File does not exist: /var/www/~tac
[Mon Apr 30 08:13:09 2007] [error] [client 127.0.0.1] File does not exist: /var/www/~tac

---

### Post by TACtech on 2007-04-30
drwxr-xr-x  4 tac  tac      4096 2007-04-30 09:21 public_html

---

### Post by RichGuk on 2007-04-30
And you have run 

```
sudo a2enmod userdir
```

And your home dir, /home/tac  has the right permissions?

```
sudo chmod 751 /home/tac
```

I currently have mine setup as

chmod 751 /home/rich/
chmod 755 /home/rich/public_html

---

### Post by TACtech on 2007-04-30
```
tac@sunrise:/home$ ls -l
total 20
drwx------  2 root root 16384 2007-04-22 15:53 lost+found
drwxr-xr-x 86 tac  tac   4096 2007-04-30 20:50 tac
```

```

drwxr-xr-x  4 tac  tac      4096 2007-04-30 09:21 public_html
```


```
tac@sunrise:/home$ a2enmod userdir
This module is already enabled!

```

```
[Mon Apr 30 20:54:19 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac
[Mon Apr 30 21:02:08 2007] [error] [client 127.0.0.1] File does not exist: /var/www/~tac

```

I know it should work but for some reason it DOESN'T :confused:

---

### Post by RichGuk on 2007-05-01
I know this might sound silly, but have you tried accessing the file directly?

[http://localhost/~tac/w00t.html](http://localhost/~tac/w00t.html)

And seeing if it works?

---

### Post by TACtech on 2007-05-01
```
[Tue May 01 21:03:08 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac
[Tue May 01 21:03:18 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac
[Tue May 01 21:03:21 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac
[Tue May 01 21:03:24 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac
[Tue May 01 21:04:04 2007] [error] [client 192.168.0.2] File does not exist: /var/www/~tac

```

same thing :confused:

---

### Post by RichGuk on 2007-05-02
Hmmm,

Does the root work /var/www ? Tried just putting a link in..

```
sudo ln -s /home/tac/public_html tac
```

and going to [http://localhost/tac](http://localhost/tac)

---

### Post by TACtech on 2007-05-02
yeah root /var/www works just fine
I am able to view anything in root

---

### Post by TACtech on 2007-05-02
I am going to try 

```
sudo ln -s /home/tac/public_html tac
```

later tonight.

---

### Post by mlind on 2007-05-02
TACtech, do you have /etc/apache2/mods-enabled/userdir.conf symlink that points to existing file ../mods-available/userdir.conf (/etc/apache2/mods-available/userdir.conf) ?

---

### Post by TACtech on 2007-05-02
Yes I do  I checked that as well .

---

### Post by mlind on 2007-05-02
I'm out of ideas then :( If you haven't customized your apache setup manually, it should work out of the box. I just tested with new user and mod_userdir worked without problems. Only thing I can point you to is the apache2.2 [userdir tutorial]("http://httpd.apache.org/docs/2.2/howto/public_html.html").

---

### Post by TACtech on 2007-05-02
I haven't customized my apache setup manually. I agree  it should work out of the box but for some reason it doesn't. I am out of ideas here too. Last one step I may go for is to complete remove apache2 and reinstall it back

---

### Post by RichGuk on 2007-05-02
I'd do that... just remove all of LAMP stuff and reinstall :D

---

### Post by TACtech on 2007-05-05
OK I removed purged everything that was apache2 related all the libapache2... etc

and then 


```
tac@sunrise:~$ sudo a2enmod
Which module would you like to enable?
Your choices are: actions alias asis auth_basic auth_digest auth_mysql authn_alias authn_anon authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_default authz_groupfile authz_host authz_owner authz_svn authz_user autoindex cache cern_meta cgid cgi charset_lite dav_fs dav dav_lock dbd deflate dir disk_cache dump_io dumpio env expires ext_filter file_cache filter headers ident imagemap include info ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http proxy rewrite ruby setenvif speling ssl status suexec unique_id userdir usertrack version vhost_alias
Module name? userdir
This module is already enabled!
tac@sunrise:~$ sudo a2dismod
Which module would you like to disable?
Your choices are: alias auth_basic authn_file authz_default authz_groupfile authz_host authz_user autoindex cgi dav dir env mime negotiation php5 setenvif status userdir
Module name? userdir
Module userdir disabled; run /etc/init.d/apache2 force-reload to fully disable.
tac@sunrice:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...                                                                 [ OK ] 
tac@sunrise:~$ sudo a2enmod userdir
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.
tac@sunrise:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...
```

and now  I'm home 

```
192.168.0.2 - - [05/May/2007:15:01:11 -0400] "GET /~tac/ HTTP/1.1" 200 36 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20070321 Firefox/2.0.0.3 (Swiftfox)"
127.0.0.1 - - [05/May/2007:15:08:39 -0400] "GET /~tac/ HTTP/1.1" 200 36 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20070321 Firefox/2.0.0.3 (Swiftfox)"

```

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) PROBLEM FIXED ! :guitar:

---

### Post by RichGuk on 2007-05-07
Good news, must of been something with apache's setup ;)

---

### Post by daybreaker on 2007-08-30
just wanted to give a shoutout to mlind, because none of the howto's anywhere actually said how to enable UserDir directive, they all just said "Oh, and to have public_html working, you shuold use UserDir"  but I'd have never figured out the a2enmod thing. Thanks!

---

