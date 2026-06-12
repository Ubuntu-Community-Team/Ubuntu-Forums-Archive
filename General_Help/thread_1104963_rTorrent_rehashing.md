---
title: "rTorrent rehashing"
date: 2009-03-24
forum: General Help
---

### Post by djungelmums on 2009-03-24
I've got a question regarding rTorrent.

Whenever i reboot my computer and start up rTorrent, the client wants to rehash all my torrents again. This is annoying since I've got more than 600GB torrents seeding and it takes a while rehashing them all.

Is'nt there a way to bypass rehashing torrents it has already hashed before?

Thank you!

---

### Post by 3Miro on 2009-03-24
I don't know for sure, but it might be something about rTorrent. I personal prefer KTorrent (one of the reasons why I am running KDE).

---

### Post by lovinglinux on 2009-03-24
> **3Miro said:**
> I personal prefer KTorrent (one of the reasons why I am running KDE).

As far as I know, you can run Ktorrent with Gnome. In fact, I think you can run any K application.

I prefer Deluge.

---

### Post by x33a on 2009-03-24
you have to quit rtorrent first, then reboot.

rtorrent rehashes if crash/reboot occurs when a torrent is active.

---

### Post by prem1er on 2009-03-24
> **djungelmums said:**
> I've got a question regarding rTorrent.

Whenever i reboot my computer and start up rTorrent, the client wants to rehash all my torrents again. This is annoying since I've got more than 600GB torrents seeding and it takes a while rehashing them all.

Is'nt there a way to bypass rehashing torrents it has already hashed before?

Thank you!

rTorrent does this as a security measure to make sure that none of your files are corrupt. There is no way to stop this process.

**sorry didn't read the post before mine.  exactly what x33a said.

---

### Post by djungelmums on 2009-03-24
Aha ok. Is there a way to make rtorrent quit in the correct way when i press reboot?

---

### Post by 3Miro on 2009-03-24
Hm, I was using BitTornado before and I had the rehashing issue, since I have only one or two small torrents, it wasn't a problem. Now am using Ktorrent and even if I reboot the computer, it starts back on without delay. I guess Ktorrent integrates with KDE and thus exits properly when I tell KDE to reboot.

---

### Post by x33a on 2009-03-24
> **djungelmums said:**
> Aha ok. Is there a way to make rtorrent quit in the correct way when i press reboot?

press ctrl+q to quit rtorrent.

or for individually stopping a torrent, select the torrent and then ctrk+k.

---

### Post by djungelmums on 2009-03-25
It rehashed after reboot even when i clicked ctrl+q first :(

---

### Post by RansomStark on 2009-03-25
Switch to deluge, I don't have this issue.

---

### Post by lovinglinux on 2009-03-25
> **RansomStark said:**
> Switch to deluge, I don't have this issue.

I agree. Deluge is awesome. It has all important features, has a nice interface and it's simple to configure.

---

### Post by x33a on 2009-03-25
have you set a sessions directory in config file ~/.rtorrent.rc?

---

### Post by djungelmums on 2009-03-25
I want to be able to control it via an terminal and ssh.


Anyone got a solution? :)

---

### Post by djungelmums on 2009-03-25
> **x33a said:**
> have you set a sessions directory in config file ~/.rtorrent.rc?

Yes i have. Thats the only way i use rTorrent.

---

### Post by lovinglinux on 2009-03-25
> **djungelmums said:**
> I want to be able to control it via an terminal and ssh.


Anyone got a solution? :)

You can control Deluge from the terminal, but I'm not sure what you can and cannot do, because I'm using an old version. It also has Webui.

[http://dev.deluge-torrent.org/wiki/Faq](http://dev.deluge-torrent.org/wiki/Faq)

---

### Post by djungelmums on 2009-03-25
> **x33a said:**
> have you set a sessions directory in config file ~/.rtorrent.rc?

Is this a problem? :P

---

### Post by x33a on 2009-03-25
no it's not a problem, in fact it's needed to remember the state of the torrents. i thought this rehashing problem was related to it being absent.

well ctrl+q should have worked, i have tested it myself. either you are doing it wrongly or there is a bug.

could you please tell how you start and quit rtorrent and post your config file here.

---

### Post by djungelmums on 2009-03-26
screen rtorrent
ctrl + q

[http://paste.ubuntu.com/138471/](http://paste.ubuntu.com/138471/)

Thank you for helping me :)

---

### Post by x33a on 2009-03-26
you said that you had set a sessions directory, but the config file doesn't say so :)
```

# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

[B]# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = ./session[/B]

```copy and paste this in your config file.
```

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = ~/.session
```and you haven't enabled encryption, if you want to, then copy/paste this too, to the .rtorrent.rc file
```
encryption = allow_incoming,enable_retry,try_outgoing
```

---

### Post by djungelmums on 2009-03-27
What does sessions do?

---

### Post by x33a on 2009-03-27
The sessions directory stores the active state of a torrent.

since you haven't set a sessions directory, rtorrent doesn't remember the state of the torrents and hence, it does a hash check.

so do as i mentioned in the previous post, and the hash check shouldn't happen after every time you start rtorrent.

---

### Post by Xiong Chiamiov on 2009-03-27
I believe that, after enabling sessions, you'll still have to quit rtorrent properly for it not to hash-check on start.  Don't take my word for it, though, since I never stop rtorrent.

> **RansomStark said:**
> Switch to deluge, I don't have this issue.
Deluge also requires a GUI, and uses more (if still low) resources.  If the OP is using rtorrent, he certainly has heard of deluge, and chosen rtorrent over it for some reason.

---

### Post by x33a on 2009-03-27
> **Xiong Chiamiov said:**
> I believe that, after enabling sessions, you'll still have to quit rtorrent properly for it not to hash-check on start.
yes, i mentioned that earlier. if we force quit rtorrent, or the computer crashes/restarts then it'll do the hash check.

but if, ctrl+q or ctrl+k and then ctrl+q is pressed, then there shouldn't be a problem.

---

### Post by djungelmums on 2009-03-27
Thank you very much! For some reason i thought schedule was session, just me remembering wrong. 

With the encryption options you showed me - whats the priorities? Will it only choose encrypted connections or will it take unencrypted connections if theres no other using encryption?

Thank you.

---

### Post by x33a on 2009-03-27
first, use it in the order i mentioned, as order is important.

secondly, you'll be able to connect to both encrypted and unencrypted peers with these options, so no drop in speed :popcorn:

---

### Post by djungelmums on 2009-03-27
Thank you for all your help!

---

