---
title: "changing date format globally"
date: 2005-12-25
forum: General Help
---

### Post by vanden on 2005-12-25
Hi all,

brand new to Linux, and have had Ubuntu on my box for 2 days. I'm liking it, but for the things I can't figure out how to change :-)

A key one for me is date formatting. I want all applications to use ISO formatted dates (i.e., 2005-12-25 05:05). Most forum posts that I have seen that touch on this (e.g. <http://ubuntuforums.org/showthread.php?t=83181>) suggest changing to an entire locale with the desired format. That seems a heavy-handed kludge; I do want much of my locales settings after all.

With some help on irc, I *think* I've worked out that /usr/shar/i18n/locales/en_CA is where my locale (English -- Canada) lives. It has chunks that look like:

```
date_fmt	"<U0025><U0061><U0020><U0025><U0062><U0020><U0025><U0065>/
<U0020><U0025><U0048><U003A><U0025><U004D><U003A><U0025><U0053><U0020>/
<U0025><U005A><U0020><U0025><U0059>"
```

I recognize the string as some for of unicode. What I would like to know is:

1) Am I right in thinking that changes here will allow me to selectively alter the locale settings?

2) Do I risk things blowing up if I try?, and

3) As I know very little about unicode, I'm not sure how I'd go about changing it. I would certainly need to know the encoding. If (1) and (2) are favourable, any suggestions for how to proceed?

Or, am I going abou this the hard way?

Thanks for any help.

---

