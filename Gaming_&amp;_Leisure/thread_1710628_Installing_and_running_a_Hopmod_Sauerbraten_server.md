---
title: "Installing and running a Hopmod Sauerbraten server"
date: 2011-03-20
forum: Gaming &amp; Leisure
---

### Post by calin rusu on 2011-03-20
Hopmod is a custom server mod for Sauerbraten written in lua and with a lot more features compared to the simple default sauerbraten server. It allows you to customize map rotation, default game mode and uses a lot of modules (limit teamkilling, limit ping, display stats and awards, control via irc and so on).
First thing you have to make sure of if you're planning to host a hopmod sauerbraten server on your LAN or PC is that you have a good connection (a good upload). From my experience, hosting 16 clients on a LAN server requires an average of 60-70 KB/s upload. So you need at least 1Mbps up to be able to host 16 clients. But 12 clients are running just fine on a connection with 1 Mbps up. Best way to host the server is to do it either on a server machine running on your lan either using a vm running on your machine, especially if you have 2 cores at least. The reason for doing this is that server will lag if you play on the same machine running the server when you connect, disconnect or issue some commands to the server. So, the best would be to take a piece of trash you don't use (MB, CPU, 128 RAM and a PSU), install ubuntu server on it, put it under your couch and use it to run the saurbraten server.
Of course you need to forward the ports in your router for the machine running the server (28785-28786 if you're running on default ports or whatever ports you like to use for hopmod).
Now, to install hopmod, you need to make sure you have all required dependancies to build it. Issue this command in terminal:

sudo apt-get install cmake subversion build-essential libsqlite3-dev libgeoip-dev zlib1g-dev

Once you did that you can download the source code in a directory called hopmod in your home dir using subversion. Type this is terminal:

svn checkout [http://hopmod.googlecode.com/svn/trunk](http://hopmod.googlecode.com/svn/trunk) hopmod

Wait for thr download to complete and then cd into hopmod folder to run a nice script that will build and compile:

cd hopmod

sh ./compile.sh

If it says 100% built target sauer-server in the end you'ready to go. Otherwise you're missing some libs eventually.
You need to edit the server configuration file now. Assuming you're doing this in cli in ubuntu-server i assume you'll use nano:

nano conf/server.conf

edit those lines (they explain very clear what they do, uncomment those you want to be enabled) and hit Ctrl+O to save it, Ctrl+X to exit.
If you want you can also modify map rotation with "nano conf/maps.conf"

After you did all that you're ready to start the server (you already are in hopmod directory):

bin/server start

If you want to stop it:

bin/server stop

Remember all this is done inside the hopmod directory.

If someone find this useful i'll come back with a more detailed tutorial about using the web control panel (which is awesome) or irc bot to control the server via irc or how to customize some banners, infos and so on...

---

### Post by Baz00 on 2011-06-01
I would love more detail about using the web control panel or irc bot!

:-)

---

