---
title: "How to build Freeciv with authentication support"
date: 2008-01-31
forum: Gaming &amp; Leisure
---

### Post by Nikusan on 2008-01-31
A default Freeciv build does not support player authentication, but it is possible to enable it with the configure flag *--enable-auth=yes*. Here are the steps to run your own Freeciv 2.1.3 server on Ubuntu 7.10 with authentication enabled.

First we install all the prerequisites, including mysql-server:
```
sudo apt-get install build-essential checkinstall libmysqlclient15-dev mysql-server mysql-admin
sudo apt-get build-dep freeciv
```

Then we download the [2.1.3 source code]("http://prdownloads.sourceforge.net/freeciv/freeciv-2.1.3.tar.bz2?download") and extract it with something like:
```
tar -xf freeciv-2.1.3.tar.bz2
```

Then we do the familiar ./configure && make && make install dance, ensuring that we pass *--enable-auth=yes* to configure:
```
cd freeciv-2.1.3
./configure --enable-auth=yes
make
sudo checkinstall -y
```

Now that the Freeciv server is ready to go, we need to setup the authentication database. Using MySQL Administrator, log in to the mysql server running on localhost. From the Catalogs menu, create a new schema named "freeciv". From the User Administration menu, create a new user named "Freeciv" and assign them all available privileges for the freeciv schema.

After that we run the script *setup_auth_server.sh* included with the freeciv source to setup the required tables. The script will generate a file named *fc_auth.conf* that must be passed to civserver to tell it which database to use for authentication.

```
bash scripts/setup_auth_server.sh
```

After that we're ready to run the server with the *-a* argument:

```
civserver -N -a fc_auth.conf
```

A good next step would be to read the [Server commands]("http://freeciv.wikia.com/wiki/Server_commands") page at the Freeciv wiki, particularly the bit about [cmdlevel]("http://freeciv.wikia.com/wiki/Server_commands#cmdlevel__-__Query_or_set_command_access_level_access.").

Thanks for reading, hope this helps someone. :)

Originally published here: [http://nikusan.net/?p=6](http://nikusan.net/?p=6)

---

