---
title: "Keyserver problems"
date: 2009-11-16
forum: Forum Feedback &amp; Help
---

### Post by Iowan on 2009-11-16
Maybe the wrong place, but...
I'm trying to digitally sign the CoC. Following the example, I've generated a PGP key, but when I try to send it:
```
Iowan@DELL4100:~$ gpg --send-keys --keyserver keyserver.ubuntu.com 12345678
gpg: sending key 12345678 to hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver send failed: keyserver error

```I've been trying for a couple of days - I can ping it.
Is the server having problems - or just me?

---

### Post by lisati on 2009-11-16
> **Iowan said:**
> Maybe the wrong place, but...
I'm trying to digitally sign the CoC. Following the example, I've generated a PGP key, but when I try to send it:
```
Iowan@DELL4100:~$ gpg --send-keys --keyserver keyserver.ubuntu.com 12345678
gpg: sending key 12345678 to hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver send failed: keyserver error

```I've been trying for a couple of days - I can ping it.
Is the server having problems - or just me?

I wasn't aware that this was possible (or required)

---

### Post by cariboo on 2009-11-16
It must be you. :) I just registered my key, as I forgot the pass-phrase, it worked as expected

```
jim@alexis:~$ gpg --send-keys --keyserver keyserver.ubuntu.com 12345678
gpg: sending key 12345678 to hkp server keyserver.ubuntu.com
jim@alexis:~$ 
```

I got the email from Launchpad, created a fingerprint and registered my new gpg key in less than 10 minutes.

Can you ping the keyserver?

Signing the Ubuntu code of conduct is a prerequisite for becoming an Ubuntu member, it is different from the forum code of conduct

---

### Post by lisati on 2009-11-16
> **cariboo907 said:**
> Signing the Ubuntu code of conduct is a prerequisite for becoming an Ubuntu member, it is different from the forum code of conduct

Thanks. This helps explain why I thought I'd either forgotten or missed something.

@iowan: I defer to the knowledge and skills of others who are in a better position to provide useful comments. Good luck.

---

### Post by Iowan on 2009-11-16
> **cariboo907 said:**
> Can you ping the keyserver?> **Iowan said:**
>  I can ping it.Hmmm... now I'm really confused.
Still won't fly - I'd hoped you broke the ice for me ;)

---

### Post by cariboo on 2009-11-16
Sorry about that I missed the ping part. :)

I want to say It's an ipv6 problem, but I'm not sure what version you're running.

---

### Post by cariboo on 2009-11-17
Could it possibly be a firewall problem?

---

### Post by Iowan on 2009-11-17
Firewall problem. Only other time the firewall has caused me trouble is trying to connect to my MSN account. Turning it to low security didn't help (but I don't think it actually took) - turning it off did take, and let me get key registered. 

Now to figure out how to edit a wiki personal page. (Different topic)

---

### Post by cariboo on 2009-11-17
It's good to see you managed to get it done.

---

