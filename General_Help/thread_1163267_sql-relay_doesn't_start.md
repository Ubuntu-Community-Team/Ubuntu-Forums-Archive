---
title: "sql-relay doesn't start"
date: 2009-05-18
forum: General Help
---

### Post by cvielma on 2009-05-18
Hi there!

Well i'm trying to connect to MS SQL Server from Ubuntu 8.04.  It is tell that it must been done with FreeTDS and sqlrelay. 

I have installed: 

[LIST]
[*]freetds-dev
[*]gda2-freetds
[*]libdbd-freetds
[*]libgda3-freetds
[*]sqlrelay-freetds
[*]libsqlrelay-0.38
[*]sqlrelay
[*]sqlrelay-dev
[*]sqlrelay-mdb
[*]sqlrelay-odbc
[/LIST]
In the file /etc/sqlrelay.conf, i have:

<?xml version="1.0"?>
<!DOCTYPE instances SYSTEM "sqlrelay.dtd">

<instances>

    <!-- Regular SQL Relay Instance -->
    <instance id="defaultid" port="9000" socket="/tmp/example.socket" dbase=**"freetds"** connections="3" maxconnections="15" maxqueuelength="5" growby="1" ttl="60" endofsession="commit" sessiontimeout="600" **runasuser="www-data" runasgroup="www-data"** cursors="5" authtier="listener" handoff="pass" deniedips="" allowedips="" debug="listener_and_connection" maxquerysize="65536" maxstringbindvaluelength="4000" maxlobbindvaluelength="71680" idleclienttimeout="-1" maxlisteners="-1" listenertimeout="0">
        <users>
           ** <user user="myuser" password="mypassword"/>**            
        </users>
        <connections>
           ** <connection connectionid="db1" string="Sybase=/etc/freetds/;user=myuser;password=mypassword; Server=MyServer2k;db=Goldmine>;" metric="1" behindloadbalancer="no"/>**        
        </connections>
    </instance>

    
</instances>

Then i run:
**sudo sqlr-start**

And it returns to me:
**Could not listen on unix socket: /var/cache/sqlrelay/tmp/sockets/defaultid-handoff**

I have followed [this]("http://plone.org/documentation/how-to/ms-sql-server-on-linux") and [this]("http://sqlrelay.sourceforge.net/sqlrelay/configuring.html") to configure the connection. Some documentation has been outdated and i could'nt find at least some other guy with the same problem or some FAQ in somewhere, so i'm sorry to bother you :S

Thanks in advance.

Greetings!

---

### Post by DonQuichote on 2009-05-29
I have a similar problem problem, but with an sqlite database. My /etc/sqlrelay/sqlrelay/conf reads:
```
<?xml version="1.0"?>
<!DOCTYPE instances SYSTEM "sqlrelay.dtd">
<instances>
  <instance id="sqlrelaytest" port="9000" socket="/tmp/sqlrelaytest.socket" dbase="sqlite" connections="3" maxconnections="5" maxqueuelength="0" growby="1" ttl="60" endofsession="commit" sessiontimeout="600" runasuser="sqlrelaytest" runasgroup="sqlrelaytest" cursors="5" authtier="listener" handoff="pass">
    <users>
      <user user="sqlrelaytest" password="test"/>
    </users>
    <connections>
      <connection connectionid="sqlrelaytest" string="db=/home/sqlrelaytest/sqlrelaytest.sqlite" metric="1"/>
    </connections>
  </instance>
</instances>

```

When I start sqlrelay:
```
sudo sqlr-start -id sqlrelaytest
```

It fails:
```
Starting listener:
  sqlr-listener -id sqlrelaytest -config /etc/sqlrelay/sqlrelay.conf
Could not listen on unix socket: /var/cache/sqlrelay/tmp/sockets/sqlrelaytest-handoff
Make sure that the file and directory are readable and writable.


sqlr-listener failed to start.
```

The SqlRelay site does not say anything about this and I do not understand any bit why the socket would not be created where I configure it (in /tmp/sqlrelaytest.socket). Is there anybody who can get sqlrelay working? The database file exists and is owned by user sqlrelaytest.

---

### Post by DonQuichote on 2009-05-29
There was a remark somewhere that sqlrelay will not start **AT ALL** if you do not have any instances defined (in /etc/sqlrelay/instances). So after defining the instance, I restarted the sqlrelay daemon:
```
sudo /etc/init.d/sqlrelay restart
```
But now it complains it cannot fall back to the sqlrelaytest user and therefore cannot read the database file :(
```
Stopping SQL Relay ....
Starting SQL Relay ... 
Starting listener:
  sqlr-listener -id sqlrelaytest -config /etc/sqlrelay/sqlrelay.conf
Warning: could not change group to sqlrelaytest
Warning: could not change user to sqlrelaytest

Starting 3 connections to sqlrelaytest :
  sqlr-connection-sqlite -id sqlrelaytest -connectionid sqlrelaytest -config /etc/sqlrelay/sqlrelay.conf
Warning: could not change group to sqlrelaytest
Warning: could not change user to sqlrelaytest
file is encrypted or is not a database
Couldn't log into database.

sqlr-connection-sqlite failed to start.
```

---

