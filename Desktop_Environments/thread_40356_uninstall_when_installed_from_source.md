---
title: "uninstall when installed from source"
date: 2005-06-08
forum: Desktop Environments
---

### Post by mattack on 2005-06-08
I compiled a program from source as directed on [this website](http://www.no-ip.com/tips.php/id/13?sid=6106ae465bb655a91a2b41e7bb096358). How can I unistall it, as I don't need it anymore?

---

### Post by Majlo on 2005-06-08
[QUOTE=mattack]I compiled a program from source as directed on [this website](http://www.no-ip.com/tips.php/id/13?sid=6106ae465bb655a91a2b41e7bb096358). How can I unistall it, as I don't need it anymore?[/QUOTE]

Try this 

*sudo make uninstall*

---

### Post by xao on 2005-06-08
You can go to the original dir from where you installed it, and then issue the command:

make uninstall

at least thats how ive done it with other programs...

---

### Post by xao on 2005-06-08
dang, majlo beat me by 1 minute

---

### Post by PhilippWollermann on 2005-06-08
You might want to use the tool "checkinstall" for installing other programs from source.. it packs the compiled stuff into a debian package before installing it, so you can remove it very easily later on (some programs don't support make uninstall :/). checkinstall is in the universe repository too.

Philipp

---

### Post by mattack on 2005-06-08
make uninstall doesn't work, with or without the sudo. I get the same error either way

```
matt@mattack:~ $ cd /home/matt/Noip/noip-2.1.1
matt@mattack:~/Noip/noip-2.1.1 $ make uninstall
make: *** No rule to make target `uninstall'.  Stop.
```

here are the contents of the make file, if that helps:
```
TGT=noip2
CC=gcc

PREFIX=/usr/local
CONFDIR=${PREFIX}/etc
BINDIR=${PREFIX}/bin

# these defines are for Linux
LIBS=
ARCH=linux

# for BSD systems that have getifaddr(), uncomment the next line
#ARCH=bsd_with_getifaddrs

# for early BSD systems without getifaddrs(), uncomment the next line
#ARCH=bsd


# for solaris, uncomment the next two lines
# LIBS=-lsocket -lnsl
# ARCH=sun

${TGT}: Makefile ${TGT}.c 
	${CC} -Wall -g -O2 -D${ARCH} -DPREFIX=\"${PREFIX}\" ${TGT}.c -o ${TGT} ${LIBS}

install: ${TGT} 
	if [ ! -d ${BINDIR} ]; then mkdir -p ${BINDIR};fi
	if [ ! -d ${CONFDIR} ]; then mkdir -p ${CONFDIR};fi
	cp ${TGT} ${BINDIR}/${TGT}
	${BINDIR}/${TGT} -C -Y -c /tmp/no-ip2.conf
	mv /tmp/no-ip2.conf ${CONFDIR}/no-ip2.conf

package: ${TGT}
	mv ${TGT} binaries/${TGT}-`uname -s`
	cd ..; tar zcvf /tmp/noip-2.0.tgz noip-2.0/*

clean: 
	rm -f *o
	rm -f ${TGT}

```

---

### Post by xao on 2005-06-08
hrm.....makes me wish i was a programmer. sadly, im a student of religion.

can you give a link to where you got the actual source? im looking on the website and i dont seem to see it. it could be the margarita i jsut drank, but i cant find where you got the program....i would like to play around with the source and see what i can find (a fresh pair of eyes can do wonders).




xao

---

### Post by xerosis on 2005-06-09
try sudo make clean

---

### Post by desdinova on 2005-06-09
[QUOTE=xerosis]try sudo make clean[/QUOTE]
 make clean merely removes everything from the source directory for a clean re-make/make install

---

### Post by xerosis on 2005-06-09
[QUOTE=desdinova]make clean merely removes everything from the source directory for a clean re-make/make install[/QUOTE]
 oops, i must have read it wrong.

---

### Post by PhilippWollermann on 2005-06-09
Just do a ```
make --dry-run install
``` again from the source directory and look at the output - I don't think that the noip client has lots of files. When you figured out (or posted the output here), you can delete them by hand. For the future you've got checkinstall, so that won't happen again. ^^

---

### Post by mattack on 2005-06-09
here's the output:

```
matt@mattack:~/Noip/noip-2.1.1 $ make --dry-run install
if [ ! -d /usr/local/bin ]; then mkdir -p /usr/local/bin;fi
if [ ! -d /usr/local/etc ]; then mkdir -p /usr/local/etc;fi
cp noip2 /usr/local/bin/noip2
/usr/local/bin/noip2 -C -Y -c /tmp/no-ip2.conf
mv /tmp/no-ip2.conf /usr/local/etc/no-ip2.conf
```


what do I delete?
also, it loads at startup, do I need to delete an entry from a startup file?

---

### Post by PhilippWollermann on 2005-06-09
Just delete

/usr/local/bin/noip2
/usr/local/etc/no-ip2.conf

I don't know why noip loads itself on startup.. the make install doesn't do anything like that. I would try to delete the files and see, whether there is any error message after a fresh reboot. If it is, we can figure out, where noip2 is called. :)

Philipp

---

### Post by mattack on 2005-06-09
[QUOTE=PhilippWollermann]Just delete

/usr/local/bin/noip2
/usr/local/etc/no-ip2.conf

I don't know why noip loads itself on startup.. the make install doesn't do anything like that. I would try to delete the files and see, whether there is any error message after a fresh reboot. If it is, we can figure out, where noip2 is called. :)

Philipp[/QUOTE]
 That seemed to do the trick...
No errors when I reboot.
Thanks.

---

### Post by az on 2005-06-09
I hopt this is not offensive.  It is not meant to be.  Is there anything about removing the software in the README?

---

### Post by mlmurray on 2005-06-09
Well, it seems as though you've found the solution to your immediate problem.

I would like to suggest, though, that that you look into a program called "checkinstall".  It's in the apt repositories and what it does, essentially, is create a .deb file while your installing.  This allows for easy uninstallation later on.

It's very easy to use (usually you just run "checkinstall" instead of "make install" and it does it's work automagically.

---

