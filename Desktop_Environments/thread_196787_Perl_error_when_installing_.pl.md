---
title: "Perl error when installing .pl"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Indifferent on 2006-06-14
I am trying to install a stats program but I get this error when I try:```
indiff@server:~$ cd /var/www/qPS
indiff@server:/var/www/qPS$ ./install.pl
bash: ./install.pl: /usr/bin/perl^M: bad interpreter: No such file or directory

```

I checked and it says that the latest version of perl is already installed. The file calls for atleast 5.6 and the Perl file says 5.8. I am running Xubuntu and a LAMP server. Any help is appreciated. Thanks in advance!

---

### Post by taurus on 2006-06-14
What is the first line of your install.pl?  Does it look something like
```

#!/usr/bin/perl

```

---

### Post by Indifferent on 2006-06-14
#!/usr/bin/perl -w

That's the very first line.

---

### Post by taurus on 2006-06-14
Remove the "-w" from it and make sure it has an executable permission...
```

chmod 755 install.pl
./install.pl

```

---

### Post by Indifferent on 2006-06-14
I tried it and got the same result:
```
indiff@server:~$ cd /var/www/qPS
indiff@server:/var/www/qPS$ chmod 755 install.pl
indiff@server:/var/www/qPS$ ./install.pl
bash: ./install.pl: /usr/bin/perl^M: bad interpreter: No such file or directory
```

When I checked the file on Windows the first line showed as:
#!/usr/bin/perl -w
But the same file on Xubuntu shows as:
!/usr/bin/perl

Which I found strange. Thanks again for your help with this. Any other ideas? OH, I checked and perl & perl5.8.7 are both in that directory so maybe I am missing support files?

---

### Post by scxtt on 2006-06-14
```
indiff@server:~$ cd /var/www/qPS
indiff@server:/var/www/qPS$ ./install.pl
bash: ./install.pl: /usr/bin/perl[SIZE="5"][color=red]**^M**[/color][/size]: bad interpreter: No such file or directory
```did someone edit this code in windows (or even a mac)?  what i colored above looks eerily similar to problems i've seen when you edit a text file in an editor that uses non-unix control characters (which ^M is) ... which means that this file needs to be edited on a unix box to strip out those "weird" character ...

---

### Post by Indifferent on 2006-06-14
No I downloaded this one directly to my Xubuntu box. It's never seen Windows AFAIK. It was originally meant for Linux boxes and then they made it Windows compatible. So, I doubt the site did it.

---

### Post by taurus on 2006-06-14
Okay, looks like we have a small problem with the ASCII thing.  Run this command to see if it gets rid of all those ^M at the end of each line...
```

dos2unix install.pl

```

---

### Post by scxtt on 2006-06-15
[QUOTE=Indifferent]No I downloaded this one directly to my Xubuntu box. It's never seen Windows AFAIK. It was originally meant for Linux boxes and then they made it Windows compatible. So, I doubt the site did it.[/QUOTE]maybe you didn't do it, but it happened regardless ... taurus's suggestion is good, but dos2unix isn't installed by default - you may need to "apt-get / synaptic" a prog. called 'tofrodos' ...

---

### Post by Indifferent on 2006-06-15
I ended up reading a few articles on this last night, but it was sooooo late that I decided to wait until today. I will try this when I get home. Thanks again!

---

### Post by Indifferent on 2006-06-15
tofrodos worked like a charm! Thanks again for all the help!

---

### Post by chiefofthejojos on 2006-12-15
thanks for this!  This saved me when installing ndiswrapper 1.28

---

