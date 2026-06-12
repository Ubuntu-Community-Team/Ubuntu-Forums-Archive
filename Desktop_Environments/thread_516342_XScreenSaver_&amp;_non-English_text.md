---
title: "XScreenSaver &amp; non-English text"
date: 2007-08-03
forum: Desktop Environments
---

### Post by kratib on 2007-08-03
I'm using Ubuntu Feisty and XScreenSaver 4.24 as a replacement to the standard Gnome ScreenSaver. My problem is this: I want to display non-English text in the hacks that output text, like Noseguy. When I write non-English text (Latin accents for example) in xscreensaver-demo's Advanced Tab > Text Manipulation section, the noseguy displays what you see attached here. Same thing happens if I point to an RSS feed that contains non-English text. 

`xscreensaver-text` says:
> 
éééééfééé


`locale` says:
> 
LANG=en_US.UTF-8
LANGUAGE=en_US:en
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


How can I go about troubleshooting and fixing this?  Thanks for your help.

---

### Post by kratib on 2007-08-03
A little more digging in XScreenSaver code revealed the following:

1. noseguy.c uses XDrawString() to display text. The Debian intro to i18n ([http://www.debian.org/doc/manuals/intro-i18n/ch-output.en.html#s-output-x-xlib](http://www.debian.org/doc/manuals/intro-i18n/ch-output.en.html#s-output-x-xlib)) suggests replacing XDrawString() with either XmbDrawString(), XwcDrawString() or Xutf8DrawString(). Other functions also need replacing. Question: does XTextWidth() need a Unicode replacement?

2. xscreensaver-text is a Perl script that fetches the text to be displayed from a file or from a URL. Right now, the script transforms UTF-8 chars fetched into Latin1. 

All of which says that the XScreenSaver system is not i18n-ready by any stretch :-)

---

### Post by kratib on 2007-08-17
Find some working code on my blog: [http://infojunkie.dyndns.org/xscreensaver_unicode](http://infojunkie.dyndns.org/xscreensaver_unicode) :-)

---

