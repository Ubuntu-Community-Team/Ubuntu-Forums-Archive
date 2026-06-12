---
title: "Problems with postfix - Am I running a spam relay now?"
date: 2008-05-29
forum: Desktop Environments
---

### Post by mistapotta on 2008-05-29
For the past week I've been having problems both receiveing and sending e-mail from my server.  I've been using Postfix on Ubuntu for almost a year with no major problems until now.

When I send an e-mail this is what I get on my logs 

```

May 29 19:57:55 draal postfix/pickup[20001]: C77A54049: uid=1000 from=<oafdaloaf>
May 29 19:57:55 draal postfix/cleanup[20454]: C77A54049: message-id=<20080530005755.GB20490@draal.texasmath.org>
May 29 19:57:55 draal postfix/qmgr[11600]: C77A54049: from=<oafdaloaf@draal.texasmath.org>, size=441, nrcpt=1 (queue active)
May 29 19:57:56 draal postfix/smtp[20471]: C77A54049: to=<texasmath@gmail.com>, relay=smtp-server.satx.rr.com[75.180.132.33]:25, delay=0.38, delays=0.04/0/0.24/0.1, dsn=5.0.0, status=bounced (host smtp-server.satx.rr.com[75.180.132.33] said: 550 Outbound Mail Refused - See http://help.rr.com/outboundemail (in reply to MAIL FROM command))
May 29 19:57:56 draal postfix/cleanup[20454]: 3BDB1404B: message-id=<20080530005756.3BDB1404B@draal.BABCOM>
May 29 19:57:56 draal postfix/qmgr[11600]: 3BDB1404B: from=<>, size=2326, nrcpt=1 (queue active)
May 29 19:57:56 draal postfix/bounce[20474]: C77A54049: sender non-delivery notification: 3BDB1404B
May 29 19:57:56 draal postfix/qmgr[11600]: C77A54049: removed
May 29 19:57:56 draal postfix/local[20473]: 3BDB1404B: to=<oafdaloaf@draal.texasmath.org>, relay=local, delay=0.04, delays=0.02/0/0/0.02, dsn=2.0.0, status=sent (delivered to command: IFS=' ' && exec /usr/bin/procmail || exit 75 #oafdaloaf)
May 29 19:57:56 draal postfix/qmgr[11600]: 3BDB1404B: removed

```

What alarms me is what follows it in the logs:

```

May 29 19:57:57 draal postfix/smtpd[20450]: connect from unknown[85.206.37.61]
May 29 19:57:57 draal postfix/smtpd[20450]: BCC0D4047: client=unknown[85.206.37.61]
May 29 19:57:58 draal postfix/cleanup[20454]: BCC0D4047: message-id=<000601c8c1f0$03c2f5f6$19deb2b6@ahkgboih>
May 29 19:57:58 draal postfix/qmgr[11600]: BCC0D4047: from=<dnennett@greiner.co.uk>, size=2729, nrcpt=1 (queue active)
May 29 19:57:58 draal spamd[11698]: spamd: connection from localhost [127.0.0.1] at port 52352 
May 29 19:57:58 draal spamd[11698]: spamd: handle_user unable to find user: 'error' 
May 29 19:57:58 draal spamd[11698]: spamd: processing message <000601c8c1f0$03c2f5f6$19deb2b6@ahkgboih> for error:5001 
May 29 19:57:58 draal spamd[11698]: Can't locate Sys/Hostname/Long.pm in @INC (@INC contains: ../lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at /usr/share/perl5/Mail/SPF/Query.pm line 336, <GEN1210> line 87. 
May 29 19:57:58 draal postfix/smtpd[20450]: disconnect from unknown[85.206.37.61]
May 29 19:58:00 draal spamd[11698]: spamd: identified spam (28.5/2.0) for error:5001 in 2.0 seconds, 2685 bytes. 
May 29 19:58:00 draal spamd[11698]: spamd: result: Y 28 - BAYES_99,HTML_40_50,HTML_MESSAGE,RCVD_IN_BL_SPAMCOP_NET,RCVD_IN_XBL,RCVD_NUMERIC_HELO,URIBL_AB_SURBL,URIBL_JP_SURBL,URIBL_OB_SURBL,URIBL_SC_SURBL,URIBL_WS_SURBL scantime=2.0,size=2685,user=error,uid=5001,required_score=2.0,rhost=localhost,raddr=127.0.0.1,rport=52352,mid=<000601c8c1f0$03c2f5f6$19deb2b6@ahkgboih>,bayes=1,autolearn=spam 
May 29 19:58:00 draal spamd[4518]: prefork: child states: II 
May 29 19:58:00 draal postfix/pickup[20001]: 3A087404B: uid=65534 from=<dnennett@greiner.co.uk>
May 29 19:58:00 draal postfix/cleanup[20454]: 3A087404B: message-id=<000601c8c1f0$03c2f5f6$19deb2b6@ahkgboih>
May 29 19:58:00 draal postfix/pipe[20455]: BCC0D4047: to=<oafdaloaf@draal.texasmath.org>, orig_to=<webmaster@texasmath.org>, relay=spamassassin, delay=2.5, delays=0.41/0/0/2.1, dsn=2.0.0, status=sent (delivered via spamassassin service)
May 29 19:58:00 draal postfix/qmgr[11600]: BCC0D4047: removed
May 29 19:58:00 draal postfix/qmgr[11600]: 3A087404B: from=<dnennett@greiner.co.uk>, size=4358, nrcpt=4 (queue active)
May 29 19:58:00 draal postfix/local[20470]: 3A087404B: to=<spam@draal.texasmath.org>, orig_to=<spam>, relay=local, delay=0.08, delays=0.06/0/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
May 29 19:58:00 draal postfix/error[20469]: 3A087404B: to=<-@draal.texasmath.org>, orig_to=<->, relay=none, delay=0.08, delays=0.06/0/0/0.02, dsn=5.1.3, status=bounced (bad address syntax)
May 29 19:58:00 draal postfix/smtp[20471]: 3A087404B: to=<oafdaloaf@draal.texasmath.orgretry>, relay=smtp-server.satx.rr.com[75.180.132.33]:25, delay=0.39, delays=0.06/0/0.23/0.11, dsn=5.0.0, status=bounced (host smtp-server.satx.rr.com[75.180.132.33] said: 550 Outbound Mail Refused - See http://help.rr.com/outboundemail (in reply to MAIL FROM command))
May 29 19:58:01 draal postfix/local[20473]: 3A087404B: to=<unix@draal.texasmath.org>, orig_to=<unix>, relay=local, delay=1.1, delays=0.06/0/0/1.1, dsn=5.1.1, status=bounced (unknown user: "unix")
May 29 19:58:01 draal postfix/cleanup[20454]: 4FCD24049: message-id=<20080530005801.4FCD24049@draal.BABCOM>
May 29 19:58:01 draal postfix/qmgr[11600]: 4FCD24049: from=<>, size=6729, nrcpt=1 (queue active)
May 29 19:58:01 draal postfix/bounce[20472]: 3A087404B: sender non-delivery notification: 4FCD24049
May 29 19:58:01 draal postfix/qmgr[11600]: 3A087404B: removed
May 29 19:58:01 draal postfix/smtp[20471]: 4FCD24049: to=<dnennett@greiner.co.uk>, relay=smtp-server.satx.rr.com[75.180.132.33]:25, delay=0.36, delays=0.02/0/0.23/0.11, dsn=5.0.0, status=bounced (host smtp-server.satx.rr.com[75.180.132.33] said: 550 Outbound Mail Refused - See http://help.rr.com/outboundemail (in reply to MAIL FROM command))
May 29 19:58:01 draal postfix/qmgr[11600]: 4FCD24049: removed

```

Spam makes it in fine (to the spam user) but incoming good email is directed to the spam account as well.  Outgoing mail just gets bounced.

The primary concern that I have a spam relay now is that I get the 550 error, which my ISP says is because I'm generating over a thousand e-mails a day.  For my group's needs, I only need to send about ten a day during the busy season, but I use my domain names to enroll in services to see who's using my accounts for spam (for example, [email]ubuntuforums.org@texasmath.org[/email] is what I used to sign up for this account.)

My main.cf:
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = draal.BABCOM
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
myorigin = /etc/mailname
mydestination = draal.texasmath.org, draal.localdomain, localhost.localdomain, localhost, www.texasmath.org, texasmath.org,  mistapotta.com
relayhost = smtp-server.satx.rr.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

header_checks = regexp:/etc/postfix/header_checks
body_checks = regexp:/etc/postfix/body_checks

```

My master.cf file:
```

#
# Postfix master process configuration file.  For details on the format
# of the file, see the Postfix master(5) manual page.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd -o content_filter=spamassassin
#submission inet n      -       -       -       -       smtpd
#	-o smtpd_etrn_restrictions=reject
#	-o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps    inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
#submission inet n      -       -       -       -       smtpd
#  -o smtpd_etrn_restrictions=reject
#  -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache	  unix	-	-	-	-	1	scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

spamassassin
          unix  -       n       n       -       -       pipe
   flags=Rq user=nobody argv=/home/spam/filter.sh -oi -f ${sender} ${recipient}retry     unix  -       -       -       -       -       error
retry     unix  -       -       n       -       -       error
proxywrite unix -       -       n       -       1       proxymap


```

Any help you can give would be appreciated.  I'm finally at the point where I'm giving finals (as opposed to reviewing my students) and have time to get this solved.  If you need additional files for help, please let me know.

Thanks,
Tony David Potter

---

