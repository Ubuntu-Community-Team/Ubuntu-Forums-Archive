---
title: "Php not running on Ub 8.10 Server on port 80 . . ."
date: 2009-01-21
forum: General Help
---

### Post by deltaniner on 2009-01-21
1. I am able to invoke ISPConfig & Phpmyadmin  using port 81 - obviously php works there

2. I am not able to get php to parse using a browser with the normal port (80)

3. In terminal I ran the following, all replying that the relevant service was running:
 a2enmod php5, ssl, rewrite, suexec and iclude

4. Also ran  /etc/init.d/apache2 restart and force-reload

5. I cleared the entire history in my browser

6. Still get only the .php file contents when running from the browser.  it is obviously not parsing the file contents.

<?php phpinfo(); ?>


7. index.html performs as expected.

8. Checked permissions and ownership of files & directories, as indicated.

root@server2:/var/www/web1# ls -l
total 1940
drwxrwxr-x  2 web1_seb21051 web1    4096 2009-01-16 06:56 cgi-bin
drwxrwxr-x  3 web1_seb21051 web1    4096 2009-01-16 06:56 ftp
-rw-r--r--  1 root          root     686 2009-01-20 05:21** index.html**
drwxr-xr-x  2 web1_seb21051 web1    4096 2009-01-16 06:56 log
drwxr-xr-x 31 web1_seb21051 web1    4096 2009-01-19 08:22 phprojekt
-rw-r--r--  1 web1_seb21051 web1 1940852 2009-01-19 08:09 phprojekt.tar.gz
drwxrwxrwx  2 web1_seb21051 web1    4096 2009-01-16 06:56 phptmp
drwxr-xr-x  2 web1_seb21051 web1    4096 2009-01-16 06:56 ssl
-rw-r--r--  1 web1_seb21051 web1      20 2009-01-20 05:10 **testphp.php**
drwxr-xr-x  3 web1_seb21051 web1    4096 2009-01-16 06:59 user
drwxrwxr-x  4 web1_seb21051 web1    4096 2009-01-18 04:00 web

9. Checked to see what ports are listening:

root@server2:/var/www/web1# netstat -lpt 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN      4881/mysqld     
tcp        0      0 *:sunrpc                *:*                     LISTEN      4391/portmap    
tcp        0      0 *:www                   *:*                     LISTEN      5899/apache2    
tcp        0      0 *:81                    *:*                     LISTEN      5708/ispconfig_http
tcp        0      0 192.168.1.3:domain      *:*                     LISTEN      6024/named      
tcp        0      0 localhost.locald:domain *:*                     LISTEN      6024/named      
tcp        0      0 *:ssh                   *:*                     LISTEN      4791/sshd       
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN      5179/cupsd      
tcp        0      0 server2.exam:postgresql *:*                     LISTEN      5017/postgres   
tcp        0      0 localhost.lo:postgresql *:*                     LISTEN      5017/postgres   
tcp        0      0 *:smtp                  *:*                     LISTEN      23113/master    
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN      6024/named      
tcp        0      0 *:https                 *:*                     LISTEN      5899/apache2    
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      5116/couriertcpd
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      5154/couriertcpd
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      5132/couriertcpd
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      5094/couriertcpd
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN      6045/proftpd: (acce
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      4791/sshd       
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      23113/master    
tcp6       0      0 localhost:953           [::]:*                  LISTEN      6024/named      

root@server2:/var/www/web1# netstat -an |grep :80 
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        1      1 192.168.1.3:53771       69.72.169.241:80        LAST_ACK   
tcp        1      1 192.168.1.3:53773       69.72.169.241:80        LAST_ACK   
tcp        1      1 192.168.1.3:53774       69.72.169.241:80        LAST_ACK   

I am at a loss as to how to fix this problem, anyone out there have some advice?

---

### Post by deltaniner on 2009-01-21
Solved the problem . . . thanks to:

[http://www.wowwebdesigns.com/power_guides/killer_trio_part_2.php#s2.4](http://www.wowwebdesigns.com/power_guides/killer_trio_part_2.php#s2.4)

The first thing to do is to edit the Apache configuration file (httpd.conf) because PHP needs Apache to run. The configuration file is found in the conf directory of Apache. /usr/local/apache/conf under Unix.

Add the following line, and restart your apache:

 AddType application/x-httpd-php .php 

 run /usr/local/apache/bin/apachectl restart).

Test whether PHP is running correctly. Create a file in the directory where you serve HTML documents that has the following line in it:

      <?php phpinfo() ?>

---

