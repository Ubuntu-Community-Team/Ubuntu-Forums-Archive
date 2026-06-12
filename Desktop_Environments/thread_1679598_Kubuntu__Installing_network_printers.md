---
title: "Kubuntu : Installing network printers"
date: 2011-02-01
forum: Desktop Environments
---

### Post by Skara Brae on 2011-02-01
***Can I pose this here, or rather at a "SLED" forum, or perhaps a KDE messageboard?***
-------------------------------------------------------------------------------------------------

How do I install network printers on PC's with KDE 3.5.1 (not on Kubuntu, but on SLED 10) as a regular user?

I am asking this, because the IT department at work is understaffed (so I was told, and I believe them, since we are _all_ understaffed) and it takes days (if at all...) before they get back to me...

Every computer has a "printer manager" (icon) on the desktop. When start that up, I end up having to choose one of the following "Backend selections":

---
o Local printer (LPT, serial, USB) (*not applicable, as it's about network printers*)
o LPD
o SMB shared printer
o Network printer (TCP)
o CUPS server (IPP/HTTP)
o Network printer w/IPP (IPP/HTTP)
o Serial fax/modem printer (*greyed out*)
o Other printer type
---

With some choices, I need to fill in information that I don't know (like "host"?).

I am able to get a network printer to work when I choose "Network printer" or "Network printer w/IPP (IPP/HTML)" and each time when I choose "RAW" (since it asks me for the model, which may not be in the list that apppears, like f.i. a Lexmark E332n).

I don't know the (any) Superuser password, so CUPS via the browser doesn't work.

When we still had W2K, I once installed a network printer as "network printer", and I managed to make the whole network (via our AIX 4.3 server) "suffocate" when I printed a PDF file :-P
(Turned out in W2K a network printer must not be installed a "network printer", but as "local printer" - as if that makes sense...)

When I get a network printer to work this way (so, with "RAW"), is this a correct way?

I figure asking this here will go faster than waiting for the IT department... ( :roll: - no offense)

---

