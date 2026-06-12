---
title: "php mail function in ubuntu"
date: 2010-11-20
forum: Desktop Environments
---

### Post by hemi519 on 2010-11-20
Hi All,

I dont no if this is place to ask this question but my pblm arrised by using Ubuntu so iam here.




I was using PHP mail function in windows it was working fine with the code i wrote. Now i shifted to UBUNTU. But that code is not able to send mail here.I installed sendmail but there is no result. here is errors it is giving in /var/www/root when i tried to send mail



From root@xxxxx-desktop Sat Nov 20 14:36:02 2010
Return-Path: <root@xxxxx-desktop>
Received: from xxxxx-desktop (localhost [127.0.0.1])
by xxxxx (8.14.3/8.14.3/Debian-9.1ubuntu1) with ESMTP id oAK961mF010585
for <root@xxxxx-desktop>; Sat, 20 Nov 2010 14:36:01 +0530
Received: (from root@localhost)
by xxxxx-desktop (8.14.3/8.14.3/Submit) id oAK961Yf010475
for root; Sat, 20 Nov 2010 14:36:01 +0530
Date: Sat, 20 Nov 2010 14:36:01 +0530
Message-Id: <201011200906.oAK961Yf010475@xxxxx-desktop>
From: root@xxxxx-desktop (Cron Daemon)
To: root@xxxxx-desktop
Subject: Cron <root@xxxxx-desktop> [ -d /usr/share/dtc/admin ] && cd /usr/share/dtc/admin && /usr/bin/php /usr/share/dtc/admin/stat_total_active_prods.php 2>&1 >> /var/log/dtc.log
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>

PHP Deprecated: Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning: require(../shared/mysql_config.php): failed to open stream: No such file or directory in /usr/share/dtc/shared/autoSQLconfig.php on line 109
PHP Fatal error: require(): Failed opening required '../shared/mysql_config.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/dtc/shared/autoSQLconfig.php on line 109




this is my code from PHP mail

Iam getting all the values for DB.

$To =$var['email'];


$Subject = "EDIT YOUR POST";


$Reply = "$var[email]";





$From= "abc.com";


$Body="";



if(mail($To,$Subject,$Body,"From:$From\r\nReply-to: $From\r\nContent-type: text/html; charset=us-ascii"))
{

echo"message is sent";
header("Location:reg.php");
exit();
}

When i submit my form page is displaying "Message is sent" but no redirecting to reg.php or no mail is thr in my gmail


__________________________________
i cahnged my php.ini file 

sendmail_path = /usr/sbin/sendmail -t -i

but still it is not wirking to me
__________________________________

---

