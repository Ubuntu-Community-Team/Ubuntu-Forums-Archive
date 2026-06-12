---
title: "Weird locale and variables problem"
date: 2007-04-22
forum: Desktop Environments
---

### Post by ylazarev on 2007-04-22
Hi,
I searched the forums to find a way to change the locale so I could type in hebrew in Microsoft Office under Crossover Office or Wine, and what I found is that I need to change the /etc/environment file.

So before the change, the output of typing 'locale' in terminal was:
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

I added the line 'LC_ALL="he_IL.UTF-8" to the end of the file, logged in again, and now the output is:
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8

Which is very strange to me...
Anyone knows how can I fix this?
Also the output of 'locale -a' is:
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
he_IL.utf8
POSIX

---

### Post by mlind on 2007-04-22
Do you have hebrew language support installed?
```

sudo aptitude install **language-pack-he**

```

---

### Post by ylazarev on 2007-04-22
I did that, it installed some 4 packages, but problem still exists.
Apparently those packages fixed an OpenOffice problem (Right-To-Left typing wrong) so thanks! But I still would like to get hebrew working under Crossover and Wine.
More suggestions?

---

### Post by mlind on 2007-04-22
> **ylazarev said:**
> I did that, it installed some 4 packages, but problem still exists.
Apparently those packages fixed an OpenOffice problem (Right-To-Left typing wrong) so thanks! But I still would like to get hebrew working under Crossover and Wine.
More suggestions?

Sorry, I meant to type **language-pack-he** which should contain more complete set of hebrew language support files.

---

### Post by ylazarev on 2007-04-23
Already had that package: (language-pack-he)
"0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded."
Something more I can try?

---

### Post by ylazarev on 2007-04-24
Any ideas where is the problem?

---

### Post by mlind on 2007-04-24
Hi, 
does it makes any difference if you launch crossover office from terminal using LC_ALL=he_IL.utf8 ?

For example, to launch openoffice for hebrean locale (from terminal)
```

LC_ALL=he_IL.utf8 **ooffice**

```

---

### Post by ylazarev on 2007-04-25
Yes it works from the Terminal! I launched it like you said and I could type in hebrew.
But when I tried to make a launcher with the exact command it didn't work... neither with Application selected nor with Application in Terminal.
Does that give you a clue where the problem might be?

---

### Post by mlind on 2007-04-25
You may have a typo in your /etc/environment or something (local) is overriding the locale settings you've defined in that file.

Make sure you set the LC_ALL in /etc/environment exactly what locale -a outputs for hebrew.
Check that you don't override system wide locales in your ~/.bashrc or ~/.bash_profile.

---

### Post by ylazarev on 2007-04-26
Thanks for the great help and fast replies.. hope you can help me a little further..
Well now it got even weirder, as I added to the end of the file ~/.bashrc the line LC_ALL=he_IL.utf8,
and now the output of 'locale' is
LANG=he_IL.utf8
LC_CTYPE="he_IL.utf8"
LC_NUMERIC="he_IL.utf8"
LC_TIME="he_IL.utf8"
LC_COLLATE="he_IL.utf8"
LC_MONETARY="he_IL.utf8"
LC_MESSAGES="he_IL.utf8"
LC_PAPER="he_IL.utf8"
LC_NAME="he_IL.utf8"
LC_ADDRESS="he_IL.utf8"
LC_TELEPHONE="he_IL.utf8"
LC_MEASUREMENT="he_IL.utf8"
LC_IDENTIFICATION="he_IL.utf8"
LC_ALL=he_IL.utf8

which apparently is good, but launching Word for example still doesn't allow typing in Hebrew, BUT, launching it from Terminal with env LC_ALL=he_IL.utf8 does allow it.
I may have forgotten to add that the documentation of Crossover says that it looks at the local variables LC_ALL, LANG, LANGUAGE in this order and sets its' locale by the first 'legal' one.
This is frustrating... any clue? Thanks again for the patience and help.

---

### Post by mlind on 2007-04-26
~/.bashrc is used for terminal sessions and it's not sourced if you're not using a terminal. In other words, settings in ~/.bashrc don't apply for GNOME/KDE apps unless launched from terminal.

Use /etc/environment (or ~/.gtkrc to define environment variables locally for GNOME).

---

