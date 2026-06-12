---
title: "Shutting down x interface temporarily"
date: 2009-01-28
forum: Desktop Environments
---

### Post by enzo12345 on 2009-01-28
Im using Ubuntu Desktop as a webserver.

If i use 
```
sudo /etc/init.d/gdm stop
```

to shutdown the desktop, will my crontab scripts still run and work? Will the webserver still work?

The scripts are run on my own user crontab, and are located on the desktop?

Thanks.

---

### Post by khelben1979 on 2009-01-28
If you choose to start scripts from a text console, you'll access them with ```
alt F1 to alt F6
``` and then when you restart the x-server with ctrl + alt + backspace the scripts should not stop.

---

### Post by ajgreeny on 2009-01-28
All your command line utilities will work, ie cron and your mail server.  Only your GUI applications will not work, though if you just do a Ctrl+Alt+F1 to get a cli, but leave the gnome desktop running, (ie, not using** sudo /etc/init.d/gdm stop**) I think your GUI stuff will still be running in the background; not totally certain, but I think that's so.

---

### Post by XanTrax on 2009-01-28
Quick question...

Why are you using Ubuntu Desktop for a server application if you're going to be using the server application and none of the GNOME enviornment?  Download the server version and do ```
sudo apt-get install apache2 php5-mysql mysql-server
```

for apache and all neccessary components.

---

### Post by enzo12345 on 2009-01-30
because to develop my php files I like to use a GUI because i find CLI word processing hard to work with.

But now I have everything set up as i need, Ive realized i can save resources shutting down the GUI.

I also use phpmyadmin to have a look at my mysql databases (they are local not set up for internet use).

How can you look at mysql databases and edit php files with syntax highlights on a CLI?

What benefits would I have from using the server edition?

Thanks

---

### Post by XanTrax on 2009-01-30
> **enzo12345 said:**
> because to develop my php files I like to use a GUI because i find CLI word processing hard to work with.

But now I have everything set up as i need, Ive realized i can save resources shutting down the GUI.

I also use phpmyadmin to have a look at my mysql databases (they are local not set up for internet use).

How can you look at mysql databases and edit php files with syntax highlights on a CLI?

What benefits would I have from using the server edition?

Thanks

Well, you can do what khelben1979 said to do above.  Press and hold ctrl+alt+F# where F# is an f1-f6 key.  That will bring you to a CLI interface completely.

For syntax highlighting in Vi/Vim you can do

```

sudo apt-get install vim vim-runtime vim-full

```

Then 

```

sudo gedit /etc/vim/vimrc

```

and look a few lines down and youll see

```

"syntax on

```

Remove the ", save the file and exit, then exit or logout of your console.  Go back in, edit a php file with

```
vi file.php 
```
and you will see the highlighting.

To read MySQL databases in CLI you can do

```

mysql -u <username> -p

```

Will log you into MySQL, then to select a database

```

use database_name;

```

where database_name is a database name.  If you want to show tables,

```

show tables;

```

If you want to show columns from a table;

```

show columns from table_name;

```

Will show all columns from table_name table.  You can also run other commands like select:

```

SELECT * FROM table_name;

```

Where * is all columns and we are selecting them from table_name table.

Well, there would not be too many benefits to it since either way, this isnt a live web server serving pages to people on the internet.  You could stick with the desktop version and use the ctrl+alt+f# keys to use an all terminal interface.  You could also just remove gnome and everything completely.  Using the server edition you will have a more server like environment for what you are doing.  No real benefits except maybe that an X server doesnt come installed on it and some other desktop services may not be running/installed on the server version.

---

