---
title: "Official oracle-xe-client_10.2.0.1-1.0_i386.deb works like charm"
date: 2006-03-11
forum: Desktop Environments
---

### Post by rverrips on 2006-03-11
Hiyee

I've been waiting for an official .deb of the Oracle client for my dual-boot laptop for a while now - At the moment I switch to my Windows partition to use an oracle client to connect the my DB's 'cause I can't be bothered to hack around linux for a stable oracle client which seems to be packaged only to run on RedHat or Suse, but today saw that Oracle have release an official deb of the client on [http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html](http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html)

However, when I try install it on "Breezy", I get the folllowing error:

Executing Post-install steps..........

```
chmod: cannot access `/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/sqlplus': No such file or directory
cat: /usr/lib/oracle/xe/app/oracle/product/10.2.0/client/scripts/oraclexe-client-merge.menu: No such file or directory
cat: /usr/lib/oracle/xe/app/oracle/product/10.2.0/client/scripts/oraclexe-client-merge.menu: No such file or directory

```

All that was needed was to uninstall the package and re-install it (weird hey?)
```

@sudo dpkg -r oracle-client-xe 
@sudo dpkg -i oracle-xe-client_10.2.0.1-1.0_i386.deb

```

It creates menu in applications and drops in a launcher for sqlplus as well as some links documentations at oracle.com

As I spend most of my life in the console I also did this symlink so sqlplus runs from anywhere

```

@sudo ln -s /usr/lib/oracle/xe/app/oracle/product/10.2.0/client/scripts/sqlplus.sh /usr/bin/sqlplus

```

Once that's done, I can simply type sqlplus anywhere in my console (or select the launcher) and I'm good.  

Interesting is that sqlplus by default starts up without a connection (i.e. sqlplus /nolog) - Further, I can't seem to find a tnsnames.ora anywhere in the client installation.  Not sure if this is the limitation of the Express client or something I've done wrong?

Anyway, to connect one thus needs the full connection string with instance hostname or ip as follows:

```

SQL>conn username/password@hostname/instance

```
i.e.
```

SQL>conn scott/tiger@192.168.0.1/mydb

```
or
```

SQL>conn scott/tiger@mydbserver/mydb

```

This package sure makes Oracle Database Admin a lot easier.

---

### Post by akiro.yamamoto on 2006-03-11
Thanks! Now that's cool ;)

---

