---
title: "[SOLVED] Missing X-Spam headers - my last try before I giving up"
date: 2009-01-01
forum: General Help
---

### Post by otx on 2009-01-01
I already presented my problem in the Server Platforms subforum, but nobody was able to solve this.

So, this is my last try before I giving up and start looking for something else.

I have an Intrepid server with working virtual mail accounts. Clamav and Spamassassin are working, everything is just fine, except that I don't have any X-Spam header in my mails. (the X-Virus are there) If I send a test message with the Gtube test string, the mail is scanned and processed by Spamassassin per rules set in the /etc/amavis/conf.d/21-ubuntu_defaults, so I can drop or discard or pass the spams, whatever I want. 

However, whatever I select, there is no X-Spam header in my mails. The only trace I can find that the mail was processed by Spamassassin is in the mail.log, where I can see if the mail was identified as a spam, or is a clean one. I have followed this tutorial, 

[http://doc.ubuntu.com/ubuntu/serverguide/C/mail-filtering.html#amavisd-new-configuration]("http://doc.ubuntu.com/ubuntu/serverguide/C/mail-filtering.html#amavisd-new-configuration")

which is an official documentation, but I have tried others too - the problem was always the same: no X-Spam headers in my mails.

Here are my files, which I think are related to this problem:

**/etc/amavis/conf.d/15-content_filter_mode content:**


```
use strict;

# You can modify this file to re-enable SPAM checking through spamassassin
# and to re-enable antivirus checking.

#
# Default antivirus checking mode
# Uncomment the two lines below to enable it
#

@bypass_virus_checks_maps = (
   \%bypass_virus_checks, \@bypass_virus_checks_acl, \$bypass_virus_checks_re);


#
# Default SPAM checking mode
# Uncomment the two lines below to enable it
#

@bypass_spam_checks_maps = (
   \%bypass_spam_checks, \@bypass_spam_checks_acl, \$bypass_spam_checks_re);

1;  # insure a defined return
```


**/etc/amavis/conf.d/20-debian_defaults**

```
use strict;

# ADMINISTRATORS:
# Debian suggests that any changes you need to do that should never
# be "updated" by the Debian package should be made in another file,
# overriding the settings in this file.
#
# The package will *not* overwrite your settings, but by keeping
# them separate, you will make the task of merging changes on these
# configuration files much simpler...

#   see /usr/share/doc/amavisd-new/examples/amavisd.conf-default for
#       a list of all variables with their defaults;
#   see /usr/share/doc/amavisd-new/examples/amavisd.conf-sample for
#       a traditional-style commented file  
#   [note: the above files were not converted to Debian settings!]
#
#   for more details see documentation in /usr/share/doc/amavisd-new
#   and at http://www.ijs.si/software/amavisd/amavisd-new-docs.html

$QUARANTINEDIR = "$MYHOME/virusmails";
$quarantine_subdir_levels = 1; # enable quarantine dir hashing

$log_recip_templ = undef;    # disable by-recipient level-0 log entries
$DO_SYSLOG = 1;              # log via syslogd (preferred)
$syslog_ident = 'amavis';    # syslog ident tag, prepended to all messages
$syslog_facility = 'mail';
$syslog_priority = 'debug';  # switch to info to drop debug output, etc

$enable_db = 1;              # enable use of BerkeleyDB/libdb (SNMP and nanny)
$enable_global_cache = 1;    # enable use of libdb-based cache if $enable_db=1

$inet_socket_port = 10024;   # default listening socket

$sa_spam_subject_tag = '***SPAM*** ';
$sa_tag_level_deflt  = 2.0;  # add spam info headers if at, or above that level
$sa_tag2_level_deflt = 6.31; # add 'spam detected' headers at that level
$sa_kill_level_deflt = 6.31; # triggers spam evasive actions
$sa_dsn_cutoff_level = 10;   # spam level beyond which a DSN is not sent

$sa_mail_body_size_limit = 200*1024; # don't waste time on SA if mail is larger
$sa_local_tests_only = 0;    # only tests which do not require internet access?

# Quota limits to avoid bombs (like 42.zip)

$MAXLEVELS = 14;
$MAXFILES = 1500;
$MIN_EXPANSION_QUOTA =      100*1024;  # bytes
$MAX_EXPANSION_QUOTA = 300*1024*1024;  # bytes

# You should:
#   Use D_DISCARD to discard data (viruses)
#   Use D_BOUNCE to generate local bounces by amavisd-new
#   Use D_REJECT to generate local or remote bounces by the calling MTA
#   Use D_PASS to deliver the message
#
# Whatever you do, *NEVER* use D_REJECT if you have other MTAs *forwarding*
# mail to your account.  Use D_BOUNCE instead, otherwise you are delegating
# the bounce work to your friendly forwarders, which might not like it at all.
#
# On dual-MTA setups, one can often D_REJECT, as this just makes your own
# MTA generate the bounce message.  Test it first.
#
# Bouncing viruses is stupid, always discard them after you are sure the AV
# is working correctly.  Bouncing real SPAM is also useless, if you cannot
# D_REJECT it (and don't D_REJECT mail coming from your forwarders!).

#$final_virus_destiny      = D_DISCARD;  # (data not lost, see virus quarantine)
#$final_banned_destiny     = D_BOUNCE;   # D_REJECT when front-end MTA
#$final_spam_destiny       = D_PASS;
#$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)

$virus_admin = "postmaster\@$mydomain"; # due to D_DISCARD default

# Set to empty ("") to add no header
$X_HEADER_LINE = "Debian $myproduct_name at $mydomain";

# REMAINING IMPORTANT VARIABLES ARE LISTED HERE BECAUSE OF LONGER ASSIGNMENTS

#
# DO NOT SEND VIRUS NOTIFICATIONS TO OUTSIDE OF YOUR DOMAIN. EVER.
#
# These days, almost all viruses fake the envelope sender and mail headers.
# Therefore, "virus notifications" became nothing but undesired, aggravating
# SPAM.  This holds true even inside one's domain.  We disable them all by
# default, except for the EICAR test pattern.
#

@viruses_that_fake_sender_maps = (new_RE(
  [qr'\bEICAR\b'i => 0],            # av test pattern name
  [qr/.*/ => 1],  # true for everything else
));

@keep_decoded_original_maps = (new_RE(
# qr'^MAIL$',   # retain full original message for virus checking (can be slow)
  qr'^MAIL-UNDECIPHERABLE$', # recheck full mail if it contains undecipherables
  qr'^(ASCII(?! cpio)|text|uuencoded|xxencoded|binhex)'i,
# qr'^Zip archive data',     # don't trust Archive::Zip
));


# for $banned_namepath_re, a new-style of banned table, see amavisd.conf-sample

$banned_filename_re = new_RE(
# qr'^UNDECIPHERABLE$',  # is or contains any undecipherable components

  # block certain double extensions anywhere in the base name
  qr'\.[^./]*\.(exe|vbs|pif|scr|bat|cmd|com|cpl|dll)\.?$'i,

  qr'\{[0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12}\}?'i, # Windows Class ID CLSID, strict

  qr'^application/x-msdownload$'i,                  # block these MIME types
  qr'^application/x-msdos-program$'i,
  qr'^application/hta$'i,

# qr'^application/x-msmetafile$'i,	# Windows Metafile MIME type
# qr'^\.wmf$',				# Windows Metafile file(1) type

# qr'^message/partial$'i, qr'^message/external-body$'i, # rfc2046 MIME types

# [ qr'^\.(Z|gz|bz2)$'           => 0 ],  # allow any in Unix-compressed
# [ qr'^\.(rpm|cpio|tar)$'       => 0 ],  # allow any in Unix-type archives
# [ qr'^\.(zip|rar|arc|arj|zoo)$'=> 0 ],  # allow any within such archives

  qr'.\.(exe|vbs|pif|scr|bat|cmd|com|cpl)$'i, # banned extension - basic
# qr'.\.(ade|adp|app|bas|bat|chm|cmd|com|cpl|crt|emf|exe|fxp|grp|hlp|hta|
#        inf|ins|isp|js|jse|lnk|mda|mdb|mde|mdw|mdt|mdz|msc|msi|msp|mst|
#        ops|pcd|pif|prg|reg|scr|sct|shb|shs|vb|vbe|vbs|
#        wmf|wsc|wsf|wsh)$'ix,  # banned ext - long

# qr'.\.(mim|b64|bhx|hqx|xxe|uu|uue)$'i,  # banned extension - WinZip vulnerab.

  qr'^\.(exe-ms)$',                       # banned file(1) types
# qr'^\.(exe|lha|tnef|cab|dll)$',         # banned file(1) types
);
# See http://support.microsoft.com/default.aspx?scid=kb;EN-US;q262631
# and http://www.cknow.com/vtutor/vtextensions.htm

# DOMAIN KEYS IDENTIFIED MAIL (DKIM)
$enable_dkim_verification = 1;

# ENVELOPE SENDER SOFT-WHITELISTING / SOFT-BLACKLISTING

@score_sender_maps = ({ # a by-recipient hash lookup table,
                        # results from all matching recipient tables are summed

# ## per-recipient personal tables  (NOTE: positive: black, negative: white)
# 'user1@example.com'  => [{'bla-mobile.press@example.com' => 10.0}],
# 'user3@example.com'  => [{'.ebay.com'                 => -3.0}],
# 'user4@example.com'  => [{'cleargreen@cleargreen.com' => -7.0,
#                           '.cleargreen.com'           => -5.0}],

  ## site-wide opinions about senders (the '.' matches any recipient)
  '.' => [  # the _first_ matching sender determines the score boost

   new_RE(  # regexp-type lookup table, just happens to be all soft-blacklist
    [qr'^(bulkmail|offers|cheapbenefits|earnmoney|foryou)@'i         => 5.0],
    [qr'^(greatcasino|investments|lose_weight_today|market\.alert)@'i=> 5.0],
    [qr'^(money2you|MyGreenCard|new\.tld\.registry|opt-out|opt-in)@'i=> 5.0],
    [qr'^(optin|saveonlsmoking2002k|specialoffer|specialoffers)@'i   => 5.0],
    [qr'^(stockalert|stopsnoring|wantsome|workathome|yesitsfree)@'i  => 5.0],
    [qr'^(your_friend|greatoffers)@'i                                => 5.0],
    [qr'^(inkjetplanet|marketopt|MakeMoney)\d*@'i                    => 5.0],
   ),

#  read_hash("/var/amavis/sender_scores_sitewide"),

   { # a hash-type lookup table (associative array)
     'nobody@cert.org'                        => -3.0,
     'cert-advisory@us-cert.gov'              => -3.0,
     'owner-alert@iss.net'                    => -3.0,
     'slashdot@slashdot.org'                  => -3.0,
     'securityfocus.com'                      => -3.0,
     'ntbugtraq@listserv.ntbugtraq.com'       => -3.0,
     'security-alerts@linuxsecurity.com'      => -3.0,
     'mailman-announce-admin@python.org'      => -3.0,
     'amavis-user-admin@lists.sourceforge.net'=> -3.0,
     'amavis-user-bounces@lists.sourceforge.net' => -3.0,
     'spamassassin.apache.org'                => -3.0,
     'notification-return@lists.sophos.com'   => -3.0,
     'owner-postfix-users@postfix.org'        => -3.0,
     'owner-postfix-announce@postfix.org'     => -3.0,
     'owner-sendmail-announce@lists.sendmail.org'   => -3.0,
     'sendmail-announce-request@lists.sendmail.org' => -3.0,
     'donotreply@sendmail.org'                => -3.0,
     'ca+envelope@sendmail.org'               => -3.0,
     'noreply@freshmeat.net'                  => -3.0,
     'owner-technews@postel.acm.org'          => -3.0,
     'ietf-123-owner@loki.ietf.org'           => -3.0,
     'cvs-commits-list-admin@gnome.org'       => -3.0,
     'rt-users-admin@lists.fsck.com'          => -3.0,
     'clp-request@comp.nus.edu.sg'            => -3.0,
     'surveys-errors@lists.nua.ie'            => -3.0,
     'emailnews@genomeweb.com'                => -5.0,
     'yahoo-dev-null@yahoo-inc.com'           => -3.0,
     'returns.groups.yahoo.com'               => -3.0,
     'clusternews@linuxnetworx.com'           => -3.0,
     lc('lvs-users-admin@LinuxVirtualServer.org')    => -3.0,
     lc('owner-textbreakingnews@CNNIMAIL12.CNN.COM') => -5.0,

     # soft-blacklisting (positive score)
     'sender@example.net'                     =>  3.0,
     '.example.net'                           =>  1.0,

   },
  ],  # end of site-wide tables
});

1;  # ensure a defined return
```


**/etc/amavis/conf.d/21-ubuntu_defaults**


```
use strict;

#
# These are Ubuntu specific defaults for amavisd-new configuration
#
# DOMAIN KEYS IDENTIFIED MAIL (DKIM)
$enable_dkim_verification = 1;
# Don't be verbose about sending mail:
@whitelist_sender_acl = qw( .$mydomain );
$final_virus_destiny      = D_DISCARD; # (defaults to D_BOUNCE)
$final_banned_destiny     = D_BOUNCE;  # (defaults to D_BOUNCE)
$final_spam_destiny       = D_PASS;  # (defaults to D_REJECT)
$final_bad_header_destiny = D_PASS;  # (defaults to D_PASS), D_BOUNCE suggested

$warnbannedsender = 1;
$warnbadhsender = 1;
$virus_admin = undef;
$spam_admin = undef;

#------------ Do not modify anything below this line -------------
1;  # insure a defined return
```

**/etc/amavis/conf.d/50-user**

```
use strict;

#
# Place your configuration directives here.  They will override those in
# earlier files.
#
# See /usr/share/doc/amavisd-new/ for documentation and examples of
# the directives you can use in this file
#

#////////////////////////////otx////////////////////////////

$myhostname = 'mail.exampledomain.com';
@local_domains_acl = ( "localhost", "exampledomain.com" );

$log_level = 2;

#------------ Do not modify anything below this line -------------
1;  # ensure a defined return
```


**/etc/spamassassin/local.cf**


```


#dcc
use_dcc 1
dcc_path /usr/bin/dccproc

#pyzor
use_pyzor 1
pyzor_path /usr/bin/pyzor

#razor
use_razor2 1
razor_config /etc/razor/razor-agent.conf

#bayes
use_bayes 1
use_bayes_rules 1
bayes_auto_learn 1
```

**/etc/postfix/master.cf**


```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
		-o content_filter=
        -o receive_override_options=no_header_body_checks
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
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
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
  
smtp-amavis     unix    -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20

127.0.0.1:10025 inet    n       -       -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
```

Any ideas about this? All I want is to pass my mails which are marked as potential spam, and process later based on their headers.

---

### Post by otx on 2009-01-02
OK, I finally figured out this. The above settings works only for the domain itself, not for the virtual domains. If you want spam filtering for all your domains you need this line in the /etc/amavis/conf.d/50-user

```
@local_domains_maps = ( read_hash("/etc/postfix/amavis_domains") );
```

And you need to comment out the 

```
@local_domains_acl
```

Of course you will need to create the above file and insert your domains one by one, but at least this way is working. Maybe there is a more elegant solution (mysql and perl script?), if somebody has a working solution please post it.

---

### Post by Ubunt2u on 2009-03-25
If you want to see SPAM headers/scores on all emails, set 
"sa_tag_level_deflt" to -9999 or something like that

$sa_spam_subject_tag = '***SPAM*** ';
$sa_tag_level_deflt  = 2.0;  # add spam info headers if at, or above that level

This way all mail headers look something like this

X-Spam-Flag: YES
X-Spam-Score: 3.331
X-Spam-Level: ***
X-Spam-Status:Yes, score=3.331 tagged_above=-9999 required=2
     tests=[AWL=-0.147, BAYES_00=-2.599, HTML_MESSAGE=0.001,
     SPF_PASS=-0.001, SUBJ_ALL_CAPS=2.077, URIBL_GREY=4]

---

