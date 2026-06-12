---
title: "Attach file in Thunderbird from Network location"
date: 2009-01-22
forum: General Help
---

### Post by jamesisin on 2009-01-22
I cannot figure out how to do this.  I have network folders present on my Desktop, but when I try to attach a file in Thunderbird those folders do not appear anywhere for me to dig into.

What's the story?

---

### Post by jamesisin on 2009-01-22
By the way, I can drag&drop the file into the mail window and that successfully attaches it.  What I am trying to do (because it saves steps) is click the Attach button and browse to the file to be attached.

---

### Post by jamesisin on 2009-01-22
Oops, sorry, not true.  It APPEARS to attach the file but rather fails miserably:

"There was an error attaching smb://blahblahblah....pdf.  Please check if you have access to the file."

---

### Post by jamesisin on 2009-01-29
Nobody else seeing this one?

---

### Post by wrax on 2009-03-16
EDIT: sorry, wrong thread.

---

### Post by jamesisin on 2009-03-31
Is it really just me and the crickets?

---

### Post by jamesisin on 2009-04-04
How about a little sympathy at least?

---

### Post by winz on 2009-04-30
Yes, I have the same problem (8.04 LTS).

UPDATE: in order to resolve this issue, do apt-get install thunderbird-gnome-support. Checked on 8.04/9.04.

---

### Post by SentientFluid on 2009-04-30
It works completely fine for me.  What version of Ubuntu and Tbird are you using?  At first look it seems to be an smb issue and not Tbird, though.

---

### Post by jamesisin on 2009-04-30
winz - I already have thunderbird-gnome-support installed.  Thanks for the suggestion.

SentientFluid - Supposing it is an SMB issue, what might I do to test or correct it?

I am using Ubuntu 8.10 and Thunderbird 2.0.0.21 on this machine.

---

### Post by dubbelodub on 2009-11-13
Hey I also had this same problem. If you have network shares over SMB 
you can access them in /home/{username}/.gvfs 

If you want to make things easy then go to a terminal and
```
ln -s ./.gvfs network
```

Then you can navigate to your shares by pointing to network from Thunderbird

---

### Post by jamesisin on 2009-11-13
So, this appears to be the shape of the problem.

Thunderbird will fail to attach any file whose path begins "smb://...":

smb://[domain];[user]@[server]/c$/Shares/Users/[user]

A workaround exists by navigating to the same file through "/home/[username]/.gvfs...":

/home/[username]/.gvfs/c$ on [server]/Shares/Users/[user]

Should this be considered an Ubuntu or a Thunderbird bug?

---

### Post by jamesisin on 2009-11-13
> **dubbelodub said:**
> 
If you want to make things easy then go to a terminal and
```
ln -s ./.gvfs network
```


The only trouble I see with your suggestion is that my system also mounts my CD drive in the .gvfs folder, which would mean that under "network" would also be found my local CD drive.

Not horrible; just annoying.

---

