---
title: "Question on needed lib for an application."
date: 2006-07-24
forum: Desktop Environments
---

### Post by otherd on 2006-07-24
I have an application that when run errors out saying it can't find libstlport.so.5.0. I see in Synaptic that libstlport 4.6.2-3 is installed. I'm guess my app needs the newer STL C++. What would be the best way to resolve this? The app was one I converted from a .rpm with alien. It did install the libstlport.so.5.0 under root in  /opt/2X/applicationserverclient/lib# but I'm guess that's not in my path so it's not seeing it?

---

### Post by taurus on 2006-07-24
If you want to add an extra lib, then edit /etc/ld.so.conf and add it to the end of it...

```

sudo gedit /etc/ld.so.conf

```
Now, add this line to it...

```

/opt/2X/applicationserverclient/lib

```
Then, either reboot (but why) or run this command...

```

ldconfig

```
Now, see if your program can find the lib file in /opt/2X/applicationserverclient/lib.

---

### Post by apjone on 2006-07-24
> **otherd said:**
> I have an application that when run errors out saying it can't find libstlport.so.5.0. I see in Synaptic that libstlport 4.6.2-3 is installed. I'm guess my app needs the newer STL C++. What would be the best way to resolve this? The app was one I converted from a .rpm with alien. It did install the libstlport.so.5.0 under root in  /opt/2X/applicationserverclient/lib# but I'm guess that's not in my path so it's not seeing it?

try

sudo ln -s /opt/2X/applicationserverclient/lib# /usr/lib/

---

### Post by otherd on 2006-07-24
> **taurus said:**
> If you want to add an extra lib, then edit /etc/ld.so.conf and add it to the end of it...

```

sudo gedit /etc/ld.so.conf

```
Now, add this line to it...

```

/opt/2X/applicationserverclient/lib

```
Then, either reboot (but why) or run this command...

```

ldconfig

```
Now, see if your program can find the lib file in /opt/2X/applicationserverclient/lib.

Awesome! Worked like a champ. Had to sudo the ldconfig command too, but no complaints.

---

