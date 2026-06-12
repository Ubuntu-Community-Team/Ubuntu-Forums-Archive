---
title: "What is the wrong with pidgin"
date: 2009-06-19
forum: General Help
---

### Post by gawadelnil2002 on 2009-06-19
I dont know what is the wrong with pidgin it was working very good yesterday and i never had a problem with it , but suddenly yesterday when i was working pidgen stopped working i was using yahoo acount and i couldnt see my contact list it just gave me white page and write connecting on the end of the messenger but it dosnt connect for hours
i removed it purgely with its all dependencies and i installed it again but that didnt change any thing , i removed all ubuntu i swear today morning and i installed fresh copy and now i tried pidgen it dosnt want to open my yahoo acount , i tried msn acount it opened it very late after 5 minutes but yahoo didnt open it for hour, sorry for my bad english but for real i seek for help , i use yahoo everyday and i dont want to be on that yahoo web it dosnt stisfy me plz if some had the same issue and solved it ,he can help

---

### Post by Soul-Sing on 2009-06-19
hmmm, there more issue's with pidgin and yahoo
: [http://ubuntuforums.org/showthread.php?t=1191064](http://ubuntuforums.org/showthread.php?t=1191064)
: [http://ubuntuforums.org/showthread.php?t=973284](http://ubuntuforums.org/showthread.php?t=973284)
Hope this will help you.

---

### Post by Gunman1982 on 2009-06-19
First of all: Calm down. The problem with multiprotocol messengers like pidgin, kopete miranda or trillian is that if one of th eprotocols is changed, i.e. Microsoft changes something in the msn protocol or yahoo changes something in theirs those changes have to be backtraced and ported into pidgin, kopete or whatever.

So just give it a day or two and a new update for pidgin will come eventually and solve that problem. 

You don't need to reinstall ubuntu or even pidgin if something like that happens. Ask first, shoot later ;-)

---

### Post by gawadelnil2002 on 2009-06-19
i installed empathy too now and it dont connect with yahoo , i dont believe im going to be crazy for real i removed all ubuntu for that and installed it again something had happened i dont know it but i think its the updates, that the first time for me i see linux generic image in updates , i dont know mayb that is the cause , scince ubuntu 9.04 have been released i was using pidgen with no problems with yahoo my windows friends when they saw that pidgin can open any account like msn and googletalk they wanted me to install ubuntu for them but now im the great upset one

---

### Post by scrooge_74 on 2009-06-19
I being using Pidgin for years, I have MSN, yahoo, google talk (even had jabber account a while back). From my experience if it can't conect to any of those accounts is their fault not pidgin's or ours.  Same here Yahoo has being having problems conecting for me since about mid day, came back in the evening and now again is having problems.  Other times is MSN the one giving problems.

So I would advice you take it easy on it.

Have fun

This works:

 Re: yahoo blocking pidgin ?
Quote:
Originally Posted by spcwingo View Post
I was having this problem again last night, so I just changed the server I was using. Instead of:

Code:

scs.msg.yahoo.com

I'm using:

Code:

cn.scs.msg.yahoo.com

No more problems since the switch.

---

### Post by gawadelnil2002 on 2009-06-19
> **scrooge_74 said:**
> I being using Pidgin for years, I have MSN, yahoo, google talk (even had jabber account a while back). From my experience if it can't conect to any of those accounts is their fault not pidgin's or ours.  Same here Yahoo has being having problems conecting for me since about mid day, came back in the evening and now again is having problems.  Other times is MSN the one giving problems.

So I would advice you take it easy on it.

Have fun
Thank u for the advice but all i want to ask form all of u now to check ur yahoo acounts on pidgen , if it worked well so the problem is from my computer or my configuration or something else, and if it didnt work with u so the problem is from yahoo protocol and i should wait for the updates ,that will nice if u did that

---

### Post by Gunman1982 on 2009-06-19
> **gawadelnil2002 said:**
> Thank u for the advice but all i want to ask form all of u now to check ur yahoo acounts on pidgen , if it worked well so the problem is from my computer or my configuration or something else, and if it didnt work with u so the problem is from yahoo protocol and i should wait for the updates ,that will nice if u did that

If you would have checked the links in leoquant's post you would have seen that you are not the only one having problems with yahoo at the moment. So wait for the updates.

---

### Post by Therion on 2009-06-19
> **gawadelnil2002 said:**
> Thank u for the advice but all i want to ask form all of u now to check ur yahoo acounts on pidgen , if it worked well so the problem is from my computer or my configuration or something else, and if it didnt work with u so the problem is from yahoo protocol and i should wait for the updates ,that will nice if u did that
If you had read any of the posts in the links provided in the earlier post you would see that, yes, Yahoo IM, via Pidgin is borked because Yahoo! is making some support changes.  There will be an updated version of Pidgin to deal with it.  In the short term see this post for a fix:

[http://ubuntuforums.org/showpost.php?p=7480983&postcount=21](http://ubuntuforums.org/showpost.php?p=7480983&postcount=21)

Worked for me.

---

### Post by gawadelnil2002 on 2009-06-19
> **Gunman1982 said:**
> If you would have checked the links in leoquant's post you would have seen that you are not the only one having problems with yahoo at the moment. So wait for the updates.
i checked the links but i didnt look at the dates sorry, thank u, i will wait for the updates

---

### Post by scrooge_74 on 2009-06-19
Check my previous post, the solution is in the other threads leoquant mentioned.  I changed the server to which yahoo ask to connect and I'm back online

---

### Post by james.wilde on 2009-06-19
And for me.  Thanks to spcwingo.

---

### Post by Therion on 2009-06-19
I'll post this fix one more time since we're on page two now.  

Credit for this fix goes to poster **spcwingo**. 

Change the server from:```
scs.msg.yahoo.com
```
to
```
cn.scs.msg.yahoo.com
```

And you should be able to connect.

---

### Post by gawadelnil2002 on 2009-06-19
> **scrooge_74 said:**
> Check my previous post, the solution is in the other threads leoquant mentioned.  I changed the server to which yahoo ask to connect and I'm back online
i see i changed it too and i was using yahoo 5 minutes ago but the offlines contacts pidgin write beside them not in serever 
and i cant see my picture and i cant see my online contact pictures
i think we should wait updates, it will fix all now im trying to be cold cause i dont know why they chnage protocols

---

### Post by scrooge_74 on 2009-06-19
As long as I can talk to people I dont mind having a few minor annoyances

---

### Post by garuhhh on 2009-06-19
> **Therion said:**
> I'll post this fix one more time since we're on page two now.  

Credit for this fix goes to poster **spcwingo**. 

Change the server from:```
scs.msg.yahoo.com
```
to
```
cn.scs.msg.yahoo.com
```

And you should be able to connect.

this works for me!!
although i also found this [link]("http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo") which explains everything.

---

### Post by kd0afk on 2009-06-22
Adding the PPA did the trick for me.

---

### Post by john_navarro on 2009-06-22
[getdeb.net]("getdeb.net") now has the lastest version of Pidgin that supports the current Yahoo protocol.

---

### Post by kd0afk on 2009-06-22
The PPA fix worked for me until I restarted my computer. I tried to open pidgin but the icon wasn't there. I opened add remove programs and it wasn't checked. I checked it but I got this warning:
[COLOR=Red]Cannot install 'pidgin'

This application conflicts with other installed software. To install 'pidgin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/COLOR][COLOR=Black]

So I switched to synaptic and tried to install it there. I got this error.

[COLOR=Red]pidgin:
  Depends: pidgin-data (<1:2.5.5-z) but 1:2.5.7-1ubuntu1~pidgin3.9.10 is to be installed
 Depends: libpurple0 but it is not going to be installed
[COLOR=Black]
So I tried to install libpurple and I got this error:
[/COLOR][/COLOR][/COLOR]
[COLOR=Red]libpurple-dev:
 Depends: libpurple0 but it is not going to be installed[/COLOR]

This is REALLY messed up.

How can I get pidgin back?

---

### Post by steveneddy on 2009-06-22
> **kd0afk said:**
> Adding the PPA did the trick for me.

YEP - I find it easier to just add the PPA and it will update automatically.

---

### Post by kd0afk on 2009-06-22
> **steveneddy said:**
> YEP - I find it easier to just add the PPA and it will update automatically.
It was easier but when I restarted my computer it vanished. Read my post just before yours.
I worked a bit with the DEB packages and got it back but still, pretty messed up.

---

### Post by wncben on 2009-06-23
Try going to the pidgin website to get the ppa.  I posted instructions here:
[http://ubuntuforums.org/showpost.php?p=7504859&postcount=10](http://ubuntuforums.org/showpost.php?p=7504859&postcount=10)

changing the servers is only a temporary fix as once yahoo updates the servers that still work, the temp fix will no longer function.

Once you install the ppa, it will allow update manager to automatically update pidgin as new versions become available.

~Cheers

---

### Post by obaidmaroof on 2009-06-25
> **kd0afk said:**
> The PPA fix worked for me until I restarted my computer. I tried to open pidgin but the icon wasn't there. I opened add remove programs and it wasn't checked. I checked it but I got this warning:
[COLOR=Red]Cannot install 'pidgin'

This application conflicts with other installed software. To install 'pidgin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/COLOR][COLOR=Black]

So I switched to synaptic and tried to install it there. I got this error.

[COLOR=Red]pidgin:
  Depends: pidgin-data (<1:2.5.5-z) but 1:2.5.7-1ubuntu1~pidgin3.9.10 is to be installed
 Depends: libpurple0 but it is not going to be installed
[COLOR=Black]
So I tried to install libpurple and I got this error:
[/COLOR][/COLOR][/COLOR]
[COLOR=Red]libpurple-dev:
 Depends: libpurple0 but it is not going to be installed[/COLOR]

This is REALLY messed up.

How can I get pidgin back?

same problem with me too..........:(((
do u find any solution???

---

### Post by Soul-Sing on 2009-06-25
: [https://launchpad.net/ubuntu/intrepid/i386/libpurple0/1:2.5.2-0ubuntu1.2](https://launchpad.net/ubuntu/intrepid/i386/libpurple0/1:2.5.2-0ubuntu1.2)

some information in relation to the conflict between
:  libpurple0
and
:  pidgin-data

---

### Post by chrisj26 on 2009-06-27
I was reading [this post]("http://mattr.info:8080/blog/2009/06/24/kopete-and-yahoo/") and I was wondering whether there's anyway I can get the update. I use GNOME so not to sure how this will affect (KDE update).

---

