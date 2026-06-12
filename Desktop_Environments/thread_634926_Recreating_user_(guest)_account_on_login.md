---
title: "Recreating user (guest) account on login"
date: 2007-12-08
forum: Desktop Environments
---

### Post by raid996 on 2007-12-08
Hey all,

Ok here's the situation: I'm building up this network for an internet cafe In Italy. And I have ecountered two main problems:

_1.Logging of internet activity from clients_
In Italy there is an anti terror-law that forces you to have all the logs of internet activity from all the clients. I know it has to come from a proxy server (squid is ok?) but I really have no idea of how to take all those logs and make CD's (that is what the law says that must be done). So basically I don't need all the logs from the server just those from internet request from all the clients...in a few words...who made the request, what url was pinged and at what time those request were made.

**2. Recreating a guest account everytime on login**
The clients are available for the public (of course, duh!) and I want all the history,cookies, logs,config to go away as soon as the client logout from the public machine. That includes: skype account information, amsn account information etc.. etc.. 

When another client comes in and logins and would like him to find all cleaned up, no cookies, no files, no configurations, no nothing... Is it possible to do something like that?

Thanks all:guitar:

---

### Post by bingoUV on 2007-12-08
Suppose guest login name is guest. In file /etc/bash.bashrc , add 
```

cd /home/guest
find -not -name . -not -name .. -exec rm '{}' \;

```

This will delete all files as soon as the user logins. When he starts browser or skype or messenger, his settings files will get created again. 

Note that this will make the files disappear even if he tries to open a terminal, or log in a text console (ctrl - alt - F1 etc). I think it is a good thing for you, but be aware of this.

---

### Post by Blutack on 2007-12-08
[http://www.dnalounge.com/backstage/src/kiosk/](http://www.dnalounge.com/backstage/src/kiosk/)

Bit out of date but the basic principle seems good - basically have a fresh /home/guest that gets copied over on every login, which would then mean you could set custom wallpapers/screensavers/whatever for your cafe.  The gnome lockdown editor is pretty good, and you can remove the guest user from specific groups.
Squid would be a good idea, you could look into Dansguardian as well if you want to use filtering.  The squid log you want is access.log, just bung that on a disc every time it gets big and make sure your clocks are spot on so you can use in it conjunction with cctv if required.
Otherwise there is a specific project here
[http://stlouis-shopper.com/~jtjsoftware/kiosk/](http://stlouis-shopper.com/~jtjsoftware/kiosk/)

---

### Post by raid996 on 2007-12-09
> **bingoUV said:**
> 
Note that this will make the files disappear even if he tries to open a terminal, or log in a text console (ctrl - alt - F1 etc). I think it is a good thing for you, but be aware of this.

I'll make sure to remove all kind of access to terminal and such, thanx, this is exactly what I needed. We need people to do only basic internet stuff such as browsing, chat, skype (maybe...), and such....
Thx, will try asap tomorrow morning!:KS:KS

---

### Post by raid996 on 2007-12-09
> **Blutack said:**
> [http://www.dnalounge.com/backstage/src/kiosk/](http://www.dnalounge.com/backstage/src/kiosk/)

Bit out of date but the basic principle seems good - basically have a fresh /home/guest that gets copied over on every login, which would then mean you could set custom wallpapers/screensavers/whatever for your cafe.  The gnome lockdown editor is pretty good, and you can remove the guest user from specific groups.
Squid would be a good idea, you could look into Dansguardian as well if you want to use filtering.  The squid log you want is access.log, just bung that on a disc every time it gets big and make sure your clocks are spot on so you can use in it conjunction with cctv if required.
Otherwise there is a specific project here
[http://stlouis-shopper.com/~jtjsoftware/kiosk/](http://stlouis-shopper.com/~jtjsoftware/kiosk/)

Checked the whole post down, I had already thought of using LTSP but the owner of the Wine Bar wants a "fat client" for every table so no-go on that one. On the other side, thx for the tip on squid's log to save.... I was wondering, is there a way to have my logs being reset every night when the pc is turned off?
That's because I want to have, at turn-off, a tar.gz backup file with the daily logs, I know how to do this but:
1- how do I tell my ubuntu server to have it done every time it shuts down?
2- how do I make my logs reset after backup (otherwise I'll be having huge backups eith many times the logs of precedent days)

I know it could be easier to have someone just erase the file, the problem is I need to set this thing "stupid-proof"... I just can't trust the owner of the Wine Bar to do things properly....because he wont =_=°°

---

### Post by raid996 on 2007-12-17
> **bingoUV said:**
> Suppose guest login name is guest. In file /etc/bash.bashrc , add 
```

cd /home/guest
find -not -name . -not -name .. -exec rm '{}' \;

```

This will delete all files as soon as the user logins. When he starts browser or skype or messenger, his settings files will get created again. 

Note that this will make the files disappear even if he tries to open a terminal, or log in a text console (ctrl - alt - F1 etc). I think it is a good thing for you, but be aware of this.

Did not work, only messed up my terminal in admin account... any1 else? please, I also tried to sync the home folder with a "clean" home folder I saved in another folder but it just skips the source folder even when I give full access to everybody (777) .
I have already used rsync for many tasks and just this time I cant understand why it keeps behaving this way... no sense at all for me...
Anyway if anyone could give me some more tips would be useful....
thx in adavnce

---

