---
title: "Remove duplicate e-mails in Evolution"
date: 2012-12-20
forum: Desktop Environments
---

### Post by achim_59 on 2012-12-20
Evolution e-mail downloads e-mails multiple times. This is a known problem, apparently. It is not clear if this is only the case when downloading from POP3 servers, but some posts do suggest that this is the case.

In this case I do not know if I can change to IMAP, but for the sake of the argument let's assume I can't. I found a post about a plugin to remove duplicates (in German): [http://johhniesblog.wordpress.com/2009/11/13/duplikate-entfernen-in-evolution/]("http://johhniesblog.wordpress.com/2009/11/13/duplikate-entfernen-in-evolution/")

I followed the instructions and got the following error when doing the install:
```

No package 'evolution-plugin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables REMOVE_DUPLICATES_PLUGIN_CFLAGS
and REMOVE_DUPLICATES_PLUGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

The "alternative" didn't make much sense to me but changing the PKG_CONFIG_PATH variable did. Especially when I discovered it was empty! So I entered the command 
```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
```
since that's where the file evolution-plugin-3.0 is located. 

Sadly, I got the same error message when I tried to install again.

Then I found the following post: [http://askubuntu.com/questions/50112/how-can-i-delete-duplicate-emails-in-evolution]("http://askubuntu.com/questions/50112/how-can-i-delete-duplicate-emails-in-evolution")

To save you all looking for the relevant text, here's a quote:
> Evolution 3.1, which ships with Ubuntu 11.10, now has that functionality integrated (Message &#9656; Remove Duplicate Messages). With 2.32 you are forced to upgrade. In addition, the function in 3.1 seems to be neither efficient nor configurable so you might still end up with lots of duplicates that give you something to do on a boring weekend.

Indeed Evolution does have this option, but in my installation it is inactive (==> greyed out) and I haven't a clue as to why.

Any ideas out there in Ubuntu-Land??

Achim

---

