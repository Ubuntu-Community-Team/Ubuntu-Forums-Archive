---
title: "Help with Wine"
date: 2006-02-25
forum: Desktop Environments
---

### Post by xXx 0wn3d xXx on 2006-02-25
I tried to install wine with automatix and I downloaded it off the offical site and installed it but it still won't work. Can anyone help ?

---

### Post by sas13 on 2006-02-25
Well, I'm no expert but I just installed wine today and it worked for me:

The easiest way I think is to add the wine repository to your list according to the instructions here:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

this will also make sure that you keep up to date with the current version.

then you can either use synaptic or via the terminal:
```
sudo apt-get install wine
```

one word of warning though - 
make sure you remove any old installation of wine you might have first.

This includes getting rid of the .wine directory (that I found out the hard way synaptic's 'remove completley' doesn't do:

```
rm -r ~/.wine
```

---

