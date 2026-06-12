---
title: "clamav and evolution integration"
date: 2004-12-17
forum: Desktop Environments
---

### Post by taygan on 2004-12-17
It seems that there are very few linux viruses.  Of those, most have been rendered obsolete.  The ones that were made could only mess up the files accesible to the user that was exposed.  Since we don't run root, we're pretty darn safe from future viruses, except for ones that my mess up our /home/$USER directory, or viruses that we could pass on to Windows.  I'd like to protect my /home files too :)

With those assumptions, I installed f-prot, a nice, easy, non-GPL command-line scanner.

I wanted a mail scanner, and would prefer a GPL program so I installed ClamAV-0.80 from source using checkinstall for easy removal.  Hmmm, not bad from the command line, couldn't get it going with Evolution.  So then I installed ClamAV-0.80 from hoary (I'm running warty)  things installed great..  config files worked (I added my countries ftp round-robin server to freshclam.conf as the CLamAV folks requested)..  IT now looks like:

DatabaseMirror db.us.clamav.net
DatabaseMirror db.local.clamav.net
DatabaseMirror database.clamav.net


NOTE:  the warty version of ClamAV does not support the round-robin servers that the hoary version does.  ClamAV folks have threatened to blacklist folks overlaoding their servers by running the older versions.


I don't really know how the whole mail system works.. I'm assuming warty runs postfix to procmail to evolution as a default for pop3 mail.  I'd like to come up with an easy way to integrate ClamAV and Evolution.

The howtos I've found on google DO NOT work for me!

What I'd love to get working is this one from within Evolution:
[http://tipps.gnome-de.org/trickkiste/evolution-clamav.php](http://tipps.gnome-de.org/trickkiste/evolution-clamav.php)

I believe it says to create a filter to pipe-to-program /usr/bin/clamscan that returns 1,  When I run this the attached test file is not caught. (I've tried 2 different test attachments), and other returns/do-not-return values catch extra stuff.

Another way is to create a script that calls clamscan:
[http://www.aoe.vt.edu/~lscharf/samd/?topic=Linux&title=Evolution+Virus+Scanning](http://www.aoe.vt.edu/~lscharf/samd/?topic=Linux&title=Evolution+Virus+Scanning)

I can get example 2 working to filter out Windows executables, but example 1 does not register with the test files.

A third way seems obsolete:
[http://www.falkotimme.com/howtos/spamassassin_clamav_procmail/index.php](http://www.falkotimme.com/howtos/spamassassin_clamav_procmail/index.php)

First of all, the config files are out-of-date, the init script isn't needed with the hoary files and I can't find the trashscan program in the clamav files.

Is there a way to interate clamav with Evolution or should I start learning how procmail works?

Thanks

---

### Post by jdong on 2004-12-17
Hmm, 

Note to self: backport Hoary ClamAV to Warty....

---

### Post by taygan on 2004-12-17
Well, I'm looking into other options, but hoping for an easy, robust, non-resource hogging solution..  anyone have good luck with clamassassin or amavis-new?  amavis-new seems to be a pretty robust script, but maybe more than I need as an email client..  Clamassassin seems simple and relatively easy (I hope).  I don't really have experience with anything other that bash scripts..  We'll see how it goes.

Well, after playing around with clamassassin, I can't find .procmailrc config scripts..  How is _spam_assassin connecting to evolution and am I wrong in thinking Ubuntu defaults to postfix>procmail for receiving pop3?

---

### Post by taygan on 2004-12-18
Hmmm, it seems I made a wrong assumption.. Looking at /etc/postfix/main.cf the procmail section is commented out..  So it looks like we use postfix>evolution without a procmail distribution inbetween. 

Fetchmail and procmail are installed but not configured? Anyone know why this is?  Or what details I'm overlooking?

Can I set up ClamAV directly in Evolution or second best?? in Postfix, or should I turn on procmail..

I'm still wondering how the universe spamassassin works without procmail, looks like spamd daemon..  Hmmm, have to check this out more..


I hope someone is helped out by this little conversation I'm having with myself..

---

### Post by taygan on 2004-12-18
it works!

Dunno what I did with the first script, is it important that I was using a .hidden file for a script?

anyway, I found another shell script for evolution to pipe to and it works:

[http://www.togaware.com/linux/survivor/Viruses.shtml](http://www.togaware.com/linux/survivor/Viruses.shtml)

I'll put together a howto in the next day or so.

EDIT:

#@$#% ugh!  it finds EICAR but not the Clam Test files.. dig deeper dig deeper..

---

### Post by taygan on 2004-12-29
well well well,  although it didn't catch the test files (can someone else try this script to make sure it's not my mail server that's complicating things)

It worked!  Caught HTML.Phishing.Pay-1 on a fake paypal email..

f-prot and aegis did not detect this file.. clamav did!

(it's a fake 'phising' email, not a virus per se..)

---

