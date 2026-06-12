---
title: "bash script problem (copy to clipboard)"
date: 2009-05-08
forum: General Help
---

### Post by darthmob on 2009-05-08
hi all. I have got a simple problem with the following bash script:

**_// SOLVED:_**
the solution was to use xclip instead of xsel. this version now works without problems.

```
#!/bin/bash

# fetches the public ip and copies it to the clipboard (paste it with CTRL+v)
# required packages:
#   curl (to fetch the page)
#   grep (to process the page information)
#   xclip (to copy ip to the clipboard)
#   notify-send (to send notifications)

# get public ip
ip=$(curl -s http://www.wieistmeineip.de/ | egrep -m1 -o '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' )

# check if ip is not empty
if [ -n "$ip" ]; then
    
    # confirm successful fetch of ip with notification
    notify-send --icon=/usr/share/icons/gnome/scalable/actions/editpaste.svg "retrieved Public IP" "$ip"
    
    # copy ip into clipboard
    echo $ip | xclip -selection clipboard
    
    # echo ip in console
    echo "retrieved Public IP: $ip"
else
    
    # notify of failed fetch
    notify-send --icon=/usr/share/icons/gnome/scalable/status/dialog-error.svg "Error" "Public IP could not be retrieved"
    
    # echo error in console
    echo "Public IP could not be retrieved."
fi
```

it is supposed to get the public ip address from wieistmeineip.de, copy it to the clipboard and send a notification. I made the script executable and copied it to /usr/bin/.

**the problem is:** it works fine when executed from terminal but it does not copy the ip to the clipboard when I start it with the alt+f2 program launcher. who knows what may be the problem?

**_// EDIT:_**
the solution was to use xclip instead of xsel. the above version now works without problems.

---

### Post by revertex on 2009-07-03
Nice one!
I reused part of your script to create a script that copy the output of dropbox.py to clipboard, works like a charm.

Dropbox needs nautilus to copy public address to clipboard, i don't want to install it, but use rox-filler instead.

You should drop egrep dependency and use cut instead, just replace

<code>ip=$(curl -s [http://www.wieistmeineip.de/](http://www.wieistmeineip.de/) | egrep -m1 -o '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' )</code>

by

<code>ip=$(curl -s [http://checkip.dyndns.org/](http://checkip.dyndns.org/) | cut -d ':' -f 2 | cut -d '<' -f 1 )</code>

---

