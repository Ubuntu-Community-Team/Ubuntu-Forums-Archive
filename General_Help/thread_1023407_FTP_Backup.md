---
title: "FTP Backup"
date: 2008-12-27
forum: General Help
---

### Post by Eviltechie on 2008-12-27
I was looking for a way to backup /home to [ftp://192.168.2.50/ivan-ubuntu](ftp://192.168.2.50/ivan-ubuntu). (nas on lan)

I tried a program, but it failed because it uploaded 40 gb to 192.168.2.50/null.

Then I thought I'd write/get a script. My first thought was to see if I could do it by hand.

So I started with
```

ftp 192.168.2.50
anonymous

rm ivan-ubuntu

```

This is where it went bad. It gave me an error saying that the directory wasn't empty, and therefore couldn't be deleted. :(

Am I doing this wrong, being stupid, or is it supposed to be like this?

If someone can whip the script up real quick, that would be nice. It must 1)Delete [ftp://192.168.2.50/ivan-ubuntu](ftp://192.168.2.50/ivan-ubuntu) and 2) copy /home to [ftp://192.168.2.50](ftp://192.168.2.50)

Thanks

---

### Post by HermanAB on 2008-12-27
This may help.  It has a FTP scripting example:
[http://aeronetworks.ca/windows-backup.html](http://aeronetworks.ca/windows-backup.html)

Cheers,

Herman

---

### Post by Eviltechie on 2008-12-27
I'm not running windows. (Ubuntu) will this still apply?

---

