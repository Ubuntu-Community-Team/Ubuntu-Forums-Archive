---
title: "determining port status"
date: 2010-03-10
forum: Desktop Environments
---

### Post by jmsgz on 2010-03-10
hi folks
   looking at the file etc/services i see a list of ports and their purpose. QUESTION, is there a program similar to "TOPS" that display machine ports on your system and their status so that they can be manipulated?

thanks in advance
:-)

---

### Post by asmoore82 on 2010-03-11
If you want to see it from inside your computer, use `netstat`
```
netstat -ant
```
`-a` = show all connection types: server(LISTEN) and client
`-n` = show numeric output: IP's and port #'s
`-t` = show only TCP info

If you want to see from outside the box looking in -
in other words, to portscan yourself, use `nmap`
```
nmap -v -sV localhost
```
`-v` = be verbose
`-sV` = probe for service "branding" and Versions #'s

---

### Post by jmsgz on 2010-03-11
> **asmoore82 said:**
> If you want to see it from inside your computer, use `netstat`
```
netstat -ant
```
`-a` = show all connection types: server(LISTEN) and client
`-n` = show numeric output: IP's and port #'s
`-t` = show only TCP info

If you want to see from outside the box looking in -
in other words, to portscan yourself, use `nmap`
```
nmap -v -sV localhost
```
`-v` = be verbose
`-sV` = probe for service "branding" and Versions #'s

Thankyou:
thats helpful!


Question: the following 631/tcp open  ipp     CUPS 1.4
   i suppose this has to do with printing? What would be an example syntax if you wanted to close port 631 ? Also can you point me in the direction to read more on this. Would there be help in usr/share/doc' ?
Or other documentation elsewhere!

:-)

---

