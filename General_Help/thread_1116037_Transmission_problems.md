---
title: "Transmission problems"
date: 2009-04-04
forum: General Help
---

### Post by elliotbeken on 2009-04-04
Hi, there

I have been playing with transmission and also the Web interface.

It was all going will till I changed the listening port from the defualt one (9091) to port 80. 

As soon as i pressed ok to save the setting transmission closed and now IT WILL NOT OPEN.

i have restarted the computer and also reinstalled transmission using the synaptic  packet manager, also i have total removed the software and again reinstalled it and there is still no hope 

i dont know what else to do!

any help would be great :) 

thanks

---

### Post by fabricator4 on 2009-04-04
It sounds like you might need to fix something in the config file.  The config file might not get removed when you uninstall because it could be part of the bit torrent protocol and could be used by other programs.

The problem is, I don't know where that config file can be found.  Well you did say _any_ help.  At least it's worth what you paid for it  ;-)

Try looking in the manual first:
man transmission  (at a terminal prompt)

Some config files can be found in ~/.config.  .config is a hidden directory in your home directory.

Hopefully someone else can be a bit more specific.

Chris.

---

### Post by elliotbeken on 2009-04-04
No its cool i knew it would be some thing but i just dont know were to look and what to edit

fast reply :P

---

### Post by jlimon on 2009-04-04
Transmission's config file can be found in $HOME/.config/transmission/

The file of interest would be settings.json and the key of interest would be "rpc-port" which for you will probably say 80.

---

### Post by fabricator4 on 2009-04-04
> **jlimon said:**
> Transmission's config file can be found in $HOME/.config/transmission/

The file of interest would be settings.json and the key of interest would be "rpc-port" which for you will probably say 80.

Thanks jlimin, I don't know how I failed to spot the transmission directory, especially since I went looking for it.

I checked the settings.json file on my system (which hasn't been changed as far as I know) and the setting in question is as follows:

   "rpc-port": 9091,

Proxy port is set to 80, but the rpc-port is set as above.

Chris.

---

### Post by jlimon on 2009-04-04
Hm, if in doubt you can rm the settings.json and re-configure it.

---

