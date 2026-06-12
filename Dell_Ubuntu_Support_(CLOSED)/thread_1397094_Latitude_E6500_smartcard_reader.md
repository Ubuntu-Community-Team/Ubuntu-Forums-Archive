---
title: "Latitude E6500 smartcard reader"
date: 2010-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by b4rt on 2010-02-02
Hi all,

Anyone had any luck using the contacted Smart Card readers they put in Dell's Latitude E-series laptops? I think the reader is a Broadcom 5800, but it doesn't work with 9.10 or the latest Lucid daily build.

Thanks in advance,

Bart G.

---

### Post by b4rt on 2010-02-09
anyone?

---

### Post by b4rt on 2010-02-11
bump

---

### Post by b4rt on 2010-02-17
yet another bump... nobody can help?

---

### Post by justfred on 2010-02-17
Got the same problem. Also when booting into Win7 the driver doesn't seem to install correctly and Win7 complains.

I had a look at [http://ubuntuforums.org/showthread.php?t=975704](http://ubuntuforums.org/showthread.php?t=975704)
and installed pcsc_scan (pscs-tools) but had the same problems as described there. libccid is installed as well

Nothing seems to happen at the level of dmesg when a card is inserted or removed. (on Win7 the system tried to find/install drivers when I inserted a card; but it failed). 


I'd be interested to know how to get to work under 9.10.

---

### Post by b4rt on 2010-02-28
> **justfred said:**
> Got the same problem. Also when booting into Win7 the driver doesn't seem to install correctly and Win7 complains.

I had a look at [http://ubuntuforums.org/showthread.php?t=975704](http://ubuntuforums.org/showthread.php?t=975704)
and installed pcsc_scan (pscs-tools) but had the same problems as described there. libccid is installed as well

Nothing seems to happen at the level of dmesg when a card is inserted or removed. (on Win7 the system tried to find/install drivers when I inserted a card; but it failed). 


I'd be interested to know how to get to work under 9.10.

I feel users using Dell's Latitude E-series laptops should unite... We should be able to get the smart card reader working, as well as the GPS receiver that some users have... Am I dreaming too much here? :D

---

### Post by justfred on 2010-03-01
It appears that there were some problems as well on windows using this smart card reader : dell issues updated drivers to solve the problem. I wonder if, as I thought Ubuntu can be pre-installed by Dell on some Dell pc's, the Ubuntu team (or Canonical) could take it up with Dell ?

Otherwise, could the new drivers be wrapped so as to work on Linux/Ubuntu ? (Note I'm not knowledgeable at all to do this myself).

Who should be contacted at Ubuntu/Canonical ? Do it need to be reported as a bug ?

---

### Post by b4rt on 2010-03-01
> **justfred said:**
> It appears that there were some problems as well on windows using this smart card reader : dell issues updated drivers to solve the problem. I wonder if, as I thought Ubuntu can be pre-installed by Dell on some Dell pc's, the Ubuntu team (or Canonical) could take it up with Dell ?

Otherwise, could the new drivers be wrapped so as to work on Linux/Ubuntu ? (Note I'm not knowledgeable at all to do this myself).

Who should be contacted at Ubuntu/Canonical ? Do it need to be reported as a bug ?

You've got my support

---

### Post by vase on 2010-05-29
Hi,

Is there any news on this problem?

---

### Post by dentaro16 on 2010-06-18
so i have installed ubuntu on a E6500 and a M6400 and i couldnt get either to work. I have only been successful with a native RHEL installation and a Scientific Linux install. 

i need help too

---

