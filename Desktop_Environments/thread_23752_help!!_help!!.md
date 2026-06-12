---
title: "help!! help!!"
date: 2005-04-03
forum: Desktop Environments
---

### Post by wxm505 on 2005-04-03
I am new to Ubuntu.I installed Warty4.10 a month ago.Everything was running well.
Then I tried to upgrade it to Hoary. What I did was that I used Synaptic package manager. I reloaded first but I found I could not connect some of the servers.So I 
gave up and close Synaptic.
When I logged out from this session and wanted to log in , it pop up some error
messages:

[COLOR=Navy]/etc/gdm/Pression/Default: Registering your Session with wtmp and utmp
/etc/gdm/Pression/Default: running : /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var
/run/utmo -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "wxm505"
/etc/gdm/Xsession: Begnning session setup .
Unable to read ICE authority file
/home/wxm505/.ICEauthority[/COLOR]

I can not neither log in gnome nor failsafe with this user(the main user).
what I can do is to log in failsafe terminal with this user or  log in gnome
with any other user.

How can I do to fix it??  any help please:(
Thank u very much indeed.

---

### Post by cwaldbieser on 2005-04-04
No need to panic!  Basically, something just went haywire with your X Display Server, and your .ICEAuthority file got locked.  In your home directory, you have this file called .ICEAuthority, and when you start up the X Display server, the file gets changed to being owned by root.  If X doesn't have a chance to shut down properly, then the next time you go to start it up, it thinks you are already using it.

The simple solution is:

```
$ sudo chown wxm505:wxm505 /home/wxm505/.ICEauthority
```

I have found that you can also do the more drastic:

```
$ sudo rm /home/wxm505/.ICEauthority
```

with no ill effects in most cases as well, though the first technique is generally considered preferrable.

---

### Post by wxm505 on 2005-04-04
Cheers mate!!  Problem solved!

another issue is I live in uni and use proxy.
When I upgraded from warty to hoary by synaptic
I can connet all the http server but ftp.
When I chose apt-get update , I can connect all the
ftp servers but http.
There must be something wrong about the proxy setting.
I did set the proxy correctly because I can access internet
successfully. 
Any help??

---

### Post by Gandalf on 2005-04-04
[QUOTE=wxm505]Cheers mate!!  Problem solved!

another issue is I live in uni and use proxy.
When I upgraded from warty to hoary by synaptic
I can connet all the http server but ftp.
When I chose apt-get update , I can connect all the
ftp servers but http.
There must be something wrong about the proxy setting.
I did set the proxy correctly because I can access internet
successfully. 
Any help??[/QUOTE]
 post in one topic please , don't spam

---

### Post by nrayever on 2005-06-05
thanks a lot, i hope a friend of mine can solve his problem, i iwll edit this post if he has success.

thanks!!

---

