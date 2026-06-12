---
title: "Evolution showsTo/CC/BCC fields odd with Exchange MAPI &amp; AutoComplete question"
date: 2009-08-06
forum: Desktop Environments
---

### Post by doyama on 2009-08-06
So I've finally gotten the Evolution Exchange MAPI plugin to work using IP addresses instead of DNS entries. And it generally works ok. However I have 2 nagging issues that makes it difficult to user

1) The To/Bcc/cc fields seem to munge the names if there is more than one email! Thus doing a reply or reply all can be sketchy This is an example of how one of my headers looks within the Evolution GUI

```
From: 	Sladek, Seth <Sladek>
Reply-to: 	"Sladek, Seth" <Sladek, Seth>
 To: 	Sladek, Seth <Sladek>, Seth>,Doherty, Steve <Doherty>, Steve>,Heistand, David <Heistand>, David>,Frantzis, Ion-Nicholas <Frantzis>, Ion-Nicholas>,Doyama, Jason <Doyama>, Jason>,LaPlante, James <LaPlante>
```

Looking at the messages source with CTRL+U shows this

```
To: "Sladek, Seth" <Sladek, Seth>, "Doherty, Steve" < Doherty, Steve>,  "Heistand, David" < Heistand, David>, "Frantzis, Ion-Nicholas" < Frantzis, Ion-Nicholas>,  "Doyama, Jason" < Doyama, Jason>, "LaPlante, James" < LaPlante, James>
```

So it appears that the original message source is ok, but for some reason it gets mangled within Evolution?

2) May be related to 1 but I cannot get address autocomplete to work. I've tried enabling a few settings but they do not seem to do anything. Is there a specific keyboard shortcut I should be using? 

Thanks

---

### Post by damageco on 2009-08-09
Hi ! Just a little up to say that I've got exactly the same problem dans question. :)

---

