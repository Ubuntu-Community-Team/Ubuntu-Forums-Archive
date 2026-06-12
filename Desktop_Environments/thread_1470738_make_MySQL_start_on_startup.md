---
title: "make MySQL start on startup"
date: 2010-05-03
forum: Desktop Environments
---

### Post by YongQing on 2010-05-03
I run Ubuntu 10.04. For some reason, MySQL won't start on startup. How do I make it run on startup?

More info:
I installed it by installing LAMP using tasksel and did everything according to: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Also, I have another problem:
When I try to start/stop/restart mysql in the terminal, the terminal will not give me any prompts after entering the command.
For eg, after entering "sudo service mysql start", nothing will happen. Even after waiting for 30min, nothing happens. I have no idea what's the prob.

---

### Post by scintilla on 2010-05-04
I have the same problem after upgrading to Ubuntu 10.04.  Mysql worked fine under 9.10 but now it doesn't start automatically. 
If I start it at a console using sudo start mysql,  it just hangs as described above (never returns from the command)
However if I start it using sudo mysqld, then it does start and works fine - until I restart the system.

* Update * I changed the bind-address in /etc/mysql/my.cnf back to 127.0.0.1 - this makes it work ok.
However I need the bind-address to be my server's real IP address for remote access to the database from mythtv - so problem only half way solved.   Now I need to understand why mysql won't start when bind-address is set to something other than 127.0.0.1

Any ideas?

---

### Post by YongQing on 2010-05-04
awesome. so i'm not the only one...

btw, if i enter "sudo mysqld", i get nothing as weel. but mysql does start up. so it's a partial win i guess

---

### Post by _0R10N on 2010-05-04
What you have to do is run the following command
```
sudo update-rc.d mysql defaults
```
That will start MySQL when the system enters in any of the default runlevels
If you want to stop the automatic start of MySQL, later, then run:
```
sudo update-rc.d -f mysql remove
```
Kind regards!

---

### Post by YongQing on 2010-05-05
> **_0R10N said:**
> What you have to do is run the following command
```
sudo update-rc.d mysql defaults
```
That will start MySQL when the system enters in any of the default runlevels
If you want to stop the automatic start of MySQL, later, then run:
```
sudo update-rc.d -f mysql remove
```
Kind regards!
i get this when i update rc.d:
```
update-rc.d: warning: /etc/init.d/mysql missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/mysql already exist.
```

before you replied, i already figured that the system is already configured to boot MySQL at start.

the problem is: MySQL does not start properly, as discussed with scintilla. manually starting, stopping or restarting MySQL does not give any prompts/response/progress.

---

### Post by TrippleDubs on 2010-05-11
you have to just manually start mysql by using sudo mysqld 

The way services start now is totally different. Not sure if update-rc.d is even relevant anymore. 

In /etc/init the mysql.conf is how it boots but apparently if eth0 is not all the way up, mysql will not start

---

### Post by scintilla on 2010-05-12
TrippleDubs, thanks for your feedback, this could explain why mysql starts OK when the bind-address is set to 127.0.0.1 but it doesn't start when it's set to the real IP address.  

It looks as if the changes to speed up the startup times have decoupled the eth0 activation from the rest of the startup - the startup scripts no longer wait for eth0 to be ready (I can see this as sometimes when I logon my IM client complains there is no internet connection).

So we await a fix to the startup.  In the meantime there seem to be two workarounds:
1.  set the bind-address in /etc/mysql/my.cnf to 127.0.0.1  (this may cause problems with remote access to the mysql server)
2.  start mysql manually (my suggestion was to start via sudo mysql, which then starts mysqld in background, but you can also start via sudo mysqld directly or you could start via sudo mysql& I think - this should start mysql directly as a background task)

---

### Post by colascdave on 2010-05-17
I haven't figured out the startup problem, but I'm also running mythtv and fixed the bind-address problem in /etc/mysql/my.cnf by simply commenting-out the bind-address = line.

> **scintilla said:**
> I have the same problem after upgrading to Ubuntu 10.04.  Mysql worked fine under 9.10 but now it doesn't start automatically. 
If I start it at a console using sudo start mysql,  it just hangs as described above (never returns from the command)
However if I start it using sudo mysqld, then it does start and works fine - until I restart the system.

* Update * I changed the bind-address in /etc/mysql/my.cnf back to 127.0.0.1 - this makes it work ok.
However I need the bind-address to be my server's real IP address for remote access to the database from mythtv - so problem only half way solved.   Now I need to understand why mysql won't start when bind-address is set to something other than 127.0.0.1

Any ideas?

---

### Post by colascdave on 2010-05-17
OK, fixed the startup problem too from post #1 item 10 on this thread:

[http://ubuntuforums.org/showthread.php?t=1475798](http://ubuntuforums.org/showthread.php?t=1475798)

change the start condition in /etc/init/mysql.conf to "start on (net-device-up IFACE=ethX)", where "X" is the interface you have mysql bound to, e.g. ETH0.

---

### Post by gerryg001 on 2010-05-25
Yup, this appears to be an old problem that's come back with a twist. As mentioned above, the problem is trying to start mysqld before the related network interface is up. The twist which causes some varying results is:

> gerryg@taka:/var/log/mysql$ status mysql
mysql respawn/post-start, (post-start) process 1024

The process hung there is from the upstart script:
> post-start script
    while ! /usr/bin/mysqladmin --defaults-file=$HOME/debian.cnf ping
    do
        sleep 1
    done
    exec $HOME/debian-start
end script


If I kill process 1024, then mysqld is running with no further action. Further, "start|stop mysql" now works normally.

Otherwise, various start|stop (or the old /etc/init.d/mysql start, which now links to the new stuff anyway) may not work. Try other things and they may fail, or it may start working normally. That (and timing differences) are why some other posts have shown varying symptoms.

I really don't think you should be tying mysql to a specific network interface. If that changes for whatever reason, a year from now you'll be scratching around for whatever happened. However, the old solution of moving the startup order for mysql later in the boot may not work anymore, due to the speeded up boot process.

And, using a mysql bind address of 127.0.0.1 is not too useful if you need to reach mysqld from other machines.

I need to see if there's a better "start on (net-device-up..." that can be used here. That might be the simplest way.

---

### Post by sebeticus on 2010-05-31
Has anyone solved this problem?  When I bind mysql to a real IP address, this problem occurs.  mysql will not start on boot nor will it start when I try to manually start it with sudo /etc/init.d mysql start or with sudo service mysql start.  With etc/init.d/mysql the command executes but mysqld doesn't start.  With service start mysql, it just hangs forever but never starts.  This is a pain.  Any help?

---

### Post by gerryg001 on 2010-06-01
Several things can cause this. Check colascdave post for a workaround on mysqld trying to start before the network is ready.

From what you gave, there may be a service process hung, as I described earlier. Try starting:
  > sudo mysqld &
and see if it will start and work. If not, check your IP in /etc/mysql/my.cnf. If an IP, verify it's valid. If a name, make sure either your router or /etc/hosts provides the IP.

Check for existence of /var/run/mysql/mysqld.sock. This is created by mysqld daemon when it runs. Check pgrep -l mysql.

Be aware that > sudo /etc/init.d mysql start will actually invoke > sudo service mysql start in Lucid so they are not two different ways to start mysql.

I now have several servers running with that workaround from colascdave. Not pretty, but it works reliably. In each case, my my.cnf bind-address is the machine name and external access to mysql is working.

---

### Post by kainos on 2010-07-26
There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/610085](https://bugs.launchpad.net/ubuntu/+bug/610085)

---

### Post by gerryg001 on 2010-07-26
Thank you for mentioning that, kainos. I added more detail to that bug report.
[https://bugs.launchpad.net/ubuntu/+bug/610085](https://bugs.launchpad.net/ubuntu/+bug/610085)

---

### Post by v1ad on 2010-07-26
this is what i do.

```

sudo apt-get install chkconfig

chkconfig mysql on


```

---

### Post by gerryg001 on 2010-07-26
v1ad, there are several possible issues that can prevent the mysqld daemon from running at boot. Any solution is only good for the particular problem it addresses, and you need to understand both the problem and how you are trying to solve it. If you read the chkconfig man page:

> chkconfig  is  used  to  manipulate  the  runlevel links at boot time 

This is similar to sysv-rc-conf. If I try your approach on my system:

> The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'mysql' missing LSB tags and overrides
insserv: exiting now without changing boot order!

If you are running earlier than Lucid 10.04, the results would differ. Here, we have the interaction with upstart. In my Lucid system, chkconfig shows "mysql off", yet mysql does start at boot and is running.

I suspect your system simply never flagged mysql to start at boot, due to some error during installation. Using either chkconfig or sysv-rc-conf would correct this, but have no bearing on the other issues raised here.

---

### Post by kainos on 2010-07-26
> **gerryg001 said:**
> Thank you for mentioning that, kainos. I added more detail to that bug report.
[https://bugs.launchpad.net/ubuntu/+bug/610085](https://bugs.launchpad.net/ubuntu/+bug/610085)

Thanks!! I just filed that this AM after spending a couple hours getting a temporary workaround.

---

