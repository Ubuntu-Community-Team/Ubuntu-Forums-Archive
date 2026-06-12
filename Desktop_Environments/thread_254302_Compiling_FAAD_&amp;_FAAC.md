---
title: "Compiling FAAD &amp; FAAC"
date: 2006-09-09
forum: Desktop Environments
---

### Post by morikaweb on 2006-09-09
Does anyone know how to compile FAAD2 adn FAAC from source. I seem to have everything needed but still errors.

Has anyone successfully compiled these two programs. And if so please tell me exactly how you did it.

I have followed many people advice on how to do it. but I get error, and different errors depending on who advice I follow.

Thanks all

---

### Post by lamego on 2006-09-09
Please post the errors you are getting.

---

### Post by morikaweb on 2006-09-10
There are way too many errors to post here. Besides the errors change depending on what configuration options I use, how I set prepare the source to be configured, and what system I'm using. 

I'm not asking for someone to troubleshoot my compilation errors, I'm asking if anyone has ever successfully compiled this software on ubuntu/kubuntu and if so how?

---

### Post by maiden30403 on 2006-10-27
Bit late but:

```

# aclocal -I .
# autoheader
# automake --add-missing
# autoconf
# ./configure
# make
# sudo make install
```

Give that a go and all should work.

---

### Post by k_dimitar on 2007-05-21
> **maiden30403 said:**
> Bit late but:

```

# aclocal -I .
# autoheader
# automake --add-missing
# autoconf
# ./configure
# make
# sudo make install
```

Give that a go and all should work.


That does not work either. Any help will be greatly appreciated. I did many searches for help on compiling FAAD and no luck so far... Here is the error i get:

```

root@gateway:~/faad2# aclocal -I .
root@gateway:~/faad2# autoheader
root@gateway:~/faad2# automake --add-missing
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
plugins/Makefile.am:6: endif without if
plugins/Makefile.am:15: endif without if
plugins/Makefile.am:16: endif without if
plugins/Makefile.am:17: endif without if
plugins/xmms/src/Makefile.am:9: endif without if
plugins/xmms/src/Makefile.am:7: invalid unused variable name: `local_LDFLAGS'
configure.in: 1020: required file `./ltmain.sh' not found
automake: Makefile.am: installing `./INSTALL'
```

Thank you

---

