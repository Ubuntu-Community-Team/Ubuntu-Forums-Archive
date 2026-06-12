---
title: "obconf size of window"
date: 2018-06-03
forum: Desktop Environments
---

### Post by VMC on 2018-06-03
Whenever you open obconf, the length of the windows is huge. 3/4 of the desktop is filled with obconf.
Searching reveals on a "normal" openbox, do this at the end of rc.xml:

```
[COLOR=#4D4D4D][FONT=&amp]<application name="obconf">[/FONT][/COLOR][COLOR=#4D4D4D][FONT=&amp]      <size>
        <width>45%</width>
      </size>
    </application>[/FONT][/COLOR]
```
Adding that code does nothing.

---

### Post by again? on 2018-06-04
Check for instructions around line# 700 in the rc.xml.
Suggests to use obxprop to get the application name. obconf may be the class name.
I don't use openbox but installed and took a look at rc.xml
Wouldn't your code need to go between **<applications>** and **</applications>**

ie disregarding the commented out instructions in my rc.xml file it would look like.
```
<applications>

[B]<application name="Openbox Configuration Manager">      <size>
        <width>45%</width>
      </size>
    </application>[/B]

</applications>

```
Didn't work though when I tried it. Also tried **<application class="obconf">**

Besides this, there is a qt implementation of obconf that behaves better.
```
sudo apt install obconf-qt
```

---

### Post by VMC on 2018-06-04
Thanks for the info. It didn't work for me either. I'll try the 'qt' you mentioned.

---

