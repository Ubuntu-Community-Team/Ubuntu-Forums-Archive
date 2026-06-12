---
title: "Yahoo! Messenger under Ubuntu"
date: 2006-06-02
forum: Desktop Environments
---

### Post by xpmaniac4ever on 2006-06-02
Anyone managed to install and succesfully run Yahoo! Messenger 7 under Wine (Ubuntu) ? I install it successfully but get this error when running it:

err:ole:CoGetClassObject no class object {24f3ead6-8b87-4c1a-97da-71c126bda08f} could be created for for context 0x7
fixme:ole:CoCreateInstance no classfactory created for CLSID {24f3ead6-8b87-4c1a-97da-71c126bda08f}, hres is 0x80070002

Any help would be appreciated. Thanks.

---

### Post by simonn on 2006-06-02
Why don't you use gaim?

---

### Post by christhemonkey on 2006-06-02
According to [this]("http://appdb.winehq.org/appview.php?versionId=3693") page, that is about as far as you can get with running it under wine.

[http://help.yahoo.com/help/us/messenger/unix/general/index.html](http://help.yahoo.com/help/us/messenger/unix/general/index.html)
They make a unix version of yahoo messenger as well though apparently.


They offer an rpm though, so you wil have to convert it.
```
sudo apt-get alien
```
```
sudo alien yahoo-messenger.rpm
```
```
sudo dpkg -i yahoo-messenger.deb
```

Other than that, it *should *just work with the linux version.
Though it might not!

---

### Post by jreyst on 2006-06-02
[QUOTE=simonn]Why don't you use gaim?[/QUOTE]
I use Gaim also. I'd like to use Yahoo as it looks like I am unable to receive files when people who are using Yahoo attempt to send files to me via Messenger. I haven't tried installing it under Wine but I did install the Messenger version that Yahoo makes available for Linux... YUCK.

---

### Post by denjin on 2006-06-02
[quote=jreyst]I use Gaim also. I'd like to use Yahoo as it looks like I am unable to receive files when people who are using Yahoo attempt to send files to me via Messenger. I haven't tried installing it under Wine but I did install the Messenger version that Yahoo makes available for Linux... YUCK.[/quote]
Yeah, the linux one they offer is UGLY!!!!  It is an incredible eyesore.

Gaim or kopete are about as good as you're going to get if you use linux and want to logon to yahoo.

---

### Post by xpmaniac4ever on 2006-06-02
[QUOTE=simonn]Why don't you use gaim?[/QUOTE]

Because it doesn`t support the 'Send file' to Yahoo! Messenger clients.

---

### Post by xpmaniac4ever on 2006-06-02
> I use Gaim also. I'd like to use Yahoo as it looks like I am unable to receive files when people who are using Yahoo attempt to send files to me via Messenger. I haven't tried installing it under Wine but I did install the Messenger version that Yahoo makes available for Linux... YUCK.

The Yahoo! Messenger version that Yahoo! puts for download on their site is an ANCIENT version of Yahoo! Messenger. I mean it`s really old. I wonder why they don`t develop YM 7.5 for Linux :-/

---

### Post by tymanthius on 2006-06-02
You can try gyach-ee for file transfer.  It's aim is to do everything yahoo for windows does, I do believe.

Hope that helps.

---

### Post by Rackerz on 2006-06-02
Kopete usually works well, have you tried installing Gaim beta 3? (I think it's beta 3).

---

### Post by eokorie on 2006-06-02
or simple just install vmware, install windows xp and use yahoo from there....  Id rather do things that way to be honest...

---

### Post by johnniecarcinogen on 2006-06-02
[QUOTE=tymanthius]You can try gyach-ee for file transfer.  It's aim is to do everything yahoo for windows does, I do believe.

Hope that helps.[/QUOTE]

Where can I find out more about gyach-ee?

---

### Post by IndigoMontoya on 2006-06-02
Anybody ever have success using a webcam in gyach or another other yahoo linux based program?

---

### Post by jimcooncat on 2006-06-02
[QUOTE=IndigoMontoya]Anybody ever have success using a webcam in gyach or another other yahoo linux based program?[/QUOTE]

I have, but not with sound too. Make sure the webcam works with Camorama first. 

The Gyach-E version I used is from:
[http://www.phrozensmoke.com/projects/pyvoicechat/](http://www.phrozensmoke.com/projects/pyvoicechat/)

I ended up not bothering with Yahoo, but serve my webcam now with camserv; and back to Gaim for chat. I guess I'd rather stick with what's in the official repositories.

---

