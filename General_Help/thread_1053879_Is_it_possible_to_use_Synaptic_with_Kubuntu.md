---
title: "Is it possible to use Synaptic with Kubuntu?"
date: 2009-01-29
forum: General Help
---

### Post by paydaydaddy on 2009-01-29
And if so, how can I add it to Kubuntu using the terminal?

---

### Post by mixmaster on 2009-01-29
I don't actually use kubuntu but I am pretty sure
```

sudo aptitude install synaptic 

```
will get you what you want.

---

### Post by paydaydaddy on 2009-01-29
Thanks for the reply. It seems that I have at least one obstacle to overcome.I get this error:

dragon@smaug:~$ sudo aptitude install synaptic
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I opened the sources list (using kate) and edited out line 56 but could not save the edited list. Got an error that there was not room to save the file. Not sure how to proceed.

---

### Post by 00Davo on 2009-01-29
> **paydaydaddy said:**
> Thanks for the reply. It seems that I have at least one obstacle to overcome.I get this error:

dragon@smaug:~$ sudo aptitude install synaptic
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I opened the sources list (using kate) and edited out line 56 but could not save the edited list. Got an error that there was not room to save the file. Not sure how to proceed.

Ouch. Can you use aptitude to download other stuff? What about apt-get? (are they the same app? :P)

EDIT: You WERE editing the file as root, right?

---

### Post by rafaelsousa on 2009-01-29
> **paydaydaddy said:**
> Thanks for the reply. It seems that I have at least one obstacle to overcome.I get this error:

dragon@smaug:~$ sudo aptitude install synaptic
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I opened the sources list (using kate) and edited out line 56 but could not save the edited list. Got an error that there was not room to save the file. Not sure how to proceed.

Can you post here your sources.list, so we can see what's wrong?

---

### Post by 3rdalbum on 2009-01-29
You need to open /etc/apt/sources.list as root. Press Alt-F2 and type this:

```
kdesu kate /etc/apt/sources.list
```

The "kdesu" bit opens a password prompt to elevate you temporarily to root.

EDIT: Yes, Synaptic works perfectly in KDE and Kubuntu.

---

### Post by ricardisimo on 2009-01-29
I don't blame you... adept sucks and synaptic is fantastic.

---

### Post by paydaydaddy on 2009-01-29
Thanks for the replies. I had to give up and get some sleep last night. I will try to edit the resources list again this evening (after work) and report back here with the results. Chow!

---

### Post by paydaydaddy on 2009-01-29
Got it fixed and synaptic installed. Turned on the computer this evening and was able to edit and save the resources list with no problems. I suspect gremlins or perhaps elves. Thanks for the replies. I will mark this as solved.(Or not)

---

