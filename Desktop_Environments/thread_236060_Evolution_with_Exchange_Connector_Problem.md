---
title: "Evolution with Exchange Connector Problem"
date: 2006-08-14
forum: Desktop Environments
---

### Post by damber on 2006-08-14
I'm having a problem with Evolution connecting to MS Exchange using the exchange connector.  Running kubuntu 6.0.6 and evolution 2.6.1 with exchange connector. 

The issue is that several of the fields for entering the configuration information is missing - this link shows screenshots of what the configuration screens should look like in the exchange section: [http://www.gnome.org/projects/evolution/doc/evolution26.pdf](http://www.gnome.org/projects/evolution/doc/evolution26.pdf) 

However, the screens do not have these fields (only the username field), and there is an entire (exchange specific) tab missing.

From things I've read so far, Evolution's exchange connector has become worse and worse since v2.0 .....

Has anyone found any resolution to this ?  an apt-get tells me I have the latest version available - should I be looking around for any other versioned packages ?  if so, which ?  

Thanks in advance for any help you can provide..

---

### Post by madscientist on 2006-08-22
Sorry for the dumb question, but you DID select "Microsoft Exchange" as the Server Type in the "Receiving Email" tab, right?

The screen you describe sounds a lot to me like you haven't selected the right server type, so it's not showing you the fields related to Exchange.

---

### Post by damber on 2006-08-23
> Sorry for the dumb question, but you DID select "Microsoft Exchange" as the Server Type in the "Receiving Email" tab, right?

<sigh>*Yes*</sigh>

I have recently got this running on my Fedora Core 5 distro, everything appears as it is supposed to.  This is with version 2.6.3 of Evolution now (though I've updated recently - and it worked with the default Evolution install in FC5, whatever version that was) - so maybe the latest release has fixed it - but... shame 2.6.3. isn't (or wasn't a few days ago) available in the repositories via apt-get...  

I'll take another look next week.. if still no joy, then I'll manually update it... :-(

---

### Post by madscientist on 2006-08-23
Sorry; I said it was a dumb question but it had to be asked.

I'm using Ubuntu 6.06.1 and Evo Connector works just fine for me: I was able to add an account, set the server type to exchange, and I saw the username field (where I entered WORKGROUP\username) and server field (where I entered the URL of the OWA server, without the /exchange extension... so something like [http://webmail.mydomain.com)](http://webmail.mydomain.com)).  It connected and worked fine.  It's possible this is a problem with using Evolution in KDE instead of Gnome...?  The one problem I have seen is that there's no tab I can find to set the outgoing mail parameters.  Various docs mention one but there isn't one anywhere that I can see.

Although Evo (and esp. Connector) is probably the worst quality of all official Gnome apps, I think it's been getting steadily better... although with very serious backwards steps here and there.  In 2.2 or so, for example, they completely broke the ability to use a workgroup name when you log in.  Etc.  I've debugged these and submitted patches: the fix was not hard, but really... that kind of thing should never get released.

I've been using Evo 2.6.1, albiet somewhat gingerly, for a few weeks now and I haven't had any crashes.  There are only a few minor nits (for example, one of my meetings doesn't show up--but the rest do).  Overall I'd say this version is by far the most stable and featureful Evo I've used (including the older 1.4 releases).  FWIW.

---

