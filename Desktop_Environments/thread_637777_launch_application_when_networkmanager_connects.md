---
title: "launch application when networkmanager connects"
date: 2007-12-11
forum: Desktop Environments
---

### Post by shorti on 2007-12-11
Hi...

what I try to achieve is to launch a X-application automatically whenever the networkmanager establishes a connection to my network at home. Therefore I put a little script in /etc/Networkmanager/dispatcher.d . Everything works fine besides launching the application. What did I do wrong? 

Heres my code:

[CODE]
#!/bin/sh
#/etc/NetworkManager/dispatcher.d/unison
#Aktion einlesen
INTERFACE=$1
ACTION=$2

#IP herausfinden
IP=`ifconfig $INTERFACE | grep 'inet Adr' | awk '{print $2}' | sed -e 's/.*://'`
IP_START=`echo $IP | awk -F. '{print $1}'`

#Skript verlassen, wenn IP nicht von zu Haus ist.
if [ $IP_START != 192 ]; then
    #echo "bin nicht zu hause..." >> /tmp/nmlog.txt
    exit 0
fi

echo "bin zu hause" >> /tmp/nmlog.txt

#Funktionen durchführen, je nach Aktion eine andere
case "$ACTION" in
    up)
        echo "interface is up" >> /tmp/nmlog.txt
        /usr/bin/xterm -display :0.0
        beep
        ;;
    down)
        killall unison
        ;;
    pre-up)
        killall unison
        ;;
    post-down)
        killall -9 unison
        ;;
    *)
        echo "$0: aufgerufen mit falschem Parameter \`$ACTION'" 1>&2
        exit 1
        ;;
esac
[CODE]

It is beeping whenever I connect but doesn't start the xterm.....
Any help apreciated...

Michael

---

