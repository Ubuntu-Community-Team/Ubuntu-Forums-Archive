---
title: "[SOLVED] Transmission Install Help - Server"
date: 2008-12-25
forum: General Help
---

### Post by falconed7 on 2008-12-25
Hey everyone.

I ahve been following this guide [http://linhost.info/2008/11/transmission-on-ubuntu-804-server-the-best-bt-client-with-a-web-interface/](http://linhost.info/2008/11/transmission-on-ubuntu-804-server-the-best-bt-client-with-a-web-interface/) to install transmission + its web GUI.

For some reason when I install it, it installs version 1.06 and not 1.34.

I also test the daemon to see if its running:
```
transmission-daemon
```
This still doesn't show anything.

Basically I would like to install transmission and the web GUI that comes with it on my home server to begin downloading a torrent.

I try to uninstall transmission:
```
sudo apt-get remove transmission-cli
```
And this doesn't do anything.

I checked me /etc folder and there is nothing there listed as transmission... I notice that it has installed into my home folder and doesn't have any config files or anything.

So basically, how can I install 1.34 (I have heard this is more stable than 1.40) and access it remotely?

Finally, Merry Christmas!

---

### Post by kostkon on 2008-12-25
> **falconed7 said:**
> Hey everyone.

I ahve been following this guide [http://linhost.info/2008/11/transmission-on-ubuntu-804-server-the-best-bt-client-with-a-web-interface/](http://linhost.info/2008/11/transmission-on-ubuntu-804-server-the-best-bt-client-with-a-web-interface/) to install transmission + its web GUI.

For some reason when I install it, it installs version 1.06 and not 1.34.

I also test the daemon to see if its running:
```
transmission-daemon
```
This still doesn't show anything.

Basically I would like to install transmission and the web GUI that comes with it on my home server to begin downloading a torrent.

I try to uninstall transmission:
```
sudo apt-get remove transmission-cli
```
And this doesn't do anything.

I checked me /etc folder and there is nothing there listed as transmission... I notice that it has installed into my home folder and doesn't have any config files or anything.

So basically, how can I install 1.34 (I have heard this is more stable than 1.40) and access it remotely?

Finally, Merry Christmas!
Did you do a
```
sudo apt-get update
```
after adding the PPA?

Also, do a
```
apt-cache policy transmission-cli
```
and see what version is installed and which is the latest version offered and from which repo.

---

### Post by falconed7 on 2008-12-25
> **kostkon said:**
> Also, do a
```
apt-cache policy transmission-cli
```
and see what version is installed and which is the latest version offered and from which repo.

Okay I did that and this is what comes up:

```
transmission-cli:
  Installed: 1.42-0ubuntu0~hardy0
  Candidate: 1.42-0ubuntu0~hardy0
  Version table:
 *** 1.42-0ubuntu0~hardy0 0
        500 http://ppa.launchpad.net hardy/main Packages
        100 /var/lib/dpkg/status
     1.06-0ubuntu6 0
        500 http://au.archive.ubuntu.com hardy-updates/universe Packages
     1.06-0ubuntu4 0
        500 http://au.archive.ubuntu.com hardy/universe Packages
```

Looks like I have 1.42 and 1.06 installed? I don't mind using 1.42 if it's stable.

Now what the guide says to do is connect to it remotely already: [http://192.168.0.17:9091/](http://192.168.0.17:9091/) for  me as my server's IP address is that.

When I do this I get an error:

401: Unauthorized
> 
Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.

---

### Post by kostkon on 2008-12-25
> **falconed7 said:**
> Okay I did that and this is what comes up:

```
transmission-cli:
  Installed: 1.42-0ubuntu0~hardy0
  Candidate: 1.42-0ubuntu0~hardy0
  Version table:
 *** 1.42-0ubuntu0~hardy0 0
        500 http://ppa.launchpad.net hardy/main Packages
        100 /var/lib/dpkg/status
     1.06-0ubuntu6 0
        500 http://au.archive.ubuntu.com hardy-updates/universe Packages
     1.06-0ubuntu4 0
        500 http://au.archive.ubuntu.com hardy/universe Packages
```

Looks like I have 1.42 and 1.06 installed? I don't mind using 1.42 if it's stable.
No, you only have 1.42 installed, so you are OK then.
> **falconed7 said:**
> Now what the guide says to do is connect to it remotely already: [http://192.168.0.17:9091/](http://192.168.0.17:9091/) for  me as my server's IP address is that.

When I do this I get an error:

401: Unauthorized
This is something specific to transimission, but, anyways, I assume there is a settings.json file in the .transimission folder you need to edit, or something like that.

---

### Post by falconed7 on 2008-12-25
> **kostkon said:**
> No, you only have 1.42 installed, so you are OK then.

This is something specific to transimission, but, anyways, I assume there is a settings.json file in the .transimission folder you need to edit, or something like that.

Okay thanks.

I can't find any config files that have to do with transmission though.

There is only one mention of transmission and that is in** ~/.config/transmission-daemon**.

After that there are sub folders that have nothing in them.

---

### Post by kostkon on 2008-12-25
> **falconed7 said:**
> Okay thanks.

I can't find any config files that have to do with transmission though.

There is only one mention of transmission and that is in** ~/.config/transmission-daemon**.

After that there are sub folders that have nothing in them.
You didn't find the transmission folder that is supposed to exist in your home?
i.e.
```
~/.transmission
```
Hmmm, that's strange.

try also for example a
```
locate settings.json
```
or something like that

---

### Post by falconed7 on 2008-12-25
> **kostkon said:**
> You didn't find the transmission folder that is supposed to exist in your home?
i.e.
```
~/.transmission
```
Hmmm, that's strange.

try also for example a
```
locate settings.json
```
or something like that

Nope I dont see .transmission.
and the locate command doesn't bring up anything either.

Whats the best way to remove everything transmission related and install it again? So it installs all the necessary folders.

---

### Post by jerome1232 on 2008-12-25
well have you tried changing the options when you launch transmission-daemon?

Check out "man transmission-daemon"

---edit--- I was looking at it and the different versions are vastly different. On my 8.04 server I get version 1.06 and it has like zero options. I can't seem to figure out how to config it either.

On 8.10 I get version 1.34 and transmission-daemon can be run with alot more options.

---

### Post by falconed7 on 2008-12-26
I did a reinstall of everything, now I can find the settings.json tab.

I have 1.42 installed (using *transmissioncli -v*):
```

Transmission 1.42 (7495) - http://www.transmissionbt.com/
No torrent specified!
```

When I try to access [http://192.168.0.17:9091/](http://192.168.0.17:9091/) I get the following error:

> 401: Unauthorized

Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.

I went to my settings.json file and it looks like this:

```
{
    "blocklist-enabled": 0, 
    "download-dir": "\/home\/jamie", 
    "download-limit": 600, 
    "download-limit-enabled": 0, 
    "encryption": 1, 
    "max-peers-global": 200, 
    "peer-port": 51413, 
    "pex-enabled": 1, 
    "port-forwarding-enabled": 0, 
    "rpc-authentication-required": 0, 
    "rpc-password": "", 
    "rpc-port": 9091, 
    "rpc-username": "", 
    "rpc-whitelist": "127.0.0.1", 
    "upload-limit": 10, 
    "upload-limit-enabled": 0
}
```

I tried adding and changing the IP address in the "rpc-whitelist" to my Servers IP address and I still get the same error.

Is there a solution to this?

Any help will be great.

---

### Post by kostkon on 2008-12-26
> **falconed7 said:**
> I did a reinstall of everything, now I can find the settings.json tab.

I have 1.42 installed (using *transmissioncli -v*):
```

Transmission 1.42 (7495) - http://www.transmissionbt.com/
No torrent specified!
```

When I try to access [http://192.168.0.17:9091/](http://192.168.0.17:9091/) I get the following error:



I went to my settings.json file and it looks like this:

```
{
    "blocklist-enabled": 0, 
    "download-dir": "\/home\/jamie", 
    "download-limit": 600, 
    "download-limit-enabled": 0, 
    "encryption": 1, 
    "max-peers-global": 200, 
    "peer-port": 51413, 
    "pex-enabled": 1, 
    "port-forwarding-enabled": 0, 
    "rpc-authentication-required": 0, 
    "rpc-password": "", 
    "rpc-port": 9091, 
    "rpc-username": "", 
    "rpc-whitelist": "127.0.0.1", 
    "upload-limit": 10, 
    "upload-limit-enabled": 0
}
```

I tried adding and changing the IP address in the "rpc-whitelist" to my Servers IP address and I still get the same error.

Is there a solution to this?

Any help will be great.
Do you mean that you changed the line
```
    "rpc-whitelist": "127.0.0.1", 
```
to
```
    "rpc-whitelist": "127.0.0.1,192.168.0.17",
```
and still nothing?

---

### Post by falconed7 on 2008-12-26
> **kostkon said:**
> Do you mean that you changed the line
```
    "rpc-whitelist": "127.0.0.1", 
```
to
```
    "rpc-whitelist": "127.0.0.1,192.168.0.17",
```
and still nothing?

Yeah I changed it to that.

I also tried adding a line:

> "rpc-whitelist-enabled": 1,

---

### Post by kostkon on 2008-12-28
> **falconed7 said:**
> Yeah I changed it to that.

I also tried adding a line:
Doh. I think we are wrong. I think you need to put in *rpc-whitelist* the IP of the machine you are trying to connect to the Deluge server and not the IP of the server itself.

---

### Post by falconed7 on 2008-12-28
> **kostkon said:**
> Doh. I think we are wrong. I think you need to put in *rpc-whitelist* the IP of the machine you are trying to connect to the Deluge server and not the IP of the server itself.

Haha, no worries. I have also placed in the IP of my PC (192.168.0.4) and still the same result.

I think something is configured wrong as I am also having trouble with accessing webmin through a dyndns hostname.

---

### Post by Caraculo on 2008-12-30
> **falconed7 said:**
> Haha, no worries. I have also placed in the IP of my PC (192.168.0.4) and still the same result.

I think something is configured wrong as I am also having trouble with accessing webmin through a dyndns hostname.


Hi :KS.

Try this command:
**transmission-daemon -p 9091 -f -T -a 192.168.0.4**

This will do the following...
 [LIST]
[*]**-f** *makes Transmission run in the foreground (you can see different logs from the program)*
[*] **-p 9091**    *use port 9091*
[*] **-T**    *no web-logon*
[*] **-a 192.168.0.4**    *the IP address to give access to the web-interface*
[/LIST]

The first Transmission will write is something like this:
[INDENT][I]Transmission 1.42 (7495) started
RPC Server: Adding address to whitelist: 192.168.0.4
RPC Server: Serving RPC and Web requests on port 9091
RPC Server: Whitelist enabled[/I][/INDENT]

Now try to run the web-interface
[http://192.168.0.17:9091/](http://192.168.0.17:9091/)
or
[http://192.168.0.17:9091/transmission/web/](http://192.168.0.17:9091/transmission/web/)

If it doesn't work try to look into the messages that you get from Transmission.

Hope this helps :popcorn:

---

### Post by falconed7 on 2008-12-30
> **Caraculo said:**
> Hi :KS.

Try this command:
**transmission-daemon -p 9091 -f -T -a 192.168.0.4**

This will do the following...
 [LIST]
[*]**-f** *makes Transmission run in the foreground (you can see different logs from the program)*
[*] **-p 9091**    *use port 9091*
[*] **-T**    *no web-logon*
[*] **-a 192.168.0.4**    *the IP address to give access to the web-interface*
[/LIST]

The first Transmission will write is something like this:
[INDENT][I]Transmission 1.42 (7495) started
RPC Server: Adding address to whitelist: 192.168.0.4
RPC Server: Serving RPC and Web requests on port 9091
RPC Server: Whitelist enabled[/I][/INDENT]

Now try to run the web-interface
[http://192.168.0.17:9091/](http://192.168.0.17:9091/)
or
[http://192.168.0.17:9091/transmission/web/](http://192.168.0.17:9091/transmission/web/)

If it doesn't work try to look into the messages that you get from Transmission.

Hope this helps :popcorn:

You bloody beauty! It worked perfectly!

Do I have to run this command everytime at startup? Not that it matters much as I usually keep this on 24/7, however I have had the power dropping out a lot lately due to thunder storms.

EDIT: How do I change the download directory of the torrent? I have changed settings.json to:
```
"download-dir": "\/media\/store\/torrents",
```

However, it still downloads to /home/user

---

### Post by falconed7 on 2008-12-31
Okay it's all good!

I found the settings icon in the web GUI.

Thanks for all the help! Happy New Years!

---

### Post by Caraculo on 2009-01-02
> **falconed7 said:**
> Okay it's all good!

I found the settings icon in the web GUI.

Thanks for all the help! Happy New Years!


Ha, ha, ha... :D that's actually what I was going to suggest. Try the "Preferences" on the web GUI.
Tell me... did it work for you?

Happy New Year!!!

---

### Post by micro77 on 2009-05-31
hi
i found a another way ;
> "rpc-whitelist": "*.*.*.*",
full setting.json is ;
> "blocklist-enabled": 0,
"blocklist-updates-enabled": 0,
"download-dir": "\/share\/Download",
"download-limit": 200,
"download-limit-enabled": 0,
"encryption": 1,
"lazy-bitfield-enabled": 1,
"max-peers-global": 300,
"max-peers-per-torrent": 100,
"peer-port": 6881,
"pex-enabled": 1,
"port-forwarding-enabled": 1,
"rpc-authentication-required": 0,
"rpc-password": "",
"rpc-port": 9091,
"rpc-username": "",
"rpc-whitelist": "*.*.*.*",
"upload-limit": 30,
"upload-limit-enabled": 0
}

---

### Post by jnbptst on 2009-11-14
Hi everyone,

I did all of that:
-whitelist set on 0
-whitelist IP set on *.*.*.*
-tested launching transmission daemon with the options

despite all of this I still get a 401 error... what's wrong with my transmission?

---

### Post by dogskull on 2010-01-06
Similar problems here.  I have manually edited settings.json and also tried the command listed here.  I still cannot connect to the web UI.  Any other input?  (I am running 1.75.)

---

