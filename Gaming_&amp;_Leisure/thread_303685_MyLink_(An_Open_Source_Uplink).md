---
title: "MyLink (An Open Source Uplink)"
date: 2006-11-20
forum: Gaming &amp; Leisure
---

### Post by TBOL3 on 2006-11-20
[http://www.happypenguin.org/show?MyLink](http://www.happypenguin.org/show?MyLink)

I can't figure out how to compile this game, could anyone help?

I have never gotten any game to compile, but until now, I have been able to find .deb files.

Thanks.

---

### Post by deepwave on 2006-11-20
Err... this program runs on Perl and Tk.  Perl is a scripting language, so no compiling should be necessary.

From description:
Additional System Requirements: Perl (and several modules), Tk

So see that you have perl, libsdl-perl and tk (mine is tk8.4). 

Personally I did not find myLink as good as uplink.  But go ahead and try it out.

---

### Post by woofcat on 2007-04-05
Hmm, i have all of those installed yet no dice. When i try to run any of the perl files included (MyLinkd.pl and MyLinkTk.pl) I get.

```

jim@jim-desktop:~/Desktop/MyLink$ perl MyLinkTk.pl
Can't locate Frontier/Client.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 .) at MyLinkTk.pl line 7.
BEGIN failed--compilation aborted at MyLinkTk.pl line 7.

```

Any advice?

---

### Post by ibuclaw on 2008-07-23
**Install Prerequisites**
```

sudo apt-get install libfrontier-rpc-perl perl-tk

```
**Download the archive**
```

wget http://home.as-netz.de/gblech/mylink/mylink.tar.bz2

```
**Extract**
```

tar jxf mylink.tar.bz2

```
**Create a script to run the executable**
```

nano MyLink/mylink.sh

```
**Paste this inside and save**
```

#!/bin/sh
EXEC=$(ls -l $0 | sed 's/^.*-> //')
EXECDIR=$(dirname $EXEC 2>/dev/null)

if [ -d $EXECDIR ]
then cd $EXECDIR
fi

if [ -x MyLinkTk.pl ]
then exec ./MyLinkTk.pl
else echo 'Error: MyLinkTk.pl Not Found'
fi

```
**Make the script executable**
```

chmod +x MyLink/mylink.sh

```
**Move to games folder**
```

sudo mv MyLink /usr/local/games/

```
**Create Symbolic Link to Game**
```

sudo ln -s /usr/local/games/MyLink/mylink.sh /usr/games/mylink

```
Then try running the game again by typing in
```
mylink
```:)

Regards
Iain

---

