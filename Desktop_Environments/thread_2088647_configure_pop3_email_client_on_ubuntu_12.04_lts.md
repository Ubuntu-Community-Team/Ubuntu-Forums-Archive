---
title: "configure pop3 email client on ubuntu 12.04 lts"
date: 2012-11-27
forum: Desktop Environments
---

### Post by speedygarth on 2012-11-27
hi there i would be grateful ifi could get help with setting up my thunderbird pop3 email account settings. i have specified my pop3 settings for the incoming and outgoing server with my workplace pop3 mail server settings but it gives me an error message about the smtp mail server setings being incorrect.

---

### Post by howefield on 2012-11-27
Don't suppose you have the email account elsewhere, that you could open the account properties, or access to your work IT support ?

Have a look in  Thunderbird > Account Settings > Server Settings > Security Settings and try the different options.

---

### Post by ZippyUbu on 2012-11-27
Hi,

Can you post the exact message that you receive please? Your authentication options must match the mail server you are connecting to... Also, make sure your release of Ubuntu is up-to-date

To update - Open the terminal
```
sudo apt-get update && sudo apt-get upgrade
```--Zu

---

### Post by speedygarth on 2012-11-28
Hi this is the message i recieved:

Sending of message failed.
An error occurred sending mail: SMTP server mail.petrahigh.co.zw is unknown. The server may be incorrectly configured. Please verify that your SMTP server settings are correct and try again.

i have checked my settings with a windows machine and they are the same, i ran the "sudo upgrade" but its still not sending or recieving my emails. 
please help!:confused:

---

### Post by SeijiSensei on 2012-11-28
> SMTP server mail.petrahigh.co.zw is unknown

Sounds like a DNS problem to me.  Open a terminal type "ping mail.petrahigh.co.zw".  Does that work, or does it say "mail.petrahigh.co.zw" is unknown?

---

### Post by speedygarth on 2012-11-29
thanks for the reply, i pinged the email server and i got an "unknown host" via the terminal.

---

### Post by SeijiSensei on 2012-11-29
If you can't resolve the server's name, you probably cannot resolve anything else.  Can you ping "www.google.com" or browse the web?

I can resolve the server's hostname from out here on the Internet.

```
mail.petrahigh.co.zw has address 79.170.44.54
```

---

### Post by speedygarth on 2012-11-29
i can browse the web and see my network, but the emails are the problem

---

### Post by SeijiSensei on 2012-11-29
I can connect to the POP3 port (110) but not to the SMTP port 25.  An nmap scan says that it is filtered:

```
Nmap scan report for mail.petrahigh.co.zw (79.170.44.54)
Host is up (0.092s latency).
rDNS record for 79.170.44.54: mail54.extendcp.co.uk
Not shown: 988 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
25/tcp   filtered smtp
110/tcp  open     pop3
111/tcp  open     rpcbind
143/tcp  open     imap
465/tcp  open     smtps
544/tcp  open     kshell
587/tcp  open     submission
993/tcp  open     imaps
995/tcp  open     pop3s
1720/tcp filtered H.323/Q.931
2105/tcp open     eklogin

Nmap done: 1 IP address (1 host up) scanned in 3.07 seconds
```

My guess is that you can only connect to the SMTP port from specific IP addresses.  Have you discussed this problem with the administrator of the server?

---

### Post by ZippyUbu on 2012-11-30
I get the below with an nmap scan. Is someone working on the server?

```
Nmap scan report for mail.petrahigh.co.zw (79.170.44.54)
Host is up (0.060s latency).
rDNS record for 79.170.44.54: mail54.extendcp.co.uk
Not shown: 985 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
25/tcp   open     smtp
110/tcp  open     pop3
111/tcp  open     rpcbind
143/tcp  open     imap
465/tcp  open     smtps
544/tcp  open     kshell
587/tcp  open     submission
993/tcp  open     imaps
995/tcp  open     pop3s
1720/tcp filtered H.323/Q.931
1863/tcp filtered msnp
2105/tcp open     eklogin
5050/tcp filtered mmcc
5190/tcp filtered aol

Nmap done: 1 IP address (1 host up) scanned in 3.85 seconds
```Are you trying to configure your mail client inside your network or form the internet? Also, can you post the contents of: ```
gedit /etc/resolv.conf
```

---

### Post by SeijiSensei on 2012-11-30
I now get the Exim prompt when I telnet to port 25.

```

[root@rocky ~]# telnet mail.petrahigh.co.zw 25
Trying 79.170.44.54...
Connected to mail.petrahigh.co.zw.
Escape character is '^]'.
220 mail54.extendcp.co.uk ESMTP Exim Sat, 01 Dec 2012 01:20:10 +0000
ehlo rocky.example.com
250-mail54.extendcp.co.uk Hello rocky.example.com [10.10.10.10]
250-SIZE 31457280
250-PIPELINING
250-AUTH PLAIN LOGIN CRAM-MD5
250-STARTTLS
250 HELP
mail from: someone@example.com
250 OK
rcpt to: root@petrahigh.co.zw
550 unknown user
quit
221 mail54.extendcp.co.uk closing connection
Connection closed by foreign host.

```

Since I'd imagine root is a valid user, it may not accept mail for the petrahigh.co.uk domain yet.

---

### Post by haqking on 2012-11-30
587 is open, try using that

---

### Post by speedygarth on 2012-12-03
thanks for the help guys, the mail server is actually on the same network as my machine (LAN) i`ll ask the sysadmin guy to verify my mail account settings if the account is still active.coz its really frustrating me now!

---

### Post by speedygarth on 2012-12-03
here are the contents of my resolve conf file:




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

---

### Post by speedygarth on 2012-12-03
I think there`s progress now, i am no longer getting the smtp error message but a message sending progress window, but it keeps loading "connecting to mail.petrahigh.co.zw" then it gives me the error message "server connection timeout"

---

### Post by ZippyUbu on 2012-12-09
> thanks for the help guys, the mail server is actually on the same  network as my machine (LAN) i`ll ask the sysadmin guy to verify my mail  account settings if the account is still active.coz its really  frustrating me now!     Try inputting the LAN IP address into your mail client instead of "mail.petrahigh.co.zw"

---

### Post by speedygarth on 2013-02-20
Hi guys, i`ve tried using the gateway IP for the network as well as the IP 79.170.44.54 but to no avail. i still cannot receive emails from my account. please advise me on the best course of action.

---

### Post by jdthood on 2013-02-20
> **speedygarth said:**
> here are the contents of my resolve conf file:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

```

In order to ensure that the problem has nothing to do with the forwarding nameserver dnsmasq, please disable dnsmasq.

1. Assuming that you are running Ubuntu 12.04 and NetworkManager and that NetworkManager is controlling your dnsmasq process, please edit /etc/NetworkManager/NetworkManager.conf
```

    sudo gedit /etc/NetworkManager/NetworkManager.conf

```
and comment out the line "dns=dnsmasq"
```

    #dns=dnsmasq

```
then save the file and restart network-manager.
```

    sudo restart network-manager

```
2. It is also possible that you have the standalone dnsmasq server package (called "dnsmasq") installed. If so then please remove it or disable it.

After you have disabled dnsmasq you should see an external nameserver address in resolv.conf instead of a loopback nameserver address. 
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 12.34.56.78

```    
If this is not the case, try rebooting.

---

### Post by jdthood on 2013-02-20
> **speedygarth said:**
> Hi guys, i`ve tried using the gateway IP for the network as well as the IP 79.170.44.54 but to no avail. i still cannot receive emails from my account. please advise me on the best course of action.

Ask your network administrator if the mail server is configured to accept POP3 connections from the LAN (and not just from the Internet).

---

### Post by speedygarth on 2013-02-20
I have added the local dns server IP adds to /etc/resolv.conf but i still cannot access the emails. the other users on our network all use windows OS and all their email accounts use pop3 mail settings.
i also disabled the dnsmasq service, but i still cannot receive my emails.

---

### Post by jdthood on 2013-02-20
> **speedygarth said:**
> I have added the local dns server IP adds to /etc/resolv.conf but i still cannot access the emails. the other users on our network all use windows OS and all their email accounts use pop3 mail settings.
i also disabled the dnsmasq service, but i still cannot receive my emails.

You should carefully compare your account settings with those on a Windows machine where you *can* access your mail. Are you using SSL, TLS or STARTTLS? Is the port correct? Etc.

---

### Post by speedygarth on 2013-02-25
I just checked a windows machine and the settings are exactly the same,the windows settings are as follows:

POP3 server
Incoming server": mail.petrahigh.co.zw
Outgoing server": mail.petrahigh.co.zw

Normal logon (without secure password authentication)

---

### Post by speedygarth on 2013-03-04
I can connect to my account using the windows host on virtual box via outlook. but i still cant receive anything using Thunderbird. help guys!!

---

### Post by Frogs Hair on 2013-03-04
I would ask the mail provider about know issues with mail clients or Linux other wise you may have to wait for someone who uses the mail service to find out what settings are being used. If the sever is not located automatically during account setup then a manual entry won't do any good.

---

### Post by speedygarth on 2013-03-05
Oh well.. it seems i`m the only linux user on my network so i`ll just have to suffer it out!! until i find a working solution.

---

