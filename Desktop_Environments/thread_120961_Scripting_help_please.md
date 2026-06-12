---
title: "Scripting help please"
date: 2006-01-24
forum: Desktop Environments
---

### Post by routerstu on 2006-01-24
hello all. i am in need of some scripting help, or if someone could even point me in the right direction it would be appreciated.

long story short, i am trying to have an icon on my desktop to launch wpa for (no loaded at startup incase i want to use networkmanager for wep) since the ipw2200  is not straightforward :)

this is what i do after i log into ubuntu in order to get wpa2 to work


---------------------------------------------

open terminal
enter
```
sudo wpa_supplicant  -i eth1 -c /etc/wpa_supplicant.conf -Dwext -w -dd

```


then open ANOTHER terminal since launching the wpa_supplicant app runs inside the 1st one
enter
```
sudo wpa_cli
```

this brings me into the interactive wpa cli, which gives me a completely different set of options like bellow:

```

jason@dapperU:~$ sudo wpa_cli
Password:
wpa_cli v0.4.7
Copyright (c) 2004-2005, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.


Selected interface 'eth1'

Interactive mode

>
>
```



now from this interactive cli i have to run 3 commands:
```
disconnect
```

```
reassociate
```

```
quit
```

which then brings me back to a normal bash prompt

then to get an ip i have to type:
```
sudo dhclient eth1
```

after this i can close the second terminal but have to keep the 1st terminal open since wpa_supplicant is still running inside it.

Ideally i would like to have one icon on my desktop to run all of this in the background.  when writing this script do i have to worry about the time between these commands since it may affect the outcome?  

thanks everyone!!!!!

---

### Post by goatflyer on 2006-01-24
I'm no expert, but I give you what hints I can.

To run a non-interactive command in the background, append an ampersand ('&') to the end of the line.  This works in bash scripts as well.

If you need delay between commands, try (for example)

sleep 3

for a 3 second pause.

Finally, for your interactive program, create a text file with the 3 commands, one per line. Name the file something useful like:

wpa_cmds

Then, try your command this way:
 
sudo wpa_cli <wpa_cmds

Good luck experimenting

---

### Post by cwaldbieser on 2006-01-24
[QUOTE=routerstu]hello all. i am in need of some scripting help, or if someone could even point me in the right direction it would be appreciated.

long story short, i am trying to have an icon on my desktop to launch wpa for (no loaded at startup incase i want to use networkmanager for wep) since the ipw2200  is not straightforward :)

this is what i do after i log into ubuntu in order to get wpa2 to work


---------------------------------------------

open terminal
enter
```
sudo wpa_supplicant  -i eth1 -c /etc/wpa_supplicant.conf -Dwext -w -dd

```


then open ANOTHER terminal since launching the wpa_supplicant app runs inside the 1st one
enter
```
sudo wpa_cli
```

this brings me into the interactive wpa cli, which gives me a completely different set of options like bellow:

```

jason@dapperU:~$ sudo wpa_cli
Password:
wpa_cli v0.4.7
Copyright (c) 2004-2005, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.


Selected interface 'eth1'

Interactive mode

>
>
```



now from this interactive cli i have to run 3 commands:
```
disconnect
```

```
reassociate
```

```
quit
```

which then brings me back to a normal bash prompt

then to get an ip i have to type:
```
sudo dhclient eth1
```

after this i can close the second terminal but have to keep the 1st terminal open since wpa_supplicant is still running inside it.

Ideally i would like to have one icon on my desktop to run all of this in the background.  when writing this script do i have to worry about the time between these commands since it may affect the outcome?  

thanks everyone!!!!![/QUOTE]

I've never used wpa_supplicant, but if you want to keep it running all the time, it is pretty easy to have the init "super-server" program monitor and run it for you when the system starts up.  Then you can just worry about the client piece for your desktop.  Basically, you edit /etc/inittab and add something like:
```

ws:12345:respawn:/usr/binwpa_supplicant  -i eth1 -c /etc/wpa_supplicant.conf -Dwext -w -dd

```
(I was not sure of the full path to wpa_supplicant-- I am just guessing /usr/bin in the above example).
Then it will run wpa_supplicant when you boot up, and if it dies for some reason, it will restart it.  You can make init re-read the config without rebooting by typing:
```

$ sudo kill -HUP 1

```
See "man inittab" for further reference.

For the client part, you are going to have to read the man pages and see if there is a non-interactive way of issuing those commands (there usually is).  If not, you could always write an "expect" script, but that is a little harder to do.

---

### Post by routerstu on 2006-01-24
thanks everyone!

---

### Post by routerstu on 2006-01-24
ok, here is more info.
i have a bash script, crude but works ok.
-------------------------------------
#!/bin/bash

wpa_supplicant command -B to daemonize

sleep 5

wpa_cli disconnect

sleep 5
wpa_cli reassociate
sleep 5
dhclient eth1



----------------------

this works well.  now im wondering how do i kill wpa_supplicant in the event i dont need it during that session anymore.  should i try "wpa_cli terminate" or kill PID, or something else?  it seems whatever i try it just turns into a stopped job and i end up rebooting to clear it up.

thanks again!

---

