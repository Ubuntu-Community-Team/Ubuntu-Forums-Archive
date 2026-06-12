---
title: "VNC - View connected users / stop server"
date: 2005-12-09
forum: General Help
---

### Post by ninocass on 2005-12-09
hi is there a commant that allows me to see the users connected to me and how do i stop the server from running.

ive tried vncserver -kill :1 but i get an error and am told to stop the server manually with Xvnc4 or something

Thanks

Nino

---

### Post by Chris Tucker on 2005-12-09
sudo killall vncserver

---

### Post by ninocass on 2005-12-09
Im getting:
```

root@Laptop:/home/nino# sudo killall vncserver
vncserver: no process killed

```

---

### Post by ninocass on 2006-06-14
old thread and all that but i wrote a small script to see if there are any open VNC connections

```

temp2=`netstat | grep 5900 | wc -m`
if [ "0" == "$temp2" ]
then
	echo "No Clients Connected"	
else
	echo "Connected Clients:"
	netstat | grep 5900
fi

```

it works under the defualt 5900 port if you have changed the port in VNC youll need to change it in the script

---

### Post by jklslvch on 2007-09-13
i kno this is old but..........

sudo killall Xvnc 

thats what worked for me

---

