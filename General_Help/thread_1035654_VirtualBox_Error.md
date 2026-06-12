---
title: "VirtualBox Error"
date: 2009-01-10
forum: General Help
---

### Post by illbashu on 2009-01-10
```
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer. 8.10

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {f39438d7-abfd-409b-bc80-5f5291d92897}

```

how do i fix this?

i need this fixed because i need to use my usb keyboard and mouse.

---

### Post by adult swim on 2009-01-10
did you install virtualbox-ose or virtualbox PUEL?

---

### Post by binbash on 2009-01-10
adding this to at the end of fstab worked for me :

usbfs /proc/bus/usb usbfs devmode=664 0 0

---

### Post by illbashu on 2009-01-12
how do i get to fstab?

---

### Post by john_spiral on 2009-01-14
> **illbashu said:**
> how do i get to fstab?

open a terminal, enter the below commands:

```
sudo cp /etc/fstab /etc/fstab.newbackup

sudo gedit /etc/fstab
```

add the "usbfs /proc/bus/usb usbfs devmode=664 0 0" line

---

### Post by jespdj on 2009-01-14
> **adult swim said:**
> did you install virtualbox-ose or virtualbox PUEL?
He's asking this because the open source edition (OSE) of VirtualBox does not support USB.

If you need USB support, get the version that's under the PUEL (Personal Use and Evaluation License) from [http://www.virtualbox.org](http://www.virtualbox.org)

---

