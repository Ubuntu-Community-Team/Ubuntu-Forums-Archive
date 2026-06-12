---
title: "puppet configuration of security services in ubuntu"
date: 2011-06-30
forum: Desktop Environments
---

### Post by deesto on 2011-06-30
I'm trying to avoid having to migrate my machine to Fedora: it's either learn to clone some existing Puppet manifests from Fedora to Ubuntu, or move back to Fedora.  I'm running into several problems, including parsing errors for rules that work for Fedora and fail for Ubuntu, presumably because the version of libaugeas-ruby is older for Ubuntu (0.3.0) than Fedora (0.4.0).  For Ubuntu, these rules fail with "Could not evaluate: Could not retrieve information from source(s)".  Another one is a failure of augeas to use the 'ins' command to insert a rule into krb5.conf.  I can't think of any good reason for these other than the older versions of the libraries render Puppet unable to parse properly.

At any rate, I was wondering whether anyone has had experience and success controlling security services in Ubuntu (Natty), such as krb5, pam, screensaver locking, etc.  I should be able to hack my way through these, but I keep hitting walls like the evaluation error above.

Thanks!

---

### Post by Dangertux on 2011-06-30
> **deesto said:**
> I'm trying to avoid having to migrate my machine to Fedora: it's either learn to clone some existing Puppet manifests from Fedora to Ubuntu, or move back to Fedora.  I'm running into several problems, including parsing errors for rules that work for Fedora and fail for Ubuntu, presumably because the version of libaugeas-ruby is older for Ubuntu (0.3.0) than Fedora (0.4.0).  For Ubuntu, these rules fail with "Could not evaluate: Could not retrieve information from source(s)".  Another one is a failure of augeas to use the 'ins' command to insert a rule into krb5.conf.  I can't think of any good reason for these other than the older versions of the libraries render Puppet unable to parse properly.

At any rate, I was wondering whether anyone has had experience and success controlling security services in Ubuntu (Natty), such as krb5, pam, screensaver locking, etc.  I should be able to hack my way through these, but I keep hitting walls like the evaluation error above.

Thanks!

I've seen the failure to retrieve information error before ; that one in my case didn't have anything to do with Ruby. 

It was generated because the module directory was not updated to take into account the new client OS in my case CentOS. It requires a subdirectory for each client operating system.

The libaugeas error may be a Ruby thing have you tried installing 0.4.0 manually? 

This might help  
[https://bugs.launchpad.net/ubuntu/+source/libaugeas-ruby/+bug/804031](https://bugs.launchpad.net/ubuntu/+source/libaugeas-ruby/+bug/804031) 


you can also try libaugeas-dev (which is unstable version 0.4.1) but it might solve your problem.

Good luck

---

### Post by deesto on 2011-06-30
> **Dangertux said:**
> 
The libaugeas error may be a Ruby thing have you tried installing 0.4.0 manually? 

This might help  
[https://bugs.launchpad.net/ubuntu/+source/libaugeas-ruby/+bug/804031](https://bugs.launchpad.net/ubuntu/+source/libaugeas-ruby/+bug/804031)
I reported that bug. ;)  Unfortunately the latest PPA for libaugeas-ruby is stuck at 0.3.0 (instead of 0.4.0, which is available for Fedora and which seems to be working for that OS).  The other puppet-related PPAs are at later versions and it has been suggested that the difference between the new versions and libaugeas-ruby at 0.3.0 is responsible for the error (though I'm not 100% sure).

---

### Post by Dangertux on 2011-06-30
> **deesto said:**
> I reported that bug. ;)  Unfortunately the latest PPA for libaugeas-ruby is stuck at 0.3.0 (instead of 0.4.0, which is available for Fedora and which seems to be working for that OS).  The other puppet-related PPAs are at later versions and it has been suggested that the difference between the new versions and libaugeas-ruby at 0.3.0 is responsible for the error (though I'm not 100% sure).

Hey that is you lol...Sorry it's getting toward the end of the week lol. 

did you try the libaugeas-dev package?

---

### Post by deesto on 2011-07-01
> **Dangertux said:**
> Hey that is you lol...Sorry it's getting toward the end of the week lol. 

did you try the libaugeas-dev package?Not a problem. ;)  But I did install libaugeas-dev and it didn't help: same exact errors ("could not evaluate: could not retrieve information from source(s)", "could not evaluate: Error sending command 'ins' with params". I was afraid it wouldn't since it's also version 0.8.0 just as libaugeas0 is.  libaugeas-ruby is the one that seems to be the problem.

Maybe there's another way to do this?  Any successful management manifests for these services in Natty?

Also, I doubt this exists and haven't been able to find it myself, but is there a comparison somewhere of how these services work between Ubuntu and Fedora/RHEL?

---

### Post by deesto on 2011-07-06
Well, my bug was "confirmed", so I guess that's progress. :/

---

### Post by deesto on 2011-07-07
I've been able to work around all issues except the one where Puppet/Augeas/libaugeas-ruby won't insert a Kerberos rule due to "params", the "params" being the required arguments to the Kerberos rule (what to insert, and before what to insert it).  Since this rule works for other OSes, which have a later version of libaugeas-ruby, I have to assume there's a problem with the version of libaugeas-ruby in Ubuntu.  As previously mentioned, I've opened a bug report, and it was "confirmed" a few days ago, so I hope that can be fixed soon.  But I don't know of a work-around in the meanwhile.

In a separate issue: from what I've read, ufw is supposed to be a "simplified" interface to iptables, but that doesn't seem to be completely true: there is no "iptables" file, as the firewall rules seem to be written dynamically into the kernel per the rules in configuration files in various places (/etc/default/ufw, /etc/ufw/*, [/var]/lib/ufw/*).  And these configuration files are different than what you would find in an iptables file, so I don't find it accurate to claim that one interfaces with the other and that the two can coexist.

Anyway ... so the wiki and the server manual seem to focus on command-line administration of the ufw rules.  I would like Puppet to manage these in the form of config files.  What is the correct way to configure ufw this way: to enable it as a service, and to add, say rules to enable TCP access from a subnet and disable it from elsewhere?  Should this go in `before-rules`?

---

### Post by deesto on 2011-07-08
Hmmm ... okay, how about this one: in order for Puppet to control  Kerberos and the PAM stack, one needs to ensure that the Ubuntu package `libpam-krb5` is installed.  Puppet can do this; the problem is that on install, the package opens an interactive window to prompt the user for a default realm.  My first question: why on earth would a package open a CLI prompt at install time, for one configuration line?  Second: is there a way to get Puppet around the prompt?  As it stands, when Puppet tries to install the package, it just drops out with an error because it doesn't know what to do with the prompt.

---

### Post by Dangertux on 2011-07-08
> **deesto said:**
> Hmmm ... okay, how about this one: in order for Puppet to control  Kerberos and the PAM stack, one needs to ensure that the Ubuntu package `libpam-krb5` is installed.  Puppet can do this; the problem is that on install, the package opens an interactive window to prompt the user for a default realm.  My first question: why on earth would a package open a CLI prompt at install time, for one configuration line?  Second: is there a way to get Puppet around the prompt?  As it stands, when Puppet tries to install the package, it just drops out with an error because it doesn't know what to do with the prompt.

does installing the package beforehand help? I know it sounds dumb, but thus is the way of the world sometimes.

If not can you reconfigure after install?

---

### Post by deesto on 2011-07-11
Hi Dangertux,
> **Dangertux said:**
> does installing the package beforehand help? I know it sounds dumb, but thus is the way of the world sometimes.Not dumb at all, but in my case, this whole configuration and management needs to be automated.  If I can't automate everything with Puppet, I'm in trouble.

> If not can you reconfigure after install?No: the automated package installation attempt dies at the point where the package pops into the interactive prompt, so installation fails.

---

