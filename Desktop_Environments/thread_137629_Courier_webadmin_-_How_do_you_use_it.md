---
title: "Courier webadmin - How do you use it??"
date: 2006-02-28
forum: Desktop Environments
---

### Post by nuzzy on 2006-02-28
Hi,

I'm an idiot.  I installed courier-webadmin so that I can use a GUI for administration but I have NO IDEA how to run it.  Can someone point me in the right direction?

---

### Post by hippyjim on 2006-03-27
[QUOTE=nuzzy]Hi,

I'm an idiot.  [/QUOTE]

But you're not the only one

[QUOTE=nuzzy]I installed courier-webadmin so that I can use a GUI for administration but I have NO IDEA how to run it.[/QUOTE]

Same here
[QUOTE=nuzzy]Can someone point me in the right direction?[/QUOTE]

It seems not - but I'm bumping this thread just in case!

---

### Post by Zimmer on 2006-03-27
Haven't got the package myself, but are there any readme's in the /usr/doc and usr/share/doc  folders that might help?...

EDIT:  Google turned this up in some text...it may work..
. ACCESSING COURIER-WEBADMIN If your web server has been installed and configured ... be accessed with the following URL: [http://localhost/cgi-bin/courierwebadmin](http://localhost/cgi-bin/courierwebadmin)

---

### Post by hippyjim on 2006-03-29
[QUOTE=Zimmer]Haven't got the package myself, but are there any readme's in the /usr/doc and usr/share/doc  folders that might help?...
[/QUOTE]
Tried that to no avail
[QUOTE=Zimmer]
EDIT:  Google turned this up in some text...it may work..
. ACCESSING COURIER-WEBADMIN If your web server has been installed and configured ... be accessed with the following URL: [http://localhost/cgi-bin/courierwebadmin](http://localhost/cgi-bin/courierwebadmin)[/QUOTE]

I could've sworn I tried that too - just tried it and it works - thanks Zimmer.

---

### Post by Zimmer on 2006-03-30
Glad to be of help, but I guess I just got lucky with the Google search :)....

---

### Post by jabster on 2006-06-17
Anybody care to tell me how to access courier-webadmin from a remote computer?

Google turned up this thread. :-/

thanks,
john

---

### Post by SuburbanWorrier on 2006-11-08
For the record, following the ssl specific instructions in this thread I was able to remotely connect.  There seem to be three options open to you:
[LIST=1]
[*]Access localhost/cgi-bin/courierwebadmin using http
[*]Access <hostname>/cgi-bin/courierwebadmin using https
[*]Access <hostname>/cgi-bin/courierwebadmin using http if you create a file called "unsecureok"
[/LIST]
I couldn't easily choose option 1 as there's no browser installed on that machine (at least none I'd be happy using).
Option 3 seemed appropriate for my private network tinkering but I couldn't figure the correct place to create it based on the instructions I found.
[http://www.courier-mta.org/?install.html~webadmin]("http://www.courier-mta.org/?install.html~webadmin")
I decided to take what initially seems like the most daunting option(2) and this thread made the process a breeze. I followed the steps from below "If you don't want SSL go to the last instructions (dav_svn.conf configurations, and users accounts)." all the way up to (but not including) "Last instruction:
Edit dav_svn configuration file and follow the instructions:"

So here's the thread - if you want want Subversion you'll probably want to follow the whole thing but read the follow-up comments first. [http://ubuntuforums.org/showthread.php?t=51753&highlight=apache+ssl]("http://ubuntuforums.org/showthread.php?t=51753&highlight=apache+ssl")

HTH

Matt

---

### Post by jsd on 2006-12-01
>   3. Access <hostname>/cgi-bin/courierwebadmin using http if you create a file called "unsecureok"
>
> Option 3 seemed appropriate for my private network tinkering
> but I couldn't figure the correct place to create it based on
> the instructions I found.
> [http://www.courier-mta.org/?install.html~webadmin](http://www.courier-mta.org/?install.html~webadmin)

Not that I would recommend it (since the password is sent in clear text over the net) I did manage to get unsecure http to work by creating an empty file called unsecureok in /etc/courier/webadmin (the above page talks about /usr/lib/courier/etc, but the corresponding directory on the Ubuntu install is in fact /etc/courier)

I'm glad to say that the SSL setup described in [http://ubuntuforums.org/showthread.p...ght=apache+ssl](http://ubuntuforums.org/showthread.p...ght=apache+ssl) worked for me too, after which I was able to remove the 'unsecureok' file and operate over SSL

-J

---

### Post by sergematveenko on 2007-05-17
Create file /etc/courier/webadmin/unsecureok and you will be able to access http://<yourhost>/cgi-bin/courierwebadmin from anywhere without ssl

the easiest way to create this file is:
```

sudo touch /etc/courier/webadmin/unsecureok

```

---

