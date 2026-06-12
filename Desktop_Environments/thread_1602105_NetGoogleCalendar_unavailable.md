---
title: "Net::Google::Calendar unavailable"
date: 2010-10-21
forum: Desktop Environments
---

### Post by rfreytag on 2010-10-21
I am getting this error when trying to run a perl script that wants Net::Google::Calendar on Ubuntu 10.04 LTS Desktop.  ...

Can't locate Net/Google/Calendar.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/s\
hare/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) 

...end included text.

I have used Synaptic to install the perl modules: libnet-google-code-perl and (for good measure) libnet-google-authsub-perl.  I have also used cpan to install Net::Google::Calendar.  The error persists (I have definitely restarted the shell).  

Any suggestions most welcome!

---

### Post by HankB on 2011-01-28
Not much help here, huh?

I'm not sure that package includes that module. 

I installed that module 'the perl way' using:

```
sudo perl -MCPAN -e install Net::Google::Calendar
```

I still get that error message. :confused:

Edit: Smashed it.
First install dependencies (using Software Center)
Net/Google/AuthSub
XML/Atom
(Just plug those strings into the Software Center search box and you will see the modules to install.)
Then download the perl module package from [http://search.cpan.org/~simonw/Net-Google-Calendar/](http://search.cpan.org/~simonw/Net-Google-Calendar/)
Unpack some place convenient and follow the directions in the README file.

-hank

---

