---
title: "GAIM for MSN Messenger through authenticated proxies"
date: 2007-05-30
forum: Desktop Environments
---

### Post by BevanFindlay on 2007-05-30
Hi all,
Setting up some machines to work for students on our College network here, where we have an authenticated HTTP proxy server and a "default-deny" firewall (which is also a NAT router).  I managed to get most things working, but GAIM refuses to connect to MSN Messenger no matter whether I tell it to use the proxy or not, or use the HTTP method or not.

MSN Messenger on our Windows boxes occasionally has problems itself, but we seem to be able to get these to work once we infom it of the proxy server (and get it to test the connection a couple of times - I don't know either).

The standard port for MSN (1863) is opened specifically out the firewall.

Has anyone ever encountered something like this, or do you know of some possible fixes?  Is there any changes that can be made to GAIM to get this sort of situation to work?

(I tried aMSN on a KDE box too and couldn't get that to work either - same sorts of problems).

P.S: Ubuntu Feisty running Gnome on some reasonably old hardware.  We are also going to be setting the machines up to log on to a Windows Active Directory domain using Winbind, so I may soon be asking how to get these settings to be applied to all users too.

Thanks! :)

---

### Post by FuturePilot on 2007-05-30
Have you tried fooling around with the Network settings in Gaim? Tools>Preferences>Network. There's some stuff in there to set up a proxy.

---

### Post by BevanFindlay on 2007-05-30
Yes, I have.  I figured that would be the obvious place to go (being that it's basically what I have to do with MSN Messenger in Windows).

I think there is something in the whole situation of being behind a default-deny firewall and authenticated proxy, so it might be a bit complex.  I am interested to know if anyone else has had a similar experience and might know how to get it to work.

One possible thought: could it be something to do with needing to change the server it is trying to connect to or something?  Would trying something at live.com work, or is MS still using the Hotmail servers for MSN Messenger?

By the way, thanks for the prompt reply! :cool:

---

### Post by asipi on 2007-06-01
gaim authenticated proxy feature sucks, I have spent a lot of time to get it work from every aspect... but with less success :(
I recommend from KDE the Kopete, MSN works with it (GTalk does not :( because of the proxy). I did not try Pidgin what is the new name of Gaim, maybe in the new version it is fixed. Give it a try and good luck! :)

Post your results if you succeed.

---

### Post by BevanFindlay on 2007-06-13
Hi,
Thanks for the suggestion - Kopete worked under KDE without too much issue, however the machines I am setting up are using Gnome, and while Kopete installed fine in Gnome, it still won't connect.

If I set that machine to be allowed straight out the firewall, it works.  Interestingly, if once it is connected I then lock down its access again, it continues to work (I can still message etc).  So, it appears to only break the signing in processes.

I ran TCPView (Google "Sysinternals") on MSN Messenger on my Windows box and saw it was hitting our proxy on 8080 (as expected), a couple of *.live.com servers on 1863 (also expected) an unnamed server in Redmond on 7001, but allowing that port out still didn't have any effect.  I have tried fiddling with the universal proxy settings in Gnome (with and without it set there and with and without the username+password).

I guess if it comes down to it, I could just use KDE instead, though I do prefer Gnome.

Any help would be appreciated.  I am happy to test things for you all if you get any suggestions (or even want to beta-test some things ;))

Cheers,
  - Bevan F.

---

### Post by BevanFindlay on 2007-06-13
Followup: Pidgin seemed to (not) work exactly the same as Gaim. :(

---

### Post by asipi on 2007-06-13
sorry I mixed the things, Kopete is not working with authenticated proxy, but works with ordinary proxy without authentication... :( sorry again. I've just now installed Kubuntu onto my machine at workplace, and tried to use the chat progs. Here what I found:

- Kopete handling the proxy authentication through KDE proxy settings and it could be buggy, because I could not make it to come alive :( I've found an info that this will be solved in KDE 4.0 so we should wait for it
- Gaim worked, but I tried also Pidgin and using it without problems for MSN and with some trick to GTalk. Only I have set the proxy type in Pidgin settings - network tab, also the proxy user&pass and it is working. For GTalk the trick was to set using the old SSL function and the connection port to 443. Also I did not set the Gnome overall proxy settings because apt-get and synaptic did not recognize it well.

So good luck!
Hope I could help.

---

### Post by BevanFindlay on 2007-06-13
Well, I have not been able to get any of the messengers to work under Gnome without bypassing the proxy and letting them out the firewall directly.  :(

But, Kopete and aMSN both work under KDE (Kubuntu).  I am testing the two window managers on two separate machines, so it is possible that something else is different (reasonably likely actually, though they are both running 7.04 versions).

Anyway, I think I should be fine to use Kubuntu instead.  It just means re-doing a few of the things I already did.  (And now I have to try and remember why it was I decided to go with Gnome not KDE...  it might have been stability, though I don't know).

Thanks for your help all the same!  If I can get the setup working as I want in Kubuntu then I guess it doesn't matter about Gnome too much... but then again I can see this coming back to bite me later on... :???:
Cheers,
  - Bevan F.

---

### Post by asipi on 2007-06-14
Could you tell me what proxy settings you use under kde for kopete?
I am unable to connect with kopete, but I prefer to use that if could.

---

### Post by BevanFindlay on 2007-06-17
I haven't set it to use proxies, though I do have proxies set up in the KDE System Settings.
Dunno if this helps any...?  :???:

---

### Post by asipi on 2007-06-18
yes I pointed to that KDE proxy settings 'cause kopete does not have own...
but my kde proxy sucks, I could not connect with 9 progs of 10 to anywhere (kde progs)
while under windows the proxy handling is perfect...

---

### Post by BevanFindlay on 2007-06-18
Hmm...  Not sure then.  I do know that authenticated proxies are not supported in a lot of software - I often find things on Windows that need to connect to the internet for some reason (usually product activation... sigh) that do not work through an authenticated proxy.  It is getting better now, but still something I run into reasonably often.  I think though that the MSN Messenger/Windows Live Messenger way of doing things changed around version 7.0 or so, such that it is now really flaky when working through a proxy and firewall - sometimes it works, sometimes it doesn't, sometimes you have to put the username and password in, sometimes even that doesn't fix it.  So, I guess I'm not too surprised that the Linux messenger clients struggle, though I really do not see why.

Let me know if you ever get any success.  It seems strange that you can get it working in Gnome and not KDE and I can get it working in KDE and not Gnome...  Could it be that different (authenticated) proxies handle it differently?

---

