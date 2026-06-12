---
title: "php5 + apache+ postgresql8.1"
date: 2006-09-03
forum: Desktop Environments
---

### Post by hoodwink on 2006-09-03
Just setup my system for php5 and postgresql8.1, but 'pg_connect' function comes up as undefined. I've done quitea bit of googling, but found no answers. 'php_pgsql' does not appear as a loaded extension. No modifications to the apache2 setup since installation.

I'm on Kubuntu 6.06, completely current, and per dpkg, here's what's installed:

```
ii  libapache2-mod-php5              5.1.2-1ubuntu3.1                        
ii  php-pear                               5.1.2-1ubuntu3.1                        
ii  php5                                   5.1.2-1ubuntu3.1                        
ii  php5-cli                               5.1.2-1ubuntu3.1                        
ii  php5-common                            5.1.2-1ubuntu3.1                        
ii  php5-curl                              5.1.2-1ubuntu3.1                        
ii  php5-gd                                5.1.2-1ubuntu3.1                        
ii  php5-mysql                             5.1.2-1ubuntu3.1                        
ii  php5-mysqli                            5.1.2-1ubuntu3.1                        
ii  php5-pgsql                             5.1.2-1ubuntu3.1                        
ii  php5-sqlite                            5.1.2-1ubuntu3.1
ii  apache2-common                         2.0.55-4ubuntu2.1                       
ii  apache2-mpm-prefork                    2.0.55-4ubuntu2.1                       
ii  apache2-utils                          2.0.55-4ubuntu2.1                       
ii  libapache2-mod-php5                    5.1.2-1ubuntu3.1
ii  postgresql-8.1                         8.1.4-0ubuntu1                          
ii  postgresql-client-8.1                  8.1.4-0ubuntu1                          
ii  postgresql-client-common               53ubuntu3                               
ii  postgresql-common                      53ubuntu3                               
ii  postgresql-contrib-8.1                 8.1.4-0ubuntu1

```

Does anyone have a clue how to resolve the problem?

---

### Post by hoodwink on 2006-09-04
After many hours of googling, I found a hint that reinstalling the php5-pgsql package might help, so I did

apt-get install --reinstall php5-pgsql

Now php pg_xxx functions are working.

That's a super bummer that the package can't install itself properly.

HTH someone else.

---

### Post by stacktracer on 2006-12-12
Thanks for the tip! I was about to start pulling hair out.

---

### Post by runningduck on 2007-02-25
Here is a bit more info that solved my issue.

For some reason [FONT="Courier New"]extension=pgsql.so[/FONT] was added to [FONT="Courier New"]/etc/php5/apache2/php.ini[/FONT] instead of [FONT="Courier New"]/etc/php5/cgi/php.ini[/FONT] when installing.  Reinstalling [FONT="Courier New"]php5-pgsql[/FONT] did not correct the issue for me.  I had to manually append the correct file.  

I am guessing that there were some changes to the default install locations and there is some lingering issues out there.

-rd

---

