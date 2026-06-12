---
title: "Evolution/Exchange Global Address List"
date: 2006-06-12
forum: Desktop Environments
---

### Post by tfandango on 2006-06-12
Hi-

(On Dapper)

I have Evolution working with my company's exchange server.  The one thing that does not work is the Global Address List, which I've come to rely quite heavilly on apparently.

Does anyone have their Global Address List working in Evolution, via exchange or LDAP?

Thanks,
troy

---

### Post by djcrash1981 on 2006-06-13
I have the same problem, it was working perfectly on Breezy but since I upgraded to dapper it stopped working.


Any ideas????? :confused:

---

### Post by maheshjagadeesan on 2006-10-18
I was hoping somebody on this thread would have a solution, but looks like we have more people with questions and none with answers :-(

---

### Post by bbarrons on 2006-10-18
I have had my share of questions with no answers with evol. AS much as I want to see a viable alternative to outlook for connecting to a ms exchange server I cant seem to find one. I am hoping the new version of evol ( avail in edgy) will solve some of these issues. JUst waiting for the final release of edgy to upgrade..... maybe there will be some answers there.

---

### Post by Das Goat on 2006-10-21
I take it that Evolution is the client side. Is there a free replacement for the server side / exchange?

---

### Post by mn_kthompson on 2006-11-13
I'm using Evolution on Edgy (version 2.8 ) and I still can't connect to the Global Address List.  I also can't seem to find any ideas on the web on what to do about this problem.

---

### Post by mn_kthompson on 2006-11-13
I just found relief in this thread [http://www.ubuntuforums.org/showthread.php?t=275565]("http://www.ubuntuforums.org/showthread.php?t=275565")

---

### Post by Jamie Jackson on 2006-11-21
The link was no help to me. I guess since my laptop is synced locally, that it's not so easy for me to tell where the exchange Global Address List is. (This is because my laptop reports a local path instead of Exchange. See attached.)

Can someone please show me what their Global Address location is? I'm just wondering about the address format, so of course I don't mind if real information is substituted with fake stuff.

Actually, if someone could post both an OWA *and* a Global Address server address, that would be perfect, as I could tell how they differ.

Thanks,
Jamie
P.S. I'm on Edgy.

---

### Post by cyberwisdom on 2006-11-22
I have this issue as well.  Evolution is working fine using OWA but I can't get the global address lis to sync.  When I check the path of GAL on my windows outlook it gives me a local directory.

Let me know if anyone has found a solution.  Thanx!

---

### Post by dcstar on 2006-11-23
> **Jamie Jackson said:**
> The link was no help to me. I guess since my laptop is synced locally, that it's not so easy for me to tell where the exchange Global Address List is. (This is because my laptop reports a local path instead of Exchange. See attached.)

Can someone please show me what their Global Address location is? I'm just wondering about the address format, so of course I don't mind if real information is substituted with fake stuff.

Actually, if someone could post both an OWA *and* a Global Address server address, that would be perfect, as I could tell how they differ.

Thanks,
Jamie
P.S. I'm on Edgy.

This is the setting in my Outlook, and when I boot Ubuntu, Evolution uses the GAL no problems at all:

BUFFY.educad.local
\Global Address List

Here is my OWA URL setting in Evolution:

[http://buffy.educad.local/exchange](http://buffy.educad.local/exchange)

Here is my Active Directory "Global Catalog Server Name":

buffy.educad.local

Note that the Global Address List will **only** show an entry when you use a Search parameter - just because it looks empty when you go to Contacts doesn't mean that it is.

---

### Post by maheshjagadeesan on 2006-11-27
> **Jamie Jackson said:**
> The link was no help to me. I guess since my laptop is synced locally, that it's not so easy for me to tell where the exchange Global Address List is. (This is because my laptop reports a local path instead of Exchange. See attached.)

Can someone please show me what their Global Address location is? I'm just wondering about the address format, so of course I don't mind if real information is substituted with fake stuff.

Actually, if someone could post both an OWA *and* a Global Address server address, that would be perfect, as I could tell how they differ.


I got this Global Catalog Server thingy sorted out today :-) Okay!!! For security reasons, I won't post the actual server name, but I am hoping that this won't be a problem.

The problem is basically two-fold: a. you need Evolution to talk to Exchange Server to send / receive email b. you also need Evolution to auto-complete names / addresses in the same way that Outlook does, seamlessly. 

For a. you definitely need the help of your network administrator who should be able to tell you what the URL for accessing your Exchange mail over the web is. For me, the URL is something like [https://mailserver1.techmahindra.com/exchange/](https://mailserver1.techmahindra.com/exchange/). Your URL will definitely be different.

For b., you need a bit of luck as well ;-) Over here, some of our network guys weren't particularly helpful. Heck, they didn't even know what a Global Catalog Server was (I don't know either, but well, I'm not a network guy, ergo I don't ***have to*** know ;-) ) If you're on a Windows domain like most others (which typically means that it's running on a Win2k / Win2k3 server), with default settings in most cases, then you're lucky - your Windows domain name can be used in Evolution's settings - Edit->Preferences->Mail Accounts-><your mail account> -> Edit -> Receiving Options -> Global Catalog Server name. E.g., my company's Windows domain is the same as our web domain - techmahindra.com. Be sure to type in this setting without the "http://" bit. And you should be back in business!

---

### Post by Jamie Jackson on 2006-11-28
Thanks dcstar and maheshjagadeesan,

I finally got it mostly working. I think mine is an unusually complicated case, so it might reveal a lot about how Evolution works.

Here's what works (*italicized* bits are fake placeholders):

**USERNAME:** *<networkName>*/*<employeeLoginId>* (e.g., "widgets-hq/52352")
**OWA URL:** https://exchange.*<domain>*/exchange (e.g.,  "https://exchange.widgets.com/exchange")
**Global Catalog server name:** *<networkname>*.*<domain>* (e.g., "widgets-hq.widgets.com")

This allows for autocomplete to work while typing in the recipient lines of an new email. However, I can't seem to *browse* contacts (I can search and autocomplete only).

Does anyone know the fix for this?

Thanks,
Jamie

---

### Post by Billquinn1 on 2006-11-28
I'll bet someone at "Microvell" knows but I'm just betting they won't be helping with that product to much from here out. 

Sorry, just had to vent.

Hope you figure it out.

---

### Post by usererror on 2007-01-09
> **Jamie Jackson said:**
> Thanks dcstar and maheshjagadeesan,

I finally got it mostly working. I think mine is an unusually complicated case, so it might reveal a lot about how Evolution works.

Here's what works (*italicized* bits are fake placeholders):

**USERNAME:** *<networkName>*/*<employeeLoginId>* (e.g., "widgets-hq/52352")
**OWA URL:** [https://exchange](https://exchange).*<domain>*/exchange (e.g.,  "https://exchange.widgets.com/exchange")
**Global Catalog server name:** *<networkname>*.*<domain>* (e.g., "widgets-hq.widgets.com")

This allows for autocomplete to work while typing in the recipient lines of an new email. However, I can't seem to *browse* contacts (I can search and autocomplete only).

Does anyone know the fix for this?

Thanks,
Jamie

Jamie, you are a lifesaver.  i am such an idiot! I know this thread is ancient but i finally got my global address book working, I forgot to do my username in the fomat above **domain\username**

I just upgraded to 6.10 with a fresh install and lost my evolution settings...now i'm taking screenshots of them to save.

---

### Post by ambar.kulkarni on 2007-09-12
hey everyone,

i have managed to get all the above working, but its not possible for me to browse the GAL in the contacts view, is there anyway i can get that started?

i am on ubuntu 7.04

---

### Post by Jamie Jackson on 2007-09-12
> **ambar.kulkarni said:**
> hey everyone,

i have managed to get all the above working, but its not possible for me to browse the GAL in the contacts view, is there anyway i can get that started?

i am on ubuntu 7.04

I don't know the answer. I can't browse it either, but I *can* search it (top right).

---

### Post by Mavtech on 2007-09-28
Just got this working on Evolution on 7.04.  I figured the GAL would be on the Exchange server.  But, ours is on the Domain Controller.  Once I found this out, I entered that server name.  I can now find those contacts.  But, I want the whole list to display.

---

