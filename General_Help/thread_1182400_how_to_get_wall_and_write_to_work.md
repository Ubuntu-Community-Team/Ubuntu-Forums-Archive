---
title: "how to get wall and write to work?"
date: 2009-06-08
forum: General Help
---

### Post by kmclaugh on 2009-06-08
Hello all.

I'm running Kubuntu 8.04 hardy on my desktop. I have a cron job that runs nightly and checks the free space on my disk drives. It is run through root, and sends an email to my user account if the disk is getting full. I rarely check my system mail, so I want to change it to instead write to my terminal. 

This should've been easy to accomplish using wall or write, but strangely neither seems to work locally. That is, if I'm logged in remotely (or ssh localhost), then the remote terminal will get wall and write messages. Otherwise they seem to get lost in space.

Any clue?

---

### Post by upbeat.linux on 2009-06-09
Could you post your code here?

---

### Post by kmclaugh on 2009-06-10
> **upbeat.linux said:**
> Could you post your code here?

Open a few terminal windows. In one of them:

```
su -
echo "blah blah blah" | wall
```

and only users logged in via ssh get the message.

---

### Post by kmclaugh on 2009-06-14
Someone must know what the deal is with this! I spent 2.5 hours on Google and found nothing.

---

### Post by upbeat.linux on 2009-06-30
Sorry about the slow reponse been ridiculously busy.

Anyhow, I think the mesg flag defaults to off for terminal whereas it is on for ssh.

You can disable and enable the message value by doing

```
mesg n
``` 

or

```
mesg y
```

To check the status of the message flag do:

```
mesg
```

For further info:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?mesg](http://unixhelp.ed.ac.uk/CGI/man-cgi?mesg)

---

### Post by kmclaugh on 2009-06-30
> **upbeat.linux said:**
> Sorry about the slow reponse been ridiculously busy.

Anyhow, I think the mesg flag defaults to off for terminal whereas it is on for ssh.

You can disable and enable the message value by doing

```
mesg n
``` 

or

```
mesg y
```

To check the status of the message flag do:

```
mesg
```

For further info:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?mesg](http://unixhelp.ed.ac.uk/CGI/man-cgi?mesg)

Thanks for the response. No help though. I had already tried that.

[CODE]$ mesg y
$ echo hi | wall
[\CODE]

Produces no output.

I assume that it works fine on your box though? If so, then I won't worry about it. I'm about to upgrade. I'll make sure to add "mesg y" to /etc/bashrc.

---

### Post by kmclaugh on 2009-07-09
> **kmclaugh said:**
> Thanks for the response. No help though. I had already tried that.

[CODE]$ mesg y
$ echo hi | wall
[\CODE]

Produces no output.

I assume that it works fine on your box though? If so, then I won't worry about it. I'm about to upgrade. I'll make sure to add "mesg y" to /etc/bashrc.

I've upgraded to 9.04 and the same problems exists...

---

