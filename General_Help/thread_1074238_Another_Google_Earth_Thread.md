---
title: "Another Google Earth Thread"
date: 2009-02-19
forum: General Help
---

### Post by Dr Zin on 2009-02-19
I can't even run the bin file```
$ sudo ./home/me/Desktop/GoogleEarthLinux.bin
sudo: ./home/me/Desktop/GoogleEarthLinux.bin: command not found
```

WTF

---

### Post by Paul Miller on 2009-02-19
Try
```

sudo /home/me/Desktop/GoogleEarthLinux.bin

```
(i.e. without the initial '.'),
or
```

sudo ./Desktop/GoogleEarthLinux.bin

```
if you're executing it from your home directory.  Of course, make sure it's executable, first (if you have any problem, just do chmod +x on the file, then rerun the sudo command).

---

### Post by Dr Zin on 2009-02-19
I have doen the chmod +x thing already. thanks for the quik help

---

### Post by Dr Zin on 2009-02-19
```
 sudo ./Desktop/GoogleEarthLinux.bin
[sudo] password for drzin:
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
drzin@drzin:~$ mv /home/drzin/google-earth/libcrypto.so.0.9.8 /home/drzin/google-earth/libcrypto.so.0.9.8bug
mv: cannot stat `/home/drzin/google-earth/libcrypto.so.0.9.8': No such file or directory
drzin@drzin:~$ mv /home/USER/google-earth/libcrypto.so.0.9.8 /home/USER/google-earth/libcrypto.so.0.9.8bug
mv: cannot stat `/home/USER/google-earth/libcrypto.so.0.9.8': No such file or directory

```

I know I am having the same issue like every one else. But I  little more help. would need the stupid take on this issue

---

### Post by binbash on 2009-02-19
go to the folder you have installed google earth and move this file : 

libcrypto.so.0.9.8

example : 

mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.backup

---

### Post by Dr Zin on 2009-02-19
Its does see any of the directories that it was installed in.```
/opt/google-earth
```it will not let do it in the shell. It will not let me do it in the GUI. It will let me in the house.

---

### Post by binbash on 2009-02-19
drzin@drzin:~$ mv /home/USER/google-earth/libcrypto.so.0.9.8 /home/USER/google-earth/libcrypto.so.0.9.8bug

dude change the user with your username.

---

### Post by Dr Zin on 2009-02-19
I did read the code above

---

### Post by Dr Zin on 2009-02-19
fail code```
:~$ sudo mv /opt/google-earth/libcrypto.so.0.9.8 /opt/google-earth/libcrypto.so.0.9.8bug
``` Now on to the next issue opengl does not work very well on my system i have a ATI 1300x

---

