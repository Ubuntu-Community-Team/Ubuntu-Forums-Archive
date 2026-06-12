---
title: "Messages in Sim/Jabber displayed twice"
date: 2007-11-21
forum: Desktop Environments
---

### Post by Goliash on 2007-11-21
Hi everybody,
I would like to ask you if anybody has the same problem like me. I am using instant messenger Sim and 3 communication protocols - Jabber, ICQ and MSN. 

When I communicate through Jabber with someone who has Pidgin / Gaim, I see his messages twice. For example:
> 
<L****> fajnfajn
<L****> je&#353;t&#283; n&#283;kdo?je&#353;t&#283; n&#283;kdo?
<Goliash> no pis
<L****> co?co?

We both have accounts on gmail.com but it does the same thing with my friend on jabber.org. When they change to other IM client like Miranda, Sim, integrated client on webmail gmail.com everything looks fine.

I tried to log some communication so maybe here is a solution. The first one is from Pidgin to my Sim:
```

<message type="chat" id="purple4656ca12" to="g****@gmail.com/sim_0.9.4.3" from="l****@gmail.com/Home6AB5D325"><x xmlns="jabber:x:event"><composing/></x><body>fajn</body><html xmlns="http://jabber.org/protocol/xhtml-im"><body xmlns="sta">http://www.w3.org/1999/xhtml">fajn</body></html><nos:x value="disabled" xmlns:nos="google:nosave"/><arc:record otr="false" xmlns:arc="">http://jabber.org/protocol/archive"/></message>

```
The second one is from client integrated on webmail gmail.com:
```
<message to="g****@gmail.com" type="chat" id="21D84AAB1224E3563" from="l****@gmail.com/gmail.38CFF36D">
odhla&#353;uju se :-)</body><met:google-mail-signature xmlns:met="google:metadata">df910818bf1487a5</met:google-mail-signature><cha:active xmlns:cha="http://jabber.org/protocol/chatstates"/><nos:x value="disabled" xmlns:nos="google:nosave"/><arc:record otr="false" xmlns:arc="">http://jabber.org/protocol/archive"/></message>

```
The third one is from Miranda:
```

<message from="h****@jabber.org/Miranda" to="g****@gmail.com/sim_0.9.4.3" xml:lang="en" type="chat" id="mir_29"><body>hu a hu</body><x xmlns="jabber:x:event"><composing/></x></message>

```
I think it can be about rich text but we couldn't find any settings to do it otherway in Pidgin.

---

