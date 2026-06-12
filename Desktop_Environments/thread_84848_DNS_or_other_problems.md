---
title: "DNS? or other problems"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Hinko on 2005-11-01
Since last friday my Ubuntubox can't reach most sites: "www.example.com can not be found."  Some sites however do load. Google for example does, ubuntuforums doesn't. On the same box I don't have the problem in Windows, It can find any site from there, and I never before had it in linux either. Not even the last two weeks in Ubuntu 5.10. Updating with synaptic doesn't work eiter since it can't find most sources. Gaim doesn't work most of the time, but is working perfectly right now. 

My computer is behind a router. DHCP and everything seems to work perfectly (like it allways did). 

I tried disabling IPv6 in firefox (didn't work). I also tried uncommenting

 # alias net-pf-10 off # IPv6

in /etc/modutils/aliases as suggested in this [thread]("http://www.ubuntuforums.org/showthread.php?t=83753&highlight=dns") but apparently I didn't have that file anyway, so there wasn't a lot to uncomment.

I also tried removing my IPv6 hosts (what do these hosts do anyway) but it doesn't help at all. Any suggestions? I'm all out of ideas](*,). Getting pretty desperate here... Might cry very soon... :cry:

---

### Post by mips on 2005-11-01
Looks like DNS problems. Please move this thread to the Networking forum or repost there and i'll respond.

Please post the following info in this thread:

1) Router Make & Model
2) Did you buy it or was it provided by the ISP
2) Connection type, Ethernet, USB or Wireless
3) Running in Bridged or Routed mode
4) Country you live in.
5) Your ISP and/or Broadband provider
6) What service are you subscribing to from them
7) Full TCP/IP config of PC + Router config details (PPPoE, VPI/VCI, DHCP, NAT etc)

Please provide links where possible to the above questions.

---

### Post by suRoot on 2005-11-01
What's in your /etc/resolv.conf?

```
sudo less /etc/resolv.conf
```

You should see something like:

```
search foo.bar
nameserver 192.168.122.1
```

If it's blank, just for testing do:

```
sudo gedit /etc/resolv.conf
```

and add the IP of your name server

```
nameserver 192.168.122.2
```

Try it & see if it works.  If so, you need to check your network config to figure out why DHCP isn't updating your DNS.


On a more general note, there are a couple tools you can use to troubleshoot DNS problems - Dig & nslookup

1.  Dig

This command will query whatever name server your box happens to be using.  If there are DNS errors, you'll see them in the output

```
$ dig www.google.com
```

Output on my machine

```
; <<>> DiG 9.3.1 <<>> www.google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18627
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         15      IN      CNAME   www.l.google.com.
www.l.google.com.       216     IN      A       64.233.187.99
www.l.google.com.       216     IN      A       64.233.187.104

;; Query time: 26 msec
;; SERVER: 192.168.122.1#53(192.168.122.1)
;; WHEN: Tue Nov  1 04:51:59 2005
;; MSG SIZE  rcvd: 84

```

The third line from the bottom - SERVER - tells you which name server you're querying.

2.  nslookup

This guy will also query your nameserver

```
$ nslookup
```

will throw you in to a console where you can enter commands

```
> set q=a
> www.linux.com
Server:         192.168.122.1
Address:        192.168.122.1#53

Non-authoritative answer:
Name:   www.linux.com
Address: 66.35.250.177
> exit
```

Both command will take other arguments, have a look at their respective man pages.  Or google it once you're back online :p

---

### Post by Hinko on 2005-11-01
```
sudo pico/less /etc/resolv.conf
``` 

gives

```
sudo: unable to lookup hinko via gethostbyname()
```

but that's probably another problem...

```
less /etc/resolv.conf
```

gives

```
kabela.oprit.rug.nl
nameserver 129.125.36.10
nameserver 129.125.4.6
nameserver 217.149.192.16
```

nslookup gives

```
> set q=a
> www.opensuse.org
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
*** Can't find www.opensuse.org: No answer
> www.linux.com
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
Name:   www.linux.com
Address: 66.35.250.177
> www.ubuntuforums.org
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
*** Can't find www.ubuntuforums.org: No answer
> www.bbc.com
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
*** Can't find www.bbc.com: No answer
> www.bbc.co.uk
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
www.bbc.co.uk   canonical name = www.bbc.net.uk.
Name:   www.bbc.net.uk
Address: 212.58.224.84
> www.bbc.net.uk
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
Name:   www.bbc.net.uk
Address: 212.58.224.84
```

As you can see, some it can find, others it can't.:rolleyes: But it consistently uses only one server, while three are in resolv.conf. I don't know much about this stuff (as you probably guessed). But this definitely illustrates the problem.

 

How can I have problems with DNS? That is resolved by my router, right? And it (DHCP, router, finding pages) works fine under Windows, and for four years it worked fine under different flavours of linux as well


@mips: I'd love to move this thread, but I couldn't find how to do that :-?

---

### Post by mips on 2005-11-01
There are know bugs with some Linux based routers like D-link etc.

---

### Post by suRoot on 2005-11-01
[QUOTE=mips]There are know bugs with some Linux based routers like D-link etc.[/QUOTE]

I don't think that's the problem here.

He did say that he's not seeing the problem running a windows box on the same connection.  That kind of takes the firewall out of the equation so far as I'm concerned.  I'd be willing to bet that the windows box is hitting a name server that works (see below).


[QUOTE=Hinko]
```
sudo: unable to lookup hinko via gethostbyname()
```
[/QUOTE]

First of all, fix this.

System -> Administration -> Networking -> Hosts tab -> Add

IP:  127.0.0.2
Alias:  hinko


Next, go to the DNS tab.

If there are any entries under search domains, delete them.  Create a new one called kabela.oprit.rug.nl.

From the DNS servers, delete 129.125.4.6.  It appears to be having problems - I'm running queries against it & seeing the same behavior you're seeing.  Some queries work, while others don't (see below).  Get rid of it so there's no chance of it being used.

I don't think the problem is so much with your setup, as it is a problem with that DNS server.

```

> set q=a
> www.google.com
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
www.google.com  canonical name = www.l.google.com.
Name:   www.l.google.com
Address: 66.249.93.99
Name:   www.l.google.com
Address: 66.249.93.104
> www.cnn.com
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
*** Can't find www.cnn.com: No answer
> www.bbc.com
Server:         129.125.4.6
Address:        129.125.4.6#53

Non-authoritative answer:
*** Can't find www.bbc.com: No answer

```

---

### Post by Hinko on 2005-11-01
I love you man. Thanks! this solved it

I added the host (I deleted the IPv6 ones, because I thought they were giving me trouble, must have deleted the normal one as well)

But these hosts are returned by the router, right? How come Windows doesn't have that problem then? Because there are more servers in the list, why are these not used?

btw: loading appears slower now, but at least it works

---

### Post by mips on 2005-11-02
> I don't think that's the problem here.

He did say that he's not seeing the problem running a windows box on the same connection. That kind of takes the firewall out of the equation so far as I'm concerned. I'd be willing to bet that the windows box is hitting a name server that works (see below).

Eh, that is exactly what happens. Works with windows pc but not Linux pc.
Manually configuring DNS on the PC will work but the problem is still there, router not being able to handle the DNS.

---

