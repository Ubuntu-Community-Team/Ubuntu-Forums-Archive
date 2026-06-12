---
title: "Launch firefox via ssh, display on remote machine"
date: 2008-12-05
forum: General Help
---

### Post by Sgurd on 2008-12-05
I have an Ubuntu 8.10 with a virtual guest XP via VirtualBox.

I'd like to pass URLs from XP to the Ubuntu Firefox.

If I SSH from XP to Ubuntu and enter ```
firefox --display=:0.0 http://www.ubuntu.com
``` I get the following error in Ubuntu:

[COLOR="DarkSlateBlue"]Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process, or restart your system.[/COLOR]

Is there a way to tell Firefox to open a new tab in the existing instance?

---

### Post by LateNiteTV on 2008-12-05
try this
```
firefox -new-tab *url*
```

---

### Post by Sgurd on 2008-12-05
> **LateNiteTV said:**
> try this
```
firefox -new-tab *url*
```

Thanks for the reply, but no luck.

```
firefox -new-tab http://www.ubuntu.com
``` returns ```
Error: no display specified
```

and

```
firefox --display=:0.0 -new-tab http://www.ubuntu.com
``` returns the same "[COLOR="DarkSlateBlue"]Firefox is already running...[/COLOR]"

---

### Post by silverglade00 on 2008-12-05
Are you doing an ssh -X virtualbox.machine.address? You can use xming [http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming) to run an xserver in windows so you can just use firefox like normal.

---

### Post by Sgurd on 2008-12-05
> **silverglade00 said:**
> Are you doing an ssh -X virtualbox.machine.address? You can use xming [http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming) to run an xserver in windows so you can just use firefox like normal.

Thanks for the suggestion.  I have considered his, but I'm wanting to use the Firefox (typically already open) 100% within Ubuntu.

---

### Post by bodhi.zazen on 2008-12-05
> **Sgurd said:**
> I have an Ubuntu 8.10 with a virtual guest XP via VirtualBox.

I'd like to pass URLs from XP to the Ubuntu Firefox.

If I SSH from XP to Ubuntu and enter ```
firefox --display=:0.0 http://www.ubuntu.com
``` I get the following error in Ubuntu:

[COLOR=DarkSlateBlue]Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process, or restart your system.[/COLOR]

Is there a way to tell Firefox to open a new tab in the existing instance?

I had to read that twice to understand what you are wanting.

To cut and paste url from guest to host, simply install the Additions in the guest :twisted:

What you are wanting to do, ie, via ssh is actually most difficult because of both X and firefox.

First, with X, it would be a security hole if you could simply access X in this way, you you need to allow your ssh user access to X (which can be done, but is a bit of a pain and I will not cover how to do this here). 

Second, firefox is strange this way. If you start firefox in the ssh session, it actually runs on the guest and is not launched on the server and forwarded to the guest as you would expect.

You have to use the -no-remote flag.

here is a little write up :

[http://www.theopensourcerer.com/2007/11/15/remote-firefox-over-xssh/](http://www.theopensourcerer.com/2007/11/15/remote-firefox-over-xssh/)

Third, to make it worse, firefox does not like it if you open multiple sessions. To do this you need to add a second session.

Run firefox -P and make a second profile :rolleyes:

---

### Post by Sgurd on 2008-12-05
> **bodhi.zazen said:**
> I had to read that twice to understand what you are wanting.
I admit it's, a bit eccentric. :p

[QUOTE=bodhi.zazen]If you start firefox in the ssh session, it actually runs on the guest and is not launched on the server and forwarded to the guest as you would expect.[/QUOTE]
This seems to be the butt of my issue.

[QUOTE=bodhi.zazen]To cut and paste url from guest to host, simply install the Additions in the guest :twisted:[/QUOTE]
This is probably what I'll do, as it'd be easiest.

Thanks for the replies.

---

