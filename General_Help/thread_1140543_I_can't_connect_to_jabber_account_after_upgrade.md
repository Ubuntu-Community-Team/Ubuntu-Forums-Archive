---
title: "I can't connect to jabber account after upgrade"
date: 2009-04-27
forum: General Help
---

### Post by reedness on 2009-04-27
Hi all,

I haven't had any problems connecting to my work's jabber account using pidgin in the past.  However, after upgrading to 9.04, the problems began.

I set my account info on pidgin using XMPP like always, and it prompts me to accept the certificate just like it used to, and it says I am signed in.... but, I can't see any of my contacts and they cannot see me.  It's like I'm not connected.  I tried with Ubuntu and Kubuntu.  I also tried other IM clients, which have never worked in the past and still don't to this day.  Pidgin was the only thing that worked.  I may have to revert back to 8.10.

I opened a debug window in pidgin, but I'm not sure if this is of any value.

16:24:15) jabber: Sending (ssl): <iq type='get' id='purple7aefd111'><ping xmlns='urn:xmpp:ping'/></iq>
(16:24:15) jabber: Recv (ssl)(203): <iq xmlns='jabber:client' id='purple7aefd111' type='error'><error type='cancel' code='501'><feature-not-implemented xmlns='urn:ietf:params:xml:ns:xmpp-stanzas'/></error><ping xmlns='urn:xmpp:ping'/></iq>

---

### Post by reedness on 2009-04-28
I would be happy if I could even use Kopete to pull this off, but I have never been able to connect with it.  Pidgin is the only thing I've had luck with when connecting to my work's Jabber.

---

### Post by reedness on 2009-04-28
Does anyone know what happened to make Pidgin no longer be able to connect to a Jabber account?

---

### Post by reedness on 2009-05-02
lol

---

### Post by reedness on 2009-05-15
In case it matters, I've isolated the problem to Pidgin.  I downloaded a copy of Winblows 7 RC and downloaded Pidgin, and it bahaves the exact same way.

It's gotta be the new version of Pidgin

---

### Post by reedness on 2009-05-22
Downloaded even newer release of Pidgin, upgraded from 2.5.5 to 2.5.6 still to no avail.  *sigh

---

