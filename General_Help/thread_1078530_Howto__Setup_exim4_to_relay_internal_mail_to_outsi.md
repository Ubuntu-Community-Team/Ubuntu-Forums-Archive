---
title: "Howto:  Setup exim4 to relay internal mail to outside address (Rogers highspeed)"
date: 2009-02-23
forum: General Help
---

### Post by sadohert on 2009-02-23
Here's the context.  My Ubuntu Gutsy machine is simply a personal-use computer.  I don't have any production servers I depend on outside of OpenSSH (and I'm the only one who cares).  I've had [logwatch]("http://www.logwatch.org/") running since I first built the system last April since it was my first forray into 100% Linux, and I wanted to know if anything bad or funny was happening on my system.  I installed [DenyHosts]("http://denyhosts.sourceforge.net/") because I'm a bit paranoid that the evil hackers will somehow get into my box and... umm.... steal pictures of my dog.  Actually, logwatch had all kinds of stuff showing me different attempts being made on my box to log in using a variety of common user names.  Denyhosts is awesome for blacklisting these hosts based on a number of statistics.

UNFortunately, these systems are configured to send their information to the local root user.  It wasn't a big deal to forward the local root user to my own personal user, but it still came in the form of an "mbox" file, that I was reading with the "mail" program, which wasn't the most fun.  I'm all over becoming a command line ninja for whatever I can, but that mail program is WAY too archaic.  I tried configuring alpine/pine to read it, and I think I got that working once, but that still stunk too.  Ultimately I wanted these logs sent to my personal email address that I could auto-filter so I have the messages in a nice gui mail client to review anytime.

SO, I set out on the problem.  Apologies for the wordy-ness... I have the "verbose" option set on by default ;).

Here, let me try to turn it off for a while:

-I needed a way to send mail off my box to the outside world.  A local smtp server setup to relay to a "smarthost" could do this for me.
-I decided to go with exim4 for the server.  My "smarthost" is my ISP here in Canada (Rogers).  At first it may seem like this would be pretty straightforward.  I have an email account I can setup with Rogers, where I have a username and passwd and pop and smtp hostnames I just point my client to, so it should be fairly straightforward to just point exim4 at Rogers, setup the passwords correctly, and boom... good to go.  I was way off the mark on this assumption, and spent a bunch of time chasing down little things to get this solved.

I'll try to spare people the annoying details now, and just list how I got around the tricky parts.  This might be mostly relevant to Rogers customers, or customers of ISPs who do things similarly.

I should probably note that most of this stuff should be done using "sudo".

1.  Install exim4
```
sudo aptitude install exim4
```

When the install is done you should end up in the dpkg-configure thing.  If you were never asked any configuration information you can type:
```
sudo dkpg-reconfigure exim-config
```

The options I used were:
-mail sent by smarthost; received via SMTP or fetchmail
-<your box hostname> (this was filled in already, I just accepted the default)
-127.0.0.1 (this was also filled in.. I just left this as is)
-<your box hostname> (again, this was filled in already, I just accepted the default)
-left the next field blank
-smtp.broadband.rogers.com (the smtp server provided by my ISP)
-I said no (the default)
-I said no (the default) for DNS lookups
-I chose the mbox format.  Don't really know why.
-I chose the "unsplit" config file option (the defaults)

If anyone needs me to explain the options I've referring to please pipe up.

2.  Enable plain text authorization.  Rogers needs authorization to happen over an unsecure connection, so this had to be done.  Create (or edit) the file /etc/exim4/exim4.conf.localmacros and add the following line to it, and save:
```
AUTH_CLIENT_ALLOW_NOTLS_PASSWORDS = true
```

3.  Setup the password for the outgoing mail account you're using by editing the file /etc/exim4/passwd.client.  Mine looks like this:
```
# password file used when the local exim is authenticating to a remote
# host as a client.
#
# see exim4_passwd_client(5) for more documentation
#
# Example:
### target.mail.server.example:login:password
smtp.broadband.rogers.com:<my rogers email account userid>:<my acct password>
ssmtp.bloor.is.net.cable.rogers.com:<my rogers email account userid>:<my acct password>
smtp-rog.mail.yahoo.com:<my rogers email account userid>:<my acct password>
```

The reason I have all 3 lines in there is that exim4 takes the smtp hostname, looks up the IP address, then does a reverse look up to see the hostname matched to that IP, so if your ISP uses aliases to the same IP, then you'll need entries for these aliases.  I might only really need the last one, but I put them all in in case.  The Rogers userid does NOT include the "@rogers.com" part.

4.  The reason for this step is that Rogers implemented a system to help with security where they will only relay mail from authorized/validated email addresses.  So this prevents me from just sending my logs out from the address root@myhostname (unless I were to actually set up a server to receive mail from the outside world at that address, which I didn't care to do).  SOO, I happened to want to relay the mail from my gmail account (the same account I'm sending to... I think I'm going to change this).  I had to go to the rogers yahoo web portal for my rogers email address and add an account and do the typical email verification step.  The instructions for this were here:
[Rogers E-mail Security Enhancements]("http://www.rogershelp.com/yahoo/article.php?id=10H-F")

5.  Next, I needed to make the email coming off my box appear like it was from this "validated" email address.  So I edited the file /etc/email-addresses to look like this:
```
# This is /etc/email-addresses. It is part of the exim package
#
# This file contains email addresses to use for outgoing mail. Any local
# part not in here will be qualified by the system domain as normal.
#
# It should contain lines of the form:
#
#user: someone@isp.com
#otheruser: someoneelse@anotherisp.com
<my local user>: me@gmail.com
root: me@gmail.com
```

6.  Finally, re-process the exim4 config, and restart the server:
```
sudo update-exim4.conf
sudo /etc/init.d/exim4 restart

```
7.  Try sending a test email using sendmail:
```
$sendmail root <enter>
Subject: test subject <enter>
test message <enter>
.<enter>
```
The dot "." at the end, followed by "enter" completes the interaction with sendmail.

8.  For debugging info take a look at  /var/log/exim4/mainlog... I like to use tail -f to see the log update:
```
sudo tail -f  /var/log/exim4/mainlog
```


So, that's about it.  I found most of the answers online except:
-The part about needing to use all the hostnames in the password file
-The part about needing to explicitly setup the email address with Rogers.

---

### Post by pkloves on 2009-07-01
Thanks for the howto!  I thought I had all of the steps correct, and it was nice to have some validation.

I should point out, however, that I needed to include my whole email address form of my account for my AT&T DSL for sbcglobal.net:

```
smtp.sbcglobal.yahoo.com:<me>@sbcglobal.net:<password>
smtp.sbc.mail.fy4.b.yahoo.com:<me>@sbcglobal.net:<password>
```

Also, I used the broken-up form of the exim files, which required that I create a macro file in /etc/exim4/conf.d/main, which I named 000_localmacros per the readme file.

Thanks again!

---

### Post by bedge on 2009-08-29
Using this config, all email sent via this relay has the "from" addr changed to the address of the gmail account being used for the relaying.

Is it possible to change this setup such that other hosts can use this exim instance as a relay and retain the original from addresses?
ie: not have gmail change the from to that of the account being used for the relay?

Thanks

-Bruce

---

### Post by sadohert on 2009-08-31
Hey Bruce,
  I'm not too sure about this.  I don't know if I myself could pull this off with the way my provider does their security.  I could not get the emails to go through unless the "From" address was actually the address of the account I had with Rogers, so I don't know how you'd get around this if your provider does things the same way.

Stu

---

