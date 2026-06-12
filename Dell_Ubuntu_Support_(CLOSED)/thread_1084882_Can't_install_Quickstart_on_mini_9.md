---
title: "Can't install Quickstart on mini 9"
date: 2009-03-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pipposanta on 2009-03-02
Hi,
I downloaded Quickstart.sh here and checked the box for execution of the file. But when I try to install it, it only downloads the program and doesn't install itself with this errors:

```
Installing QuickStart... tar: /home/carlotta/Desktop/QuickStart.tar.gz: Impossibile open: Non è una directory
tar: Errore irrimediabile: esco

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Uscita per errore ritardata dall'errore precedente
/home/carlotta/Scaricati/Install_QuickStart.sh: line 51: /home/carlotta/Desktop/QuickStart.desktop: Non è una directory


cp: impossibile fare stat di `/home/carlotta/Desktop/QuickStart.desktop': Non è una directory
```

Sorry if they are in italian.

Thanks in advance for any answer!!

---

### Post by Rallg on 2009-03-02
The error message (if in English) suggests that you did not successfully download the complete file. Try re-download?

---

### Post by pipposanta on 2009-03-02
here the errors in english:

```
Installing QuickStart ... tar: / home / carlotta / Desktop / QuickStart.tar.gz: Can not open: Not a directory
tar: Error irremediable: esco

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from error to previous
/ home / carlotta / Download / Install_QuickStart.sh: line 51: / home / carlotta / Desktop / QuickStart.desktop: Not a directory


cp: unable to stat di `/ home / carlotta / Desktop / QuickStart.desktop ': Not a directory
```

---

### Post by Rallg on 2009-03-02
What I meant was, in any language, it suggests a bad download. There are other possibilities, but that is most likely.

If re-download does not help : Did you get a "nightly build" ? Perhaps the file is corrupt at its server. Try a previous build.

---

### Post by ugm6hr on 2009-03-03
Quickstart is a privately programmed script (i.e. closed source).

It may not work with the Mini 9 version of Ubuntu.

If you need support for it, I think the app author has his / her own forum somewhere.

---

### Post by Sector11 on 2011-06-18
> **ugm6hr said:**
> Quickstart is a privately programmed script (i.e. closed source).

It may not work with the Mini 9 version of Ubuntu.

If you need support for it, I think the app author has his / her own forum somewhere.

[http://quickstart.freeforums.org/](http://quickstart.freeforums.org/)

Unfortunately QS is dead. The site is down. mdpalow went back to Windows for work reasons and it was too difficult maintaining QS to keep up with the 6 month cycles of Ubuntu, Xubuntu and Kubuntu.

I know it's an old thread, but this is the answer being looked for.
Such a great little app too!

---

