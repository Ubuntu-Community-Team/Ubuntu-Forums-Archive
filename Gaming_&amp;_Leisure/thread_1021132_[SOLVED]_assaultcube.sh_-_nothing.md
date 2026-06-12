---
title: "[SOLVED] assaultcube.sh - nothing"
date: 2008-12-25
forum: Gaming &amp; Leisure
---

### Post by enchesss on 2008-12-25
so I changed to AssaultCube_v1.0 directoy and type assaultcube.sh as it says in the install instructions on teh web site but nothing happens?

What wong

---

### Post by mister_k81 on 2008-12-25
Did you try typing it as *./assaultcube.sh* and not just *assaultcube.sh*?

Also what kind of message are you getting in the terminal?

---

### Post by enchesss on 2008-12-25
tried both but it says command not found

Have tried to install using these instructions:

[http://assault.cubers.net/wiki/Ubuntu_Support](http://assault.cubers.net/wiki/Ubuntu_Support)


but when i try to install libraries 


```
 sudo apt-get install build-essential libsdl1.2debian libsdl1.2debian-pulseaudio libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev libopenal1 libopenal-dev libvorbis-dev

```

it says:

```
E: Couldn't find package libopenal1

```

everything seems to go ok when installing openal-soft-1.6.372.tar from here - [http://connect.creativelabs.com/openal/Downloads/Forms/AllItems.aspx](http://connect.creativelabs.com/openal/Downloads/Forms/AllItems.aspx)

but again when trying to install the libraries


```
 sudo apt-get install build-essential libsdl1.2debian libsdl1.2debian-pulseaudio libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev libopenal1 libopenal-dev libvorbis-dev

```

it says:

```
E: Couldn't find package libopenal1

```

---

### Post by enchesss on 2008-12-25
Don not know why but it works now - thanks

---

