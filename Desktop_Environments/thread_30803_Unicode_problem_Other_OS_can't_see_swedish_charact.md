---
title: "Unicode problem? Other OS can't see swedish characters."
date: 2005-04-30
forum: Desktop Environments
---

### Post by stoffe on 2005-04-30
Hello, I have a problem. When communicating with other people sitting on other operating systems, primarily Windows but I think Mac also, they can't see swedish characters (åäöÅÄÖ) displayed properly. This is not true for all means of communication: doing ICQ via GAIM for instance, seems to work just fine no matter what the other side uses, but sending mail (I use gmail, so it is via Firefox)  yields strange letters on the other side, like Ã¶ and Ã¥ and doing IRC via several ways, both Chatzilla and via GAIM gives similar result, although I think the escapes might be different sometimes. 

I do think that it is mainly the clients (IRC, mail, browser, whatever they use) on the other sides that can't handle unicode properly and that it is their escapes that are seen; I can see thier characters just fine. However, since I'm the only one all of my contacts see having problems, it is a bit of a hard time convincing them that I'm doing "the right thing" especially since I can't provide them with any "just do X" solutions - in fact I have no idea if there even exists solutions in several cases.

So, can I disable unicode on my side somehow? Preferably globally, so I don't need to think about it? I'd just like to use Western European coding or whatever is commonly in place.

I do realize that unicode is the future, and want to use it, but as it is now I'm hardly promoting it by using it, as everyone just sees it as something wrong. Furtermore, I use and want to continue to use this computer for business work, writing and contacts, so I need to fix this somehow on my end, I think.

Or maybe there is some other kind of problem - either way, does anybody recognize this and know of some kind of solution? It would be much appreciated.

---

### Post by jobezone on 2005-04-30
you can reconfigure your locales by doing:
"sudo dpkg-reconfigure locales"

---

### Post by stoffe on 2005-04-30
[QUOTE=jobezone]you can reconfigure your locales by doing:
"sudo dpkg-reconfigure locales"[/QUOTE]Thanks, this looks helpful, although I'm still not sure what I should reconfigure to?

I want my system and all its messages to be in English (for several reasons, but mostly because that is how I like it, and many things have no translation, the mix gives me headaches). All incoming email, IM and so forth that I know of displays just fine no matter what characters or originating program/OS. 

But I want my machine to send out characters that other (probably half-broken but very common) programs on other OS can display correctly - most importantly åäöÅÄÖ which are specific to Sweden, but I occasionally also write some sentences in German (ü).

My keyboard uses the Swedish layout. My locale.gen (mentioned in the command you showed me) looks like this:```
en_US ISO-8859-1

en_US.UTF-8 UTF-8
```

If there is more info I can provide, just tell me where to get it and I will. :)

Does this make any sense? Can it be fixed? It's pretty important for me to be able to communicate in a way that looks serious, but I'd also like to be able to use Ubuntu. I'm very attached to this particular OS nowadays. :)

---

### Post by jobezone on 2005-04-30
Those two locales are the ones you have generated, only one is the default, and if you installed Hoary it should be the UTF-8 one. The command I showed you allows you to change the system's default, but this is maybe not what you want?

Firefox allows to change the encoding you want to use to see webpages, but I guess gaim doesn't?(haven't searched for it)
I use it, and so far no one has complained of problems like yours to me, and they use MSN messenger. And I also use letters like ç and ã . But maybe they just haven't complained... Anyone else has this happening to them?

---

### Post by jobezone on 2005-04-30
Forgot to mention, to **not** use UTF8, choose the following as the default, when running
dpkg-reconfigure locales:

en_US ISO-8859-1

---

### Post by stoffe on 2005-04-30
[QUOTE=jobezone]Those two locales are the ones you have generated, only one is the default, and if you installed Hoary it should be the UTF-8 one. The command I showed you allows you to change the system's default, but this is maybe not what you want?[/QUOTE]To be honest, I'm not completely sure what I want. :) Character sets and encoding is a strange and fearsome jungle, where there seems to be few certain paths...

It might be that I want to change my systems default, if that means my system will send characters in an encoding the world in general will be able to see and understand. Like I've said before, I strongly suspect that the problem is that programs and/or OS:s out there can't handle unicode properly. I haven't investigated enough, but it is probably programs like mIRC and Outlook Express (or similar, don't take this as truths, just guesses) that are the culprits - they are extremely common, and quite possibly ignores any such features because in their view most don't need it. And the regular user does not request it either, because they only know that "some guys Linux box sends strange letters, all my Windows friends send correct ones". 

Like I said, everything works on my side: I see the correct letters no matter who send and from what, I can input the correct letters with the correct layout on keyboard, and I have my systems messages in English so they're readable. But for some, emails and IRC (and probably other things) come out garbled on the other side.[QUOTE=jobezone]Firefox allows to change the encoding you want to use to see webpages, but I guess gaim doesn't?(haven't searched for it)[/QUOTE]Yep, but there's never any problem viewing any messages on my side. Does that encoding change the input too? If so, it could be a workable workaround, until next program misbehaves - that is why I wish for a global solution if available, will settle for local tweaks if that is it. :)[QUOTE=jobezone]I use it, and so far no one has complained of problems like yours to me, and they use MSN messenger. And I also use letters like ç and ã . But maybe they just haven't complained... Anyone else has this happening to them?[/QUOTE]No problem in ICQ either, which is what I usually use GAIM for, only time GAIM has a problem is with IRC, and that is the same if I try to go via Firefox (chatzilla). Also, mails I send via webmail is broken for some clients, but not for me if I mail myself and view it on Windows. That is one of the reasons I suspect that some programs on the other side is broken (say mIRC or whatever) but since they aren't gonna change, I want to "downgrade" my system. I don't need more than a western european encoding, so I can do without UTF-8 if needs be.

Hope that makes my wishes a bit more clear - hard to explain when not sure what is the problem. :)

Maybe I should just change my systems default? Will that affect what language my system speaks to me (ie LANG)? And will it affect what my programs send, by changing what is input into them? If so, that sounds like what I want. Any suggestions what I should change it into for a Swedish locale?

Thanks for your patience, it is much appreciated.

---

### Post by jobezone on 2005-04-30
Changing the system default locales to en_US ISO-8859-1 will keep your system english (from the US) and in the ISO-8859-1 enconding, which actually is the one I had been using in linux up until I upgraded to Hoary in Ubuntu. See if it solves the problem.

About firefox, I don't know if it changes the encoding of text you write (and send to other people). And now I remember I've seen what you mention in a e-mail sent to me: what I had written was very much screwed up. I've changed the locale of firefox to ISO-8859-1, but haven't tested if it happens again.

If you want, try asking what programs your friends use, and then go check the program's websites to see if they handle utf-8. I think windows uses utf-8 for a long time now, but I'm not sure.

---

### Post by MrMunson on 2005-05-26
Sweet thread! Sorted me right out! THX a bunch!

Ran the terminal configuration app mentioned above and chosed the ISO8859-1 set (as deafault as well).

---

### Post by orbital on 2008-02-20
When I run sudo  dpkg-reconfigure locales i only get:

```
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

```

How am I supposed to change locales? I need to change the UTF-8 (curtrent locale) to ISO 8859-1 in gnome-terminal, but everytime I run the terminal I get UTF-8 (and need to change the locale manually).

---

