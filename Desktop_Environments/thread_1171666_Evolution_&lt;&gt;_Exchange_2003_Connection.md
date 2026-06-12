---
title: "Evolution &lt;&gt; Exchange 2003 Connection"
date: 2009-05-27
forum: Desktop Environments
---

### Post by PerfectReign on 2009-05-27
I've done some research on this and cannot find the same problem I'm having.

I am running 9.04 with GNOME on a laptop connected to an Active Directory network. We use Exchange 2003 for our mail/calendaring. Most people have Outlook 2003 or 2007 on their desktops.

I can access email via OWA or using remote desktop into my Vista or XP boxes. I prefer a local email client.

[http://www.perfectreign.com/stuff/outlook_save.jpg](http://www.perfectreign.com/stuff/outlook_save.jpg)

I had used Crossover Office with Outlook 2003 in the past under SUSE/openSUSE but wanted to get away from that. In addition, I'd always run into frustration trying to reply to emails when the cursor wouldn't position correctly.

I can get Evolution working fine for email. It connects to the Exchange OWA box (I cannot use the IMAP connector as it apparently just crashes - many posts on this issue I've found.) and can send/recieve emails. I cannot - however - see my calendar.

I get the following errors:
[FONT=Courier New][/FONT]
[COLOR=Blue](evolution:12217): libecal-WARNING **: e-cal.c:320: Unexpected response

** (evolution:12217): WARNING **: couldn't connect to daemon at $GNOME_KEYRING_SOCKET: /tmp/keyring-P5R4Cn/socket: Connection refused

** (evolution:12217): WARNING **: couldn't connect to daemon at $GNOME_KEYRING_SOCKET: /tmp/keyring-P5R4Cn/socket: Connection refused

** (evolution:12217): WARNING **: couldn't connect to daemon at $GNOME_KEYRING_SOCKET: /tmp/keyring-P5R4Cn/socket: Connection refused

** (evolution:12217): WARNING **: couldn't connect to daemon at $GNOME_KEYRING_SOCKET: /tmp/keyring-P5R4Cn/socket: Connection refused

** (evolution:12217): WARNING **: couldn't connect to daemon at $GNOME_KEYRING_SOCKET: /tmp/keyring-P5R4Cn/socket: Connection refused

(evolution:12217): calendar-gui-WARNING **: Unable to load the calendar Unknown error [/COLOR]

Any idea what might be going on?

---

### Post by v3xtra on 2009-05-27
Looking online a bit, here are a couple topics that seem to be the same as you:

[unable to authenticate with Exchange server](http://www.nabble.com/unable-to-authenticate-with-Exchange-server-td18612915.html)

I don't know if it will really help you though, but it is definitely worth a shot?

Just as a heads up though, I also use Evolution and Exchange, although I'm not quite sure what Exchange version it is.  My e-mail, calendar, tasks, and contacts all work perfectly ( even sync with the server, as I sync the server with my mobile phone ).  If you would like something to maybe compare with, let me know.

---

### Post by feronymos on 2009-07-19
Hi, I have the same problem with PerfectReign. I followed the suggestions from the link v3xtra posts, but
the problem remains. More specifically:
1. The configuration is the same as PerfectReign. (Ubuntu 9.04 client, MS Exchange 2003 server)
2. I can have access to Global Access List on the server.
3. I can have access to others Contacts (if they give the appropriate permission to me)
4. I cannot have access to others Calendars (even if they allowed me to do so).
5. The messages I get are the same as PerfectReign.
Additional notes:
The usernames in the Active Directory Network are of the form: <f>.<lastname>
<f> = Initial of first name.
When I created a user in the Active Directory Network with username without dot in, and tried to see its
calendar,  I got the message Access Denied (Or something similar).
How can we enable trace of the messages exchanged between Ubuntu/Evolution and MS Exchange 2003
server? This trace maybe useful.
Thanks in advance,

---

