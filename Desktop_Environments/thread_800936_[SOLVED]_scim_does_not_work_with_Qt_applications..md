---
title: "[SOLVED] scim does not work with Qt applications."
date: 2008-05-20
forum: Desktop Environments
---

### Post by gobi on 2008-05-20
I am using ubuntu 8.04 hardy. I tried to use software Anki which is built on Python with Qt libraries. But SCIM input method does not work. It works with no problem with other programs.

Could someone help me please.

---

### Post by gobi on 2008-05-21
Buzz

---

### Post by gobi on 2008-05-21
Buzz

---

### Post by gobi on 2008-05-21
Buzz

---

### Post by atomkarinca on 2008-05-22
> Edit the file /etc/X11/xinit/xinput.d/scim by typing in a terminal (Applications>Accessories>Terminal):

sudo gedit /etc/X11/xinit/xinput.d/scim

If you want to use scim input in KDE applications, you will also have to change the following line : 
QT_IM_MODULE=xim

into : 
QT_IM_MODULE="scim-bridge"

You can find information [here]("https://help.ubuntu.com/community/SCIM").

---

### Post by gobi on 2008-05-22
atomkarinca

thanks for reply. I checked what you suggested but I set that already up. My file looks like this.
> 
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE="scim-bridge"
QT_IM_MODULE="scim-bridge"
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"


what else should I check?

---

### Post by Zorael on 2008-05-22
Does it work with other Qt programs and this Anki being the sole exception? Because I can't get scim to work in OpenOffice if I install the openoffice.org-kde package (which arguably changes something that breaks it), but if I replace it with the openoffice.org-gnome package everything checks out. If it's only Qt programs that won't obey it, I'd triple-check those files under [FONT="Courier New"]/etc/X11/xinit/xinput.d/[/FONT].


I just reinstalled 8.04 on this machine I'm typing on and the only things I did was to edit that file you already pasted the contents of, and made sure that relevant xinput alternatives in [FONT="Courier New"]/etc/alternatives/[/FONT] were set correctly.
```
$ cat /etc/alternatives/xinput* -l
lrwxrwxrwx 1 root root 28 2008-05-21 15:23 xinput-all_ALL -> /etc/X11/xinit/xinput.d/skim
lrwxrwxrwx 1 root root 28 2008-05-21 14:39 xinput-en_US -> /etc/X11/xinit/xinput.d/skim
lrwxrwxrwx 1 root root 35 2008-05-21 15:23 xinput-ja_JP -> /etc/X11/xinit/xinput.d/scim-bridge
*(truncated)*
```

```
$ sudo im-switch -z all_ALL -c
System wide default for all_ALL locale is marked with [+].

There are 4 alternatives which provide `xinput-all_ALL'.

  Selection    Alternative
-----------------------------------------------
          1    /etc/X11/xinit/xinput.d/none
 +        2    /etc/X11/xinit/xinput.d/default
          3    /etc/X11/xinit/xinput.d/default-xim
*         4    /etc/X11/xinit/xinput.d/skim

Press enter to keep the default[*], or type selection number: 4
Using '/etc/X11/xinit/xinput.d/skim' to provide 'xinput-all_ALL'.
```

---

### Post by gobi on 2008-05-22
Zorael

thank you for advice. Some thing is really strange on my side here.

```
gobi@gobi-laptop:/etc/X11/xinit/xinput.d$ ls -l
total 8
lrwxrwxrwx 1 root root  30 2008-05-23 00:17 ja_JP -> /etc/alternatives/xinput-ja_JP
lrwxrwxrwx 1 root root  30 2008-05-23 00:17 ko_KR -> /etc/alternatives/xinput-ko_KR
-rw-r--r-- 1 root root 680 2008-05-23 00:28 scim
-rw-r--r-- 1 root root 692 2008-04-08 02:20 scim-immodule
lrwxrwxrwx 1 root root  30 2008-05-23 00:17 zh_CN -> /etc/alternatives/xinput-zh_CN
lrwxrwxrwx 1 root root  30 2008-05-23 00:17 zh_HK -> /etc/alternatives/xinput-zh_HK
lrwxrwxrwx 1 root root  30 2008-05-23 00:17 zh_SG -> /etc/alternatives/xinput-zh_SG
lrwxrwxrwx 1 root root  30 2008-05-23 00:17 zh_TW -> /etc/alternatives/xinput-zh_TW

```

and 

```
gobi@gobi-laptop:/etc/alternatives$ ls xinput* -l
lrwxrwxrwx 1 root root 31 2008-05-23 00:01 xinput-all_ALL -> /etc/X11/xinit/xinput.d/default
lrwxrwxrwx 1 root root 35 2008-05-23 00:27 xinput-ja_JP -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-23 00:27 xinput-ko_KR -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 30 2008-04-26 20:01 xinput-th_TH -> /etc/X11/xinit/xinput.d/th-xim
lrwxrwxrwx 1 root root 35 2008-05-23 00:27 xinput-zh_CN -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-23 00:27 xinput-zh_HK -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-23 00:27 xinput-zh_SG -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-23 00:27 xinput-zh_TW -> /etc/X11/xinit/xinput.d/scim-bridge

```

I dont have any /etc/X11/xinit/xinput.d/scim-bridge file. Does system generate this file? Is links above correct?

What should I do now?

---

### Post by gobi on 2008-05-22
Also I don't have /etc/X11/xinit/xinput.d/default

Where has it gone? May be several times reinstalled. What's happening I don't understand :(

---

### Post by Larir on 2008-05-22
I had a problem with QT apps too.

[https://help.ubuntu.com/community/SCIM?highlight=(scim](https://help.ubuntu.com/community/SCIM?highlight=(scim))

check this out, for me I just had to do the last step. Which is:

---cut---

**In case all of this doesn't work**

You might have to add your locale as a supported locale, by editing (you might have to create it) the file ~/.scim/global (the ~ means it's in your home directory, the . that .scim directory is a hidden file. Just type in a terminal :

```
gedit ~/.scim/global 
```

If you can find a line like

```
/SupportedUnicodeLocales = en_US.UTF-8
```

add your locale to it after a coma, not forgetting you need to add the full name reported by locale | grep LANG= after LANG= . In case of English for Great Britain, your line would look like this one :

```
/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8 
```

If the line wasn't there, create it, then save the file.

Log out, then log in and you should be able to use SCIM input in every application. 

---paste---

Just try the stuff in there, maybe it'll work for you too, good luck 	[-o<

---

### Post by gobi on 2008-05-23
Larir

Thanks for advice. I will check that when I go home. 

But I remember that after I installed SCIM I deleted ~/.scim and ~/.xinput.

So that file should be created by the system. Even system creates this file should above problem exist?

---

### Post by gobi on 2008-05-23
I have tried everything what is here.

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

But I still can not input qt applications.

What should I do, really do not understand. :(

---

### Post by gobi on 2008-05-23
My Hardy was installed in a way online upgrading from Gutsy, would it tell something?

---

### Post by gobi on 2008-05-23
I tried to set as said [here]("http://www.scim-im.org/wiki/documentation/installation_and_configuration/all/system_configuration")

But when I input this command:

```
skim -d -f
```

then it crashes. The backtrace is here I attached.

What the hell is going on really do not understand.

---

### Post by gobi on 2008-05-24
I installed my ubuntu from the CD and problem has disappeared. Looks upgrading distro online works not so good such.

---

### Post by eduardowb on 2010-02-27
> **Larir said:**
> I had a problem with QT apps too.

[https://help.ubuntu.com/community/SCIM?highlight=(scim](https://help.ubuntu.com/community/SCIM?highlight=(scim))

check this out, for me I just had to do the last step. Which is:

---cut---

**In case all of this doesn't work**

You might have to add your locale as a supported locale, by editing (you might have to create it) the file ~/.scim/global (the ~ means it's in your home directory, the . that .scim directory is a hidden file. Just type in a terminal :

```
gedit ~/.scim/global 
```

If you can find a line like

```
/SupportedUnicodeLocales = en_US.UTF-8
```

add your locale to it after a coma, not forgetting you need to add the full name reported by locale | grep LANG= after LANG= . In case of English for Great Britain, your line would look like this one :

```
/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8 
```

If the line wasn't there, create it, then save the file.

Log out, then log in and you should be able to use SCIM input in every application. 

---paste---

Just try the stuff in there, maybe it'll work for you too, good luck 	[-o<

Yay! I was waiting for this solution A LOT! The line /SupportedUnicodeLocales wasn't on my file, but I just created it and DONE! It worked!

Even though the input on QT programs is a bit slow than in GTK ones, it works and the delay isn't so much to be afraid :P

---

