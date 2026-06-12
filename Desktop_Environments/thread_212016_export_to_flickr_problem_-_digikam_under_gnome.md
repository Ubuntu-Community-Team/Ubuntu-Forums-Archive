---
title: "export to flickr problem - digikam under gnome"
date: 2006-07-09
forum: Desktop Environments
---

### Post by alexfittyfives on 2006-07-09
Hi,

I'm using the Dapper digikam and kipi-plugins packages under gnome and have noticed that to use the export to flickr plugin, if I need to log in to flickr, digikam complains that:

```

could not launch the browser:

could not find service 'kfmclient'

```

A bit of googling shows that this a command line tool for communicating with konqueror. Sure enough installing konqueror solves the problem but it' not obvious.

is there a way to change it so that it will use firefox or whatever my default browser is? I don't really want to have to install konqueror (and all it's dependencies) just to do this.

Cheers,

---

### Post by gometro33 on 2006-12-18
I have this problem too.  The reason digikam needs to do this is to tell flickr to authorize uploads coming from it.  I've been searching for a way to do this but to no avail...I'll be sure to post back if I get it.

---

### Post by alexfittyfives on 2006-12-18
Hi,

Hmmm. ths was a while back... I've since switched to using f-spot instead of digikam.

However, I seem to remember that the export to flickr plugin assumes that konqueror is installed so it tries to launch it to go through the authorization. So installing konqueror  should fix this.

I think that you might even be able to go through the autorization in another browser (eg firefox) and then skip that step in digikam, can't remember details though.

Hope that helps!

---

### Post by Abdi110 on 2007-04-09
I remember reading a thread somewhere on digikam's forums, or somewhere. It's a known issue and there really isn't a way to work around it other then I think installing konqueror, as Alexfittyfives said.

---

### Post by mindhaq on 2007-05-14
> **Abdi110 said:**
> I remember reading a thread somewhere on digikam's forums, or somewhere. It's a known issue and there really isn't a way to work around it other then I think installing konqueror, as Alexfittyfives said.

For me, this does not work even when Konqueror is installed. When I open Export -> flickr, Konqueror opens, and I can approve Flickruploader. Thing is, I have to do this after every start of the program. Also, I cannot upload any pictures. It takes some time, and then there is an error "wrong signature", whatever that means.

So it seems the settings are not stored, and get lost.

Anyone got a solution? Digikam is really nice, but I don't want to switch to KDE...

---

### Post by orb9220 on 2007-05-14
I use FotoFox extension in firefox. Works great not dependent on program can drag and drop from nautilus,Tag ,see remaining space left to upload,assign to groups,etc...

[https://addons.mozilla.org/en-US/firefox/addon/3945](https://addons.mozilla.org/en-US/firefox/addon/3945)

---

### Post by pjvolders on 2008-05-06
Anybody know how to fix this? I'm having the same problem now...

Cheers,
PJ

---

### Post by pjvolders on 2008-05-11
installing konqueror fixed it...:guitar:

---

