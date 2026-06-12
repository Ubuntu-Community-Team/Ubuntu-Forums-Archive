---
title: "How to set € symbol to work in console?"
date: 2005-01-10
forum: Desktop Environments
---

### Post by ladoga on 2005-01-10
I have finnish keyboard layout and € symbol works in nautilus, openoffice etc. 
pretty much everywhere else but not in terminals. 

Any help to get euro symbol to work in gnome-terminal would be appreciated. 

Thanks in advance.

---

### Post by DharmaOne on 2005-01-11
Have you tried the ASCII equivilent?

[http://www.asciitable.com/](http://www.asciitable.com/)

Though I did not see that character on this table, your character set
should contain it. Use the "ALT" key plus the three digits to display
the ascii code you need.

-DharmaOne

---

### Post by ladoga on 2005-01-11
Yes, but shouldnt it be possible by pressing alt-e, just like in windoze?

---

### Post by zeroK on 2005-01-11
[QUOTE=ladoga]Yes, but shouldnt it be possible by pressing alt-e, just like in windoze?[/QUOTE]
 Strange. It was working before but now I've tried it again and it doesn't work here either :(

---

### Post by Ufo on 2005-01-11
I have finnish keyboard layout too.
For me € symbol works everywhere I tried, including terminals and console.
If any help, locale prints:

LANG=fi_FI@euro
LC_CTYPE="fi_FI@euro"
LC_NUMERIC="fi_FI@euro"
LC_TIME="fi_FI@euro"
LC_COLLATE="fi_FI@euro"
LC_MONETARY="fi_FI@euro"
LC_MESSAGES="fi_FI@euro"
LC_PAPER="fi_FI@euro"
LC_NAME="fi_FI@euro"
LC_ADDRESS="fi_FI@euro"
LC_TELEPHONE="fi_FI@euro"
LC_MEASUREMENT="fi_FI@euro"
LC_IDENTIFICATION="fi_FI@euro"
LC_ALL=

---

### Post by ladoga on 2005-01-12
[QUOTE=Ufo]I have finnish keyboard layout too.
For me € symbol works everywhere I tried, including terminals and console.
If any help, locale prints:

LANG=fi_FI@euro
LC_CTYPE="fi_FI@euro"
LC_NUMERIC="fi_FI@euro"
LC_TIME="fi_FI@euro"
LC_COLLATE="fi_FI@euro"
LC_MONETARY="fi_FI@euro"
LC_MESSAGES="fi_FI@euro"
LC_PAPER="fi_FI@euro"
LC_NAME="fi_FI@euro"
LC_ADDRESS="fi_FI@euro"
LC_TELEPHONE="fi_FI@euro"
LC_MEASUREMENT="fi_FI@euro"
LC_IDENTIFICATION="fi_FI@euro"
LC_ALL=[/QUOTE]

Which file should i edit to configure those? 
I want to keep system language as english, so setting all to fi_FI@euro doesnt work for me.

---

### Post by Ufo on 2005-01-12
Locale variables are configured in file /etc/environment.
Setting finnish locales is described in Finnish-HOWTO document, it also describes this € problem. It can be found from here example:

[http://www.tldp.org/HOWTO/Finnish-HOWTO/index.html](http://www.tldp.org/HOWTO/Finnish-HOWTO/index.html)

I tried again € symbol in various places and it did work everywhere else, but in console it did not. Yesterday it did, which is strange.

---

### Post by ladoga on 2005-01-13
[QUOTE=Ufo]Locale variables are configured in file /etc/environment.
Setting finnish locales is described in Finnish-HOWTO document, it also describes this € problem. It can be found from here example:

[http://www.tldp.org/HOWTO/Finnish-HOWTO/index.html](http://www.tldp.org/HOWTO/Finnish-HOWTO/index.html)

I tried again € symbol in various places and it did work everywhere else, but in console it did not. Yesterday it did, which is strange.[/QUOTE]

I got it working on gnome-terminal by changing font back to monospace. 
In aterm i guess i just dont have font with € symbol in it.

Kiitos avusta. :)

---

### Post by Ufo on 2005-01-13
Eipä kestä  :-P 

So it was font problem. Glad you got it working on gnome-terminal.

In my Ubuntu € symbol works again even in console.
I'm not sure what I did that it did not work yesterday, but it seems that booting computer for the night helped.

---

