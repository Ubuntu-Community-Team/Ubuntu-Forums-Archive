---
title: "Bash script to enter data into database"
date: 2009-03-13
forum: General Help
---

### Post by t0p on 2009-03-13
I want to periodically log network connection speed.  So, I think I'll write a script that performs **iptotal** to get the connection speed, then writes that data and the time to a database.  Then I can make a cronjob to run the script periodically.

I know how to get a script to write this data to a text file, but I don't know how to make it write to a database.  Can someone enlighten me to the commands I need?  I've got sqlite and sqlite3 installed on my machine.  Should I use one of them?

---

### Post by heindsight on 2009-03-13
well, firstly iptotal doesn't give the connection speed, it "measures IP bandwidth usage".

I personally think you'd be much better off just writing your data to a text file. 

If you really want it in a database, how you achieve it will depend entirely on what type of database you want.

EDIT:
Sorry, my bad. I missed the part about sqlite in your post :(

---

### Post by aeiah on 2009-03-13
inserting, retrieving and manipulating data in sqlite is really easy in python. [this would probably be all you'd need](http://www.devshed.com/c/a/Python/Using-SQLite-in-Python/) but of course you're talking about bash scripting and not python...


it seems like its really simple though. the only quick result i got was [this](http://mailliststock.wordpress.com/2007/03/01/sqlite-examples-with-bash-perl-and-python/)

---

### Post by lovinglinux on 2009-03-13
sqlite and sqlite3 are awesome and they will do the job.

First you need to create the database and tables. An easy way to do this is using  [SQLite Manager]("https://addons.mozilla.org/en-US/firefox/addon/5817") extension for Firefox or the standalone sqlitebrowser.

```
sudo apt-get install sqlitebrowser
```

Once you have the database and the tables, you can insert values this way:

```
#!/bin/bash

DATE=$( date +%Y-%m-%d )
TIME=$( date +%H:%M )
SPEED=$( here goes whatever code you have to get the network speed )

sqlite3 $HOME/network.sqlite "insert into netspeed (speed,time) values ('${SPEED}','${DATE} ${TIME}');"
```

Where:

network.sqlite - is the name of the database 
netspeed - is the name of the table in the database
(speed,time)  - are the table collumns

You can choose any name you want for the parameters above, as long as the names on the script match the names on the database.

EDIT: if you need more help with sqlite3 commands, keep asking in this thread and I will try to help. I have a lot of scripts using sqlite3 commands in my FF extension (link in the signature).

---

### Post by t0p on 2009-03-14
Thanks to all who've answered.  Lovinglinux, I shall see what I can knock up tomorrow, and if I need help I will surely let you know!

---

