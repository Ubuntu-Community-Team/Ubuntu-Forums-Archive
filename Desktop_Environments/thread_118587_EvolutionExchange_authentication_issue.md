---
title: "Evolution/Exchange authentication issue"
date: 2006-01-17
forum: Desktop Environments
---

### Post by djjazzyjeff on 2006-01-17
I have seen some posts around regarding this issue but no solutions. When I start Evolution 2.4.1 configured with the Exchange server connector, I get prompted for username and password. I enter them correctly and receive the same username/password request dialog, I enter them again and get an error dialog that reads ""Could not authenticate to server" (password incorrect?) Evolution then proceeds to connect to my Exchange server sucessfully (not too fast tho) and displays my mailbox and all is then normal. This happens each time I start Evolution, even if is the second or additional times in a given day. I also notice that in my Preferences, even though I check off "Make this my default account" in my Exchange server account (the only one configured) this setting is never retained. Thirdly, when I create the first new message of the day, my Exchange server Global Address List is never the default, I have to click "To" in a new message window and select "Global Address List" from the address book dropdown under show contacts. I'd appreciate any help from similar victims out there as I am fully operation with Breezy otherwise and hate the thought of maintaining a winbloze box just for the sake of crappy m$ outlook. :evil: Thanks.............Jeff

---

### Post by tighem on 2008-01-16
I'm having a similar issue, but I don't ever get to connect to my exchange server. From the bug report I started:

This started this morning after last night's updates. I've been trying
to troubleshoot this off and on all day with little luck. Evolution
popped up this morning with a "new account wizard" which was strange
since I've been using the same account all along.  I went ahead and
played along and was unable to get it to create a new account (always
hung at the authenticate with exchange screen).  Not so much hung as the
forward button wouldn't become available. After much messing around with
deleting .evolution directory and trying to force it to start I finally
was able to get it to create the account using the exchange-connector-
setup-2.22 program.

That worked, but when I run exchange it get the following error:

(evolution:8421): e-data-server-ui-WARNING **: Key file does not have
key 'exchange:__doe_j;auth_Basic@owa_exchange.server.com_'

And I fail to authenticate to the OWA server.  I don't think it's really
even trying.

---

### Post by Oerb on 2008-04-25
It's the same to me. I installed Hardy 64bit yesterday and the first thing I had to test was the Evolutionconnector. The connector isn't working. 
The next thing I test was the Activedirctory Connectiontool. And it isn't working to. Seam to be the typical problems with my MS Small Business Server 2003. XP and Vista have no problems with this Server.
The only way I see is to kick off this MS Server and put OpenXchange and OpenLdap in the grid.

---

### Post by redwing629 on 2008-04-29
When did you update? Recently (April 26, 2008) I installed the usual patches/updates using Ubuntu 7.10 and then all of a sudden I could not connect to my Exchange server using evolution. I also upgraded to version 8.04 and it still will not connect to OWA. I asked the administrators about this and they said nothing has changed with the Exchange server. To test the theory out that a recent set of patches/updates caused the problem I reinstalled version 7.10 without updating and voila it works. So what was pushed out to us recently that affected the exchange connector?

Joe

=========

> **tighem said:**
> I'm having a similar issue, but I don't ever get to connect to my exchange server. From the bug report I started:

This started this morning after last night's updates. I've been trying
to troubleshoot this off and on all day with little luck. Evolution
popped up this morning with a "new account wizard" which was strange
since I've been using the same account all along.  I went ahead and
played along and was unable to get it to create a new account (always
hung at the authenticate with exchange screen).  Not so much hung as the
forward button wouldn't become available. After much messing around with
deleting .evolution directory and trying to force it to start I finally
was able to get it to create the account using the exchange-connector-
setup-2.22 program.

That worked, but when I run exchange it get the following error:

(evolution:8421): e-data-server-ui-WARNING **: Key file does not have
key 'exchange:__doe_j;auth_Basic@owa_exchange.server.com_'

And I fail to authenticate to the OWA server.  I don't think it's really
even trying.

---

