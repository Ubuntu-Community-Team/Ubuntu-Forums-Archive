---
title: "engage problem in Gnome"
date: 2006-03-16
forum: Desktop Environments
---

### Post by lizardking on 2006-03-16
Hello folks
I installed E17 from this repostitory
```
deb http://soulmachine.net/breezy unstable/
```
and all ok.
Then I tryed to follow [this guide]("http://www.bootlog.cl/archives/2005/11/barrita_mac_ubuntu.html") in spanish (i'm italian)
to run engage on Gnome.
All goes well instead of the result I got this
in the attachement.
[B]As you can see from the file i have onyl half engage.
where is the upper part of that?[/B]

some help,please? :-k 
thanx

---

### Post by nalmeth on 2006-03-16
I couldn't figure out how to get engage, and kind of gave up on it. Can you direct me where to get it? I used to know spanish, but that was a long time ago.. :oops: Then I will try it and find out if I have the same problem.

Is there a repository or do you have to compile it?


Does it have the same problem in E17? Maybe its not meant to be run in gnome?

---

### Post by lizardking on 2006-03-16
[QUOTE=nalmeth]Does it have the same problem in E17? Maybe its not meant to be run in gnome?[/QUOTE]
[Binary fromt the repository]("http://www.soulmachine.net/wiki/index.php?title=Enlightenment_on_Ubuntu_5.10_%28Breezy_Badger%29")
but now I hacked a bit and don't work me E17 too
When I start it I go in segmentation fault!
[-(

---

### Post by nalmeth on 2006-03-16
Hmm i'll need a little time to set this up it seems. Engage totally screwed up gnome. In enlightenment the bar was there but no icons, only question marks. Have to 'populate ~/.e/enlightenment/engage'

Do you get any negative terminal output you can post? I'm getting this:

```
***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        This program is calling:

        ewl_callback_append();

        With the parameter:

        w

        being NULL. Please fix your program.
engage: symbol lookup error: engage: undefined symbol: ewl_menu_separator_new
```


I want to get this working too, so I will pick away at it today.  I'm certainly not getting the same problem as you from the get'go

---

### Post by nalmeth on 2006-03-16
what kind of files should populate ~/.e/enlightenment/engage ? EAP's?
I can't find very good documentation for engage

---

### Post by bijoux on 2006-03-16
[QUOTE=lizardking]Hello folks

[B]As you can see from the file i have onyl half engage.
where is the upper part of that?[/B]

some help,please? :-k 
thanx[/QUOTE]

looks like engage background is too small thus cutting it in half. try passing -H 100 see what it does.  for more options, type engage -h

---

