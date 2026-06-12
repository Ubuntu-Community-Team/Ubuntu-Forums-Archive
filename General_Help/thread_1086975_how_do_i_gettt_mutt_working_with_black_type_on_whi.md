---
title: "how do i gettt mutt working with black type on white?"
date: 2009-03-04
forum: General Help
---

### Post by kline on 2009-03-04
I just installed mutt on my Ubuntu desktop; it's been on my main, BSD desktop for years.  Trouble is that here, mutt shows up in my Konsole as black with a white font and I'd like the reverse. Can anybody help me figure out which file to edit so that mutt displays a white bg and black type?  tia, guys.

---

### Post by brian_p on 2009-03-04
> **kline said:**
> I just installed mutt on my Ubuntu desktop; it's been on my main, BSD desktop for years.  Trouble is that here, mutt shows up in my Konsole as black with a white font and I'd like the reverse. Can anybody help me figure out which file to edit so that mutt displays a white bg and black type?  tia, guys.

```
editor ~/.muttrc
```

On my system:

```
less /etc/Muttrc.d/colors.rc
```

Also:

```
less /usr/share/doc/mutt/manual.txt.gz
```

or the F1 key when mutt is displayed.

---

### Post by kline on 2009-03-05
Thanks for your help.  I did find the /etc/Muttrc, but didn't look in the Muttrc.d directory.  Should have.  I've altered the colors file but still, the best I can do is get grey/gray rather than black.  The text of the mail is black on a white bg; but there are areas of grey+white elsewhere.  If you know how I can get a plain white bg with black font, will you kindly clue me in!

Anyway, thanks again; it helps alot!

gary

---

### Post by brian_p on 2009-03-05
> **kline said:**
> 

The text of the mail is black on a white bg; but there are areas of grey+white elsewhere.  If you know how I can get a plain white bg with black font, will you kindly clue me in!

This may not suit you in all respects:

```
color normal     black white
color attachment brightyellow white
color hdrdefault blue white
color indicator  yellow white
color markers    brightred white
color quoted     yellow white
color signature  cyan white
color status     white blue
color tilde      yellow white
color tree       magenta white
color body       brightyellow white   [\-\.+_a-zA-Z0-9]+@[\-\.a-zA-Z0-9]+
color body       brightblue white  (https?|ftp)://[\-\.,/%~_:?&=\#a-zA-Z0-9]+
```

I think a pure white background may not be achievable.

---

### Post by kline on 2009-03-06
> **brian_p said:**
> This may not suit you in all respects:

```
color normal     black white
color attachment brightyellow white
color hdrdefault blue white
color indicator  yellow white
color markers    brightred white
color quoted     yellow white
color signature  cyan white
color status     white blue
color tilde      yellow white
color tree       magenta white
color body       brightyellow white   [\-\.+_a-zA-Z0-9]+@[\-\.a-zA-Z0-9]+
color body       brightblue white  (https?|ftp)://[\-\.,/%~_:?&=\#a-zA-Z0-9]+
```

I think a pure white background may not be achievable.

This is something like what is in my ~/.mutt/muttrc file on my FreeBSD system, and also what I edited the /etc/Muttrc.d/colors* file to.  When I type 

% mutt

it comes up in part light-grey, with colors, but when I reply to an email, then *yes* then konsole is all white!  thanks for your help.

gary

---

### Post by Dr Small on 2009-03-06
> **kline said:**
> This is something like what is in my ~/.mutt/muttrc file on my FreeBSD system, and also what I edited the /etc/Muttrc.d/colors* file to.  When I type 

% mutt

it comes up in part light-grey, with colors, but when I reply to an email, then *yes* then konsole is all white!  thanks for your help.

gary
Did you put that in your ~/.muttrc file?

---

### Post by kline on 2009-03-06
> **Dr Small said:**
> Did you put that in your ~/.muttrc file?

yeah, it was the first thing i did after playing with the glocal colors file.  i'm happy with the initial list being displayed with a grey bg as long as vi/nvi/vim is exec'd correctly.

---

