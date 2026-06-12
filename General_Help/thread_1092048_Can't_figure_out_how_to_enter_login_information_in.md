---
title: "Can't figure out how to enter login information in Pan"
date: 2009-03-10
forum: General Help
---

### Post by Pfredpfudpucker on 2009-03-10
I installed Ubuntu a few weeks ago, and finally got around to setting up the newsreader.  After installing, I opened Pan and looked around for preferences so that I could enter the information for my provider.  No place to do that, so I poked around in the help menu and ended up at the Pan Rebel site, that informed me that a user manual was under construction....?

So, I Googled and found a site that said that when Pan was first opened, a setup wizard would open.  Didn't happen.  Soooo, I uninstalled Pan and reinstalled it.  Still didn't happen.  Seems ubuntu retains files even when the application that created them is uninstalled.

Does anyone know how a mindless twit like myself can access the setup wizard, or the menu in Pan that lets one put in the proper particulars needed to get Pan up and running?

I would appreciate the help.

---

### Post by stanz on 2009-03-10
> **Pfredpfudpucker said:**
>  ubuntu retains files even when the application that created them is uninstalled.

for sure!
I don't know this program--but to try to give a hand...
you installed/uninstalled thru synaptic package manager?
did you need root priv's to do this?
in a terminal..try "sudo pan" to run it as root--maybe bringing on
that wizard.

somewhere, there's a pan folder with that wizard script in it!

---

### Post by stanz on 2009-03-10
For my curiosity...I installed pan on my sandbox and my first startup gave
me a welcome and request for a server.
might this be the wizard??

---

### Post by oldos2er on 2009-03-10
Don't run 'sudo pan.'

 Pan can't do much unless you point it to a newsserver and create and account. Under the Edit menu you'll find 'Edit newsservers,' 'Edit profiles,' etc.

---

### Post by dcstar on 2009-03-11
> **oldos2er said:**
> Don't run 'sudo pan.'

 Pan can't do much unless you point it to a newsserver and create and account. Under the Edit menu you'll find 'Edit newsservers,' 'Edit profiles,' etc.

And for those of you who don't like the "Beta" PAN in the repositories (like me), you can still manually download and install the old version .deb package from:

[http://packages.ubuntu.com/dapper/pan](http://packages.ubuntu.com/dapper/pan)

But hurry, once Dapper goes unsupported then the files will to!

---

### Post by Pfredpfudpucker on 2009-03-14
Aha!  The answer was right under my mouse.  I was poking around in preferences, and discovered that when I hit add new newsgroup the box came up to allow me to enter the information on the newsgroup.  

I also discovered that the information provided by the newsgroup account setup was somewhat cryptic.  It indicated that the newsgroup name should be something other than news.xxxxx.news.  Ain't so.

---

### Post by stanz on 2009-03-15
> **oldos2er said:**
> Don't run 'sudo pan.'

 Pan can't do much unless you point it to a newsserver and create and account. Under the Edit menu you'll find 'Edit newsservers,' 'Edit profiles,' etc.

...er, ok then...

---

