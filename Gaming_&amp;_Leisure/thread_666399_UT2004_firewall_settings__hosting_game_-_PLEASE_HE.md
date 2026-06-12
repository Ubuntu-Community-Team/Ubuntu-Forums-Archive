---
title: "UT2004 firewall settings / hosting game - PLEASE HELP"
date: 2008-01-13
forum: Gaming &amp; Leisure
---

### Post by perixx on 2008-01-13
Hello there... 

help requested on how to set up iptables-firewall for use with Unreal Tournament 2004!!

Can someone please explain how to:

1) set up iptables for UT2004 online gaming (and other games) 
2) find a solution for hosting a "list server" game / "dedicated server" game (what's the difference please?)

Currently, when 'firestarter' is enabled, I can in fact download a list of availible game servers, but 'ping' times aren't updated/shown and I can't connect to servers; I've already enabled OUTbound connection on ports 7777 and 7778 with firestarter, but no success so far (I can't seem to specify TCP/UDP - both are needed AFAIK - btw.).

When trying to start a 1on1 server for gaming with a friend, we can't seem to set up a connection; I can't pose a non-dedicated server (I can start the game, but aren't enlisted - probably due to firewall settings) and the friend can set it up (and is also listed in the server's list), but I can't connect it, even if I disable firestarter). We both have used the 'announce server to list' in the server options.

I'm using a simple DSL-modem (direct access), friend is using XP and is behind a DSL/WLAN-router + firewall (Comodo). Obviously, we've got different problems to iron out, in order to 'link together' - where it's not unlikely that the main probs are on my side.

We can both connect to an already listed game-server.

When currently looking at firestarter's events, I get the following OUTbound messages after running UT2004 and trying to start different games/servers; 
which one's are actually really needed to be enabled and what all those ports are opened for :confused:
> port 28902 tcp
port 9778 udp
port 10778 udp
port 7778 udp
port 8001 udp
port 7003 udp
port 7221 udp
port 11777 udp (dedicated)

What's the difference between 'list server' and 'dedicated server'? 
When trying to run the latter, I get a game-crash and a terminal-like window will pop up telling me about starting messages of the dedicated server, trying to connect to the master server and  and that something's not 'enabled'....

PLEASE HELP!!

perixx

---

### Post by perixx on 2008-01-13
**[COLOR="Teal"]*** PARTLY SOLVED ***[/COLOR]**

Thanks to the info on this page:
[http://community.games4mac.de/lofiversion/index.php/t7628.htmlversuchen.http://community.games4mac.de/lofiversion/index.php/t7628.html]("http://community.games4mac.de/lofiversion/index.php/t7628.htmlversuchen.http://community.games4mac.de/lofiversion/index.php/t7628.html")
> The default ports are:

7777 UDP/IP (Game Port)
7778 UDP/IP (Query Port)
7787 UDP/IP (GameSpy Query Port)
28902 TCP/IP (Allows your Server to Connect to the UT2004 Master Server Browser)
xxxx TCP/IP (Port set via ListenPort that your WebAdmin will run on)
I was able to apply OUTbound-rules to 'Firestarter' and establish access to the gaming servers and UT2004 master server!

Now I still got to set up a working game host to play with friends... perhaps going past the router will require 'forwarding' settings, don't know yet.

perixx

---

### Post by JohnLM_the_Ghost on 2008-03-24
Hey Man!

If you use router you have to forward 7777 port to host a server, and to allow traffic on these ports (Allow them through firewall).

I don't filter outbound packets though, there might be some more configuration

---

### Post by perixx on 2008-03-25
Hi John, 

nah, I'm just using a plain DSL-modem, so no need for port forwarding... although - still no need, when I'm using 'Iptables'?

perixx

---

### Post by JohnLM_the_Ghost on 2008-03-25
Well, I don't quite know the "INs and OUTs" of the iptables. But if it's blocking any traffic to local 7777 port, you have to configure to allow it. (Or any other port you might host a server on)

The other guy(s) can also try to connect manually by using
```
OPEN xxx.xxx.xxx.xxx
```
command in game's console (replace X'es with your IP)

or 

```
OPEN xxx.xxx.xxx.xxx:port
```
if you use any other port than default 7777 (replace the PORT with port you use)

for example

```
OPEN 192.168.123.1:6666
```

J

---

### Post by perixx on 2008-03-25
Ah, well, yes... I remember now, opening these ports for UT2004 in my Firestarter app - how could UT have even worked without that? 

^^)

perixx

---

