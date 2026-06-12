---
title: "Cannot change locale"
date: 2012-04-28
forum: Desktop Environments
---

### Post by hurryUpHarry on 2012-04-28
hi all

I'm running Ubuntu 11.04 in a VirtualBox with xfce. I cannot seem to set the locale for utf8. This started because I wanted to checkout zsh, which has more options for prompts etc. As you can see from the outputs below, it's looking pretty crummy so far because of the locale settings. Here the various outputs/file contents I have:

```
&#65533;&#65533;&#65533;  ~  locale
LANG=
LANGUAGE=
LC_CTYPE=
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

&#65533;&#65533;&#65533;  ~  cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG=en_CA.utf8
LANGUAGE=en_CA:en
LC_ALL=en_CA.utf8

&#65533;&#65533;&#65533;  ~  cat /etc/default/locale
LANG="en_CA.utf8"
LANGUAGE="en_CA:en"
LC_ALL="en_CA.utf8"

&#65533;&#65533;&#65533;  ~  LANG=en_CA.UTF-8
&#65533;&#65533;&#65533;  ~  locale
LANG=
LANGUAGE=
LC_CTYPE=
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=


```I have tried 'sudo dpkg-reconfigure locales', but it did not make a difference. Also, I have rebooted after making these changes.

I also have:

LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LC_ALL=en_CA.UTF-8

in my .zshrc file. I am also not sure if the settings should have quotes around them or not. Also, I do have 'en_CA.utf8' in the list when I do 'locale -a' 

Anyone know what I'm doing wrong? Sorry if it's something obvious and I honestly have tried to find this particular problem in forums but no luck.

Thanks.

---

### Post by hurryUpHarry on 2012-04-30
As an update, I now have the following showing up for locale:

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$ locale
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=en_CA.UTF-8

I have removed all entries from /etc/default/locale, and my /etc/environment looks like this:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_CA.UTF-8"
LC_ALL="en_CA.UTF-8"

Also I have the following in my .zshrc:

export LANG="en_CA.UTF-8"
export LC_ALL="en_CA.UTF-8"
export LANGUAGE="en_CA:en"

Note I have added 'export' to these lines. I know that it is the .zshrc lines that are controlling what I see in the 'locale' output, because when I take them out, the output reverts to "POSIX".

Clearly the entries in /etc/default/locale were not having any effect, and /etc/environment is not being read when gnome-terminal starts, I don't think.

I'm not sure if I was yet using gnome-terminal when I opened this thread, I think I was still using xfce-terminal. So now I can use 'Terminal->Set Character Encoding' in gnome-terminal to switch from the default of 'ANSIX3.4-1968' (no idea where it gets that from) to 'Unicode ( UTF-8 )'. When I do that and hit return, I see the prompt as intended:

&#9581;&#9472;paul 10:24  ~ 
&#9584;&#9472;$

But I have to do that everytime I open a terminal. Not the end of the world, but it seems all I have to do is get it do default to UTF-8 in the first place.

I'm assuming this is something simple, any ideas?

Just to clarify my setup, I am running VirtualBox  v4.1.14 on Mac OS X 10.6.8, and it's Ubuntu 11.10 from alternate ISO install. I installed just the command prompt version to begin with, then added Xorg, Xterm, Slim, Fluxbox and finally Xfce4.

Thanks

---

### Post by hurryUpHarry on 2012-05-04
So after some more investigation, I figured this out. To recap, I found that no terminals, whether xfce4-terminal, gnome-terminal, XTerm, etc, were displaying in utf8, so my nice new zsh prompt was all mangled. I ended up using gnome-terminal as at least I could use the menu Terminal->Set Current Encoding to switch to UTF-8 (from the selected current locale ANSIX4.3-1968 ).

However as locale reported I was all set up for UTF-8, this did not make sense. It turns out it is to do with the order in which settings are read upon login. I posted my /etc/environment contents in the previous post, but I needed something earlier in the process. So I added the first two lines to my ~/.initrc:

export LANG=en_CA.UTF-8
export LC_ALL=en_CA.UTF-8
exec /usr/bin/startxfce4

and now all is good! Hopefully this can help someone sometime, as it took me a while to figure out and apparently is not widely known/understood.

---

