---
title: "Using Wubi to install on Netbook with Atom chip?"
date: 2008-12-10
forum: General Help
---

### Post by 8daysaweek.co.uk on 2008-12-10
I apologize in advance if this is covered elsewhere, but I have searched for "Netbook" and "Atom" etc. but not found an answer.

When looking for an Ubuntu iso the other day I noticed this:
[quote="http://releases.ubuntu.com/8.10/"]Low-Power Intel Architecture MID USB image
For devices using the Low-Power Intel Architecture, including the A1xx and Atom processors.[/quote]

I have successfully installed Xubuntu on my Netbook using Wubi, but would like to try installing the above, via Wubi, if possible.

I know Wubi can use an ISO in its own folder:
[quote=http://wubi-installer.org/faq.php]Can I use an existing ISO/CD instead of letting Wubi download a new one?

Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe.[/quote]

But...
a) this isn't an iso (the file is ubuntu-8.10-mid-lpia.img) and
b) I wonder if it needs its own entry in the Wubi drop-down menu?

So, the question is, is it possible to install this version of Ubuntu using Wubi, or will it be in the near future?  If not, is it possible to achieve the same setup (Ubuntu in Add or Remove Programs) manually?

TIA :),

---

### Post by 8daysaweek.co.uk on 2008-12-15
Any ideas?

---

### Post by Jammanuser on 2008-12-15
> **8daysaweek.co.uk said:**
> 
But...
a) this isn't an iso (the file is ubuntu-8.10-mid-lpia.img) and
b) I wonder if it needs its own entry in the Wubi drop-down menu?

So, the question is, is it possible to install this version of Ubuntu using Wubi, or will it be in the near future?  If not, is it possible to achieve the same setup (Ubuntu in Add or Remove Programs) manually?

TIA :),

If all else fails, u can always **download** an ISO from [HERE]("http://releases.ubuntu.com/8.10/"). And then simply put the ISO in the same folder as "wubi.exe" and run Wubi! ;)

GL and let me know how it goes! :guitar:

Cheers! ):P

Jam Man

:popcorn:

---

### Post by 8daysaweek.co.uk on 2008-12-15
Thanks for posting, I know about that link (as I already referenced it in my post above) that's where I found the other file.

The thing is, the file **isn't an ISO** it's an img file...
> this isn't an iso (the file is ubuntu-8.10-mid-lpia.img)

BFN,

---

### Post by Jammanuser on 2008-12-15
> **8daysaweek.co.uk said:**
> Thanks for posting, I know about that link (as I already referenced it in my post above) that's where I found the other file.

The thing is, the file **isn't an ISO** it's an img file...


BFN,

hmm...it seems like we have a **bit** of an misunderstanding here! :D The link that i gave is to the ubuntu site, where u can **download** the ISO. And of course, i had already noticed what u said about the img file...

That's why i posted an answer suggesting u could maybe try **downloading** an ISO, instead of using the **non-ISO** that u already have! :D

Cheers! ):P

Jam Man

:guitar:

---

### Post by 8daysaweek.co.uk on 2008-12-15
> I have successfully installed Xubuntu on my Netbook using Wubi
I have already downloaded and used K/X/Ubuntu ISO files with Wubi (many, many times).

I was interested in whether there's any way that the img file that is specifically for "devices using the Low-Power Intel Architecture, including the A1xx and Atom processors" can be used with Wubi.

There isn't an ISO provided for Atom processors on the page that you and I have both referenced ([http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)).

Thanks :)

---

### Post by Jammanuser on 2008-12-15
> **8daysaweek.co.uk said:**
> I have already downloaded and used K/X/Ubuntu ISO files with Wubi (many, many times).

[COLOR="Red"]I was interested in whether there's any way that the img file that is specifically for "devices using the Low-Power Intel Architecture, including the A1xx and Atom processors" can be used with Wubi.[/COLOR]

There isn't an ISO provided for Atom processors on the page that you and I have both referenced ([http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)).

Thanks :)

Ok...then in that case, i simply don't know! :D my advice would be to try it, by putting the IMG file in the same folder as "wubi.exe", and then running the Wubi installer. I have serious doubts that that will work...but no harm in trying! :p There may be a way to get Wubi to use that file instead of the usual ISO, and my guess is if there is, it would be in the "advanced options" when installing Wubi, but i couldn't tell u for sure, because i've never done that. Or there may be some way to configure it via the command line, but i can't help u there either.

I guess we'll have to wait then until Ago gets here... ;)

Cheers! ):P

Jam Man

:guitar:

---

### Post by ago on 2008-12-15
> **8daysaweek.co.uk said:**
> 
b) I wonder if it needs its own entry in the Wubi drop-down menu?

Yes and while atom is supported as a processor, any distro (mid in particular) that is not in the current list is not supported.

---

