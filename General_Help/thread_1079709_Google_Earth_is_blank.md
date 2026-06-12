---
title: "Google Earth is blank"
date: 2009-02-24
forum: General Help
---

### Post by SlickRick on 2009-02-24
I tried installing google earth 5.0 and when I run it, all i can see where the earth should be is a blank black space.

I don't know why but I also can't run it from the terminal by typing googleearth.When I try to go to file>preferences it just won't let me click. When I click server login, a blank window pops up and immediately disappears.

These three things might be somehow related to the original problem.

---

### Post by taurus on 2009-02-24
Do you have compiz on?  If you do, try turning it off and see if googleearth works now.

---

### Post by SlickRick on 2009-02-24
nope, just says "bash: command not found"
when running normally it's still blank
tryed killing the compiz process tree too, didn't work

---

### Post by taurus on 2009-02-24
You mean you got that message "bash: command not found" when you tried to run it from a terminal?  Maybe googleearth is not in your path so you have to either change directory to where you installed or include the whole/complete path.

---

### Post by SlickRick on 2009-02-24
reinstalled it again and not it runs from terminal, comes up with this error
```
Warning: Unable to create prefs directory '/home/mynde/.googleearth'. File exists.
```

---

### Post by taurus on 2009-02-24
Did you install it as root or as a user mynde?  What happens if you remove that directory and then run googleearth again?

```
rm -rf ~/.googleearth
```

---

### Post by SlickRick on 2009-02-24
installed as user
if i remove it nothing happens, it's created again. No errors come up but still blank.
if i run google earth as root then the tips pop up which desn't happen as normal and then it crashes

---

### Post by RikoW on 2009-02-26
Hi,

had the same problem. Try to change the ownership of the following dir structure:

```
sudo chown -R username:username ~/.config/Google
```

of course, changing username to your username.

Apparently, when googleearth runs as root, it creates this directory as root and you cannot write to it anymore, when you start googleearth as normal user.

You may also want to make sure, that the following is owned by you:

```

sudo chown -R username:username ~/.googleearth
sudo chown -R username:username ~/.local

```

Let us know, if that solved your problem.

Cheers,
             Riko

---

### Post by SlickRick on 2009-02-26
```
Warning: Unable to create prefs directory '/home/mynde/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```

same running as user and root

Crashes every time

BUMP

---

### Post by RikoW on 2009-02-26
I seem to remember, for this error you need to rename libcrypto to something else, so that it uses the lib installed in your ubuntu and not the one which comes with google-earth:

```

> cd to_where_you_google-earth_is_installed
> mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.save

```

Maybe you have to do 
```
sudo mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.save
```
if google-earth is not installed in your home dir.

Good luck,

           Riko

---

### Post by SlickRick on 2009-02-26
> **RikoW said:**
> I seem to remember, for this error you need to rename libcrypto to something else, so that it uses the lib installed in your ubuntu and not the one which comes with google-earth:

```

> cd to_where_you_google-earth_is_installed
> mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.save

```

Worked like a charm

Thank you so much ;}

---

### Post by binbash on 2009-02-26
[http://www.ubuntu-inside.me/2009/02/howto-install-google-earth-50-beta-on.html](http://www.ubuntu-inside.me/2009/02/howto-install-google-earth-50-beta-on.html)

---

